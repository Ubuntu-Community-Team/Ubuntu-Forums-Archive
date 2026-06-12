---
title: "hdmi pulse audio ubuntu 10.04"
date: 2011-02-23
forum: Multimedia Software
---

### Post by owenlinx on 2011-02-23
Thanks for any eyes that may spot the problem but I am at a loss. Dual X screens btw.
pc=screen 0.0
tv=0.1
usb audio = pc
hdmi = tv

Recentally I setup xbmc hdmi audio with this site(all with ppa's):
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")

/etc/modprobe.d/sound.conf = [http://paste.ubuntu.com/570923/](http://paste.ubuntu.com/570923/)

/etc/pulse/default.pa = [http://paste.ubuntu.com/570918/](http://paste.ubuntu.com/570918/) (line 44)

/etc/asound.conf = [http://paste.ubuntu.com/570924/](http://paste.ubuntu.com/570924/)

Sound works on XBMC, Banshee, Totem, M_player, VLC.

Doesn't work on **Chrome**.** Firefox**, **SMplayer**.

Thanks for any and all help!!!

---

### Post by owenlinx on 2011-02-25
"/etc/modprobe.d/sound.conf"

**should be**

```
"/etc/modprobe.d/alsa-base.conf" 
```

[http://paste.ubuntu.com/572240/]("http://paste.ubuntu.com/572240/") is my working file

MSI N210 MD512H  & GWC USB 5.1 Channel Audo Adapter AA1500 5.1 Channels USB Interface Sound Card

To fix Chrome, Firefox, SMPlayer see this link

[http://ubuntuforums.org/showpost.php?p=9131334&postcount=1]("http://ubuntuforums.org/showpost.php?p=9131334&postcount=1")

I am on lucid and it worked for me.

---

### Post by jamestrowbridge on 2012-05-16
Turns out that in the sounds settings area, you have to choose a specific output device with some devices, unless you use paprefs as per the below.

Maybe this will help someone one day..

[http://askubuntu.com/a/78179]("http://askubuntu.com/a/78179")

---

