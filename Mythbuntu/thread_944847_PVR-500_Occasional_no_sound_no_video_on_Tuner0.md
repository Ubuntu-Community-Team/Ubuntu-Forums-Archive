---
title: "PVR-500 Occasional no sound no video on Tuner0"
date: 2008-10-11
forum: Mythbuntu
---

### Post by mjsameth on 2008-10-11
Thanks for taking the time to read this post.  This is a little bizarre - but curious if anybody has any recommendations.  

I have a working mythbuntu installation AMD64 Athalon, PVR-500, HDHomeRun.

The only things that have changed before my problem arose was the fact that yesterday I did a sudo apt-get update & sudo apt-get upgrade.  Juse a couple of packages installed.

Problem:

On boot-up both tuners are working fine.  No problems.  However, when running rhythmbox or firefox on the desktop or inside a ssh session - I find that one of my tuner inputs will not display audio or video.  I simply switch inputs to other tuner and everything is fine.  However, I am now limited to one working tuner.  A reboot will always clear the problem.  Both tuners will work.  But it is highly repeatable.  Running audio in firefox or for that matter any other non-myth application causes one of the tuners not to display sound and audio.  

Any suggestions?

Thanks for taking the time to respond.

---

### Post by ian dobson on 2008-10-12
Hi,

Do you see anything in syslog when you lose sound? 
What happens when you lose sound, then unload the ivtv drivers then reload them again?
What motherboard/chipset do you have? There were some DMA problems with VIA chipsets.

I'm running a PVR-500 in my MythTV backend and haven't seen any problems.

Regards
Ian Dobson

---

### Post by mjsameth on 2008-10-12
Thanks for reply.  I checked the syslog at the times that I ran the applications and their doesn't seem to be anything related to the pvr500 or anything else for that matter related to the problem I have described.

I currently have an asus m2n-sli motherboard.  Could you provide the commands for loading and unloading ivtv drivers.  Little unsure about syntax.  Don't want to make my media center unusable.

---

### Post by ian dobson on 2008-10-12
Hi,

Use rmmod to remove loaded modules (rmmod ivtv).
Use insmod to insert modules (insmod ivtv).


Regards
Ian Dobson

---

### Post by mjsameth on 2008-10-12
No change and unless I'm really stupid - following those commands caused me to have to reinstall ivtv from source... once removed  - I couldnt insmod ivtv - I'm back up and running - but still have this oddity - not sure what else to do....

---

### Post by ian dobson on 2008-10-12
Hi,

Humm thats strange, maybe you can use modprobe. See [http://en.wikipedia.org/wiki/Modprobe](http://en.wikipedia.org/wiki/Modprobe)

On my box I increased the mpgbuffers by creating a file (/etc/modprobe.d/ivtv.conf) with the following line:-
options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2

To help with buffer overruns when recording 2 programs at the same time with a "high" quality.

Regards
Ian Dobson

---

