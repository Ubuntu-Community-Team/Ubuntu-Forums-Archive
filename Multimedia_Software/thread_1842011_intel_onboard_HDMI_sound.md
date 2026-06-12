---
title: "intel onboard HDMI sound"
date: 2011-09-10
forum: Multimedia Software
---

### Post by brawlz33 on 2011-09-10
Hey guys,

Total noob when it comes to Ubuntu and Linux, I've played around with terminal a bit and am not afraid to try new things even if it messes the comp up (fresh install).

Anyways i have an Intel DH67CF with a i3 2100t and 4 gigs of ram. I would like to use the onboard HDMI as i am trying to keep this machine low power as a HTPC comp. Well anyways i have beautiful video, but as a lot of people seem to find i have no audio. Ive done tons of research and have messed around with quite a few settings, but i still can't seem to get sound. 

Alsamixer options are all unmuted. I do a aplay test and i get sound from 0,7 port, but to be honest I'm not sure where to go from there i can't fine around.conf or any of the other seemingly important files to edit (do i create them?)

But I'm kind of stumped here and could really use some help 

Thanks in advance ):P

Justin

---

### Post by brawlz33 on 2011-09-10
Bump for help

I'm sure it's something simple that I'm overlooking

---

### Post by selectedusername on 2011-09-11
What does aplay -l give you?

---

### Post by brawlz33 on 2011-09-13
aplay -l gives

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Justin

---

### Post by Pariah819 on 2011-09-14
Try to run the command line version of alsamixer (at terminal type "alsamixer"), check all the way to the right screen and see if there is a channel called SPDIF.   If there is make sure it is unmuted.  I had this problem on an HTPC build I did a while back, for some reason this channel doesn't show up in the graphical version of alsamixer.

---

### Post by humbfig on 2012-01-31
Hi!
Was wandering if this issue has been solved....
I also have a DH67CF with a i3-2100T and can't get the sound to work in Ubuntu 11.10
This is a bit frustrating because I built this computer to work as a HTPC.

Facts:
1) No sound stream is ouput from hdmi. My AV amp detects no stream. Video is OK.
2) I know there's no hardware problem because the system was tested under Windows7. The sound outputs from hdmi, 7.1, no problem.
3) aplay -l gives the same result as posted in this thread.
4) running alsamixer, all seems ok. I have no muted SPDIF.
5) dmesg | grep sound gives nothing.
6) restarting sound driver "snd-hda-intel" makes no difference.
7) unistalling and reinstalling sound makes no difference.

Anyone can help me?
thanks

---

