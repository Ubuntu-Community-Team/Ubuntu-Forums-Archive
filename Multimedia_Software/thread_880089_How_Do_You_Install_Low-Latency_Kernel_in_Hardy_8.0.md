---
title: "How Do You Install Low-Latency Kernel in Hardy 8.04 (x64 amd) ?"
date: 2008-08-04
forum: Multimedia Software
---

### Post by Nitroadict on 2008-08-04
I've been reading that for audio playback & production stuff, a low latency kernel might make things much smoother & faster.  I mainly use TuxGuitar, Audacity (splitting mp3's etc.), and Wine for Guitar Pro 4 & 5, and until I messed around Timidity's settings, MIDI playback was a bit choppy.  It's much more bearable now, but I still notice it's not as smooth as I'd like it.

I was wondering how does one go about to installing a low-latency kernel?  

I was considering installing UbuntuStudio at one point, but when I read you don't need it to install the low-latency kernel, I lost interest. 

Thanks :).

---

### Post by treehouse on 2008-08-28
[Look here](http://ubuntuforums.org/showthread.php?t=897783)


Edit:
[Also approriate, the Ubuntustudio upgrade doc](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy). 

[code]
#low-latency kernel
sudo apt-get install linux-rt
#typical audio programs
sudo apt-get install ubuntustudio-audio
#audio plugin package
sudo apt-get install ubuntustudio-audio-plugins

---

