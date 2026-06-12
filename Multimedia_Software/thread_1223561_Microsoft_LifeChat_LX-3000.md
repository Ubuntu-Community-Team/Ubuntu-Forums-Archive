---
title: "Microsoft LifeChat LX-3000"
date: 2009-07-26
forum: Multimedia Software
---

### Post by reed026 on 2009-07-26
I can not seem to get these to work, period. I do not have speakers, and would prefer to use the headphones by default. I tried using [this guide]("http://ubuntuforums.org/showthread.php?t=205449"), but it didn't seem to help me.

Using Ubuntu 9.04, these headphones worked perfect in 7.04, so I do not know why they fall off with the upgrade.

---

### Post by lucasdss on 2009-08-20
Hi,

I just added to /etc/modprobe.d/blacklist.conf :

# added to make work the LX-3000 headset
blacklist snd_hda_intel

It's working like a charm for me.
I'm using gnome with pulse as default sound server, so, probably every program capable to use pulse will work.

---

### Post by ajaykumarb on 2011-09-05
Hi 
It worked for me too.
Thanks a lot for the post.
I am just curious to know what that command does(blacklist snd_hda_intel)

Thanks again 
Ajay

---

### Post by Parsley72 on 2012-03-25
The blacklist method is a bit like using a sledgehammer to crack a walnut - it stops the snd_hda_intel module being loaded, which is why if you unplug the headphones you won't hear anything.

I've found a better method here:
[http://superuser.com/questions/172514/alsa-usb-audio-hotplug](http://superuser.com/questions/172514/alsa-usb-audio-hotplug)

By editing the file ```
/etc/modprobe.d/alsa-base.conf
``` you can change the relative preferences of the USB audio:
```
options snd_usb_audio index=-1
options snd_hda_intel index=-2

```This works fine for me in Ubuntu 11.10 with KDE (although I had to turn off the notifications from KDE every time I unplugged).

---

