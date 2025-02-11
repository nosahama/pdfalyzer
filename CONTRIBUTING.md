Contributions are welcome, just make sure that before you open a pull request:

1. The test suite passes (run by typing `pytest`)
1. You add a description of your changes to [the changelog](CHANGELOG.md)

If your pull request includes some `pytest` setup/unit testing you'll be my new favorite person.

# Development Environment Setup
1. `git clone https://github.com/michelcrypt4d4mus/pdfalyzer.git`
1. `cd pdfalyzer`

After that there's a forking path depending on whether or not you use [poetry](https://python-poetry.org) to manage your python lifestyle.

Note that the minimum versions for each package were chosen because that's what worked on my machine and not because that version had some critical bug fix or feature so it's entirely possible that using earlier versions than are specified in [pyproject.toml](pyproject.toml) or [requirements.txt](requirements.txt) will work just fine. Feel free to experiment if there's some kind of version conflict for you.

#### With Python Poetry
These commands are the `poetry` equivalent of the traditional virtualenv installation followed by `source venv/bin/activate` but there's a lot of ways to run a python script in a virtualenv with `poetry` so you do you if you prefer another approach.

```sh
poetry install
source $(poetry env info --path)/bin/activate
```

#### With A Manual `venv`
```sh
python -m venv .venv              # Create a virtualenv in .venv
. .venv/bin/activate              # Activate the virtualenv
pip install -r requirements.txt   # Install packages
```

Note that I'm not sure exactly how to get the `pdfalyze` command installed when developing outside of a `poetry` env, but creating a simple `run_pdfalyzer.py` file with these contents would do the same thing:

```python
from pdfalyzer import pdfalyzer
pdfalyzer()
```


# Testing
Run all tests by typing `pytest`. Test coverage is relatively spartan but should throw failures if you really mess something up. See [How To Invoke pytest](https://docs.pytest.org/en/7.1.x/how-to/usage.html) official docs for other options.

```bash
# include slow tests:
pytest -v --slow

# only slow tests:
pytest -m slow --slow:
```
