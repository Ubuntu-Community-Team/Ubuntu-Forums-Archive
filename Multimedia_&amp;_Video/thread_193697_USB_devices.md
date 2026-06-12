---
title: "USB devices"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by falkenberg_cph on 2006-06-10
Hi
Phew, i have had endless problems trying to go from Xp to ubuntu. I actually ended up reinstalling xp in a rage against ubuntu. But now i will try a less radical installation, where i keep xp on one partition.

Here are some problems i came upon, when trying to follow the well written breezy studio setup guide. As a complete newbe the whole ubuntu/linux universe was quite confusing. I hope you can comment on my notes:

1. Being unsure if a managed to install the patched vanilla kernel. How do i check it.

2. How low latency can i get with ubuntu studio. Right now i have less than 2 msec input in cubase.

3. When i installed ubuntu studio it only showed jackd and 2 other programs, not the whole bunch. Even though it clearly was installed. Why is that.

**4. Jackd never managed to communicate with my soundcard. I have a Lexicon Omega usb audio-interface. It has no Linux drivers. How do i install and use it with ubuntu studio - I really feel usb interfaces needs a special remark in the setup guide.**

I hope you can help. Particularly with number 5
Thank you very much

Carsten

---

### Post by balleklorin on 2006-06-11
I'm having a bit problems with usb audio devices too, the first thing is latency... even with the RT kernel installed USB latency doesn't impress me very much, windows actually has just as god latency, which is weird with the RT kernel. 

I'd like to see some guide on how to improbe usb latency, I've been fiddeling around with nrpacks etc but it doesn't seem to change anything.

I've got some problems with jack when used from qsynth it will halt midi playback from rosegarden after a little while, if I bypass jack and use the alsa or oss driver inside qsynth it works alright...

---

### Post by bwanab on 2006-06-15
[QUOTE=balleklorin]I'm having a bit problems with usb audio devices too, the first thing is latency... even with the RT kernel installed USB latency doesn't impress me very much, windows actually has just as god latency, which is weird with the RT kernel. 

I'd like to see some guide on how to improbe usb latency, I've been fiddeling around with nrpacks etc but it doesn't seem to change anything.

I've got some problems with jack when used from qsynth it will halt midi playback from rosegarden after a little while, if I bypass jack and use the alsa or oss driver inside qsynth it works alright...[/QUOTE]
This doesn't make sense to me. I use a laptop with non-rt kernel with a usb interface and it works very well. My suggestion is to post the specifics of what you're seeing on the linux-audio-users mail list. There are people who know this stuff very well on that list.

---

### Post by dolson on 2006-06-15
Ubuntu Studio Launcher is just that, a Launcher. It lists music apps that you have installed. It is not a virtual package that depends on tons of other software that you may or may not want. Please run `man ubuntustudio`

---

