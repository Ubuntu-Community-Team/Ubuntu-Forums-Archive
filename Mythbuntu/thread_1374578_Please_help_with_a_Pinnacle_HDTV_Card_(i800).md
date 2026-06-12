---
title: "Please help with a Pinnacle HDTV Card (i800?)"
date: 2010-01-07
forum: Mythbuntu
---

### Post by thrylax on 2010-01-07
I am trying to get my Myth box running properly and I believe that my Pinnacle HDTV card, an i800 I believe, may be no good.
I am running a fresh install of Mythbuntu 9.10. and have the HDTV Card hooked up to a DirectTV box via Coaxial Cable.
I have read several posts on the subject and have read the [wiki page for the card here]("http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Card_%28800i%29") and when I got the correct drivers I found that they already were in my /lib/firmware directory.....I read elsewhere that the drivers were not needed for Mythbuntu 9.10 and since I was asked if I wished to overwrite the firmware when I tried to place it there, I assumed that it was true and did not replace them.
Myth Setup sees my tuner correctly and I set it up as a V4L Analog Card as per the wiki, but whenever I try to scan for channels I get nothing and whenever I try to run it in Myth the screen just goes black for a second and then reverts back to the main Myth menu.
Could someone out there please help me determine if I am setting it up correctly or if my card is bad?
Thanks in advance.

---

### Post by thrylax on 2010-01-09
I had an issue with MythBuntu that required me to reinstall the entire system. This time I went with regular Ubuntu 9.10 and then installed MythTV overtop.....got the system itself working OK, but I'm still having the same issue with the TV tuner.
Does anybody have any insight on this......has anybody else had any issues with a Pinnacle Card?
Could someone out there who has a working Pinnacle HDTV card please share your mythbackend-setup info with me for this particular card so that I know if I'm setting it correctly?
Thanks in advance.

---

### Post by thrylax on 2010-01-09
For the record, I am currently using this config in mythbackend-setup.
> Card Type: Analog VL4 Capture Card
Probed Info: Pinnacle PCTV HD i800 [cx8800]
VBI Device: /dev/vbi0
Audio Device: /dev/dsp2
Audio Sampling Rate: None (with Do Not Adjust Volume Unchecked)
Default Input: Television
Can someone please verify for me that this is correct?

---

### Post by crez79 on 2010-01-10
My card (Pinnacle PCTV HD 800i) is set up as:

card type: IVTV MPEG-2 encoder card
Video device: /dev/video0
default input: tuner 1

I am using mine with regular cable since Charter Communications feels the need to encrypt everything but one channel. As far as I can remember I followed the wiki for jaunty and then upgraded to karmic.

---

### Post by thrylax on 2010-01-12
I tried setting the card to various other types, starting with IVTV MPEG-2, but nothing works it seems.
Whenever Mythbackend starts I keep getting errors about the tuner already being in use and the only idea I got for that was to change a checkbox in recording options under the DVB Card Section.....even with that box checked I still could not get the card to start.....I'm starting to think the card is bad now.
Anybody got any advice about what tuner card will give me the least hassles when using it in MythTV?

---

