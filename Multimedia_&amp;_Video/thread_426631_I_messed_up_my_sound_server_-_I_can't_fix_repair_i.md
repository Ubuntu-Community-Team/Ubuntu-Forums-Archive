---
title: "I messed up my sound server - I can't fix repair it"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by vargadanis on 2007-04-28
Hey all!

I am using Ubuntu 7.04. It is pretty impressive, however my sound stuff got messed up somehow. I installed Audacity and followed couple of the stuff I found on the not to get it working. Next reboot, the system can't find any sound device in the Sounds settings.
That sucks, doesn't it? So anyways. I tried the /etc/init.d/alsa-utils reset 0 
or something like that. Didn't work at all.
When clicking on GStreamer volume controller:
> No volume control GStreamer plugins and/or devices found.
lspci:
> 00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

if you need anything, let me know

Thanx

---

### Post by superyounan1 on 2007-04-28
hello friend, 

I'm pretty new to the scene, but i recently had audio problems after a feisty upgrade, lots of people are getting them. This is what helped me out.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Take special notice of the part where it tells you to reinstall GDM. Even after doing that though, my computer set KDM as the default window manager - I have KDE installed as well. I dont really know what would have happened if I didnt have KDE installed, I'm guess it would have either defaulted to GDM or gave me a command line...

What i did to get GDM back to default is this:

```
sudo dpkg-reconfigure gdm
```

it will ask you to choose.

Since I'm new, I would either wait for someone to second my suggestion or to give you different suggestions, but i guess if no one else replies, go for it.

---

### Post by deadgobby on 2007-04-28
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

