---
title: "lastfmsubmitd --configure"
date: 2009-02-04
forum: Multimedia Software
---

### Post by telseth on 2009-02-04
I'm trying to install lastfmsubmitd and am getting this error:

Setting up lastfmsubmitd (0.37-2) ...
Starting Last.fm submission daemon: Traceback (most recent call last):
  File "/usr/bin/lastfmsubmitd", line 346, in <module>
    conf = LsdConfig()
  File "/usr/bin/lastfmsubmitd", line 259, in __init__
    lastfm.config.Config.__init__(self, search=DAEMON_NAME)
TypeError: __init__() got an unexpected keyword argument 'search'
invoke-rc.d: initscript lastfmsubmitd, action "start" failed.
dpkg: error processing lastfmsubmitd (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for python-support ...
Errors were encountered while processing:
 lastfmsubmitd
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone have some insight into it?  I have tried apt-get purge and reinstalled, with the same outcome.

---

### Post by telseth on 2009-02-04
bump

---

### Post by telseth on 2009-02-04
hello?

---

### Post by slosd on 2009-02-08
I have exactly the same problem. The weird thing is that it worked until I removed the package to try the version from [http://www.red-bean.com/decklin/lastfmsubmitd](http://www.red-bean.com/decklin/lastfmsubmitd) but I uninstalled it because I got the error 'lastfmsubmitd: no account info found; exiting'. 
Now when I try to install the package from the repository I get this error:
```
Vorkonfiguration der Pakete ...
/tmp/lastfmsubmitd.config.85621: 19: /usr/lib/lastfmsubmitd/conftool: not found
/tmp/lastfmsubmitd.config.85621: 19: /usr/lib/lastfmsubmitd/conftool: not found
Wähle vormals abgewähltes Paket lastfmsubmitd.
(Lese Datenbank ... 251336 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke lastfmsubmitd (aus .../lastfmsubmitd_0.37-2_all.deb) ...
Wähle vormals abgewähltes Paket python-musicbrainz.
Entpacke python-musicbrainz (aus .../python-musicbrainz_2.1.5-2ubuntu1_all.deb) ...
Verarbeite Trigger für man-db ...
Richte lastfmsubmitd ein (0.37-2) ...
Starting Last.fm submission daemon: Traceback (most recent call last):
  File "/usr/bin/lastfmsubmitd", line 346, in <module>
    conf = LsdConfig()
  File "/usr/bin/lastfmsubmitd", line 259, in __init__
    lastfm.config.Config.__init__(self, search=DAEMON_NAME)
TypeError: __init__() got an unexpected keyword argument 'search'
invoke-rc.d: initscript lastfmsubmitd, action "start" failed.
dpkg: Fehler beim Bearbeiten von lastfmsubmitd (--configure):
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
Richte python-musicbrainz ein (2.1.5-2ubuntu1) ...

Verarbeite Trigger für python-support ...
Fehler traten auf beim Bearbeiten von:
 lastfmsubmitd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by slosd on 2009-02-08
It works now. I just changed the name of one argument in lastfmsubmitd and config.py

/usr/bin/lastfmsubmitd:
before:
```
lastfm.config.Config.__init__(self, **search**=DAEMON_NAME)
```
after:
```
lastfm.config.Config.__init__(self, **name**=DAEMON_NAME)
```

/usr/share/python-support/lastfmsubmitd/lastfm/config.py:
before:
```
    def __init__(self, path=None, **search**=None):
        self.cp = SaneConfParser()
        if path:
            self.cp.read([path])
        elif search:
            self.cp.read([SYS_CONF % **search**, USER_CONF % **search**])
```
after:
```
    def __init__(self, path=None, **name**=None):
        self.cp = SaneConfParser()
        if path:
            self.cp.read([path])
        elif search:
            self.cp.read([SYS_CONF % **name**, USER_CONF % **name**])
```

I'm not really into python and I have no idea why it has problems with an argument "search". However, that fixed the problem for me.

---

### Post by telseth on 2009-02-08
Thanks! I'll try it later.

---

### Post by telseth on 2009-02-08
That worked great! Thanks so much! :)

---

### Post by insyte2 on 2009-02-14
I get the following errors when running lastfmsubmitd and lastmp.

Ive already written my account and mpd settings in /etc/lastfmsubmitd.conf. I have mpd running.

> 
lastfmsubmitd: no account info found; exiting

lastmp: no MPD host specified


what should i do to make it work with mpd? Thanks in advance :)

---

### Post by paulerickson on 2009-03-04
This was frustrating, I just tried a hundred things.
I substituted "search" with "name" as above, finally got the repo version installed.
When I tried running /usr/lib/lastfmsubmitd/lastfmsubmit, I got an ugly permission denied error.
So I just did
```
sudo chmod 777 /usr/lib/lastfmsubmitd/lastfmsubmit
```
maybe a bad fix, but it works for me :)

Hope this helps you.

---

### Post by durand on 2009-03-24
Do you have a config file for lastmp?

```
durand@Deuterium ~> cat /etc/lastmp.conf 
[mpd]
host: localhost
port: 6600
```

If you have a password, add that to the bottom.

---

