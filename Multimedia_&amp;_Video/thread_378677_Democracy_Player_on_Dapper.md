---
title: "Democracy Player on Dapper"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by Chamith on 2007-03-07
Hi,

I'm trying to install Democracy Player on Ubuntu Dapper.  I followed the advice on the ubuntuguide and I tried downloading directly from their site but I keep on getting an unsolvable dependency error.

I know it works on Edgy - and that an older version worked on Dapper - is there anyway to install this on Dapper anymore?

Thanks,
Chamith

---

### Post by Perfect Storm on 2007-03-07
You could hack the .deb pack dependency so it match dapper or remove it as whole.

Which dependency is unsolved?

---

### Post by Chamith on 2007-03-08
I just realised that I've been using the instructions on the Democracy Player website which is for Edgy.

I downloaded the packages for 0.9.0.2 and installed them manually and everything seems to be working alright.

Thanks.

---

### Post by djieno on 2007-04-05
This worked for my with dapper drake: 

[https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs]("https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs")

I had ** basic development tools** allready installed but if not: ```
sudo apt-get install build-essential
```

```
sudo apt-get install subversion python2.4 libboost-python-dev python2.4-gnome2 python2.4-gnome2-extras python-gnome2-extras-dev python2.4-pyrex python2.4-gtk2 python2.4-glade2 python-gtk2-dev mozilla-dev mozilla-psm libxine-dev gettext libxine-extracodecs libxmu-dev python-pysqlite2
```

download the tar.gz (in my case 0.9.5)
```
wget [ftp://ftp.osuosl.org/pub/pculture.org/democracy/src/Democracy-0.9.5.tar.gz](ftp://ftp.osuosl.org/pub/pculture.org/democracy/src/Democracy-0.9.5.tar.gz)
```

extract and use the console:

```
cd tv/platform/gtk-x11
./run.sh
```

Djie

---

### Post by maubp on 2007-06-15
Did version 0.9.6 work for you? I haven't tried democracy before, but this is failing with some sort of database problem...

After installing lots of dependancies (including the python sqlite bindings) I can get run.sh to do something useful.

After asking me if I want Democracy to start automatically, and if I want it to search for existing movies (which it did), I then get an error pop up:

"An unknown error has occurred while finishing starting up."

And the following at the command prompt, which suggests this is related to opening the database:

...
Version:    0.9.6
Serial:     20070604000
Revision:   unknown
Time:       Fri Jun 15 17:05:57 2007
When:       while finishing starting up

Exception
---------
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 608, in _finishStartup
    database.defaultDatabase.liveStorage = storedatabase.LiveStorage()
  File "/usr/lib/python2.4/site-packages/democracy/storedatabase.py", line 899, in __init__
    self.openDatabase()
  File "/usr/lib/python2.4/site-packages/democracy/storedatabase.py", line 948, in openDatabase
    self.cursor.execute("""CREATE TABLE IF NOT EXISTS dtv_objects(
OperationalError: near "NOT": syntax error

Call stack
----------
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/usr/lib/python2.4/threading.py", line 422, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/python2.4/site-packages/democracy/eventloop.py", line 260, in loop
    event()
  File "/usr/lib/python2.4/site-packages/democracy/eventloop.py", line 117, in processNextIdle
    dc.dispatch()
  File "/usr/lib/python2.4/site-packages/democracy/eventloop.py", line 49, in dispatch
    util.trapCall(when, self.function, *self.args, **self.kwargs)
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 599, in <lambda>
    eventloop.addIdle(lambda :self._finishStartup(gatheredVideos), "Finishing startup")
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 758, in _finishStartup
    util.failedExn("while finishing starting up")
  File "/usr/lib/python2.4/site-packages/democracy/util.py", line 132, in failedExn
    failed(when, withExn = True, **kwargs)

Threads
-------
Current: Event Loop
Active:
- MainThread
- ThreadPool - 0 [Daemon]
- Event Loop
- ThreadPool - 2 [Daemon]
- ThreadPool - 1 [Daemon]

INFO     ----- END OF CRASH REPORT -----

---

