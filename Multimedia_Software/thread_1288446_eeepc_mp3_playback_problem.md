---
title: "eeepc mp3 playback problem"
date: 2009-10-11
forum: Multimedia Software
---

### Post by ackray on 2009-10-11
eeepc 900A
2 gig ram
60 Gig SATA

New UNR installed.

installed miro.

Installed VLC.

Downloaded videos from miro are saved as a .mp3 file.  however neither miro or VLC will play them.  I thought I had added the unsupported codecs from the repository but I must still be missing something.

Thanks.

Edit note: In both cases I can hear the audio but no video is displayed.

---

### Post by Sven6210 on 2009-10-15
I had this problem half a year ago when I installed Ubuntu 9.04 on my EeePc 900a. Actually I was looking for an easy way to watch xvid compressed videos with Ubuntu. The easiest and smartest way I found was the following:

I deinstalled 'totem-gstreamer' using Synaptics and the I installed 'totem-xine'. Xine brought along the codec for xvid and after I installed it I did not have any more problems. And using xine I can even scale the sice of a video by using 'Ctrl' and '+' or '-'.

I only tried VLC once but did not like it as much as using the 'totem-xine' engine.

Please let me know if you want a more detailed installation manual and I will send it to you.

---

