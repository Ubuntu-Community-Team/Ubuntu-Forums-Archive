---
title: "gnome-volume-control 2.27.5 missing features"
date: 2009-07-29
forum: Multimedia Software
---

### Post by modmadmike on 2009-07-29
(I tried to report it in launchpad but kept getting errors)
In ubuntu Karmic alpha3 (9.10) the new volume control is missing some features that were available in 9.04 such as switches for controls such as analogue loop-back and surround up-mixing, personally I prefer the older volume control found in Jaunty because Im more used to it (I think there should be an option to switch between the new and the old when karmic is released) and I find it easier, but I like the controls for individual applications.

[Juanty]
[IMG]http://fc01.deviantart.com/fs48/f/2009/195/4/4/ASUS_XONAR_D2X_LINUX_by_modmadmike.png[/IMG]

[Karmic Alpha 3]
[IMG]http://fc09.deviantart.com/fs46/f/2009/210/0/3/Volume_control_P1_Karmic_by_modmadmike.png[/IMG]
[IMG]http://fc05.deviantart.com/fs47/f/2009/210/3/3/Volume_control_P2_Karmic_by_modmadmike.png[/IMG]
[IMG]http://fc05.deviantart.com/fs48/f/2009/210/4/b/Volume_control_P3_Karmic_by_modmadmike.png[/IMG]
[IMG]http://fc08.deviantart.com/fs48/f/2009/210/a/e/Volume_control_P4_Karmic_by_modmadmike.png[/IMG]
[IMG]http://fc04.deviantart.com/fs48/f/2009/210/d/7/Volume_control_P5_Karmic_by_modmadmike.png[/IMG]

---

### Post by igorzwx on 2009-07-30
"In ubuntu Karmic alpha3 (9.10) the new volume control is missing some features..."

If you feel very experimental, you may try OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

It has a very interesting OSS Mixer, and some other things too.

info is here:

[LIST]
[*][Sorry State of Sound in Linux]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html")
[*][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")
[*][OSS is dead. Long live OSS!]("http://4front-tech.com/hannublog/?p=5")
[/LIST]

---

### Post by modmadmike on 2009-07-30
> **igorzwx said:**
> "In ubuntu Karmic alpha3 (9.10) the new volume control is missing some features..."

If you feel very experimental, you may try OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

It has a very interesting OSS Mixer, and some other things too.

info is here:

[LIST]
[*][Sorry State of Sound in Linux]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html")
[*][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")
[*][OSS is dead. Long live OSS!]("http://4front-tech.com/hannublog/?p=5")
[/LIST]

thanks! I forgot there were other mixer utilities out there for some odd reason :D

---

### Post by modmadmike on 2009-07-30
Im getting no sound with OSS but the VU meters in ossxmix are active.

---

### Post by igorzwx on 2009-07-30
have tried 

osstest

---

### Post by igorzwx on 2009-07-30
see:
[7.1 Troubleshooting HDAudio devices]("http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices")
[http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices](http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices)

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
If you have OSS installed properly, but still have issues, the OpenSound project has free user support forums and an IRC channel. Be sure to include the output from these commands so the experts don't have to prompt you for them 
ossmix
ossinfo -v3Also, you'll want to note if the osstest command works and plays sound. 
 
**Forums**

 You can make a thread on [the OpenSound user forums]("http://www.4front-tech.com/forum/index.php").  
 
**IRC**

 [Freenode]("http://freenode.net/irc_servers.shtml") hosts the OSS support channel (#oss). You can paste your support information from the aforementioned commands [here]("http://oss.pastebin.com/")

---

### Post by igorzwx on 2009-07-30
the output from these commands so the experts don't have to prompt you for them 

ossmix

ossinfo -v3

---

### Post by modmadmike on 2009-07-30
sry I reverted to ALSA, and I'm using a ASUS XONAR D2X not HDA

---

### Post by igorzwx on 2009-07-30
It looks like your hardware is not supported by OSS4.
The result of your experiment was, perhaps, predictable.

[http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux](http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux)
    18oss_cmi878x	pci1043,834f	Asus Xonar D1 (AV100)

    19oss_cmi878x	pci1043,8275    Asus Xonar DX (AV100)

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Does OSS Support My Hardware?**


Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux").
Some devices may not have full functionality (e.g. the X-fi module is
limited to stereo output at the time of this writing, and jack sensing
may not work on Azalia-compliant "High-Definition" devices, which are
very common on motherboards and laptops today). If you're in doubt,
consult the "Additional Support" sources found towards the end of this
document.

---

### Post by isecore on 2009-08-24
For what it's worth - I'm REALLY missing the old volume control. The new thing doesn't cut it. Either import all the features of the original volume control or reinstate the original.

As it stands I cannot control digital out and various other features which were identified just fine in the previous volume control.

---

### Post by modmadmike on 2009-09-02
> **isecore said:**
> For what it's worth - I'm REALLY missing the old volume control. The new thing doesn't cut it. Either import all the features of the original volume control or reinstate the original.

As it stands I cannot control digital out and various other features which were identified just fine in the previous volume control.

Exactly, also In the previous i could use more than one card at a time if i wanted but in the new one i cant without using kmix.

---

