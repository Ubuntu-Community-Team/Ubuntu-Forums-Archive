---
title: "Trying to install CATT on Ubuntu 19.10"
date: 2019-11-14
forum: Multimedia Software
---

### Post by michael312 on 2019-11-14
Hello everyone,
I am running Ubuntu 19.10 on a Lenovo IdeaPad L340. It is a fresh install.
I'm trying to set up Chromecast so I can get rid of Xfinity bill

I came across CATT Cast at [https://www.computerhope.com/issues/ch001980.htm](https://www.computerhope.com/issues/ch001980.htm) and I'm installing CATT via terminal. 
I checked python3 and got this output:

mshumer@WMS-IdeaPad-L340:~$ python3 --version
Python 3.7.5rc1

I installed pip and got this:

mshumer@WMS-IdeaPad-L340:~$ sudo apt install python3-pip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3-pip is already the newest version (18.1-5).

Then I attempted to install catt and got this output:

mshumer@WMS-IdeaPad-L340:~$ python3 -m pip install catt
Collecting catt
  Downloading [https://files.pythonhosted.org/packages/45/8c/a6c0df9f5772bb7c18a945e1222fbf9aa1ee5a9ee2c1df5e319a10e43f36/catt-0.10.2-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/45/8c/a6c0df9f5772bb7c18a945e1222fbf9aa1ee5a9ee2c1df5e319a10e43f36/catt-0.10.2-py2.py3-none-any.whl)
Requirement already satisfied: requests>=2.18.4 in /usr/lib/python3/dist-packages (from catt) (2.21.0)
Requirement already satisfied: PyChromecast>=2.4.0 in /usr/lib/python3/dist-packages (from catt) (2.4.0)
Requirement already satisfied: ifaddr>=0.1.4 in /usr/lib/python3/dist-packages (from catt) (0.1.6)
Requirement already satisfied: Click>=5.0 in /usr/lib/python3/dist-packages (from catt) (7.0)
Requirement already satisfied: youtube-dl>=2019.01.24 in /usr/lib/python3/dist-packages (from catt) (2019.9.28)
Collecting casttube>=0.2.0
  Downloading [https://files.pythonhosted.org/packages/31/ef/acf3646cf670d095cf29e1f21b7cfc4eb6f896d6dfe0f7264ed6a624e8c7/casttube-0.2.0-py3-none-any.whl](https://files.pythonhosted.org/packages/31/ef/acf3646cf670d095cf29e1f21b7cfc4eb6f896d6dfe0f7264ed6a624e8c7/casttube-0.2.0-py3-none-any.whl)
Installing collected packages: catt, casttube
ERROR: Could not install packages due to an EnvironmentError: [Errno 13] Permission denied: '/usr/local/lib/python3.7/dist-packages/catt-0.10.2.dist-info'
Consider using the `--user` option or check the permissions.

I checked /usr/local/lib/python3.7/dist-packages/ and there's no folder or file named "catt-0.10.2.dist-info'
I'm guessing the install aborted before that point.
I can't seem to figure out how to use the '--user' option.

Help!

---

### Post by Holger_Gehrke on 2019-11-18
The install aborted because it couldn't create that directory. You'd have to be root (by using 'sudo') to write there. I don't understand why pip wants to install system wide instead of just for the user, but then I usually call it with 'pip3' instead of 'python3 -m pip' and I'm not using 19.10. You might want to give that a try, on my 18.4 it installed (and was removed 30 seconds later because I don't have anything to use it with).
```
pip3 install catt
```
Alternatively you can force a user install (an installation into your $HOME, in '~/.local/bin' for the program and '~/.local/lib' for the various libraries it needs) with ```
python3 -m pip install **--user** catt
```

Holger

---

