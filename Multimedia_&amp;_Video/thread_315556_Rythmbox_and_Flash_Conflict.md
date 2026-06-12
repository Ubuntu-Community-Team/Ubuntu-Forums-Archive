---
title: "Rythmbox and Flash Conflict"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by DrMilo on 2006-12-09
So if I play tunes in Rythmbox there's no sound on Flash media on YouTube. If I shut down Rythmbox and restart Firefox it works again. If I pause Rythmbox the problem is still there. Also seems to work in reverse.

Flash 9 (Linux), with the new plugin.

Firefox 2.

Rhythmbox 0.9.3.1.

Ubuntu 6.06 Dapper Drake.

Perhaps there's a setting in ALSA to deal with it but I haven't a clue how.

---

### Post by ThrobbingBrain66 on 2006-12-09
You do have an old version of Rhythmbox (newest is 0.9.6), so I'm assuming that's the problem.  Edgy with Flash 9 beta and Rhythmbox 0.9.6 works great.

you can get the latest build for Dapper here
[http://mighmos.org/packages.php](http://mighmos.org/packages.php)

---

### Post by The Iron Curtain on 2006-12-09
Hi. I have the exact same problem, so I'm glad there's an answer :)

However I don't know howto update rhythmbox.

Synaptic lists only the old version (0.9.3.1). I found the sourcecode on [http://www.gnome.org/projects/rhythmbox](http://www.gnome.org/projects/rhythmbox)

Will I have to compile from code or is there a way to update?

---

### Post by DrMilo on 2006-12-09
> **The Iron Curtain said:**
> Hi. I have the exact same problem, so I'm glad there's an answer :)

However I don't know howto update rhythmbox.

Synaptic lists only the old version (0.9.3.1). I found the sourcecode on [http://www.gnome.org/projects/rhythmbox](http://www.gnome.org/projects/rhythmbox)

Will I have to compile from code or is there a way to update?

I found a deb here:

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fr%2Frhythmbox%2Frhythmbox_0.9.6-3_i386.deb&md5sum=9a914060f3e4c0b08ef8c23c29451799&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fr%2Frhythmbox%2Frhythmbox_0.9.6-3_i386.deb&md5sum=9a914060f3e4c0b08ef8c23c29451799&arch=i386&type=main)

but I need a sudo command to install it. Not one that I know.

---

### Post by The Iron Curtain on 2006-12-10
Thank you! I downloaded the deb and when I ran it in the terminal, I got this:

```

dfoer@dfoer-laptop:~/Desktop/Downloads$ sudo dpkg -i rhythmbox_0.9.6-3_i386.deb
Password:
(Reading database ... 108632 files and directories currently installed.)
Preparing to replace rhythmbox 0.9.3.1-0ubuntu9 (using rhythmbox_0.9.6-3_i386.deb) ...
Unpacking replacement rhythmbox ...
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on libatk1.0-0 (>= 1.12.2); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 rhythmbox depends on libavahi-client3 (>= 0.6.13); however:
  Version of libavahi-client3 on system is 0.6.10-0ubuntu3.2.
 rhythmbox depends on libavahi-glib1 (>= 0.6.12); however:
  Version of libavahi-glib1 on system is 0.6.10-0ubuntu3.2.
 rhythmbox depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 rhythmbox depends on libcairo2 (>= 1.2.4); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.
 rhythmbox depends on libdbus-1-3; however:
  Package libdbus-1-3 is not installed.
 rhythmbox depends on libdbus-glib-1-2 (>= 0.71); however:
  Version of libdbus-glib-1-2 on system is 0.60-6ubuntu8.
 rhythmbox depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-1.1ubuntu12.
 rhythmbox depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.2.
 rhythmbox depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 rhythmbox depends on libgnome-keyring0 (>= 0.6.0); however:
  Version of libgnome-keyring0 on system is 0.4.9-1ubuntu1.
 rhythmbox depends on libgnome-media0; however:
  Package libgnome-media0 is not installed.
 rhythmbox depends on libgnutls13 (>= 1.4.0-0); however:
  Package libgnutls13 is not installed.
 rhythmbox depends on libgpg-error0 (>= 1.4); however:
  Version of libgpg-error0 on system is 1.1-4.
 rhythmbox depends on libgstreamer0.10-0 (>= 0.10.10); however:
  Version of libgstreamer0.10-0 on system is 0.10.6-0ubuntu2.
 rhythmbox depends on libmusicbrainz4c2a (>= 2.1.4); however:
  Version of libmusicbrainz4c2a on system is 2.1.2-2ubuntu3.1.
 rhythmbox depends on libpango1.0-0 (>= 1.14.7); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 rhythmbox depends on libpopt0 (>= 1.10); however:
  Version of libpopt0 on system is 1.7-5.
 rhythmbox depends on libsoup2.2-8 (>= 2.2.96); however:
  Version of libsoup2.2-8 on system is 2.2.93-0ubuntu1.
 rhythmbox depends on libtasn1-3 (>= 0.3.4); however:
  Package libtasn1-3 is not installed.
 rhythmbox depends on libtotem-plparser1 (>= 2.16.1); however:
  Version of libtotem-plparser1 on system is 1.4.3-0ubuntu1.
 rhythmbox depends on libxfixes3 (>= 1:4.0.1); however:
  Version of libxfixes3 on system is 1:3.0.1.2-0ubuntu3.
 rhythmbox depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
 rhythmbox depends on python-support (>= 0.2); however:
  Package python-support is not installed.
dpkg: error processing rhythmbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rhythmbox
dfoer@dfoer-laptop:~/Desktop/Downloads$


```

I'm not sure where to start fixing the dependancies...

---

### Post by ThrobbingBrain66 on 2006-12-10
i gave you guys a link to a deb built for dapper in my first post...no need to do the extra work:)

---

### Post by DrMilo on 2006-12-10
> **ThrobbingBrain66 said:**
> i gave you guys a link to a deb built for dapper in my first post...no need to do the extra work:)

Ah I see now! I thought it was something else. Thank you!

---

### Post by DrMilo on 2006-12-10
However the upgraded Rhythmbox doesn't fix it. This is a problem more to do with Flash 9 I think. This only started after I got Flash 9.

---

### Post by The Iron Curtain on 2006-12-11
> **ThrobbingBrain66 said:**
> i gave you guys a link to a deb built for dapper in my first post...no need to do the extra work:)

Wow. I can't believe I missed it.

Well, after uninstalling the previous version and installing the one you gave, I finally got rhythembox to work...but not at the same time as you tube. however, if I have the youtube tab closed I can play my music, but if it's open, then I can't. Once I close the tab, I get my music back. That's not much of a problem for me, because now I don't have to restart either application.

Thank you!

BTW: I have Flash 7, not 9.

---

