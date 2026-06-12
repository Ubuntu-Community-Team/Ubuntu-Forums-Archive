---
title: "Low Latency Kernels"
date: 2007-06-15
forum: Multimedia Production
---

### Post by niglch on 2007-06-15
I'm currently on Ubuntu 7.04 and I'm using Rosegarden, Audacity, JACK, and Fluidsynth for MIDI sequencing and music production. However, I am experiencing some performance problems especially with Rosegarden (not to mention the timer resolution warning I get every time it starts). I have heard that having a low-latency or real-time kernel can improve performance significantly. However, I'm hesitant to install Ubuntu Studio which comes with this type of kernel because my computer is mostly used for normal tasks (word processing, web browsing, games, etc). Is it possible to install a low-latency kernel without having to completely change my distro, or am I better off just using Ubuntu Studio?

---

### Post by damu on 2007-06-15
better off using UbuntuStudio which offers everything of Ubuntu + multimedia production...so not much to loose and loads to get :)

You can upgrade your ubuntu to UbuntuStudio with Synaptic but you have to know that some audio stuff won't be configured automatically for you the way they would be with a fresh install of Ubuntustudio. So my 2 cents are that if your datas are backed up, and that you are ok for a reinstall, then go this way. 

If you have your own tailored Ubuntu with loads of data and don't want to reinstall, upgrade with Synaptic and check this forum to know which steps you have to follow to configure it properly


Good luck

---

### Post by umattu on 2007-06-15
actually you do not need to install ubuntustudio to accomplish this, if you visit this page [http://ubuntustudio.org/downloads]("http://ubuntustudio.org/downloads")
at the bottom of the page you will see the key to the repo. runthe command given, then you can install the ubuntustudio-audio and ubuntustudio-audio-plugins package, this will install the lowlatency kernel, it will install all of the ubuntustudio audio apps and plugins and will not affect your office apps and what not. There is a list on that page of the packages in their repos, I installed ubuntu feisty, then installed all of the packages froom that repo and now have the best of both worlds.

In my case I did not want the lowlatency kernel (no particular reason at all) but when I installed the ubuntustudio-audio package it installed the lowlatency kernel so that probably what you would want to do.

---

### Post by christhemonkey on 2007-06-15
Lowlatency kernel is in standard ubuntu repositories,
just run:
```
sudo apt-get install linux-lowlatency 
```

Then reboot and select that kernel from the GRUB list.


It should have no detrimental effects at all on normal usage.

---

### Post by fredj on 2007-06-16
There are three different Ubuntu kernels and here are the differences between them.
1. the ordinary kernel provides a clock tick that fires at about 250 times a second. If you try to
use a midi/audio program such as Rosegarden it will warn you that this clock is too slow to enable
it to offer the full precision it is capable of. You will not be able to obtain a low latency on a soundcard
using this kernel.
2. The low latency kernel. THis provides a clock that tick at a thousand times a second (or more).
Rosegarden will be happy with this. I don't think this kernel does anything to improve soundcard 
latency.
3. The Realtime Kernel. This provides a suitable clock signal and also allows you to run the jackd
audio server at a low latency in Realtime. Cannot be beaten for audio and is the only serious choice
for someone who wants professional quality audio under Linux. Ubuntu now has a good Realtime 
Kernel available.

---

### Post by christhemonkey on 2007-06-17
Just to say that ubuntu does not have a proper fully preemptible kernel.

To have that, kernel source needs to patched with Ingo Molnars patches and then the kernel compiled with CONFIG_PREEMPT_RT=y, whereas ubuntus -lowlatency kernel just has CONFIG_PREEMPT=y
(which is better than the standard kernel for low latency audio work)


When you have a preemptible kernel to achieve realtime access to it, you need to have PAM patched (which it has been for a while now in ubuntu) then you can just set "@audio - rtprio 99" and "@audio - nice -10" in /etc/security/limits.conf.
Then you can run with realtime enabled in jackd.


EDIT:
The ubuntu studio project does indeed have one, my mistake. See here:
[http://ubuntuforums.org/showthread.php?t=441366](http://ubuntuforums.org/showthread.php?t=441366)

---

### Post by tgalati4 on 2007-06-17
Burn yourself a Dynebolic 2.4.2 disk.  Boot it live.  Create a "nest" (1 GB or more) which is a place on your harddisk to store your settings and your /home directory and try running your audio applications.  Dynebolic is slimmed down and see if it solves your timing issues.

When you are not doing audio work, your normal Ubuntu system is untouched.

---

### Post by nigelt on 2007-06-18
> **fredj said:**
> There are three different Ubuntu kernels and here are the differences between them.
1. the ordinary kernel provides a clock tick that fires at about 250 times a second. If you try to
use a midi/audio program such as Rosegarden it will warn you that this clock is too slow to enable
it to offer the full precision it is capable of. You will not be able to obtain a low latency on a soundcard
using this kernel.
2. The low latency kernel. THis provides a clock that tick at a thousand times a second (or more).
Rosegarden will be happy with this. I don't think this kernel does anything to improve soundcard 
latency.
3. The Realtime Kernel. This provides a suitable clock signal and also allows you to run the jackd
audio server at a low latency in Realtime. Cannot be beaten for audio and is the only serious choice
for someone who wants professional quality audio under Linux. Ubuntu now has a good Realtime 
Kernel available.

Can you tell what the advantage is, if any, to running the ordinary kernel instead of the lowlatency for anyone even if you don't run audio programs that need the faster clock tick? Why doesn't everyone just run the latter?
Just interested ...... Thanx

---

### Post by christhemonkey on 2007-06-18
Supposedly the faster timer resolution can make people using laptops batteries run down quicker as the kernel is waking up 1000 times a second as opposed to 250 times.

This may no longer be true though. (but it probably is)


Other than that, the low latency patches from Ingo werent very stable for a long time, though for the last few years they have become more and more stable to the point now where they are begining to be included in the main kernel tree.

---

### Post by nigelt on 2007-06-18
WOW! Thanks for the quick reply Chris! Interesting as I am now using FF 7.04 on both Laptop and Desktop. I will pay attention to the battery life on the Laptop when using either Kernel. I'm SO impressed with the product and now the support. A complete convert. TKS.

---

### Post by christhemonkey on 2007-06-18
No worries, come back to us if you have any problems.

---

