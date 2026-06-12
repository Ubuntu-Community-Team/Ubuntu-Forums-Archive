---
title: "Where is XBMC?"
date: 2010-08-11
forum: Multimedia Software
---

### Post by PrvSAT on 2010-08-11
I have freshly installed lucid 10.04 and upgraded to latest provided by ubuntu.

I have tried to install XBMC as many times as before, from terminal or from Synaptic but now at terminal 
after:

```

sudo apt-get install python-software-properties pkg-config
sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone


``` it gives me: "Couldn't find package xbmc" even if I tried variants like just "XBMC" or "XBMC-live",. still the same result.

The Synaptic Package can not find XBMC as it used before to show many variants of it.
The respo's are added accordingly:
```

deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu lucid main
```



[SIZE=3]Is it something going on and the repo's or the launchpad do not work at this time? It seems that this problem is present during last 24 hours. Is anyone aware of it? [/SIZE]

If that's the case, I wonder how come nobody in charge of XBMC repo's did not announced anything?

---

### Post by thaseint on 2010-08-11
Asked a similar question in a thread below.

Just did a little reading and it seems that the repos are being reorganized/cleaned up.

[LIST]
[*][http://forum.xbmc.org/showthread.php?t=33327&page=91](http://forum.xbmc.org/showthread.php?t=33327&page=91)
[/LIST]
No official date/time has been given as to when the official repo will go back up. Going to try and find a working archived build tonight. Looks like svn32246 is stable and should work. 

Will post back with results if someone doesn't beat me to it first. :)

---

### Post by PrvSAT on 2010-08-11
Thanks a lot thaseint! :)

---

### Post by thaseint on 2010-08-12
> **PrvSAT said:**
> Thanks a lot thaseint! :)


Sorry for not getting back sooner. Anyways, here is the thread I followed and it seems to have worked. Not sure if I'd consider it a permanent thing since it's a svn; but it seems stable enough...

[http://forum.xbmc.org/showpost.php?p=577378&postcount=4](http://forum.xbmc.org/showpost.php?p=577378&postcount=4)

---

### Post by iClouseau88 on 2010-08-13
Hi,

Post#4 of BurningSky from the XBMC.ORG forum ([http://forum.xbmc.org/showthread.php?t=78223]("http://forum.xbmc.org/showthread.php?t=78223")) works for me, but only after I installed some packages to resolve unmet dependencies.  For my 32-bit Lucid Ubuntu system, these are the following:

[COLOR="Blue"]libfaac0, libmicrohttpd5, libmysqlclient16,libpcrecpp0, libsdl-image1.2, libsdl-mixer1.2, and libvdpau1[/COLOR].

I didn't get xbmc-live installed because it is in conflict with GDM.

---

