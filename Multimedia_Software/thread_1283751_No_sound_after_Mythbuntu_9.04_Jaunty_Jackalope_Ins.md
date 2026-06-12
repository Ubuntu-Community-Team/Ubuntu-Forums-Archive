---
title: "No sound after Mythbuntu 9.04 Jaunty Jackalope Install"
date: 2009-10-05
forum: Multimedia Software
---

### Post by mythuser on 2009-10-05
Hi all,

I recently configured a spare PC for a media center and installed Mythbuntu 9.04. After the install, everything appeared to work decent; the video was a bit sluggish, and over the air HDTV reception was much worse than my $40 Zenith DTV converter box. I managed to speed up the video by decreasing the video quality; I guess my hardware is not fast enough for it. 

AMD Athlon XP 2800+ 
2GB RAM 
NVIDIA 512MB Video Card
pcHDTV 5500

Flash video looks better than my brand new Intel Centrino Notebook, so video is no problem, but there is **NO SOUND.** I had sound a couple of days prior with a standard Ubuntu 9.04 install, but it does not function with Mythbuntu 9.04. I tried several comprehensive sound guides with no success.

Here is some information on the problem:


```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
``````
$ sudo asoundconf list
[sudo] password for user: 
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
CX8801
```I've also tried purging:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
``````
$ sudo lspci -v
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Flags: medium devsel, IRQ 22
    I/O ports at c000 [size=256]
    Capabilities: [c0] Power Management version 2
    Kernel modules: snd-via82xx
```I've tried countless other methods, but it's really just me guessing and seeing what happens.. not very effective so far. I've used Linux for a couple years now, and it seems like such a simple problem would only take a few minutes to fix, but I've spent at least 6 hours trying to get it to work. I just started a comprehensive Linux intro [book]("http://www.amazon.com/Introduction-Linux-Hands-Guide-Beginners/dp/1440471010/ref=sr_1_2?ie=UTF8&s=books&qid=1254792554&sr=1-2") (no I don't work for Amazon/the Author), so hopefully that'll teach me how to fix this on my own in the future.

Any advice on the issue is appreciated!


-Mythbuntu user

---

### Post by mythuser on 2009-10-08
No one?

---

### Post by mythuser on 2009-10-10
reposted: [http://ubuntuforums.org/showthread.php?p=8084700#post8084700](http://ubuntuforums.org/showthread.php?p=8084700#post8084700)

---

