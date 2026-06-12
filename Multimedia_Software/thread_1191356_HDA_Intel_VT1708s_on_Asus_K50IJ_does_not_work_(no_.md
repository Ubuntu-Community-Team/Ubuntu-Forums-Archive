---
title: "HDA Intel VT1708s on Asus K50IJ does not work (no sound)"
date: 2009-06-18
forum: Multimedia Software
---

### Post by Sasa Vilic on 2009-06-18
Hi,

i got my asus K50IJ, and I have installed ubuntu 9.04. I get no sound. I have HDA Intel VT1708s sound card. Does anybody has any solution?

Thanks

---

### Post by mutrax on 2009-06-19
Haha, I'm converting one for a customer as we speak (leterally!) . I'll keep you posted when I have found the solution....

Now I'm looking for the correct model string for alsa-base.conf ( [http://ubuntuforums.org/archive/index.php/t-1125004.html](http://ubuntuforums.org/archive/index.php/t-1125004.html) ). I'll keep you posted when I find the solution, please do the same.

Thanks!

---

### Post by mutrax on 2009-06-19
> **mutrax said:**
> .............
Now I'm looking for the correct model string for alsa-base.conf ( [http://ubuntuforums.org/archive/index.php/t-1125004.html](http://ubuntuforums.org/archive/index.php/t-1125004.html) ). .....


nothing there... I've removed pulseaudio and reverted to alsa.
When setting all volumes to max with alsamixer. I get a working microphone at boot, but stops when alsa loads, so, alsa and ubuntu are communicating with the sound hw, but therse no output.... 
Evrything else I tried,

Fiddling with various settings...
Its a via vt1708s intel hda chipset btw.

Please, anyone else? (for the sake of spreading ubuntu among "normal" computer users  ;) )

---

### Post by Sasa Vilic on 2009-06-19
Just before I installed Ubuntu, I tried Open Solaris and it worked great. But under Ubuntu, I get no sound....

---

### Post by KoKuToru on 2009-07-16
Sound with Ubuntu here:
[http://ubuntuforums.org/showthread.php?t=1204735](http://ubuntuforums.org/showthread.php?t=1204735)

---

### Post by mutrax on 2009-08-02
Well, this pretty much solved it for me!

Install alsa 1.0.20 as described here;
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

And tweak the hda-verb thingy described in following post;
[http://georgia.ubuntuforums.org/showthread.php?p=7564125](http://georgia.ubuntuforums.org/showthread.php?p=7564125)


> ```
sudo -s
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz
tar xf hda-verb-0.3.tar.gz
cd hda-verb-0.3
make
cp hda-verb /usr/bin
gedit /etc/rc.local
```

And add this line before "exit 0"
```

hda-verb /dev/snd/hwC0D0 0x1c SET_EAPD_BTLENABLE PCM


```

Now I have a working k50ij. To bad I had to buy a HP to satisfy the customer... A "just works" laptop brand would be nice. (I'm starting up a ubuntu business in Belgium)

---

### Post by neoroses on 2010-01-27
sweet thanks man

---

### Post by moosesoom on 2010-01-28
@neoroses

You have to install Ubuntu 9.10 and upgrade Alsa to 1.0.22.1

There are 2 threads about that on:

[http://moosesoom.blogspot.com/2009/12/asus-k50ij-x5dij-audio-english.html](http://moosesoom.blogspot.com/2009/12/asus-k50ij-x5dij-audio-english.html)
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

---

