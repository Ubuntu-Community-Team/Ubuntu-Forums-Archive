---
title: "bino 3d"
date: 2011-05-21
forum: Multimedia Software
---

### Post by beew on 2011-05-21
Hi, 

I installed bino 3d player on Ubuntu 11.04 from this ppa [https://launchpad.net/~lion-simba/+archive/bino-mt]("https://launchpad.net/%7Elion-simba/+archive/bino-mt")

My 11.04 is installed on an external hard drive so I can test it on different machines. bino works on a HP netbook with an AMD/ATI card using the open source driver (with obvious limitation due to cpu power and ram) but on my Samsung laptop with the nouveau driver (+ mesa exprimental package)  it crashes.

This is the error message I get by running it on the terminal. 
> bino: [err] Caught signal 11 (SIGSEGV). Aborting.
bino: [err] Report bugs to <bino-list@nongnu.org>.
Aborted
Doesn't seem too informative. I have install from the xorg-edgers ppa in order to get OpenGL 2.1

Another piece of information. I have a Maverick installation on the same hard drive as a portable and it uses also nouveau + the mesa experimental package and bino works on both the HP netbook and the SamSung (My work OS is also Mav but installed internally on  the SamSung  and with the Nvidia proprietary driver)

---

