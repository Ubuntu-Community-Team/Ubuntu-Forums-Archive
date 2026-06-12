---
title: "SB Live not working"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by mohnkern on 2007-07-23
I know sounds probably the most common problem people raise here, but I'm at my wits end.

My Configuration:

Ubuntu Feisty
Onboard Audio Disabled in Bios (but Feisty is still seeing it, for some strange reason)
USB Headset
SB Live Value edition audio card (This is where the speakers are plugged into).

I ran the following:
$ sudo asoundconf list
Names of available sound cards:
Headset
V8237
U0x46d0x8d7
Live
$ sudo asoundconf set-default-card Live


and checked the alsa-base file:

$ tail /etc/modprobe.d/alsa-base
#options cx88-alsa index=-2
#options saa7134-alsa index=-2
#options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
#options snd-via82xx-modem index=-2
#options snd-usb-audio index=-2
#options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
#options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-emu10k1 index= -1
mohnkern@Casa-Scott:~$ cd 

However, when I play anything through Amarok, or any other sound player, it doesn't come through the headset, the onboard audio, or the SB Live Card.  

What's really strange is when I run Windows applications in wine, it's coming through the headset.

I know that the system is seeing the sound card, and I can even run a "test tone" out the SB live when I'm running kmix.  I just can't get any applications to use it.

---

### Post by mohnkern on 2007-07-23
Well, after testing some more, the SB Live now won't load:

$ sudo modprobe snd-emu10k1
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.20-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko): Invalid argument
FATAL: Error running install command for snd_emu10k1


Here's the results from kern.log
Jul 23 23:19:21 Casa-Scott kernel: [  640.312000] snd_emu10k1: `' invalid for parameter `index'
Jul 23 23:22:31 Casa-Scott kernel: [  830.000000] snd_emu10k1: `' invalid for parameter `index'
Jul 23 23:24:46 Casa-Scott kernel: [  965.124000] snd_emu10k1: `' invalid for parameter `index'
Jul 23 23:31:37 Casa-Scott kernel: [ 1375.868000] snd_emu10k1: `' invalid for parameter `index'
Jul 23 23:33:21 Casa-Scott kernel: [ 1479.360000] snd_emu10k1: `' invalid for parameter `index'


Amazingly, now the headset is working for everything but windows applications running under wine.

---

### Post by MARIUSmarius on 2007-07-24
Well, i have SB0220 emu10kl and it is also not working for me. Althought it had worked before nvidia driver instalation. Any idea, how to fix this?

---

### Post by mohnkern on 2007-07-24
Have not found an answer, interesting point about the nvidia driver.  Which one are you running?

---

### Post by mohnkern on 2007-07-24
I was able to eliminate the errors by rerunning asoundconf to make some corrections to the file.  So now I don't get the errors when doing a modprobe snd-emu10k1 and Alsa clearly sees the card, kmix can put out a test tone, but applications are still not sending sound out to the card.

---

### Post by chaos2286 on 2007-07-24
yeah have the same driver and it doesn't work either.  had to remove the card and use the less than stellar onboard sound

---

### Post by mohnkern on 2007-07-24
The following is purely anecdotal evidence, based upon one reboot, however, I have my SB Live card working currently.


from the prompt I typed:

sudo nvidia-xconfig

Then I rebooted.


There is zero, I repeat zero reason why this should work at all, and was purely based upon someone's statement that They had the problem between an Nvidia card and an Sblive.

Audio is currently working through Amarok.

If there's someone else reading this that is running an Sblive and an Nvidia card, and they try this, I'd like to hear their results.

---

### Post by MARIUSmarius on 2007-07-25
Thank's mohnkern. It worked for me. I hope, that i don't have t odo that after every reboot :))

---

### Post by mohnkern on 2007-07-25
Just wanted to confirm.  You're running an SBLive audio card, and an Nvidia video card, and running nvidia-xconf solved your problem?


We may actually have a solution to a oft-existing problem.

---

### Post by theorganloft on 2007-07-25
I found that when my system booted the SB Live always took sound 0 (zero).  I edited modules to force the card to Sound 1 and also added the options list that did not allow that driver (snd-emu10k1) to ever select Sound 0. I wanted my on-board VIA sound to use for playback and I use the SB-Live for recording. 

I am not in front of my system to give an example of the modules file but look through this forum for no sound. It is a common problem but very fixable.

Going back to the basics is important.  Start with lpci -a command to determine if your card is actually there.  Move on to Alsa-mixer, the examine your alsa-base/modules configuration.  

Remember that if you have hardware conflicts, your card cannot sound.

---

### Post by mohnkern on 2007-07-25
I had actually done all of that, and until I did the nvidia-xconfig none of it worked.

(It was really annoying because alsamixer was seeing the card, and I could even run test tones through it in Kmix)

---

