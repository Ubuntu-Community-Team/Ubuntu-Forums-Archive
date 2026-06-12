---
title: "Live TV Jjittery"
date: 2007-12-10
forum: Mythbuntu
---

### Post by matt_aus on 2007-12-10
Hi everyone,

I am looking at moving my Vista Media Centre across to mythbuntu.

I have spent the whole weekend playing around, trying to get it to work.

Details of my system are:

Mainboard:  Gigabyte 8I865-GME
CPU:  INTEL CEL2.6Ghz
RAM: 1Gb DDR
Video:  ATI Radeon 9550 AGP
TV Card:  Compro DVB-T300
Hard Drive 1: 160Gb IDE (main drive)
Hard Drive 2: 160Gb IDE (Drive to hold Videos/Music etc)
Optical Drive:  DVD Burner

I am able to scan and receive all channels here in Adelaide Australia (have to manually enter in Frequencies for it to work properly, but I can handle this.)

the problem is - when watching live TV, the picture will work for a second, freeze for a second, work for a second... you get the idea.

Sound is fine.

I have tried changing the playback codecs to no avail.

Im sure its not the hardware, as my VISTA system runs on the exact same hardware.

At present im leaving it to run under VISTA, but would like to eventually get my MCE moved over to linux.

any help would be appreciated.

Kind Regards

Matt

---

### Post by tohc1 on 2007-12-12
Try running mythfrontend from a console. When you go to watch TV alt-tab to the console window to look at any error messages being displayed. It might be that you haven't got xv overlay enabled which makes the video drop frames, in which case you'll see something like "no video overlays detected unable to scale video....will drop frames or be slow" (or something along those line).

Hope that helps.

---

### Post by matt_aus on 2007-12-13
thanks tohc1,

I will give that a go, as soon as i have a free moment, and the wife isnt using the mce.

Cheers

Matt

---

