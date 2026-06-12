---
title: "Issue with Audacity recorder in Ubuntu"
date: 2014-04-01
forum: Multimedia Software
---

### Post by muruga86 on 2014-04-01
Hi All,

I am having a 64 bit x86 labtop running Ubuntu [12.04 LTS]("http://en.wikipedia.org/wiki/Ubuntu_12.04_LTS_Precise_Pangolin") which was lated updated to RT version.

Linux 3.8.0-35-generic #52~precise1-Ubuntu SMP Thu Jan 30 17:24:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

I installed Audocity 2.0.0, but i an unable to record any audio from microphone port.

I've attached both the screen shots.

The auocity logs tag displays following data.
==============================
Default capture device number: -1
Default playback device number: -1
No devices found

Even tried after installing JACK audio system, but still same issue.
Could some one help?

Regards,
Murugan

---

### Post by su:bhatta on 2014-04-02
Hi,

You are not using RT (Real Time) kernel but the generic kernel. RT kernel is not avialable in Ubuntu by default, but I guess you can install it, but low latency is generally sufficient.
If you want to use you should install low-latency kernel which is available in Ubuntu and can be installed easily with Synaptic 
or via the command"

```
sudo apt-get install linux-lowlatency.
```
Read this : [https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)


Using the  Low-latency kernel will give this output from terminal:
> 
~$ uname -a
Linux  3.13.0-20-lowlatency #42-Ubuntu SMP PREEMPT Fri Mar 28 10:25:59 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
What is the problem you are facing when recording? You have to select the 'Recording Device' Channel etc before you can record from microphone.
If you are using Jack and start Jack using QjackCtl then you have to choose Jack to be the client for Audacity.

Refer to Audacity guide: [https://help.ubuntu.com/community/Audacity](https://help.ubuntu.com/community/Audacity)
[http://wiki.audacityteam.org/wiki/Release_Notes_2.0.0](http://wiki.audacityteam.org/wiki/Release_Notes_2.0.0)

---

