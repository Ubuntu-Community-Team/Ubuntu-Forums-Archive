---
title: "How can I disable power management to the video card via shell?"
date: 2011-06-30
forum: Multimedia Software
---

### Post by tombeard on 2011-06-30
I installed the latest 32 bit (intel) Xubuntu on an IBM Aptiva E Series 585 with a 500MHZ pentium and 256MB ram. Video is Gforce MX/MX400. I think I have a couple of problems but first is the video seems to power down after a while and won't restart. Worked fine under W2K so it's not hardware.

How can I disable power management to the video card via shell?

---

### Post by dFlyer on 2011-06-30
What version of ubuntu did you install, hopefully not 11.04 as I believe it take 512 meg.

---

### Post by Toz on 2011-07-01
Power management in Xubuntu 11.04 is configured and managed in the Power Manager settings **xfce4-power-manager-settings** dialog (see Monitor tabs in the "On AC" and "On Battery" sections) and the screensaver **xscreensaver-command -prefs** dialog (see Display Power Management on the Advanced tab).

For command line configuration, look at the **~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-power-manager.xml** and **~./Xscreensaver** files. Search for the keyword dpms.

Earlier versions of xubuntu should be similar, but I cannot confirm.

---

### Post by tombeard on 2011-07-01
> **Toz said:**
> For command line configuration, look at the **~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-power-manager.xml** and **~./Xscreensaver** files. Search for the keyword dpms.

Thanks Toz, that sounds like what I am looking for. I thought it would be easy from the gui, but since I cant get that to run ... 
Appreciate your help, I really need to figure out how all this is tied together someday.

---

