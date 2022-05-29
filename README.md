## Properly Installing Python

##### There’s a good chance that you already have Python on your operating system. If so, you do not need to install or configure anything else to use Python. 
##### Having said that, I would strongly recommend that you install the tools and libraries described in the guides below before you start building Python applications for real-world use. 
##### In particular, you should always install Setuptools, Pip, and Virtualenv — they make it much easier for you to use other third-party Python libraries. 
<br />

### Installing Python 3 on Linux
##### To see which version of Python 3 you have installed, open a command prompt and run

```
python3 --version
```

#### If you are using Ubuntu 22.04 or newer, then you can easily install Python 3.10 with the following commands:

```
sudo apt-get update
sudo apt-get install python3.10
```

#### If you’re using another version of Ubuntu (e.g. the latest LTS release) or you want to use a more current Python, we recommend using the deadsnakes PPA to install Python 3.8:

```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.8
```

#### Working with Python 3
```
$ python3
```

#### This will always launch the Python 3 interpreter.
<br />

### Setuptools & Pip
#### The two most crucial third-party Python packages are setuptools and pip.

#### Once installed, you can download, install and uninstall any compliant Python software product with a single command. It also enables you to add this network installation capability to your own Python software with very little work.

#### To see if pip is installed, open a command prompt and run

```
command -v pip
```
#### To install pip, follow the official pip installation guide - this will automatically install the latest version of setuptools.

##### Note that on some Linux distributions including Ubuntu and Fedora the pip command is meant for Python 2, while the pip3 command is meant for Python 3.

```
command -v pip3
```
However, when using virtual environments (described below), you don’t need to care about that. 
<br />
 
 
 ## Pipenv & Virtual Environments

 ### ☤ Make sure you’ve got Python & pip

#### Before you go any further, make sure you have Python and that it’s available from your command line. You can check this by simply running:

```python3 --version```

#### You should get some output like 3.6.2. If you do not have Python, please install the latest 3.x version from python.org or refer to the Installing Python section of The Hitchhiker’s Guide to Python.


Pipenv: Python Development Workflow for Humans
==============================================

[![image](https://img.shields.io/pypi/v/pipenv.svg)](https://python.org/pypi/pipenv)
[![image](https://img.shields.io/pypi/l/pipenv.svg)](https://python.org/pypi/pipenv)
[![CI](https://github.com/pypa/pipenv/actions/workflows/ci.yaml/badge.svg)](https://github.com/pypa/pipenv/actions/workflows/ci.yaml)
[![image](https://img.shields.io/pypi/pyversions/pipenv.svg)](https://python.org/pypi/pipenv)

------------------------------------------------------------------------

**Pipenv** is a tool that aims to bring the best of all packaging worlds
(bundler, composer, npm, cargo, yarn, etc.) to the Python world.
*Windows is a first-class citizen, in our world.*

It automatically creates and manages a virtualenv for your projects, as
well as adds/removes packages from your `Pipfile` as you
install/uninstall packages. It also generates the ever-important
`Pipfile.lock`, which is used to produce deterministic builds.

![GIF demonstrating Pipenv's usage](https://gist.githubusercontent.com/jlusk/855d611bbcfa2b159839db73d07f6ce9/raw/7f5743401809f7e630ee8ff458faa980e19924a0/pipenv.gif)

The problems that Pipenv seeks to solve are multi-faceted:

-   You no longer need to use `pip` and `virtualenv` separately. They
    work together.
-   Managing a `requirements.txt` file [can be
    problematic](https://kennethreitz.org/essays/2016/02/25/a-better-pip-workflow),
    so Pipenv uses the upcoming `Pipfile` and `Pipfile.lock` instead,
    which is superior for basic use cases.
-   Hashes are used everywhere, always. Security. Automatically expose
    security vulnerabilities.
-   Give you insight into your dependency graph (e.g. `$ pipenv graph`).
-   Streamline development workflow by loading `.env` files.

You can quickly play with Pipenv right in your browser:

[![Try in browser](https://cdn.rawgit.com/rootnroll/library/assets/try.svg)](https://rootnroll.com/d/pipenv/)

Installation
------------

**Pipenv can be installed with Python 3.6 and above.**

If you\'re using Debian Buster+:

    sudo apt install pipenv

Or, if you\'re using Fedora:

    sudo dnf install pipenv

Or, if you\'re using FreeBSD:

    pkg install py36-pipenv

Or, if you\'re using Windows:

    pip install --user pipenv

When none of the above is an option, it is recommended to use [Pipx](https://pypi.org/p/pipx):

    pipx install pipenv

Otherwise, refer to the [documentation](https://pipenv.pypa.io/en/latest/#install-pipenv-today) for instructions.

✨🍰✨

☤ User Testimonials
-------------------

**David Gang**---

:   *This package manager is really awesome. For the first time I know
    exactly what my dependencies are which I installed and what the
    transitive dependencies are. Combined with the fact that installs
    are deterministic, makes this package manager first class, like
    cargo*.

**Justin Myles Holmes**---

:   *Pipenv is finally an abstraction meant to engage the mind instead
    of merely the filesystem.*

☤ Features
----------

-   Enables truly *deterministic builds*, while easily specifying *only
    what you want*.
-   Generates and checks file hashes for locked dependencies.
-   Automatically install required Pythons, if `pyenv` is available.
-   Automatically finds your project home, recursively, by looking for a
    `Pipfile`.
-   Automatically generates a `Pipfile`, if one doesn\'t exist.
-   Automatically creates a virtualenv in a standard location.
-   Automatically adds/removes packages to a `Pipfile` when they are
    un/installed.
-   Automatically loads `.env` files, if they exist.

The main commands are `install`, `uninstall`, and `lock`, which
generates a `Pipfile.lock`. These are intended to replace
`$ pip install` usage, as well as manual virtualenv management (to
activate a virtualenv, run `$ pipenv shell`).

### Basic Concepts

-   A virtualenv will automatically be created, when one doesn\'t exist.
-   When no parameters are passed to `install`, all packages
    `[packages]` specified will be installed.
-   To initialize a virtual environment with system python3, run
    `$ pipenv --three`.
-   Otherwise, whatever virtualenv defaults to will be the default.

### Other Commands

-   `shell` will spawn a shell with the virtualenv activated.
-   `run` will run a given command from the virtualenv, with any
    arguments forwarded (e.g. `$ pipenv run python`).
-   `check` asserts that PEP 508 requirements are being met by the
    current environment.
-   `graph` will print a pretty graph of all your installed
    dependencies.

### Shell Completion

To enable completion in fish, add this to your configuration `~/.config/fish/completions/pipenv.fish`:

    eval (env _PIPENV_COMPLETE=fish_source pipenv)

There is also a [fish plugin](https://github.com/fisherman/pipenv), which will automatically
activate your subshells for you!

Alternatively, with zsh, add this to your configuration `~/.zshrc`:

    eval "$(_PIPENV_COMPLETE=zsh_source pipenv)"

Alternatively, with bash, add this to your configuration `~/.bashrc` or `~/.bash_profile`:

    eval "$(_PIPENV_COMPLETE=bash_source pipenv)"

Magic shell completions are now enabled!

☤ Usage
-------

    $ pipenv
    Usage: pipenv [OPTIONS] COMMAND [ARGS]...

    Options:
      --where          Output project home information.
      --venv           Output virtualenv information.
      --py             Output Python interpreter information.
      --envs           Output Environment Variable options.
      --rm             Remove the virtualenv.
      --bare           Minimal output.
      --man            Display manpage.
      --three          Use Python 3 when creating virtualenv.
      --python TEXT    Specify which version of Python virtualenv should use.
      --site-packages  Enable site-packages for the virtualenv.
      --version        Show the version and exit.
      -h, --help       Show this message and exit.


    Usage Examples:
       Create a new project using Python 3.9, specifically:
       $ pipenv --python 3.9

       Remove project virtualenv (inferred from current directory):
       $ pipenv --rm

       Install all dependencies for a project (including dev):
       $ pipenv install --dev

       Create a lockfile containing pre-releases:
       $ pipenv lock --pre

       Show a graph of your installed dependencies:
       $ pipenv graph

       Check your installed dependencies for security vulnerabilities:
       $ pipenv check

       Install a local setup.py into your virtual environment/Pipfile:
       $ pipenv install -e .

       Use a lower-level pip command:
       $ pipenv run pip freeze

       Generate a requirements.txt file (including dev):
       $ pipenv requirements --dev > requirements.txt

    Commands:
      check         Checks for security vulnerabilities and against PEP 508 markers
                    provided in Pipfile.
      clean         Uninstalls all packages not specified in Pipfile.lock.
      graph         Displays currently–installed dependency graph information.
      install       Installs provided packages and adds them to Pipfile, or (if no
                    packages are given), installs all packages from Pipfile.
      lock          Generates Pipfile.lock.
      open          View a given module in your editor.
      run           Spawns a command installed into the virtualenv.
      scripts       Displays the shortcuts in the (optional) [scripts] section of
                    Pipfile.
      shell         Spawns a shell within the virtualenv.
      sync          Installs all packages specified in Pipfile.lock.
      requirements  Generates a requirements.txt compatible output directly from Pipfile.lock
      uninstall     Un-installs a provided package and removes it from Pipfile.

Locate the project:

    $ pipenv --where
    /Users/kennethreitz/Library/Mobile Documents/com~apple~CloudDocs/repos/kr/pipenv/test

Locate the virtualenv:

    $ pipenv --venv
    /Users/kennethreitz/.local/share/virtualenvs/test-Skyy4vre

Locate the Python interpreter:

    $ pipenv --py
    /Users/kennethreitz/.local/share/virtualenvs/test-Skyy4vre/bin/python

Install packages:

    $ pipenv install
    Creating a virtualenv for this project...
    ...
    No package provided, installing all dependencies.
    Virtualenv location: /Users/kennethreitz/.local/share/virtualenvs/test-EJkjoYts
    Installing dependencies from Pipfile.lock...
    ...

    To activate this project's virtualenv, run the following:
    $ pipenv shell

Installing from git:

You can install packages with pipenv from git and other version control systems using URLs formatted according to the following rule:

    <vcs_type>+<scheme>://<location>/<user_or_organization>/<repository>@<branch_or_tag>#<package_name>

The only optional section is the `@<branch_or_tag>` section.  When using git over SSH, you may use the shorthand vcs and scheme alias `git+git@<location>:<user_or_organization>/<repository>@<branch_or_tag>#<package_name>`. Note that this is translated to `git+ssh://git@<location>` when parsed.

Valid values for `<vcs_type>` include `git`, `bzr`, `svn`, and `hg`.  Valid values for `<scheme>` include `http,`, `https`, `ssh`, and `file`.  In specific cases you also have access to other schemes: `svn` may be combined with `svn` as a scheme, and `bzr` can be combined with `sftp` and `lp`.

Note that it is **strongly recommended** that you install any version-controlled dependencies in editable mode, using `pipenv install -e`, in order to ensure that dependency resolution can be performed with an up to date copy of the repository each time it is performed, and that it includes all known dependencies.

Below is an example usage which installs the git repository located at `https://github.com/requests/requests.git` from tag `v2.19.1` as package name `requests`:

    $ pipenv install -e git+https://github.com/requests/requests.git@v2.19#egg=requests
    Creating a Pipfile for this project...
    Installing -e git+https://github.com/requests/requests.git@v2.19.1#egg=requests...
    [...snipped...]
    Adding -e git+https://github.com/requests/requests.git@v2.19.1#egg=requests to Pipfile's [packages]...
    [...]

You can read more about [pip's implementation of vcs support here](https://pip.pypa.io/en/stable/reference/pip_install/#vcs-support).

Install a dev dependency:

    $ pipenv install pytest --dev
    Installing pytest...
    ...
    Adding pytest to Pipfile's [dev-packages]...

Show a dependency graph:

    $ pipenv graph
    requests==2.18.4
      - certifi [required: >=2017.4.17, installed: 2017.7.27.1]
      - chardet [required: >=3.0.2,<3.1.0, installed: 3.0.4]
      - idna [required: >=2.5,<2.7, installed: 2.6]
      - urllib3 [required: <1.23,>=1.21.1, installed: 1.22]

Generate a lockfile:

    $ pipenv lock
    Assuring all dependencies from Pipfile are installed...
    Locking [dev-packages] dependencies...
    Locking [packages] dependencies...
    Note: your project now has only default [packages] installed.
    To install [dev-packages], run: $ pipenv install --dev

Install all dev dependencies:

    $ pipenv install --dev
    Pipfile found at /Users/kennethreitz/repos/kr/pip2/test/Pipfile. Considering this to be the project home.
    Pipfile.lock out of date, updating...
    Assuring all dependencies from Pipfile are installed...
    Locking [dev-packages] dependencies...
    Locking [packages] dependencies...

Uninstall everything:

    $ pipenv uninstall --all
    No package provided, un-installing all dependencies.
    Found 25 installed package(s), purging...
    ...
    Environment now purged and fresh!

Use the shell:

    $ pipenv shell
    Loading .env environment variables...
    Launching subshell in virtual environment. Type 'exit' or 'Ctrl+D' to return.
    $ ▯

☤ Documentation
---------------

Documentation resides over at [pipenv.pypa.io](https://pipenv.pypa.io/en/latest/).
