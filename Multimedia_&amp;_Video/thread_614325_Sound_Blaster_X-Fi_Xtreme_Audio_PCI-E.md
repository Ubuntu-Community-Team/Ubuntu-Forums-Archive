---
title: "Sound Blaster X-Fi Xtreme Audio PCI-E"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by JonG1969 on 2007-11-15
How do I get a Sound Blaster X-Fi Xtreme Audio PCI-E to work in Ubuntu 7.10??

---

### Post by flarkit on 2007-11-16
Unless I'm mistaken, the short answer is: you don't. Creative have not brought out official Linux drivers as yet.

There are unofficial 64-bit drivers here, though: see [link](http://opensource.creative.com/soundcard.html#X-FI) and [here](http://asia.creative.com/support/downloads/download.asp?searchString=XFiDrv_Linux)

Good luck though! I opted to use my NF4's onboard sound and use the X-Fi only for gaming in Windows.

---

### Post by JonG1969 on 2007-11-16
Thank I though I was going to have some problems with it. My onbord  card is kinda messed up the Digital out is not working and I need to hook it up to my Bose surround sound system. My PC is in my home theater room and I run all my movies thew  it. I have 2 nvidea 8800s Sli I'm also trying to find the best drivers for that card? The video works OK but not  as good as in windows. Im also getting this weard speaker that pops up on my screen and I dont know how to get rid of it??

---

### Post by mattchess on 2007-11-17
How did you get the onboard sound working without taking out the x-fi?  That is what I am currently trying to do myself...will continue to use the x-fi in windows and will use onboard sound for the time being...but the system does not seem to recognize the onboard sound either.  Thanks...doing a lot of reading up now.

Nevermind - I solved my problem.  The issue was simple - the bios had the onboard sound disabled.  Suggest others with the issue double check that.

---

### Post by 2161warrior on 2008-03-11
Bump. It's really urgent for me to know this! :confused:

---

### Post by Shakey_Jake33 on 2008-03-12
> **flarkit said:**
> Unless I'm mistaken, the short answer is: you don't. Creative have not brought out official Linux drivers as yet.

There are unofficial 64-bit drivers here, though: see [link](http://opensource.creative.com/soundcard.html#X-FI) and [here](http://asia.creative.com/support/downloads/download.asp?searchString=XFiDrv_Linux)

Good luck though! I opted to use my NF4's onboard sound and use the X-Fi only for gaming in Windows.
The Xtreme Audio PCI should work actually, since it's not actually a true X-Fi, it's a rebranded AudigySE.  Not sure if the existing drivers would know about the PCI-E version though.

---

### Post by soccrstar on 2008-05-08
> **Shakey_Jake33 said:**
> The Xtreme Audio PCI should work actually, since it's not actually a true X-Fi, it's a rebranded AudigySE.  Not sure if the existing drivers would know about the PCI-E version though.

unfortunately neither the hacked creative x-fi drivers or CA0106 drivers are unable to  locate the PCI-E sound card

03:00.0 PCI bridge: Creative Labs Unknown device 7006
04:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

---

