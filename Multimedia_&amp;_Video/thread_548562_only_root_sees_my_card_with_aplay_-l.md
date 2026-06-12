---
title: "only root sees my card with aplay -l"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by mkramer on 2007-09-11
**SHORT PROBLEM SUMMARY**: After sufficient tinkering, ALSA now fails to detect my card while running as kramer, the regular user, but succeeds as root.  Purging and reinstalling ALSA drivers does not fix the problem.

**EDIT: ONE PROBLEM SOLVED**.  Changing the audio line in /etc/group to audio:x:29:kramer solved the issue of ALSA failing to detect my card as kramer.  However, still no sound.  (ALSA now thinks it is playing tracks, but no sound.  The usual fix, which is to disable the digital audio jack in alsamixer, doesn't fix my problem).

I've been trying to configure sound in my Fiesty 7.04.  I have been relying heavily on this troubleshooter: [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+card](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+card).  From the fresh install, aplay -l successfully detected my SB Audigy 1 (SB0090) card.  However sound didn't work and after sufficient tinkering, ALSA now fails to detect my card while running as kramer, the regular user.
```

kramer@hatha:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
...
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
...
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

kramer@hatha:~$ aplay -l
aplay: device_list:222: no soundcards found...

```

Things I have tried after forum searching. 
**#1 Group membership**
kramer is a member of the audio group:
```

kramer@hatha:~$ cat /etc/group | grep audio
audio:x:29:kramer:root

```

**#2  ~/.asoundrc**
~/.asoundrc - have commented out the line that includes ~/.asoundrc.asoundconf
Many users with sound blaster cards got their sound to work after commenting out the line in ~/.asoundrc.  This did not work for me.

**#3 Purging ALSA and reinstalling from scratch**
This code comes from the troubleshooter linked at the top of this post.
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
Does not work

**#4 /etc/asound**
A post somewhere told me to delete this file, but it did not exist on my host.
[B]
#5 Manually configure /etc/modprobe.d/alsa-base[/B] with the name of my sound module 
from: #2 [http://ubuntuforums.org/showthread.php?t=480723&highlight=.asoundrc](http://ubuntuforums.org/showthread.php?t=480723&highlight=.asoundrc)
This did not work.  (if you found this thread searching SB Audigy 1 problems, I wonder if you know the name of the correct driver?  This [ALSA's Wiki Page]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") lists emu10k2 as the name, however, that driver does not exist when I run dpkg-reconfigure.  Therefore I'm using snd-emu10k1 and snd-emu10k1x.)

#6 Compiling from scratch
I haven't been able to compile the ALSA drivers from scratch.  (I keep getting errors).  Since root correctly detects ALSA, I don't think the drivers are actually the problem, and I gave up trying to compile from scratch after an hour.  Instead I have made this post...I'll keep you updated if I figure anything out.  In the meantime, help is appreciated.

---

### Post by flint_ on 2007-09-11
I have a similar problem, in that the LTS installations I do allow the prime user to sound but no one else.  I am going to try your idea of adding them to the audio group and see what happens.

Thanks and...

Kindest Regards,

Flint

---

