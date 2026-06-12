---
title: "Mythbuntu 9.04 and with 0.22 daily build - black border around live tv picture"
date: 2009-11-06
forum: Mythbuntu
---

### Post by davetibbs on 2009-11-06
I recently had problems with the kernel on Mythbuntu 9.10 so have gone back to 9.04 but installed and updated with the daily builds repo - I've now got a problem I never had with myth 0.21 on 9.04 - when watching Live TV there appears to be a black border of maybe 100 pixels at the top and the bottom of the picture, and maybe 20 pixels at the sides.

This is *not* letterboxing or aspect ratio on the broadcast because under myth 0.21 on the same channels there was no border.

Aside from wasted screen space it's annoying as you can often get a flickering line of pixels at the top and the bottom of the picture which never used to happen.

I've checked all the obvious settings (screen position setup, appearance settings) and can't find anything untoward.

I've also noticed that the picture quality seems worse and grainier than under 0.21.

I'm using a DVB-C card and an onboard nVidia 8200 - I'm using the latest 190.x drivers.

I've tried using VDPAU in myth but the A/V sync is out (something I experienced with mplayer until I used the lavf demux - any idea how to do this in mythtv?)

Does anyone have any ideas as to where else I can look?

Thanks

---

### Post by davetibbs on 2009-11-06
I should probably also mention:

* I'm watching this on a 40" LCD with an HDMI cable plugged directly into the on-board card
* I don't have the problem with myth-tv gui, menus, xfce, etc - only Live TV screen
* I've tried changing the nVidia overscan settings TNA.

---

