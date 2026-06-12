---
title: "Video Resolution on HDMI TV changes every time I change inputs on TV"
date: 2013-04-19
forum: Mythbuntu
---

### Post by sisson_d on 2013-04-19
I'm having an issue that seems a little different than the issues others are having with the Nvidia drivers. I am using an HDMI connection to a HDTV driven by a Nvidia GTS250 using the 304.88 drivers. I can set the TV resolution to 1920x1080 in the Nvidia X Server Settings window. And when I first start the PC, or login, it is set to that. I have turned the screen saver off and all power saving settings are off as well. The PC never sleeps and never turns off the display. However, as soon as I change the inputs on my TV and switch back (even within seconds) the resolution has changed to "auto" in the Nvidia settings. "Auto" resolution in this case is 1280x720.

I don't see anything obviously wrong in etc/x11/xorg.conf. The resolution is set correctly in there even after the res has changed. I tried the older driver release just prior to this one with no change. I have no clue where to start looking or what to try.

I could care less about the lack of overscan adjustment in the new drivers since this PC is primarily a backend/frontend and I just adjust the MythTV Frontend settings to properly fill the screen. But this change in resolution is unacceptable. I refuse to watch my recordings in 720p and I really don't want to have to fix this everytime I switch inputs or turn off the TV (not to mention my wife will kill me if I suggest how to change the res). Please help!

TIA,
Doug

---

### Post by sisson_d on 2013-04-19
I forgot to mention that, while I've been using Mythbuntu for 2 years now, I'm still a bit of a novice. I'm a renaissance man of OS. I was learning basic on my C64 when I was 10. I've rooted my 1st gen Kindle. I've got XBMC running on Ubuntu and Windows PC's. I love my Android phone. And I'm okay with the wife's iPad. I work in video post and broadcast TV production......etc..etc.  So, I'm a jack of all trades and a master of none. So, please take it easy on me. Please list the locations of any files or settings I should be working with. To be safe, assume I don't know anything. I'm not that bad, but it may save me having to ask stupid questions.

Thanks again.

---

### Post by Akriss on 2013-04-19
I have been reading up on all of the "update to 304.88 threads" I can before actually doing the up date this weekend. Just in case I run in to trouble.

Now I don't know if this well help at all, but trying wont do any harm.

try adding "  Option "UseHotplugEvents" "False" "  To your xorg.conf, under the "Monitor" section. 

It seems to have helped others with similar troubles with the 304.88 driver update.

I hope it helps.

Kris.

---

### Post by sisson_d on 2013-04-20
> **Akriss said:**
> 
try adding "  Option "UseHotplugEvents" "False" "  To your xorg.conf, under the "Monitor" section. 

That fixed it. Thank you!

---

### Post by Xernie on 2013-09-04
> **Akriss said:**
> 
try adding "  Option "UseHotplugEvents" "False" "  To your xorg.conf, under the "Monitor" section. 


I had the same problem and this fixed it. I'm using 313.30.

Thanks a million!

---

