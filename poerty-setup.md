# 🚀 Poetry Setup & Dependency Installation Guide

This guide covers how to correctly set up **Poetry**, install dependencies, and resolve common issues related to virtual environments and package installations.

---

## **1️⃣ Setting Up Poetry in Your Project**

### **📌 Ensure Poetry is Installed**
Check if Poetry is installed by running:
```sh
poetry --version
```
If not installed, install it using:
```sh
curl -sSL https://install.python-poetry.org | python3 -
```
On Windows, use PowerShell:
```powershell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | python3 -
```

After installation, restart your terminal.

---

## **2️⃣ Configuring Poetry for a Local Virtual Environment**
By default, Poetry creates virtual environments in a global cache directory. To create it inside the project folder, run:
```sh
poetry config virtualenvs.in-project true
```
Now, remove the existing virtual environment:
```sh
poetry env remove python
```
And recreate it:
```sh
poetry install
```
This will create a `.venv` folder inside your project.

To activate the virtual environment manually (if needed):
```sh
.venv\Scripts\activate  # Windows
source .venv/bin/activate  # macOS/Linux
```

---

## **3️⃣ Correcting `pyproject.toml` for Dependency Management**
Edit your `pyproject.toml` file to properly define dependencies:

```toml
[project]
name = "web_crawler"
version = "0.1.0"
description = "Just a Learning Project"
authors = [{name = "Yogesh Singh", email = "yogeshsingh0286@gmail.com"}]
readme = "README.md"
requires-python = ">=3.12,<4.0"  # Ensure compatibility

dependencies = []

[tool.poetry]
package-mode = false
name = "web_crawler"
version = "0.1.0"
description = "Just a Learning Project"
authors = ["Yogesh Singh <yogeshsingh0286@gmail.com>"]

[tool.poetry.dependencies]
python = ">=3.12,<4.0"
crawl4ai = "^0.4.248"   # Add required dependency

[build-system]
requires = ["poetry-core>=2.0.0,<3.0.0"]
build-backend = "poetry.core.masonry.api"
```

Now, **re-run the following commands:**
```sh
poetry lock
poetry install
```

---

## **4️⃣ Installing and Checking Dependencies**
To install dependencies (e.g., `crawl4ai`):
```sh
poetry add crawl4ai
```
To verify the installed packages:
```sh
poetry show crawl4ai
```

If you need to install all dependencies from `pyproject.toml`, use:
```sh
poetry install
```

---

## **5️⃣ Running Your Script**
Finally, try running your script:
```sh
python main.py
```
If you still get `ModuleNotFoundError: No module named 'crawl4ai'`, ensure that you're running Python from the correct environment:
```sh
poetry run python main.py
```

---

## **🎯 Summary of Fixes Applied**
✔ Configured Poetry to use **local virtual environments**
✔ Fixed `pyproject.toml` by **restricting Python version**
✔ Installed **dependencies correctly**
✔ Ensured Python runs from the correct virtual environment

🚀 **Let me know which solution worked for you, and update this document for future reference!**

