---
title: "Surround should not be this hard."
date: 2009-10-25
forum: Multimedia Software
---

### Post by bhboyle on 2009-10-25
I have a Asus P5E-VM motherboard that has onboard Intel HDA sound. This has worked well(in stereo using the coax digital) for at least a year now.

My problem is I just hooked up all my surround speakers and only got stereo. I followed guides that talked about changing the "default-sample-channels = 6" setting to 6 and uncommenting this line in the daemon.conf file. 

The instant I do this, sound stops working. I can see audio in the pavmeter application but i get nothing on the output. I have gone into every mixer I can get my hands on and made sure all the volumes are up and that the SPDIF is on, but still no sound. 

As soon as I comment this line again in the daemons.conf file sound returns.

I have tryed adding "options snd-hda-intel" to the end of /etc/modprobe.d/alsa-base.conf, this did nothing.

I have also tryed changing the device settings to every single item in the list in the sounds appication but still no dice.

Relevent details:
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
Linux version 2.6.28-16-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009
64bit ubuntu

root@Trinity:~# lspci
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

Please help, I need surround! I miss it so......

Cheers.

Brian.

---

### Post by bhboyle on 2009-10-25
Can someone please help!  i really need surround.

---

### Post by bhboyle on 2009-11-06
So if anyone cares,this is how i solved this problem.

first I uninstalled Pulse Core in Synaptic Package Manager

Then after a reboot I used the following in a asound.conf file (I must note that i found this in another posting and sadly I do not remember who I got it from but I must thank the individual who made it)

pcm.!default {
 type plug
    slave {
    pcm "spdif"
    rate 48000
    format S16_LE
    }
}

after that all was well. it is important to note that this just "dumps" everything outto the SPDIF out and the amp has to do all the work but that is what i wanted anyway.

I hope this helps othrs.

Cheers.

---

