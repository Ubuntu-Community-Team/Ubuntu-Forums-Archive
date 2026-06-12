---
title: "mysterious sound problem"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by John Azelvandre on 2007-05-22
I'm having a sound problem I can't seem to figure out.  Upon boot-up, the sound seems not to initialize.  Sometimes a reboot (or 2 or 3) cures the problem.  I thought this might relate to some updates that were applied on Friday.  But I'm not sure, because it happened a few times before that.

I'm using a LinuxCertified laptop.  aplay -l gives me this:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So everything looks normal.  But there is no sound.  No system sounds, and RhythmBox acts as if it is playing, except time in the song doesn't elapse and there is no sound.  I checked volume control, etc, and everything is turned on.

I'm going to try yet another reboot after this post - my sixth this morning!  and see if that does it. ... Any ideas?

---

### Post by John Azelvandre on 2007-05-22
Well, wouldn't you know it, the sixth reboot brought back sound!  (I also reinstalled alsa-base for good measure).

But still, I'd like some feedback.  I bet this will happen again.  Any suggested diagnostics I can perform when it does?

Thanks in advance.

---

### Post by jkflying on 2007-05-22
when it's not working try sudo lshw
look in the hardware listed to see if your soundcard is in there.

---

### Post by John Azelvandre on 2007-06-09
My mysterious sound problem is happening again: no sound on reboot.  sudo lshw gives me the following, regarding sound:

 ```
*-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:febfc000-febfffff irq:16

```

I'll try a reboot and see if it comes back.  In the meantime, any ideas?

---

### Post by mistergq on 2007-06-09
its the 16 kernel that did it.  I am running 15 kernel right now because I have sound with 15.  Something is wrong with the 16 kernel - but it does not seem to be across the board...unless others are not posting.

---

### Post by John Azelvandre on 2007-06-10
Whatever it is, it's not consistent.   A reboot fixed the problem, for now.

---

### Post by mistergq on 2007-06-11
I was hoping todays updates would fix the problem, but I did not see anything installed - like a new kernal - that would.

---

### Post by wondering_jew on 2007-06-11
I have found it to be the case that if I  just restart without shutting down completely I will lose sound, but if i shutdown completely as part of a reboot sound always works when I turn it back on... pretty much been like that for me since warty- see if it makes a difference for you as well.

---

### Post by dys4ic on 2007-06-14
I've been having similiar sound problems on my new feisty install. That the sound just disappears seemingly at random times and xmms and other apps just continues with no problems, but no sound.

I have the hda intel soundcard, lswh:
```
*-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
```


A simple reboot always makes the sound work again so reloading the sound modules etc. will  take care of the problem without at least rebooting.

a simple script like this does that:
```

#!/bin/bash
kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*)
sudo modprobe -r snd-hda-intel && sudo modprobe snd-hda-intel model=auto
```

as posted in this thread: 
[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

---

### Post by utopial on 2007-06-14
try the fresh kernel install:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by malrost on 2007-06-16
Hm, I ran across the same thing today. Weird.

A restart did not work, but shutting it down and powering it back on did.

dys4ic, I tried your commands but neglected to replace snd-hda-intel with the appropriate drivers for my system. I'll give it a shot if this happens again, though.

Sound has been working fine since I installed this a few weeks ago. It was working fine earlier today, then just stopped. I wasn't getting any application error, and audio files would open and appear to be playing --just no sound. The headphone jack was also dead.

I checked this thread [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") but it wasn't useful -- my 2 soundcards were both recognized, a Hammerfall DSP for recording and an Audigy 4 for listening.

I'm not sure if it will help track down this bug, but there was one additional problem I noticed when this occurred. I'm using two sound cards, and have the Audigy 4 set as the default for the volume contol. When I first went to check the volume control the level was completely turned down. I tried to increase the volume using the slider but as soon as I released the mouse the fader would snap back to the bottom.

Then I checked the settings and found that the default sound card had switched from the Audigy to the Hammerfall. I didn't switch this setting, and restoring the Audigy didn't help.

---

### Post by fadastic on 2007-06-19
I've had similar problems before. You have to open up /etc/modprobe.d/alsa-base and set the soundcard you want to use to an index of 0. I believe it usually automatically picks the soundcard, and if you have multiple soundcards it may pick one that you are not using. 

Also what you might want to try is typing "alsamixer" in the terminal and making sure nothing is muted.

I've had to do both before to get my sound working and I had the same problem of having the sound randomly work that you guys are having.

---

### Post by dys4ic on 2007-06-19
Well...I've discovered that this only occurs when playing some mp3 files with xmms, I suppose it  has something to with the sound modules and the hardware output (thus reloading the modules etc. fixes it). Now I've switched to the eSound output plugin and I'm using Beep media player instead (was using alsa and xmms)...and so far so good :)

---

### Post by John Azelvandre on 2007-07-26
The script supplied dys4ic fixes my sound problem.  Wish it wouldn't happen at all, however.  

Could somebody remind how to turn this set of commands into a script/executable file ...?
Thanks.

---

### Post by kubilaycan on 2007-07-27
i shall be the bringer of good news...

i had the same problem. i had 3 soundcards, an audigy, a usb voip phone and onboard sound. the problem was that at each reboot, it would load the devices in random order and then i would sometimes be lucky and have sound. i dont know if you had the same problems as i did, but even if i did not hear any sounds at log in or could not get sound from my main mp3 player, amarok (which did not give any error messages, just no sound), i was still able to hear sound from some other programs such as totem..

anyways, the solution is start sytem>administration>synaptic package manager, search for "asoundconf-gtk" and install it. then run it from system>preferences>default sound card.  you can choose your default sound device no matter in which order ubuntu feels like loading them at start-up.

if this works then i am happy and you should be too. also you might notice that now sometimes you hear the sounds when being asked for your user name and password and sometimes you don't because up until there it is random load. but as soon as you enter them and ubuntu starts, it makes use of the default sound card u selected and you should be hearing everything...

cheers

---

### Post by John Azelvandre on 2007-09-27
I hate to be the bringer of bad news, but the previously mentioned good news does not solve the problem in my case.  The problem remains as originally stated.  Sometimes sound works on boot up, and sometimes not.  This would not be an issue if I was running ubuntu on a desktop that I always kept on, but I am running it on a laptop that I regularly shut down.  

Nor would I expect the asoundconf thing to work -- as I only have one sound card!  Why it fails to be recognized sometimes remains a mystery.  Any further ideas?

---

### Post by dumshi on 2007-09-28
Hi,

If you guys are dual booting then take a look at this

[http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved](http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved)

I ran into similar problem.. and i think it's got something to do with drivers.. m' expecting fix in Gusty :)

---

### Post by John Azelvandre on 2007-09-29
Strictly Ubuntu here -- no dual-boot.  So that's not the problem in my case.

---

