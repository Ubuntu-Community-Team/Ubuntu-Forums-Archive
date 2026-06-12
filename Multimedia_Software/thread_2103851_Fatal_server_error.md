---
title: "Fatal server error"
date: 2013-01-11
forum: Multimedia Software
---

### Post by jim1112 on 2013-01-11
I have a MSI mother board with VIA/unichrome graphics chip. I am running ubuntu 12.04. I am not getting the screen resolution I need, so I booted into Recovery Mode and ran

X -configure

I received the following error message:

Fatal server error:
Could not create lock file in /tmp/.tXO-lock

I went to [http://wiki.x.org](http://wiki.x.org) but was not able to find a solution to getting X to run or configured. Anyone have any thoughts? Thanks, Jim

---

### Post by steeldriver on 2013-01-11
Hello Jim

Did you remount the filesystem with read-write permissions before running the configuration command? recent versions mount everything read-only in recovery mode - that would prevent X from writing its lock file for sure

```

# mount -o remount,rw /
# X -configure

```(note that there is no space between the remount,rw options). Alternatively you could skip recovery mode altogether and just kill the X server from one of the text-based virtual terminals

[LIST]
[*]log out of your GUI session (not strictly necessary - but will prevent data loss from any open apps)
[*]hit Ctrl-Alt-F1 or Ctrl-Alt-F2 etc.
[*]login with your normal (sudo-able) account at the text prompt and then do
[/LIST]
```
$ sudo service lightdm stop
$ sudo X -configure
$ sudo service lightdm start
```

I've used this successfully for Xorg -configure, I'm not sure what the difference is between that and X -configure but it should work the same way I think

---

### Post by jim1112 on 2013-01-11
When I ran in those commands in both Terminal mode and in Recovery Mode, I got the following error message:

(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Number of created screens does not match number of detected devices.

Configuration failed.

ddxSigGiveUp: Closing log

Server terminated with error (2). Closing log file.

Does anyone know a possible solution to this? Thanks, Jim

---

