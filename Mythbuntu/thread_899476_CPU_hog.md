---
title: "CPU hog"
date: 2008-08-24
forum: Mythbuntu
---

### Post by jensk on 2008-08-24
I have a setup with a backend in my basement and several laptops as frontends. Laptops configured with Ubuntu 8.04 and Mythtv Frontends through 802.11g network to backend - great setup showing very good quality of both tv and recordings.

In the living room I am using an IBM tower - 2Ghz P4, with 512 Mbyte ram, Nvidia 6200 based video out through DVI-HDMI to my Philips lcd tv - resolution 1280x768. The living room pc is connected via 100Mbit/sec wired network to the same network as the backend.

My problem is that when showing tv og recordings on the living room frontend the video is stuttering or should i say jumping frames ever now and then.

If I run top on the living room frontend it shows that CPU is running above 1.00 (sometimes 2.5) so the jumping of frames must be the frontend attempting to hang on to the video stream from the backend.

Myth is configured to utilize "stream from backend" on both the living room frontend and on the wireless laptops.

I have tried to scan through the forums and the mythtv forum to get informations on this topic but couldn't find a solution to fix this.

I should mention that i have enabled the Nvidia restricted driver so i should be using the proprietry Nvidia driver.

Actually I thought that the Nvidia card had onboard MPEG2 decoding but it looks like in an using CPU based decoding in stead. How do i switch to use hardware decoding on the Nvidia in stead of sw decoding.
/jk

---

### Post by ian dobson on 2008-08-24
Hi,

What play back profile are you using?

My 1.8GHz Core2Duo with a 7300LE only uses about 10-15% cpu (from top) when watching SD video.

If you enable xV in your playback profile Myth with use the hardware acceleration from the graphic card.

Regards
Ian Dobson

---

### Post by jensk on 2008-08-24
Thank you for the quick reply.

I enabled the playback profil CPU-- and moved the XvMC 720x576 (i live in Pal teritory) to the top (#1) and the ivtv to the bottom.

CPU top now say 0.5 average CPU util.

Do you know if I have to enable the deinterlace or does the Nvidia proprietary driver deinterlace it self.
/jk

---

### Post by ian dobson on 2008-08-24
Hi,

From what I know the Nvidia driver doesn't do deinterlacing. 
Try out the various deinterlacers to find which one gives the best display/cpu usage on your box.

Regards
Ian Dobson

---

### Post by jensk on 2008-08-26
I will try different deinterlacing methods on Nvidia TV-out.

I am a bit suprised over the CPU load even without deinterlacing. 

When i used the PVR-350 Tv-out the load on the CPU was very low

Nvidia nondeinterlaced CPU load = 0.5
PVR-350 deinterlaced CPU load = 0.2

Strange figures since the picture quality was a little better using PVR-350 Tvout.

To bad my PVR350 tv-out wouldn't work under Mythbuntu. Had it running under Knopmyth but wanted to shift to mythbuntu all together for both frontends and backends :(
/jk

---

