---
title: "Ubuntu + DeMuDi Kernel?"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by sirbrown on 2006-06-11
Hello all,

I'm stuck in a bit of a quandary.  I tried patching the Ubuntu kernel as per the instructions on the ubuntustudio wiki and, as they warned I might, ran into quite a few problems.  So I gave up and decided to try A/DeMuDi.  That yielded good results, but was difficult to configure due to problems with networking hardware recognition.

I have heard that Ubuntu can be run with the DeMuDi kernel instead of the default kernel.  Has anyone here done so?  Care to volunteer a HOWTO?  I think this is something a lot of people would be interested in, as I've seen numerous posts on various forums expressing interest in combining the best aspects of the two distros.

---

### Post by bwanab on 2006-06-11
The latest Demudi kernel is based on 2.6.14.x. Ubuntu is currently at 2.6.15.23 IIRC. You don't want to go in that direction. To be honest, on my desktop AMD system, I'm using the previous demudi (1.2.1) which is based on 2.6.12.x and it is a dream, but I don't think dapper is going to be happy going back to 2.6.14.x.

---

### Post by BobSongs on 2006-06-16
[QUOTE=bwanab]The latest Demudi kernel is based on 2.6.14.x. Ubuntu is currently at 2.6.15.23 IIRC. You don't want to go in that direction. To be honest, on my desktop AMD system, I'm using the previous demudi (1.2.1) which is based on 2.6.12.x and it is a dream, but I don't think dapper is going to be happy going back to 2.6.14.x.[/QUOTE]
My only reason for being interested in DeMuDi (or Musix) would be if it had the ability to record multiple tracks in Audacity. So far Breezy and Dapper have let me down in that respect and I'm forced to boot back into XP to get multi-tracking abilities.

Have you had success with this? Even a test with a microphone and Audacity and recording two tracks successfully would be encouraging.

---

### Post by christhemonkey on 2006-06-16
I used to use the musix kernel (with full realtime preemption) but i found it unreliable and generally nowhere near as good as my current custom compiled fully realtime preemptibleness kernel.
So my advice would be; to not give up on the custom kernel compiling, it willl work eventually!

---

### Post by dolson on 2006-06-17
I echo what chris said... Post your issues with the kernel compile and we can help.

---

### Post by noou on 2006-06-27
Hello I'm a complete Linux newbie and I'll use it as a platform for developing audio applications as a researcher at university. There they're currently using demudi and Fedora + planet CCRMA, but they like to have a new Linux distro in the family... so I'm going to install Ubuntu (I tried the Live cd and I think it's great!) but I'm really interested in having low latency as in demudi.

it seems to me that ubuntu studio is not as optimized as demudi concerning latency. in that case i wish to know if there is/will be a tutorial to help newbies patching Ubuntu with the demudi kernel.

by the way I downloaded the demudi 1.2.1 live cd and discovered it's based on ubuntu 5.04!!! that's interesting!

thanks!

---

### Post by zettberlin on 2006-06-27
[QUOTE=noou]I'm really interested in having low latency as in demudi.
[/QUOTE]

i can work sane and stable at latencies of about 3 ms and with some caution with 1.3 ms, special setups for livesynths (with 96000Hz) work very well at settings for less then one millisecond.
All with the ubuntu dapper standardkernel out of the box.

uname:
2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux
cpuinfo:
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 3
cpu MHz         : 2806.660
cache size      : 1024 KB

1024 RAM installed Terratec EWX 24/96 (envy24)

---

### Post by dolson on 2006-06-28
[QUOTE=noou]Hello I'm a complete Linux newbie and I'll use it as a platform for developing audio applications as a researcher at university. There they're currently using demudi and Fedora + planet CCRMA, but they like to have a new Linux distro in the family... so I'm going to install Ubuntu (I tried the Live cd and I think it's great!) but I'm really interested in having low latency as in demudi.

it seems to me that ubuntu studio is not as optimized as demudi concerning latency. in that case i wish to know if there is/will be a tutorial to help newbies patching Ubuntu with the demudi kernel.

by the way I downloaded the demudi 1.2.1 live cd and discovered it's based on ubuntu 5.04!!! that's interesting!

thanks![/QUOTE]
You are right. Ubuntu is not a distro tailored to musicians, so of course it is not as low latency as DeMuDi is. Just like Red Hat is not, neither is SUSE, nor is Slackware, nor even Debian.

Have you looked at the wiki? There is a tutorial there on getting a kernel similar (nearly identical) to what Free (from DeMuDi) built for DeMuDi. You can get the same result by simply getting the .deb packages from DeMuDi and installing them on Ubuntu, but you risk breaking certain hardware support, as Ubuntu adds many patches to their kernel source, which neither DeMuDi nor a vanilla kernel have.

I would love to patch the Ubuntu kernel, but it is very hard because they spend a lot of time backporting fixes from newer kernels than the one they standardize on earlier in the development process, plus they add in a ton of extra drivers. I'm not a kernel whiz, and I can't do it on my own.

I have been talking to a few people and we have some ideas on making it easier, but we need time to do it, and we all work full-time jobs.

---

### Post by noou on 2006-06-28
thank you all very much...

soon I'll get a new HD so I will install Ubuntu (so far I just used it live) and I'll give it a try.

I'll mainly use pure data because we develop audio applications in C/C++ as externals for pure data.

---

### Post by JamesB on 2006-11-27
> **BobSongs said:**
> My only reason for being interested in DeMuDi (or Musix) would be if it had the ability to record multiple tracks in Audacity. So far Breezy and Dapper have let me down in that respect and I'm forced to boot back into XP to get multi-tracking abilities.

Have you had success with this? Even a test with a microphone and Audacity and recording two tracks successfully would be encouraging.

I had problems with ubuntu and Audacity but found audour worked well with realtime multi track recording. But now I use dyne-bolic 2.3 (live cd, save to external disk) or my mac with logic express. 64Studio is ment to be pretty good to.

---

