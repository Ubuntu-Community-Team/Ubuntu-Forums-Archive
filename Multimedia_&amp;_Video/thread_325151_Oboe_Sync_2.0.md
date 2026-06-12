---
title: "Oboe Sync 2.0"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by rykel on 2006-12-25
Hi,

I would like to use Oboe Sync 2.0 to upload my music to Oboe Locker at mp3tunes.com.

However, I always get Python problems (see below)... and when I try to install the "relevant" Python files, I get TONS of python-this and python-that...
[INDENT]
**$ python run_oboe.py**
Traceback (most recent call last):
  File "/home/rykel/oboe-2.0/oboe_exe.py", line 1, in ?
    import global_imports
  File "/home/rykel/oboe-2.0/global_imports.py", line 7, in ?
    from PyQt4 import Qt, QtCore, QtGui
  File "/usr/lib/python2.4/site-packages/PyQt4/Qt.py", line 4, in ?
    from PyQt4.QtOpenGL import *
ImportError: No module named QtOpenGL[/INDENT]

Do you happen to know how to get Oboe to work with Edgy?

---

### Post by chiefofthejojos on 2006-12-28
All you need is this:

```
sudo apt-get install python-psyco python-imaging python-qt4 python-qt4-gl python-qt4-sql
```

the psyco library is supposedly not required, just recommended, but I installed it anyway.  I'm using oboe sync right now.  I'm so stoked that I will soon finally have my entire collection online!

---

### Post by rykel on 2006-12-29
> **chiefofthejojos said:**
> All you need is this:

```
sudo apt-get install python-psyco python-imaging python-qt4 python-qt4-gl python-qt4-sql
```

the psyco library is supposedly not required, just recommended, but I installed it anyway.  I'm using oboe sync right now.  I'm so stoked that I will soon finally have my entire collection online!


Hi,

I tried your suggestions, but I am stuck... Oboe just does not seem to run...

[INDENT]$** python run_oboe***
Attempting to open package.
Loading package: oboesync2.dei
[/INDENT]

Any ideas?

---

### Post by chiefofthejojos on 2006-12-29
How long have you waited for it to start?  It seems like the program hasn't been optimized too well.  It took at least 30 seconds to load on my mid level machine.

---

### Post by Thenotsowyzewun on 2007-01-01
Didn't work for me either; I'm running Edgy and it gives me this:

> duncan@duncan-laptop:~/Desktop/oboe-2.0$ python run_oboe.py
Traceback (most recent call last):
  File "/home/duncan/Desktop/oboe-2.0/oboe_exe.py", line 1, in <module>
    import global_imports
  File "/home/duncan/Desktop/oboe-2.0/global_imports.py", line 4, in <module>
    import urllib, urllib2, PyQt4, sip, sets, ConfigParser, commands
ImportError: No module named PyQt4

I'm looking for a solution, but not having much luck. Any suggestions welcome!

---

### Post by Thenotsowyzewun on 2007-01-01
I think [this]("http://mats.gmd.de/pipermail/pykde/2004-July/008172.html") indicates that I've got 2 (or more!) copies of Python installed, and that's the problem.
So I did
> whereis python
and got
> python: /usr/bin/python /usr/bin/python2.4 /etc/python /etc/python2.4 /usr/lib/python2.3 /usr/lib/python2.4 /usr/lib/python2.5 /usr/X11R6/bin/python /usr/X11R6/bin/python2.4 /usr/bin/X11/python /usr/bin/X11/python2.4 /usr/local/bin/python2.5 /usr/local/bin/python2.5-config /usr/local/bin/python /usr/local/lib/python2.4 /usr/local/lib/python2.5 /usr/include/python2.4 /usr/include/python2.5 /usr/share/python /usr/share/man/man1/python.1.gz

Hmm, 2.3, 2.4 and 2.5 all get mentioned, that can't be good! I'm going to try and remove one of these copies of Python, never uninstalled anything before!

---

### Post by chiefofthejojos on 2007-01-01
> **Thenotsowyzewun said:**
> Hmm, 2.3, 2.4 and 2.5 all get mentioned, that can't be good! I'm going to try and remove one of these copies of Python, never uninstalled anything before!

Before you uninstall, you may want to try running oboe-sync with the different python versions like "python2.3 run_oboe.py" or "python2.4 run_oboe.py".

---

### Post by Thenotsowyzewun on 2007-01-01
> **chiefofthejojos said:**
> Before you uninstall, you may want to try running oboe-sync with the different python versions like "python2.3 run_oboe.py" or "python2.4 run_oboe.py".

Thanks for the tip! Tried 2.3, 2.4 and 2.5 but I got the same error message, and 2.3 doesn't appear to be installed).
I've posted a thread in the beginner's forum explaining the problem and what i've done so far in the fullest detail, I'll edit it now to show this too.

EDIT: Here's a link to that thread:

[http://ubuntuforums.org/showthread.php?t=329530]("http://ubuntuforums.org/showthread.php?t=329530")

---

### Post by rykel on 2007-01-01
> **chiefofthejojos said:**
> Before you uninstall, you may want to try running oboe-sync with the different python versions like "python2.3 run_oboe.py" or "python2.4 run_oboe.py".

Hey, THANK YOU!!!

I tried python2.4 run_oboe.py and it works... although it took a LONG TIME (1 minute perhaps?) to load... the 2nd attempt onwards to run Oboe is OK...

Sometimes I wonder why Oboe for Linux must be run with python...   = P

I mean, can't we start Oboe from GNOME/KDE instead of the commandline?

Speaking of which, can we create an Oboe menu launcher?

---

### Post by Thenotsowyzewun on 2007-01-02
Sure, the command would be "/path/to/oboe/python2.4 run_oboe.py" I think (check that command on the command line), to add it to the menu go System | Preferences | Menu Layout | Sound & Video, then click the New Item button over on the right and create the item. Not sure if an icon is included though, maybe you could DL mp3tunes.com's logo and use that (presuming you can use a file type over than an icon for an icon, never tried on linux.

Hope that helps :)

My problem isn't solved yet though, haven't got much on here, maybe I should just reformat (I prefer fixing problems properly though).

---

### Post by chiefofthejojos on 2007-01-03
> **Thenotsowyzewun said:**
> Sure, the command would be "/path/to/oboe/python2.4 run_oboe.py" I think 
I believe Thenotsowyzewun means "python2.4 /path/to/oboe/run_oboe.py". ;)

---

### Post by Thenotsowyzewun on 2007-01-05
> **chiefofthejojos said:**
> I believe Thenotsowyzewun means "python2.4 /path/to/oboe/run_oboe.py". ;)

Thanks for that, I just got it working (had to reformat, oh well) and I was just trying to figure out how to add it to my menus since the command I daftly came up with didn't work!!

---

### Post by Buggin on 2007-01-15
I followed the first responders reply about installing the python packages and my oboe 2.0 is working just fine... only took about 10 seconds to load up

working with a 2.0 GHZ intel and 1.5GB ram

---

### Post by Buggin on 2007-01-15
try this

```
which python
```


> **Thenotsowyzewun said:**
> I think [this]("http://mats.gmd.de/pipermail/pykde/2004-July/008172.html") indicates that I've got 2 (or more!) copies of Python installed, and that's the problem.
So I did

and got


Hmm, 2.3, 2.4 and 2.5 all get mentioned, that can't be good! I'm going to try and remove one of these copies of Python, never uninstalled anything before!

---

### Post by rykel on 2007-01-27
Hi friends,

On Edgy, I managed to get Oboe to work properly after installing all the relevant Python files (although it did take a loooong time [3 minutes] before Oboe started its GUI) but now that I am back on Dapper, I cannot get the same results again.

These are the error messages... any help please?

[INDENT]**$ python run_oboe.py**
Traceback (most recent call last):
  File "/home/rykel/oboe-2.0/oboe_exe.py", line 1, in ?
    import global_imports
  File "/home/rykel/oboe-2.0/global_imports.py", line 4, in ?
    import urllib, urllib2, PyQt4, sip, sets, ConfigParser, commands
ImportError: No module named PyQt4

[B]$ sudo apt-get install python-psyco python-imaging python-qt4 python-qt4-gl python-qt4-sql
[/B]Password:

Reading package lists... Done
Building dependency tree... Done
python-imaging is already the newest version.
E: Couldn't find package python-qt4[/INDENT]

---

### Post by go1dfish on 2007-01-29
Hey, this is Alex from the MP3tunes client team.

The lag some of you are experiencing in startup is due to the update check.  Oboe Sync checks for updates when it is started, and this will sometimes cause it to delay a bit when starting.

---

### Post by rykel on 2007-01-30
Hi Alex,

Glad to have you here on Ubuntuforums with us.

Using Oboe Sync on Linux is quite a pain (since we need to come to this particular thread in this particular forum to find out that there is a whole list of python files we have to download BEFORE running Oboe Sync, AND finding that the instructions do NOT work for Dapper, not to mention other versions/distros), so I wonder if Oboe can come as a "complete" program on its own, just like the way it is installed on Windows XP?

If making an Oboe Linux installer is the issue, perhaps your team might like to take a look at the Linux Installer project here --> **[http://www.autopackage.org](http://www.autopackage.org)**. If Oboe comes as a graphical installer with all the necessary files packaged into it like Firefox, Scribus, GAIM etc. which you can find on the project Downloads page, it would be beautiful.

Thanks for making Linux THE choice for people who wants a free operating system.   =)

---

### Post by go1dfish on 2007-02-09
Just wanted to let you guys know we just launched our own forum here: [http://forum.mp3tunes.com/](http://forum.mp3tunes.com/)  and wiki at [http://wiki.mp3tunes.com/](http://wiki.mp3tunes.com/)

See ya there.

---

### Post by sysop on 2007-02-19
I know this doesn't help the original python issues in this thread, but I gave up on trying to make the Oboe 2.0 GUI work with Edgy and just went with the CLI version with a config file. Seems to work great for me.

Here is the MP3Tunes link for more information:
[http://wiki.mp3tunes.com/index.php/Oboe_CLI]("http://wiki.mp3tunes.com/index.php/Oboe_CLI")

---

### Post by rykel on 2007-10-25
Hey pals,

I am already on Gutsy Gibbon and trying to run LockerSync (Oboe 3) but unfortunately, it is NOT working again... 

I installed all the python stuff and well, the LockerSync splash screen does come up, but it simply hangs there... I will try waiting for it for at least 5 minutes and let you guys know if it successfully launches this time.

Why can't we have programs start up smoothly in Linux like in Windows, sometimes I wonder...   : P

---

### Post by SourceV on 2007-10-25
Oboe 3.0 on Gutsy I used the following and it worked:

```

sudo apt-get install python-pysqlite2 python-imaging python-qt4 python-qt4-gl python-qt4-sql python-psyco

```

---

### Post by rykel on 2007-10-25
> **SourceV said:**
> Oboe 3.0 on Gutsy I used the following and it worked:

```

sudo apt-get install python-pysqlite2 python-imaging python-qt4 python-qt4-gl python-qt4-sql python-psyco

```

hey, it works!! the missing file was **python-pysqlite2** apparently...

btw, where did you find this solution? Is this sort of answers readily available on the mp3tunes website/forum?

ps. thanks a million.

---

### Post by 43moon on 2007-11-11
I got it working on a new install.  I just jumped to the end of this post and installed everything that I needed right up front.  Thanks to everyone that worked this one out.  :guitar:

---

### Post by erthian on 2007-11-28
yea, thanks.  that did work.  i couldn't figure it out.

---

### Post by rykel on 2008-05-11
hi guys,

i am now on hardy heron... wat should i install BEFORE i run LockerSync?

thanks for helping!

p/s. could someone at mp3tunes basically please remove the need for these dependencies or package them into the installer? (via autopackage.org)

UPDATE 14 May 2008: I finally found a way to get LockerSync to work on Ubuntu Hardy without 95% of the hassle... I wonder when the devs will stop favoring Windows, Mac and Linspire/CNR with a nice little installer, while the rest of the Linux world has to deal with hunting down extra files and solutions?   :)

[B][INDENT]$ sudo install python-qt4
$ cd oboe-3.0
$ python oboe_exe.py[/INDENT][/B]

Now to create the menu launcher...   :(

UPDATE: In case you wonder why I did not just install using CNR, I did, and it says, "Installation status for this product: This product is not available for your distribution." (see screenshot)

---

