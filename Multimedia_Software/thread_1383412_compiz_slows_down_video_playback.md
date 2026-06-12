---
title: "compiz slows down video playback"
date: 2010-01-17
forum: Multimedia Software
---

### Post by neoguy on 2010-01-17
Hi everybody! ;)

I'm using Ubuntu Hardy on laptop Asus X51RL with Radeon Xpress 200M on board. I have a problem with video playback when the compiz window manager id turned on :confused:. This issue appears when using full screen mode. When 1:1 - playback is normal. When desktop effects are turned off - playback in full screen mode is normal too.

Thanx fr your help! Have a nice day!

---

### Post by sports.car.guy on 2010-01-17
> **neoguy said:**
> Hi everybody! ;)

I'm using Ubuntu Hardy on laptop Asus X51RL with Radeon Xpress 200M on board. I have a problem with video playback when the compiz window manager id turned on :confused:. This issue appears when using full screen mode. When 1:1 - playback is normal. When desktop effects are turned off - playback in full screen mode is normal too.

Thanx fr your help! Have a nice day!


I am betting it is because you need to enable textured video where you are using most likely the open source driver. Another factor is which of the open source drivers the GPU uses too. The xf86-video-ati driver I know has the ability to use textured video and I am not sure about the driver that covers later hardware including the HD series.

The newer GPU's can use the xf86-video-ati driver if it is an option to get faster rendering. All you need to do is enable textured video in xorg.conf

Option "TexturedVideo" "on"
I hope this helps.
 []("http://www.phoronix.com/scan.php?page=search&q=xf86-video-ati")

---

### Post by apocalypse80 on 2010-01-17
First install the compiz configuration manager.
```
sudo apt-get install compizconfig-settings-manager
```

Then open that and go to general->general options->general and check the box titled "unredirect fullscreen windows".

---

### Post by gradinaruvasile on 2010-01-17
Well thats normal. Compiz is causing slower video play/tearing (except Nvidia's VDPAU output as far i experienced it). And coupled with the opensource ati drivers its even worse. Just turn off compiz.
Install fusion-icon, it makes the turning compiz on/off one-click affair.

---

### Post by neoguy on 2010-01-18
Thank you guys for your quick reply! I'm so pleased to feel you friendly shoulders (don't how say that in English :-) 

Thank you, apocalypse80! This checkbox really works!

See you!

---

