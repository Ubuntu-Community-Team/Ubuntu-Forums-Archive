---
title: "Having video playback issues in web browsers"
date: 2011-03-27
forum: Multimedia Software
---

### Post by ImageJPEG on 2011-03-27
For example, sites like YouTube, the video lags horribly...sometimes it doesn't lag at all. I am also using HTML5 in Google Chrome. It does this in both Chrome and Firefox. I'm running Ubuntu 10.10 64 bit. I use to have the 64 bit Flash plugin but I'm now using the one you can get with the package manager. The audio in the videos play just fine...it's just the video.

It does this in both Flash and HTML5 videos. I even edited my ondemand file and added this line:

for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
do
[ -f $CPU_THRESHOLD ] || continue
echo -n 15 > $CPU_THRESHOLD
done

With no luck...the guide even told me to set it to 40% but that didn't do jack...so I tried 15% with no luck.

Here's the output from dmesg:

[60291.027442] npviewer.bin[4021]: segfault at 30 ip 00000000f5e25dad sp 00000000ff9c85f0 error 4 in libflashplayer.so[f5dcb000+b5f000]
[61064.158768] ptrace of non-child pid 4144 was attempted by: gdb (pid 4148)
[62767.657511] lo: Disabled Privacy Extensions
[67841.503918] lo: Disabled Privacy Extensions
[67987.090977] npviewer.bin[4617]: segfault at 0 ip 00000000f61ed8d1 sp 00000000ff9a0790 error 4 in libflashplayer.so[f5e25000+b5f000]
[70368.979560] npviewer.bin[5314]: segfault at f57b30ac ip 00000000f619d8e7 sp 00000000ffbd9d90 error 4 in libflashplayer.so[f5dd5000+b5f000]

---

### Post by ImageJPEG on 2011-03-28
bump

---

### Post by ImageJPEG on 2011-03-30
bump

---

### Post by ImageJPEG on 2011-04-01
[http://www.youtube.com/watch?v=tj9VelE6ckI&feature=channel_video_title](http://www.youtube.com/watch?v=tj9VelE6ckI&feature=channel_video_title)

This is my issue that I'm having.

---

### Post by |{urse on 2011-04-01
This is not a solution to your flash issues but you could always use the html5 version of youtube until you get things working correctly.

> [http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by wolfen69 on 2011-04-01
> **|{urse said:**
> This is not a solution to your flash issues but you could always use the html5 version of youtube until you get things working correctly.

Please read previous posts more carefully next time. The OP wrote that it's the same with flash *and* HTML5.

Did you install gnash by any chance?

---

### Post by |{urse on 2011-04-02
Ah yeah thx.

---

### Post by ImageJPEG on 2011-04-03
Nope, I have Adobe's Flash player currently installed.

---

### Post by ImageJPEG on 2011-04-04
bump

---

### Post by wolfen69 on 2011-04-04
What about regular videos? Do they play well?

---

### Post by ImageJPEG on 2011-04-06
Yes, I have normal play back with regular videos on the computer.

---

### Post by fsancho on 2011-09-05
I have the same issue. Please, try again to play regular file videos in your computer. I have the same problem, just like web browsers.

I have an Nvidia 8400GS with latest drivers 280.13, in Ubuntu 10.04 X64 and a double monitor configuration. Everything works ok but the video. I have spent hours finding a solution, but nothing have worked.

It's not a problem of shared interrupts. I have had Nvidia Card sharing an interrupt with ehci_hcd:usb1, but now I have Nvidia Card alone in a PCI-MSI-edge interrupt and the problem goes on.

It's not a Adobe Flash problem because all video players in my system has the same problem.

If someone find a Bug opened in launchpad, please, report it. I havent found it.

---

