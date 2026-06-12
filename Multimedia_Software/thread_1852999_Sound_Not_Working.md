---
title: "Sound Not Working"
date: 2011-10-01
forum: Multimedia Software
---

### Post by DaimyoKirby on 2011-10-01
I had a [thread]("http://ubuntuforums.org/showthread.php?t=1845700") stating the same problem, but since then I have installed Xubuntu, and removed Ubuntu, so I felt like the problem, troubleshooting, and solution might be different.

I'm running Xubuntu 11.04.

So basically, my sound isn't working. There is no output whatsoever.
When I run "aplay -l", I get:
```
alden@Laptop:~$ aplay -l
aplay: device_list:240: no soundcards found...
```

Also, I tried installing PulseAudio, and then Gnome Alsa mixer, but neither seem to have done anything, so I've uninstalled them both.

What should I do to fix my sound?

---

### Post by DaimyoKirby on 2011-10-01
bump

---

### Post by syntheticowls on 2011-10-01
Hi,

 I am also experiencing sound issues in Xubuntu 11.04, though I am not sure if my issues are the same as yours. I find that if I restart my computer, the sound turns off. I then have to go into 
Applications / Multimedia / Mixer / and re-select and push up the volume levers on multiple playback options and then click the switches tab and click the headphone checkbox in order for sound to come back on.

---

### Post by Jose Catre-Vandis on 2011-10-01
> **DaimyoKirby said:**
> I had a [URL="[/URL] stating the same problem, but since then I have installed Xubuntu, and removed Ubuntu, so I felt like the problem, troubleshooting, and solution might be different.

I'm running Xubuntu 11.04.

So basically, my sound isn't working. There is no output whatsoever.
When I run "aplay -l", I get:
```
alden@Laptop:~$ aplay -l
aplay: : no soundcards found...
```

Also, I tried installing PulseAudio, and then Gnome Alsa mixer, but neither seem to have done anything, so I've uninstalled them both.

What should I do to fix my sound?

Was this a clean install of Xubuntu 11.04 or install of xubuntu-desktop packages on your existing system?

Try installing alsa-base and alsa-utils from the command line and see what happens...

---

### Post by DaimyoKirby on 2011-10-01
Well, I'm honestly baffled now. I just turned on my computer, and my sound's now working. So I'm just confused...

But anyway, it was a clean install. I made a Xubuntu startup disk on my usb drive, installed it alongside Ubuntu, moved a few personal files from the Ubuntu home folder to my new Xubuntu home folder, and erased the Ubuntu partition.

But I'll still try that.

---

### Post by yaryar on 2011-10-01
I have been having similar issues with my New Sound Blaster X-FI Xtreme. I just completely powered dwn the PC. Pulled the card out rebooted. Then I looked thru the thread:[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) (**** 			                          			 			[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")). I skipped dwn to the part where it says: [SIZE=2]_Getting the ALSA drivers from a *fresh* kernel_[/SIZE][SIZE=2][/SIZE]
[SIZE=2][SIZE=2](1) Remove these packages 	Code:
 	sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
[/SIZE]I then shut dwn the PC and reinserted the audio card.
The card now works upon login.






[/SIZE]

---

### Post by zircon_fox on 2011-10-01
Sorry Dude i didn't try even to work on Xubuntu before :oops:

---

