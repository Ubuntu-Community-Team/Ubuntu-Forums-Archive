---
title: "miro and mirobridge issues"
date: 2010-09-04
forum: Mythbuntu
---

### Post by davidstoll on 2010-09-04
The new mirobridge concept is cool, but I'm having a few problems with it.

I can't play the miro downloads from a remote frontend.  However, my combo front/backend plays them just fine.  When I say "play them", I mean from the mythtv interface.  I can see the entries, I click the play/select button, I see "Please wait" for about 2 seconds and then it goes back to the listing of recordings in Mythtv.

Also, miro doesn't seem to download automatically.  I have a script in crontab, but it only seems to download if I manually run miro.  I have my feeds to download "auto".  I think part of the problem is that my feeds are paid subscriptions and require a username and password...?  But I guess it doesn't ask me when I manually download the feeds.

Thanks for any help you can provide.

---

### Post by ian dobson on 2010-09-04
Hi,

Do you see anything in your log files (/var/log/mythtv) when you try and play a video. It could be a permissions problem, I'm not sure I don't use miro.

Regards
Ian Dobson

---

### Post by davidstoll on 2010-09-04
> **ian dobson said:**
> Hi,

Do you see anything in your log files (/var/log/mythtv) when you try and play a video. It could be a permissions problem, I'm not sure I don't use miro.

Regards
Ian Dobson

Actually, I did try to 777 them, but no luck... :(

---

### Post by davidstoll on 2010-09-06
Miro creates a symbolic link to the download(s) in the .miro folder.  The name of the link does not necessarily match the name of the download.

What's strange is that some miro downloads do play on my remote frontend (all play on my local frontend/backend).

The only difference I can see between the videos that play and those that don't is that the one's that don't have a "#" character in the name.  This is not the download name, but rather, the symbolic linked name.

Any suggestions?

---

### Post by davidstoll on 2010-09-06
Here is another strange thing...something changed the permissions of the miro log files in ~/.miro/
The permissions of the log files there change to root rw_r__r__, and miro cannot be run by running it form the gui or simply typing "miro" from the command prompt (you get the error below).  If I change the permissions back to my login name and/or 777, I can once again rum the program.  I'm not sure if it's related to my original problem, but I'm not sure...

```
$ miro
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 269, in <module>
    startapp()
  File "/usr/bin/miro.real", line 226, in startapp
    startup(props_to_set)
  File "/usr/bin/miro.real", line 150, in startup
    startup.initialize(parsed_options.theme)
  File "/usr/lib/pymodules/python2.6/miro/startup.py", line 149, in initialize
    setup_logging()
  File "/usr/lib/pymodules/python2.6/miro/plat/utils.py", line 120, in setup_logging
    rotater = logging.handlers.RotatingFileHandler(config.get(prefs.LOG_PATHNAME), mode="w", maxBytes=100000, backupCount=5)
  File "/usr/lib/python2.6/logging/handlers.py", line 107, in __init__
    BaseRotatingHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/handlers.py", line 59, in __init__
    logging.FileHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/__init__.py", line 819, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.6/logging/__init__.py", line 838, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 13] Permission denied: '~/.miro/miro-log'
```

---

### Post by davidstoll on 2010-09-06
Completely removing and purging miro and reinstalling solved the permissions issue.

However, I still have problems playing files on a remote frontend.

It looks like it is related to mythrename.pl (now mythlinks.pl).

I'm going to start another thread because I'm going down a different path.

[http://ubuntuforums.org/showthread.php?t=1569482](http://ubuntuforums.org/showthread.php?t=1569482)

---

