---
title: "Realtime Kernel"
date: 2010-04-17
forum: Multimedia Software
---

### Post by cmmcnamara on 2010-04-17
Hey everyone.

My band and I have just finished putting together a computer from spare parts we had lying around so that we could use it as an audio workstation running ardour and jack under a realtime kernel. We were using my laptop a Dell Vostro under 64 bit Ubuntu with the real time kernel without any hiccups but this new machine is struggling. First here are the specifications if it makes any difference:

XFX 780i SLI Motherboard
Intel Core 2 Quad 9300
8GB DDR2-800 RAM
250GB Seagate 7200.11 HDD
7900 GT Video Card (PCIe)
Ubuntu 9.10 x64

Ubuntu runs perfectly under 64-bit generic kernel but upon installing real time two things happen:

1) The NVIDIA drivers fail and I have to enter console mode and install them again or run the low-res session.

2)When I actually get to the desktop many things fail, even the menu application. The desktop background wont load, the wireless drivers don't load ,etc. 

Once loaded to the desktop under realtime I cannot even restart properly as the shutdown applicaton fails as well. I can get into console mode as well, so are there any commands I can run to clue you in to what is actually happening? Any help is greatly appreciated.

---

### Post by cchhrriiss121212 on 2010-04-17
I had the same issues with the rt kernel that is in the karmic repos. [This one]("https://launchpad.net/%7Ednjl/+archive/kernel") however has worked perfectly for me. With that setup and a decent interface, you should have very nice performance.

---

### Post by cmmcnamara on 2010-04-17
So you are using the linux-rt or linux-meta-rt on that page? How would I install from there? Everything seems compatible?

---

### Post by cchhrriiss121212 on 2010-04-17
I don't know what the meta package is for. I just went into "show package details" and under linux-rt I downloaded the .debs for the headers and kernel, as you are using 64 bit ubuntu choose the amd64 packages. To install a .deb package you just click on it.

Once you have the kernel and headers installed you can use startup manager to select it as default.

---

### Post by Linuxforall on 2010-04-18
The RT Kernel in Ubuntu works fine with nvidia drivers installed from the hardware drivers applet, the nvidia drivers from nvidia's site with run file won't work on rt kernels as it doesn't have the rt patch.

---

### Post by cchhrriiss121212 on 2010-04-18
> The RT Kernel in Ubuntu works fine with nvidia drivers installed from the hardware drivers applet, the nvidia drivers from nvidia's site with run file won't work on rt kernels as it doesn't have the rt patch.
Works fine on my machine with 195.36.07 ([from here]("http://ubuntuforums.org/showthread.php?t=990978")) and the rt kernel linked to above. What does the rt kernel have to do with the nvidia driver?

---

