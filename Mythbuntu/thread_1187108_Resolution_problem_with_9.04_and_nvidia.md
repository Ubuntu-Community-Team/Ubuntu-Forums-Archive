---
title: "Resolution problem with 9.04 and nvidia"
date: 2009-06-14
forum: Mythbuntu
---

### Post by daschatten on 2009-06-14
Hi,

i just reinstalled 2 frontends with 9.04. In both are nvidia cards (7300 & 9800) using the nvidia driver. No matter what i specify in xorg.conf, the resolution is on both frontends always:

* 1080i 59 hz when connected to my lcd tv (benq something, should be 1080p)
* 1080p 60hz when connected to my projector (epson 3000, is also 1080p)

If i put 'Modes "1280x720_50"' (or something else) in xorg.conf nothing changes. After reboot the Xorg.log shows that this mode is correct and sets it. But the resolution remains as noted before.

With 8.04 i didn't have these problems. What has changed between this 2 versions?

One more note: If i remove xorg.conf then the default nv driver is loaded and 1280x720 works! But its much slower than with nvidia driver.

Thanks,
daschatten

---

### Post by ian dobson on 2009-06-14
Hi,

Are you connecting to your "monitor" through DVI/HDMI or VGA?

Regards
Ian Dobson

---

### Post by daschatten on 2009-06-16
Via HDMI/DVI-Adapter. VGA does not support these resolutions.

---

### Post by klc5555 on 2009-06-16
I have a 7300 (AGP) card, and I've only recently noticed that 9.04's default 180.x series NVidia drivers don't seem to be able to recognize which GPU the card has. The card and driver work, and work quickly, but some resolutions and features (e.g. on-screen video controls) are not available to me on this installation. I wonder whether your situation is similar, and whether the 180.x series driver is at fault.

I've been considering trying a downgrade to the optional 173.x series driver, to see whether it does a better job with regard to the 7300 card, but haven't done so yet.

---

### Post by AlecJ on 2009-06-16
[http://www.avenard.org/media/Ubuntu_Repository/Archive.html](http://www.avenard.org/media/Ubuntu_Repository/Archive.html)

---

### Post by daschatten on 2009-06-17
> **klc5555 said:**
> I have a 7300 (AGP) card, and I've only recently noticed that 9.04's default 180.x series NVidia drivers don't seem to be able to recognize which GPU the card has. The card and driver work, and work quickly, but some resolutions and features (e.g. on-screen video controls) are not available to me on this installation. I wonder whether your situation is similar, and whether the 180.x series driver is at fault.

I've been considering trying a downgrade to the optional 173.x series driver, to see whether it does a better job with regard to the 7300 card, but haven't done so yet.

It really seems to be the driver, i updated a 8.04 mythbuntu and the same weird thing happened. So i will try to upgrade and/or downgrade the driver.

---

### Post by klc5555 on 2009-06-17
> **daschatten said:**
> It really seems to be the driver, i updated a 8.04 mythbuntu and the same weird thing happened. So i will try to upgrade and/or downgrade the driver.

With the reports of the new 185.x series drivers randomly locking up systems, you may be better off trying a backlevel to 173.x first.

I'm pretty sure I'll be doing the same this weekend, when I get an hour or two with the other members of our viewing audience out of the house.

Good luck.

---

### Post by daschatten on 2009-06-18
I installed 177.x and finally managed to get 720p with nvidia-settings :-)

Thanks @ all

---

### Post by klc5555 on 2009-06-20
> **daschatten said:**
> I installed 177.x and finally managed to get 720p with nvidia-settings :-)

Thanks @ all

Better luck than me, I'm afraid. 173.x on 9.04 can't identify my 7300 NVidia GPU either. So, while the driver works fine, I still don't have the full range of NVidia features, in particular On Screen picture controls. My other myth machines are either Ubuntu without NVidia, or NVidia on Slackware, in all of which cases the On Screen picture controls are present and functional. So I have no real solid other example for comparison.

Oh well, I guess I'll keep plugging away at it. It's only a small irritation.

All the best! :)

---

