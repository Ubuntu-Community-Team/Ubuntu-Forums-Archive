---
title: "Configuring for HDR-1250"
date: 2016-09-03
forum: Mythbuntu
---

### Post by scharkalvin on 2016-09-03
In the Capture Card config section I am seeing my Hauppauge card under several sections:

for DVB-t/s/c atsc tuner cards I see it as /dev/dvb/adapter0/frontend0 (I think)
for V4L2 encoder I see it as /dev/video0 and it lists the card "wintv-hvr1250 [cx2385] as the probed device
for analog to mjpeg encoder (matrox200 ...)  I see it as /dev/video0 and it lists the card type as above.
So what do I select?

Also I have TWO of these cards plugged into different pcie/1 slots, but only one shows up in /dev and in lspci.  Could one be defective, or is it not possible to have two cards in the same PC?  (I could try plugging on into the pcie/8 slot as I am not using a video card as the motherboard has built in graphics that are good enough for a front end.)

---

### Post by scharkalvin on 2016-09-04
I configured both the DVB and V4L2 options and now have 4 capture cards (each card is two modes).
I see that only the DVB 'cards' are tuners, the V4L2 'cards' are analog capture-no tuner.  Since the HVR-1250 analog options are reported not to work under linux (can't use the analog input jacks on the card), I guess those options won't be used.....

And it seems that the reason I only saw one card is that my low profile computer case has a thin metal back that was bowed backwards when I connected the coax cables to the cards lifting one of them out of the PCIe socket!  Think I'll need to jam a piece of foam between the cards and the lid of the computer case to keep them in place.

---

