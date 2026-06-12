---
title: "Cannot open system settings or change workspaces"
date: 2020-08-27
forum: MINT
---

### Post by andrewkirk on 2020-08-27
This problem has arisen on one of my computers that runs Linux Mint. My understanding is that Mint is mostly based on Ubuntu so I am hoping that an Ubuntu-based solution might be able to fix it.

The computer is a Sony Vaio laptop running desktop Cinnamon on Mint 19.1 Tessa.

I occasionally use multiple workspaces and just the other day noticed that the command I used to use to switch between them - Ctrl-Meta-Left/Right - no longer works. I tried using the mouse and that didn't work either. I then tried to enter Keyboard Settings to reassign keyboard shortcuts for that, and found I could not get into settings at all. When I type Menu > Preferences > Keyboard nothing happens.

I have been coding in python and have installed some IDEs and maybe (can't remember for sure) some python versions not through the distro's inbuilt software channel. I found an internet post with a similar problem arose beacsue python was installed in '/usr/local/bin/python' rather than '/usr/bin/python'. But my python is in the latter, so that doesn't seem to apply. Below are some responses to things I tried.

I hope somebody can help me get back my workspace switching capability and settings panels!

Thank you

```
andrew@andrew:~$ which python
/usr/bin/python
andrew@andrew:~$ python - version
Python 2.7.15+ (default, Nov 27 2018, 23:36:35) 
[GCC 7.3.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> q
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'q' is not defined
>>> exit
Use exit() or Ctrl-D (i.e. EOF) to exit
>>> exit()
andrew@andrew:~$ python --version
Python 2.7.15+
andrew@andrew:~$ ls /usr/local/bin/python*
ls: cannot access '/usr/local/bin/python*': No such file or directory
andrew@andrew:~$ cd /usr/local/bin/
andrew@andrew:/usr/local/bin$ sudo rm python python2
[sudo] password for andrew:       
rm: cannot remove 'python': No such file or directory
rm: cannot remove 'python2': No such file or directory
andrew@andrew:/usr/local/bin$ cinnamon-settings python2
Traceback (most recent call last):
  File "/usr/share/cinnamon/cinnamon-settings/cinnamon-settings.py", line 619, in <module>
    window = MainWindow()
  File "/usr/share/cinnamon/cinnamon-settings/cinnamon-settings.py", line 247, in __init__
    for module in modules:
  File "/usr/share/cinnamon/cinnamon-settings/modules/cs_backgrounds.py", line 5, in <module>
    import imtools
  File "/usr/share/cinnamon/cinnamon-settings/bin/imtools.py", line 623, in <module>
    if Image.VERSION == '1.1.7':
AttributeError: module 'PIL.Image' has no attribute 'VERSION'
andrew@andrew:/usr/local/bin$ cat /etc/issue
```

---

### Post by coffeecat on 2020-08-27
*Thread moved to **Mint** sub-forum. *

---

### Post by TheFu on 2020-08-27
I have no clue about GUI stuff, but never, ever, ever, ever, ever, replace a system tool with one you grab from outside the Canonical repos.
For having multiple python versions installed, use something like pyenv, which don't touch the system python.  The system python, ruby, perl, php, golang and other scripting languages are there for all the code distributed by Canonical and other distro specific teams. That specific version is necessary.

For the specific version of python you need/want for your programming projects, either
[LIST]
[*]use the system python and system available modules
**or**
[*]use a tool like pyenv
[/LIST]

Those are the choices.  There are a few options similar to pyenv - doesn't matter which you use.  Just don't touch the system version of python.

Ok, so ... what can you do about this today? Let's check some stuff on a 20.04 box:
```
$ /usr/bin/[COLOR="#00FF00"]python[/COLOR] --version
Python 2.7.18rc1

$ /usr/bin/[COLOR="#00FF00"]python3[/COLOR] --version
Python 3.8.2

```

So, the fix I'd use is to reinstall both those tools from the repos.
```
sudo apt install --reinstall python python3
```
and see how that goes.

Then you'll need to deal with your local environment for python development.   [https://github.com/pyenv/pyenv](https://github.com/pyenv/pyenv)

Don't manually touch programs in /usr/bin/ until you really understand what's going on.  With scripting interpreters, it is very dangerous to even place those different versions into /usr/local/bin/ ... which is where local versions of system-wide, end-user, programs generally belongs.  For software development stuff, keep that in your HOME.

IMHO.

---

### Post by andrewkirk on 2020-08-31
Thank you for your post and sorry for the delay in replying. I did the reinstall with the command you wrote above. The reinstall completed without error messages, but unfortunately the problem remains.

---

### Post by TheFu on 2020-08-31
> **andrewkirk said:**
> Thank you for your post and sorry for the delay in replying. I did the reinstall with the command you wrote above. The reinstall completed without error messages, but unfortunately the problem remains.

Then I'd reinstall the OS and restore from backups.  Too hard to troubleshoot problems from a distance. The reinstall and restore should be about 30-45 minutes. That's my answer whenever something is broken and I've spent about 30 minutes trying to solve it first. After that - wipe and begin again.

At a minimum,  getting really good at backups, restores and installing a fresh OS are excellent skills to have.  It is sorta like how corporate IT just uses a re-image tool for corporate desktops for pretty much every problem. It is too hard to do anything else and end up with a trustworthy system that works.

Obviously, learn from this and don't do it again.

---

### Post by andrewkirk on 2020-09-01
I'd appreciate any alternatives people can suggest to an OS reinstall which is the 'nuclear option' for me. In my experience, reinstalls take about a day. It may be the hardware I'm using is not so linux-compatible, but I find that when I install linux as OS quite a few programs don't work OOTB, and I have to troubleshoot for ages to get them working. Plus I have to download many GB of additional packages for things like R, Rstudio, LaTeX. And I have to redo all my settings.

---

