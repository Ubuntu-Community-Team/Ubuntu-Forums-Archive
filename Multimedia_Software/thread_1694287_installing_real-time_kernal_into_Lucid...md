---
title: "installing real-time kernal into Lucid.."
date: 2011-02-24
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2011-02-24
Could anyone please help me to install the latest real-time kernal into my current Lucid 10.04 distro?

I know I could download and use Ubuntu Studio, but 1.7Gb is too much for my monthly download allowance to handle, especially when all I need it for is to address the major latency issues I have with Audacity.


Cheers,
Baldrick

---

### Post by zenwalker on 2011-02-24
This might help u [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Baldrick_NZ on 2011-02-24
> **zenwalker said:**
> This might help u [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Thanks for that, but I don't want to do anything special, just replace my existing kernal with the latest real-time one; and some fairly basic instructions as to how to go about it, please.

Cheers.

---

### Post by cchhrriiss121212 on 2011-02-24
What latency are you getting and with what settings? What hardware do you have? CPU and soundcard will be the relevant factors for latency.

There are a whole bunch of things you can try to reduce latency, but a new kernel wouldn't hurt. I'd recommend using the low-latency variant in this PPA (it has instructions on how to use a PPA if you don't know):
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")
The rt kernels are good, but they are a a bit older and won't offer any better performance than the newer low-latency versions.

Once the new kernel is installed, hold shift when you boot up to select it from the GRUB menu. If it doesn't help, there are other things I can suggest.

---

### Post by Baldrick_NZ on 2011-02-24
> **cchhrriiss121212 said:**
> What latency are you getting and with what settings? What hardware do you have? CPU and soundcard will be the relevant factors for latency.

There are a whole bunch of things you can try to reduce latency, but a new kernel wouldn't hurt. I'd recommend using the low-latency variant in this PPA (it has instructions on how to use a PPA if you don't know):
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")
The rt kernels are good, but they are a a bit older and won't offer any better performance than the newer low-latency versions.

Once the new kernel is installed, hold shift when you boot up to select it from the GRUB menu. If it doesn't help, there are other things I can suggest.

It's an Sempron 3300+ processor, and an AC97 internal soundcard, with 2gB of system RAM.
My biggest problem, and what all of this is about, is recording something from a line-source through audacity, audacity simply stops recording at it's whim. Sometimes a few seconds, other times a couple of minutes.

There is plenty of RAM, and it works flawlessly on the same PC under XP. I've played with the latency settings, increasing them to 1000 and -500, where it does record a whole song, but the graphical lag takes ages to catch up after the song has finished.

So I thought that having the latest rt kernel would help with this issue immensely, which makes sense since Ubuntu Studio uses it. 

I'm also using the latest kernel (2.6 32-28)

I'll have a play with that PPA you provided. Once installed, what software should I choose from synaptic?

Cheers.

---

### Post by cchhrriiss121212 on 2011-02-24
> So I thought that having the latest rt kernel would help with this issue  immensely, which makes sense since Ubuntu Studio uses it. 
It shouldn't really be necessary for most users unless you do something really intensive. The last Studio to include an rt kernel was 9.10, 10.04 and 10.10 both had a generic. Future releases will have a low latency kernel as it is easier to maintain yet gives the same results.

> Once installed, what software should I choose from synaptic?
The kernel image, along with the header files, if you mark one for installation any dependencies will be added automatically. Choose the rt or the low latency, or both if you would like to compare, sometimes new kernels don't always play nice, so always keep a functional kernel installed.

---

