---
title: "multiple screen scynronization problem"
date: 2013-01-08
forum: Multimedia Software
---

### Post by ydoganc on 2013-01-08
I have the following problem for which i was unable to find a solution on the internet. If someone thinks that this post belongs to another category, i will move it, for now i don't know a better place.

I am using 3 displays consisting of 1 laptop screen and 2 monitors. I'm running Ubuntu via windows7 host using 2 monitors as extended desktops (via vmplayer). 

The problems is that when i'm working with monitor1 a part of the monitor1 screen is displayed in monitor2 vice versa when working on monitor2. 

I'm using the following configuration: 
vmplayer
5.0.1 build 894247
host os: windows 7 prof 64bit 7601 sp1

running ubuntu 10.10
Linux ubuntu 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:19:45 UTC 2012 i686 i686 i386 GNU/Linux

native monitor resolutions:
1280x1024 monitor1
1280x1024 monitor2

within ubuntu displays 2560x1024

To clarify the above problem i have included a screen capture.
[IMG]https://sites.google.com/site/shareglobal1/_/rsrc/1355502751613/home/vmplayer_ubuntu_problem.png[/IMG]

---

### Post by gordintoronto on 2013-01-08
You mean you are running Ubuntu 10.10 in a VM on your laptop?

Ubuntu 10.10 expired almost a year ago. A later version might give different results.

What does the VM present as the video adapter? What is the actual video adapter? I am not aware of a laptop which supports two external monitors. It's rare enough on desktop systems, unless they have multiple video cards.

---

### Post by ydoganc on 2013-02-19
following link gives more information.

[http://techblog.shield.id.au/vmware-player-5-multiple-monitors-overlaying-each-other/](http://techblog.shield.id.au/vmware-player-5-multiple-monitors-overlaying-each-other/)

The proposed solution doesn't work for me, so i have given up. I'm going to wait for the next release of vmplayer. If the issue is still not fixed then i will look further. 

I'm running Ubuntu 11.04

I was not able to find a way to close this thread without marking it solved.

---

