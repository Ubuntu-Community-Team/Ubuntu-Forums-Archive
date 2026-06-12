---
title: "sopcast sound not working with 14.04"
date: 2014-04-23
forum: Multimedia Software
---

### Post by brendan5 on 2014-04-23
Hi there,

I have a full buffer on sopcast, but the audio cuts out.  The video is good.  The strange part is, while sopcast is loading, the sound works intermittantly (when ~30% buffer, you hear scraps of audio), but when it gets to 100%, nothing.

Any ideas? Thanks!

---

### Post by Dmitry_Veselov on 2014-05-17
The same for me
Anyone can help?

---

### Post by dvwiz on 2014-07-20
I have exactly the same problem as the OP. Though it should be noted that it is only true for most, not all, sopcast streams. 
In the terminal I always see these errors for the affected streams:

> 
mpgatofixed32 audio converter error: libmad error: bad main_data_begin pointer

ts demux error: libdvbpsi (PSI decoder): TS discontinuity (received 14, expected 9) for PID 17



Any help would be much appreciated :D

edit: Ubuntu 14.04 64 bit and the relevant packages are sp-auth 3.2.6, sopcast-player 0.8.5, vlc 2.1.4

---

### Post by fudo_999 on 2014-08-06
i have found a solution, it is only temporary but can help you until someone finds a better one
copy the stream from vlc and open another vlc window and play it with "open network stream" option. Both vlc windows must remain open.

---

### Post by bachwerm on 2014-08-23
Nice, that worked for now at least. Looking forward to a real fix.

---

### Post by jempa333 on 2014-11-09
Found a solution;

Play stream in VLC

In VLC, change audio to Alsa, Pulseaudio soundserver

Save, restart vlc

Should work....

---

### Post by martins-k on 2015-08-18
I can confirm, jempa333 solution work.
I have Ubuntu 15.04 x64.

---

