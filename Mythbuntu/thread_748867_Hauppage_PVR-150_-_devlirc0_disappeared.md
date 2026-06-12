---
title: "Hauppage PVR-150 - /dev/lirc0 disappeared?"
date: 2008-04-07
forum: Mythbuntu
---

### Post by Pebby on 2008-04-07
Hello all,

I have been lurking here for a while as I venture into the world of mythtv, ubuntu, linux, etc., and I've been making out pretty well with the info I've found. After spending a good week trying to get the IR blaster on my pvr-150 working, I finally did it, but I still felt confused as to what just happened (or why it worked - I don't like not understanding what I did!). I was at the point where I was just happy to have it working after so much frustration and reading through old/bad instructions.

My mythtv box was happily chugging along, working with the remote and the capture card, until one day, when it booted, the old /dev/lirc0 device was gone, and I couldn't read my remote anymore (since irw failed to find any IR devices). The video device still works, as mythtv still works, but my remote just... vanished. Any ideas on what may have happened or where I can look for debugging?

I already followed instructions on [this page]("http://ubuntuforums.org/showthread.php?t=587732&page=2") back when I was trying to get it to work in the first place.

Additionally, doing 'lsmod | grep lirc' results in this (the 0 in the first line seems odd; I don't think it used to be 0):

```
lirc_pvr150            19764  0 
lirc_dev               15860  1 lirc_pvr150
ivtv                  134928  1 lirc_pvr150
i2c_core               26112  9 lirc_pvr150,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,tveeprom,nvidia,i2c_sis96x

```

The /dev/lircd and /dev/lircm devices are still there, though.

Edit: The machine is running Mythbuntu 7.10 with mythtv 0.21, on a Shuttle FS51g with a 1.8 Ghz Pentium 4-a, with 512MB of RAM and a GeForce 3, if that makes any difference.

Thanks in advance!

---

