---
title: "HDMI sound not working on ATI Sapphire Radeon HD 5450"
date: 2011-06-22
forum: Multimedia Software
---

### Post by alexoz on 2011-06-22
I recently installed ubuntu 10.10 on HTPC, after having a few RAM and SATA issues everything seems to be working fine,
The audio (using HDMI) does not work. Have PC connected using HDMI for video (and I am hoping for audio too, this card is made for this and it has been tested with other OS) however the audio does not work, although in the audio preferences it shows to be using the correct hardware. Testing for sound under sound preferences does not play anything, acts as it it was, but no sound, no error messages either.
I went ahead and installed ATIs proprietary drivers in hopes that it would make the audio work, but not luck so far. If there's anyone out there that would be kind enough to point me in the right direction I would appreciate it.

---

### Post by Yellow Pasque on 2011-06-22
HDMI doesn't work with open-source drivers on RHD 5k+ card right now: [http://phoronix.com/forums/showthread.php?41121-HDMI-Audio-for-Evergreen](http://phoronix.com/forums/showthread.php?41121-HDMI-Audio-for-Evergreen)
What version of the proprietary drivers did you install?

---

### Post by alexoz on 2011-06-22
Installed the ones suggested when checking for additional hardware/drivers from ubuntu. Installed from there, unfortunately I don't have the version number right now.
Video works fine at 1080 res w/o any issues, audio is the only part that does not work.

---

### Post by Yellow Pasque on 2011-06-22
Try the latest Catalyst. See this to remove the Ubuntu-supplied proprietary driver: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)
Then, install according to: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by alexoz on 2011-06-22
Thank you, I am gonna try that, although someone already mentioned that for the evergreen line of Radeon video cards, hdmi audio is not supported yet :(

---

### Post by ahang on 2011-06-30
I had the same issue, installing the proprietary drivers will fix it. It will add another sound card device, (hdmi sound drivers) choose that as your default, it will not set automatically after installing catalyst. btw are you able to view hd video with this card, my video clips constantly and frames get dropped, but in windows this card works fine.

thanks and good luck.

---

### Post by subrandom249 on 2011-08-08
I am having the same issues as the original poster. Pulse recognizes the card, or so it seems but thinks that it is only two channels.
Alsamixer shows no channels at all to output to when that card is selected.

This link contains my Alsa file..
[http://www.alsa-project.org/db/?f=380c5fb3ec94cdaea2291323ce9a7f0f2cd3263a]("http://www.alsa-project.org/db/?f=380c5fb3ec94cdaea2291323ce9a7f0f2cd3263aWas") 
was the end result of the OP that the card's audio is unsupported? I recall reading that there were no compatibility issues with the onboard 5.1...?

FYI.. 

uname -a
Linux 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

