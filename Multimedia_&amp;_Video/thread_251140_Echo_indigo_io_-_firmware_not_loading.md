---
title: "Echo indigo io - firmware not loading"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by agrabah on 2006-09-05
Hello!

First I'd like you to point to my first post regarding this issue:
[http://www.ubuntuforums.org/showthread.php?t=250510]("http://www.ubuntuforums.org/showthread.php?t=250510")

and it seems my problem is similar to the one mentioned in this post:
[URL="http://www.ubuntuforums.org/showthread.php?t=229778&highlight=echo+indigo"]http://www.ubuntuforums.org/showthread.php?t=229778&highlight=echo+indigo
[/URL]
This is not a double post - more of a "bump", but I have learned some new things about th problem and made some progress...
I have consulted with the man who wrote the original alsa drivers (thanks Giuliano!), and he advised me to install hotplug scripts; I installed them (not the packages from debian, as I feared they could break udev, but source files). This went well, but the computer still wouldn't load the firmware, complaining that the firmware could not be found.
I made all the symlinks for hotplug to find the firmware: /lib/firmware links to /usr/lib/hotplug/firmware; 
I even tried to load the firmware manualy via /sbin/hotplug with the command:

```
sudo /sbin/hotplug firmware indigo_io_dsp.fw
``` 

which returned:

```
Firmware '' event not supported
```

The man pages for hotplug weren't exactly helpful.

I checked the my kernel configuration... It said that firmware loading was enabled; I believe that the only thing missing now is to point the computer to the location of the firmware. 
Could I somehow manually load the firmware (because the card is working - alsaconf is recognizing it, only the firmware isn't loaded); and where exactly is ubuntu searching for firmware (and how does this mechanism work)?

Thanks for any input...

Tine

---

