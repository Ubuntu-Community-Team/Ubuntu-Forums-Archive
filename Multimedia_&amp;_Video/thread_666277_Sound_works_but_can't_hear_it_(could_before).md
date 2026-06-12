---
title: "Sound works but can't hear it (could before)"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by mgp on 2008-01-13
WAS: Sound works but can't hear it (could before)

Hi,

I installed Kubuntu recently. Sound worked fine. After a few reboots and software installs I lost the sound. Everything works fine, the players actually play the sound but I just can't hear it. After trying to solve it without success I decided to reinstall kubuntu. It all worked fine again. Until on y 3rd reboot (having installed a few packages) I have the same problem. I've been through most of the threads to solve sound problems and in most cases similar problems to mine are solved by unmuting, but my sound doesn't seem to be muted. 

Following the sound problem thread: [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound")

```
mgp@magpie:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I reinstalled alsa just in case:

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

and rebooted and still no sound.
Then checked alsamixer and saved settings
```

sudo alsactl store 0

```

Does not solve the problem.
To end I try:
```
mgp@magpie:~$ cat /proc/asound/modules
 0 snd_hda_intel

```

So I have a sound card and it works. Amarok actually plays it and the visualization moves according, but I can't hear it.I really don't know where to go on from here.

Thanks for your time,

Michael

---

### Post by balaknair on 2008-01-13
Try this first
sudo modprobe snd-hda-intel

Usually this should get your sound working, even if it doesn't, finish the following steps and reboot- chances are it'll be OK after restart.

 Next find what codec your card uses
cat /proc/asound/card0/codec#* | grep Codec


Then go to this page and find the descriptions for your codec
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)
Choose the description which matches your system the best

Then in terminal
sudo nano /etc/modprobe.d/alsa-base

Scroll down to the end of the file(with your down arrow key) and paste this line as the last line
options snd-hda-intel model=MODEL

Replace MODEL with the dsecription you selected earlier(laptop, laptop-hp or laptop-eapd)

Reboot

For further details see [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) from which I got these instructions.
Please reply and tell me how it went(if it doesn't work, mention what happened)
All the best

---

### Post by mgp on 2008-01-13
Hi,

Thanks for the reply. Unfortunately I have already reinstalled kubuntu yet again. I didn't format my /home partition and after reboot on the new system I didn't have any sound. So I figured out some config in my home directory was what was wrong. Removing a few sound related files (i.e. all of .kde and other .things that I thought I could be related to sound). Rebooted and got sound back. That does not mean I fixed the problem as probably the configuration problem was inhereted of me trying to fix the sound before the reinstallation and the installation is what solved the original problem. However, I have the suspicion that the sound will fail again soon and then I promise to come back and finish off the thread to help other users. Thanks again for the reply. I will not set the thread as solved yet. I'll wait a few days and see if I get the problem again, if not I'll set it as solved. Thanks for the help.

Michael

---

### Post by balaknair on 2008-01-13
OK
I got similar issues(everything seems to play, aplay -l etc all give the correct output, but I hear no sound) just after I made the earlier post. It started after I installed Pulseaudio, it seemed to break the ALSA-OSS module, so I uninstalled pulseaudio. The sound was still working after that, but when I adjusted the volume with alsamixer I lost sound(though Amarok continued to play in the background, and it wasn't muted, I just wasn't hearing anything). Rebooting restores sound and it works as long I don't touch the volume control.
I aim to get down to fixing it, just not now(got work to do, exams in Feb to prepare for). So  I'll check this thread later- it just might be of use to me too.
Thanks, and wishing you luck
bye

Update: I started up my system this morning and things were back to normal and all channels and speakers worked even without me changing anything. the only thing that doesn't work now is I can't bring up alsamixer with the CLI- get something like
 *** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

I can live with that for now. I'll troubleshoot later after my exams.

---

### Post by mgp on 2008-01-15
Figured out what triggers the problem. It happens when I boot in Windows and then boot back in Linux. Obviously the configurations in /home had nothing to do with it. Someway or another windows mutes the card. Futhermore, and following the instructions on the webpage you suggested it seems that my model is not supported:

```
mgp@magpie:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20549 (Venice)
```

I even compiled alsa-lib and alsa-utils. Alsa-driver copilation fails.

I've also found:
[http://ubuntuforums.org/showthread.php?t=608664#post3769008]("http://ubuntuforums.org/showthread.php?t=608664#post3769008")
Bad news :( ... but mine initially worked! so does not seem to be the same bug.

Now I'm following this tutorial that is for a laptop similar to mine:
[ http://ubuntuforums.org/showthread.php?t=455147]("http://ubuntuforums.org/showthread.php?t=455147")

I'll report back.

Michael

---

### Post by mgp on 2008-01-15
From the last article, after recompilng my alsa  found:

"""
2. There is still an issue unresolved, the 'no sound after a windows session ' and can be fixed by unplugging the power cord before booting Ubuntu. If it doesn't work, reboot again with no power cord.

There's no solution for the 'no sound after Windows yet, but:

2.1 If you are in Windows unplug the AC cable and plug it back after you logged into Ubuntu.
2.2 If you are already on Linux after a Windows session and you didn't follow point 1.1estat, Unplug the AC cable, then SHUTDOWN , not restart the computer. Start it again manually and plug the cable back after you logged into Ubuntu
"""
Or also:

The guy in this thread has the same problem as me. Seems there is a few bugs with alsa and acpi.

[http://ubuntuforums.org/archive/index.php/t-493196.html]("http://ubuntuforums.org/archive/index.php/t-493196.html")

So I am going to reinstall and keep the original drivers and use the fixes when I boot in windows. I'll set the thread as closed and will change title from "Sound works but can't hear it (could before)" to "No sound after windows boot". Thanks again for the help.

Hope this helps someone else.

Michael

---

### Post by balaknair on 2008-01-15
Yes that is a possibility. wonder if anyone's filed bug reports about this
Anyway, glad to hear you've got your problem under control(at least partially)
All the best.

---

