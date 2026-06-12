---
title: "Intel 82801G problem in Gutsy"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by checho4 on 2007-11-21
My girlfriend has a Toshiba Satellite P205-S6307 with Kubuntu Gutsy 32-bit installed.  Everything works pretty well except for two things: the wireless and the sound.  I think I can figure out the wireless with a bit more searching.  However, the sound is doing something freaky.

The volume mixer icon in the taskbar does nothing.  It doesn't matter whether it is at 0 or 100, the sound is the same.

The volume knob on the front of the laptop does nothing either.  It displays a little volume thing that jumps from 68 to 91 and back, but the volume is the same.  I don't understand how to fix it!!!  Any help is greatly appreciated.

---

### Post by checho4 on 2007-12-04
I also just hooked up my girlfriend with Gutsy on her Toshiba p205, and the wireless and sound didn't work out too well.  As for the volume in the taskbar:

Right-click the kMix button
Click "Select Master Channel"
Select "Front"

I'm currently struggling with the wireless.

---

### Post by birdydon on 2008-03-29
Upgrade to Hardy and you should not have a problem with sound.

You will still have a problem with wireless. The problem is the Atheros AR242x wireless chip. You can easily find a Vista driver for it, but neither NDISwrapper nor madwifi support it at this time.

Your best option is to forget built-in wireless for the time being and install a wireless USB adapter with NDISwrapper. I had an older D-Link DWL-G132 working under Feisty. That device finally failed and I now have a Netgear WG311 working under Hardy. Extracting the driver from the Windows install disk was tricky but I'll give it to anyone who wants it and reads this post.

---

