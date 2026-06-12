---
title: "No video with &quot;nvidia&quot; driver..."
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by Donshyoku on 2008-03-18
Simple problem.  With VESA or nv, I get picture great.  The system is fully functional.  However, when I switch to the nvidia driver from Restricted Drivers, I get no video past the bootloader.  I removed that, reconfigured, and used Envy to install the latest nvidia.  Same problem, I have to constantly revert to the nv driver.

This a media center that I just moved over from Vista in response to SP1 issues.  I intend to run Fluendo's Elisa on it, but can't even launch the app without Nvidia 3D drivers.  Any idea on how I can resolve this?

TIA, all. :guitar:

---

### Post by LeoSolaris on 2008-03-18
What model of Nvidia Graphics card do you have?

---

### Post by addisor on 2008-03-18
What version driver has Envy installed, as I know you ca get 169.12 and even 171.05 & 171.06.

---

### Post by Donshyoku on 2008-03-18
Both obvious things I forgot about!

I am using the latest Envy for Gutsy which installed for me the 169.12 driver.  Also, my card is a GeForce 8600GTS... I had it on Ubuntu Gutsy before working correctly with the Restricted Driver Manager, then installed Vista, moved back to Ubuntu today and suddenly it doesn't work.  No hardware changed, no BIOS setting changed... simply doesn't output video with nvidia now.

---

### Post by Donshyoku on 2008-03-18
Reformat/reinstall fixed it.  Only thing I could think of to try after all of this.

The only thing I can imagine is that it has something to do with the nvidia-settings package.  I've always used it in the past, this time I avoided it, and things are good so far.

---

### Post by LeoSolaris on 2008-03-19
> **Donshyoku said:**
> Reformat/reinstall fixed it.  Only thing I could think of to try after all of this.

The only thing I can imagine is that it has something to do with the nvidia-settings package.  I've always used it in the past, this time I avoided it, and things are good so far.


I had a few strange glitches with the nvidia settings pack, too. There may be a small bug in the software somewhere, but it would take someone far more experienced than I in coding to root it out.

Leo

---

