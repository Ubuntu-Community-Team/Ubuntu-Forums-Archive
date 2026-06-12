---
title: "NOVA T 500 Remote How"
date: 2008-07-24
forum: Multimedia Software
---

### Post by hairshirt on 2008-07-24
Hello all

Has anyone managed to the get the Huap. Nova T 500 remote control FULLY working as per the buttons on the remote.  If so, how and what was your information source?

Had a look at the parker1 website (it's ok but many of the screen shots are out of date.)  Anyway ... got the card working but the links on the page, in particular, the link to the other web site (MythTV I think) appears to be irrelevant as (from what I understand) the card and remote is supposed to be fully supported in hardy, so no need to re compile the kernel (which I have done in the past but with little success regards the remote itself)  ...  any ideas, info, pointers and or advice.

I do NOT wish to use Mythbuntu.  I want to install MythTV on a new install of Hardy.

Many thanks.

PS. Also - sound is routed through fiber optic SPDIF to Amp for all sound from PC.  Can never seem to get the remote to control sound.  Is there a way and if so, how.  Some silly person some time ago on another post said: "that's the way it should be".  I disagree as I and I'm sure many others don't want to keep crossing the room to adjust the volume and mute sound.  Sort of defeats the whole object really.  Thanks again.

---

### Post by hairshirt on 2008-07-25
BumP ... 

This is becoming par for the course here at Ubuntu Forums.

---

### Post by xc3RnbFO8P on 2008-07-25
Did you se this:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500")

---

### Post by hairshirt on 2008-07-25
Thanks for the pointer ... no, I haven't read this page.  Reconstipation of the kernel means no more kernel updates for me, does it not?  From my understanding, could cock things up if I do a: apt-get dist-update - or am I wrong?

Thanks.



> **Ringi said:**
> Did you se this:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500")

---

### Post by hairshirt on 2008-07-25
Anyway, don't have a problem with the card itself ... only the remote (programing ALL buttons on the remote).


> **Ringi said:**
> Did you se this:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500")

---

### Post by xc3RnbFO8P on 2008-07-25
> From my understanding, could cock things up if I do a: apt-get dist-update - or am I wrong?
You never know,I find it best to make a fresh install.

---

### Post by wyliecoyoteuk on 2008-08-04
There are more than one version of the Nova-T500 remote.

You really need to look at the Lirc information.
I use a Nova-T500 and a Nova-T100, the remotes look identical, and use the same codes, but have different timings.(I have also noticed some config files on the net have the wrong codes, so there are probably more variants).
I used irrecord to create the config files for each.
Then you need to set up a local config file in your home directory with the mappings for MythTV (or any other app). Mythbuntu does most of this automatically.

To get the tv, video, etc buttons working, you need to set kepmappings in MythTV

The section on Lirc config here is helpful.
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

---

### Post by hairshirt on 2008-08-16
Thank you wyliecoyoteuk

This looks very useful indeed.

I'll that a go

Another thank you to you and all

---

### Post by Tom Mann on 2009-05-11
I don't know if it's worth mentioning, but there was a problem a while back with the up, down, left and right buttons registering twice per press...

Please check the following link for a fix :)

[http://ubuntuforums.org/showthread.php?t=763739]("http://ubuntuforums.org/showthread.php?t=763739")

---

