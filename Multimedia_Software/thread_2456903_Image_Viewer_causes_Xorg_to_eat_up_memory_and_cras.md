---
title: "Image Viewer causes Xorg to eat up memory and crash the desktop environment."
date: 2021-01-21
forum: Multimedia Software
---

### Post by alexbriss on 2021-01-21
Hi, when browsing images (jpegs, 5-10MB) with Image Viewer (EOG / Eye of gnome) my desktop environment crashes and returns me to the logon screen. It seems that bigger images causes the crash to happen sooner (it can happen already after a few images). By looking in /var/log/syslog I have determined that the crash happens because the machine is out of memory and decides to kill Xorg:[INDENT][FONT=courier new]
Xorg: page allocation failure: order:0, mode:0x104cd2(GFP_HIGHUSER|__GFP_RETRY_MAYFAIL|__GFP_RECLAIMABLE), nodemask=(null),cpuset=/,mems_allowed=0
Out of memory: Killed process 93065 (Xorg) total-vm:10917808kB, anon-rss:31088kB, file-rss:0kB, shmem-rss:2981192kB, UID:1000 pgtables:6356kB oom_score_adj:0[/FONT][/INDENT]

I proceeded by monitoring memory usage with htop while I was browsing Images. Already after viewing 5 images, 95% of the machines physical memory was in use, and the /usr/lib/xorg/Xorg process had allocated 10GB of virtual memory.[INDENT][FONT=courier new]
96259 user  20   0 10.4G 2969M 2938M S  0.0 39.0  1:11.32 /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3[/FONT][/INDENT]

My system is Ubuntu 20.04 LTS running on an Asrock J5005-ITX motherboard with 8GB of RAM and an Intel Pentium Silver Processor J5005 with Integrated Intel UHD Graphics 605[INDENT][FONT=courier new]
user@ubuntu:~$ lspci -k | grep -EA3 'VGA|3D|Display'
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 605 (rev 03)
        DeviceName: Onboard - Video
        Subsystem: ASRock Incorporation UHD Graphics 605
        Kernel driver in use: i915[/FONT][/INDENT]


So what are your thoughts on this problem? What further troubleshooting can I do, or where should I report the problem?

---

### Post by simon-webb on 2021-01-21
Hi Alex...and wow, that's nasty! Firstly just so that you can view images without crashing your whole desktop, you could try a different image viewer to see if your issue's an EOG bug. Typing apt install gliv will give you a little GL-accelerated image viewer that you can launch from the shell or assign to the right-click "open with" menu in a GUI file browser. GLiv's using GL makes it fast and allows it to do cool things like free rotation...plus it might be different enough from EOG to avoid the crash even if it's an issue with the underlying graphics system rather than just EOG. Then, based on whether other image browsers cause the same crash, you'll have a better idea as to whether the issue you're seeing is an EOG bug (in which case it would be good to report it as such). If the problem persists no matter what image browser you use, I'm not sure where to go from there. 8GB should be plenty to run your desktop without crashing...unless...I know this is highly unlikely, but have you checked your available *disk* space? If your virtual memory's being allocated dynamically on a disk that's nearly full, I guess hitting the limit of available disk space might cause the crash.

---

### Post by alexbriss on 2021-01-22
I tried gliv like you suggested and it works fine, it uses about 150MB of memory and the xorg-service uses 30MB. Shotwell and gThumb also works fine.

I have to admit I've been running without any swap :-), so I added an 8GB swap file. The problem is stil there but instead of a sudden crash, my swap file starts filling up and EOG gets so unresponsive it just shows a black picture. As soon as a force quit EOG my memory usage is back to normal.

Anyway, gThumb seems nice and quick so I'll stick with that. Thanks for your help :p

---

### Post by simon-webb on 2021-01-22
Great, I'm glad it was just EOG and not some more serious underlying issue. You shouldn't need swap, if you have a decent amount of RAM (8GB or more for a modern desktop)...although it does depend on what you're doing (editing media can suck up lots of memory), so it was probably a good idea that you added some just in case. Please do let the EOG developers know about the issue so they can fix it: typing ubuntu-bug eog in a terminal window can help you file the bug report. It looks to be working fine on my setup (I've just fed it a big directory of huge images and while scanning through that lot repeatedly, the memory usage sat very calmly and reasonably at around where I'd expect it to be), so your report could be really useful as it may make them aware of a particular hardware combination or whatever that's triggering the issue.

---

