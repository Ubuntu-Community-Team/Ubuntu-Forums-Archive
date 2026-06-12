---
title: "[HELP] Analog signal PAL countries"
date: 2009-05-18
forum: Mythbuntu
---

### Post by kaede15 on 2009-05-18
Hello everyone, I'm trying to build a PVR with Mythbuntu with a Hauppauge MCE500 (dual tuner).
The problem is I'm living in Argentina, a PAL-N or PAL-NC country and finding the useful instructions for PAL countries with that card is really HARD.

Right now I'm running a Pentium IV 1.5Ghz, 512Mb Ram, nv Geforce2 Mx 400, Hauppauge MCE500 pci, SB live! sound cad and a 40Gb hdd for this settings, and I've just installed the Mythbuntu 9.04.

The thing is when I tried to scan the channels every channel returns with "timeout". And in Live Tv I only get static.

[http://zaf.geek.nz/projects/mythtv/setup.php](http://zaf.geek.nz/projects/mythtv/setup.php) This is the only page I found regarding mythbuntu and PAL signal, it's very outdated and I'm new with linux commands.

please help!

---

### Post by kaede15 on 2009-05-19
anyone? hauppage 500MCE - PAL-N - Mythbuntu 9.04.. Anyone with these settings?

---

### Post by nickrout on 2009-05-19
There is no magic to PAL. The card should find the channels.

What specifically is the error you are getting?

---

### Post by ianhaycox on 2009-05-19
Have you tried plugging a TV into the aerial lead to check the antenna is OK ?

---

### Post by nickrout on 2009-05-19
Also, I assume you do have a PAL version of the PVR-500?

---

### Post by joshoekstra on 2009-05-22
I never used the scan-option and there's a way to bypass it(depnding on your setup) I first used a xmltv-grabber via mythtv-setup to make a channel-lineup and then after installing mythweb I entered the right frequencies to each channel.
The card itself should be auto-detectedby the kernel as a PAL-version.

---

### Post by kaede15 on 2009-05-23
Thanks for all the replies. :)

The main problem as stated earlier was that the card cannot tuned to any channel, after the autoscan, which most channel returned with a  "timeout" the remaining of the channels which seems to have some signal about 3 channels top, all I get is static.

First, my feed is cable with 80chs aprox in PAL-N format, I tested with an old Tv set which let me manually select the formats from PAL-N to NTSC-M, so I'm pretty sure about the format and the feed quality.

The Hauppauge MCE500 is PAL capable, this info was confirm by the Hauppauge support team before I purchased it from Newegg. Plus, I was able to use it with Windows 7 Ultimate x64 Media Center application, which works but has some serious bug and terrible image quality. Then I tested with Snapstream BeyondTV ver.4.2 which works really good, the image has excellent quality and no artifacts. BUT once I return from the Live TV session to the main menu the capture card CAN'T be initialize again... :( I send some inquiries for this problem to the support team they haven't reply yet so I decided to give Mythbuntu a try.
In short I assure you, this card is PAL-N capable and WORKS great. Once it starts working of course. (the link above I mentioned, that person has the same card and works perfectly in a PAL country)

I will search for the PAL frequencies for each channel, how can I edit them manually? Can you post the procedures please?

---

