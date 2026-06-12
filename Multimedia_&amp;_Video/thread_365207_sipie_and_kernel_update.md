---
title: "sipie and kernel update"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by myname on 2007-02-19
Hello all,

I got an update on my kubuntu box at work this past friday which had me reboot, no biggie.  When I booted to a no GUI, I realized that it must have been a kernel and re-installed the video drivers.

However, now when I try to run Sipie (for sirius radio), I am getting the following:

> ~$ sipie
Traceback (most recent call last):
  File "/usr/bin/sipie", line 890, in ?
    checkForUpdates()
  File "/usr/bin/sipie", line 800, in checkForUpdates
    hd = sipie.geturl('http://eli.criffield.net/sipie/LATESTIS')
  File "/usr/bin/sipie", line 164, in geturl
    handle = urllib2.urlopen(req)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 358, in open
    response = self._open(req, data)
  File "/usr/lib/python2.4/urllib2.py", line 376, in _open
    '_open', req)
  File "/usr/lib/python2.4/urllib2.py", line 337, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.4/urllib2.py", line 1021, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.4/urllib2.py", line 996, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error (-3, 'Temporary failure in name resolution')>


Anyone else getting this?

--Kevin

---

### Post by tomwsmf on 2007-02-20
This thread .. [http://www.ubuntuforums.org/showthread.php?t=284893](http://www.ubuntuforums.org/showthread.php?t=284893) .. has the current quick fix to make it work. Long term though is still anyones guese.

---

### Post by elicriffield on 2007-02-20
Sorry about that, My website was down and that caused sipie to bomb on startup when it checked for an update. 

My website is backup and theres a new version at [http://eli.criffield.net/sipie/sipie](http://eli.criffield.net/sipie/sipie) that doesn't reply on my website to be up.

Eli Criffield

---

### Post by myname on 2007-02-20
You Rock Eli.

Sipie is one of the coolest utilities/pieces of software that I've seen in quite some time.

Keep up the good work.

How do you think the XM/Sirius merger will affect Sipie?

--k

---

### Post by Knewguy on 2007-03-06
I just updated to Feisty and now my Sipie isn't working.

I'm still pretty new to Ubuntu and would like to know how to get Sipie working again.

Thanks for the help.

---

### Post by tipalm73 on 2007-05-25
Website down?

```
Resolving eli.criffield.net... 216.58.238.243
Connecting to eli.criffield.net|216.58.238.243|:80... failed: Connection timed out.
Retrying.

--10:50:10--  http://eli.criffield.net/sipie/sipie
  (try: 2) => `sipie'
Connecting to eli.criffield.net|216.58.238.243|:80... 


```

---

### Post by elicriffield on 2007-05-29
Yeah my server is down. Not sure when its coming back.

Sipie checks my server to see if a new version is available, and to get the playlist. If you commet out the checkForUpdates() around line 925 it will start. And you can turn off playlist in the config by setting popups = False and showplaying = false.


A version with these changes is available at [http://deadspot.com/~eli/sipie/](http://deadspot.com/~eli/sipie/) 

Sipie will be moving to [http://sourceforge.net/projects/sipie](http://sourceforge.net/projects/sipie)
With the next version.

Be sure to check the forums there for updates.

Eli Criffield

---

