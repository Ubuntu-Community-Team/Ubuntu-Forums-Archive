---
title: "Acer revo screen res problem"
date: 2009-12-31
forum: Multimedia Software
---

### Post by seoras on 2009-12-31
I have an Acer Revo Intel Atom dual core running Nvidia driver version 185 and Ubuntu 9.10 I have connected the system to my Hitachi 42FPDEUDA1 HDMI TV and everything is fine apart from the screen resolution. Nvidia detects the TV and has set the resolution to the max 1920x1080 but the edges are off screen so I cannot see the edge panels and so cannot see the menus etc. I have tried all the other resolutions in the Nvidia list but none work correctly. Any ideas? Cheers Seoras

---

### Post by xc3RnbFO8P on 2009-12-31
Check if you can change it in TV settings, on my 42" Philips, I use the remote (Format button> **unscale**)

---

### Post by seoras on 2009-12-31
> **Ringi said:**
> Check if you can change it in TV settings, on my 42" Philips, I use the remote (Format button> **unscale**)

Just got the TV today so I'm not that familiar with it. I had a look but there doesn't seem to be anything in the controls that will allow me to do this. The TV allows PC connection through VGA and here is a screen positioning tool with this, but I've connected it with HDMI cable so this is not an option. Thanks for replying, Cheers

---

### Post by Sutareteiru on 2009-12-31
I also have the Acer Revo, I put ubuntu 9.10 on it and am using the same 185 drivers. I am connecting it via HDMI to my LG 47SL90tv and unfortunately after every reboot it resets my resolution to 800x600, I am trying to determine if it's an issue with my tv or the revo itself.

---

### Post by xc3RnbFO8P on 2010-01-01
@seoras
I had this scaling problem in Vista and scaling option in TV was the only way to solve it.
@Sutareteiru
Did you try in System> Preferences> Display (choose no) to change resolution there?

---

### Post by Sutareteiru on 2010-01-05
I did, however the settings do not stay through a reboot. Also I am using boxee and am trying to stream media to the tv and for some reason I am getting choppy video. It seems to get more choppy the higher the res is. I am trying to figure out if both of these occurences are connected.

---

### Post by Radiocode on 2010-01-05
Hi Seoras,

I have just overcome exactly the same problem on a 42" Panasonic Viera plasma, connected to my Revo via HDMI.

It is a configuration issue with the TV, not the Revo - I had to turn "Picture overscan" off in the TV setup menu.

Thanks to all the other people that posted to this thread - your comments pointed me in the right direction.:KS

I'm typing this on the Revo, sitting in front of the plasma TV in 1920x1080p - wow!

Cheers,

Lee

P.S. I'm using the latest 190.53 drivers off Nvidia's website.

> **seoras said:**
> I have an Acer Revo Intel Atom dual core running Nvidia driver version 185 and Ubuntu 9.10 I have connected the system to my Hitachi 42FPDEUDA1 HDMI TV and everything is fine apart from the screen resolution. Nvidia detects the TV and has set the resolution to the max 1920x1080 but the edges are off screen so I cannot see the edge panels and so cannot see the menus etc. I have tried all the other resolutions in the Nvidia list but none work correctly. Any ideas? Cheers Seoras

---

### Post by seoras on 2010-01-07
thanks to all respondents. The consensus seems to be that it's a scaling issue with the TV, as Ringi suggested *Format button> unscale* and Radiocode suggested *Picture overscan*. I have yet to figure out if this is possible on my Hitachi TV so far it looks like I can alter the picture whilst in DTV mode but not in HDMI. I have written to Hitachi but so far no reply. 

many thanks
Seoras

---

### Post by abrennan on 2010-10-13
Hi Seoras,

I had the same problem with this exact model Hitachi. It was a TV setting. In the menu, go to Feature, then scroll down to "Full Mode" and change it to 1:1. Then the full screen shows!

Thanks to the others for pointing me in the right direction.

Cheers,
AB

---

