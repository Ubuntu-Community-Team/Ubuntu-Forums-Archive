---
title: "fglrx - black screen feisty amd64"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by kingpico on 2007-07-02
i have a x1600 g.card . I tried to install fglrx drivers from apt-get , manually ( package build) and with envy. I just cant make it work! I m not new to linux.. i tried every possible way but no result. I purge removed everything and install em again many times.
I know that fglrx is compiled for 7.1 X.org and not for 7.2 but i saw that many users can get fglrx working with 7.2 X.org. I m using the 8.37.6 drivers version( tried the 8.38.6 as well which makes no difference). ired all fglrx posts as well...

These are the **last **lines from my **Xorg.log **

(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	ABI class: X.Org Server Extension, version 0.3


After loading fglrxdrm sub module does nothing, as a result the black screen ...

i cant understand why it stucks there and is not continuing.. 
Anyone got a clue what's going on here? 
thank you in advance

---

### Post by IanW on 2007-07-02
Try using the "Envy" script available from [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

This works with both Nvidia & ATI graphics drivers for me.

---

### Post by kingpico on 2007-07-02
thank u for the reply 
but as i wrote, i have already used envy

---

### Post by MCSE_Crossover on 2007-07-02
is that card PCI-E or AGP? Sorry, I don't typically use ATI...  What type of motherboard do you have?

---

### Post by kingpico on 2007-07-02
is PCI -E 
lspci gives me this
03:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
03:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)

MB is Asus:M2NPV-MX
the is no on board graphics card

---

### Post by applefreakpeeps on 2007-07-03
the bug exists for mcp51 boards still on x64 kernels..

the problem is an IRQ clash plaguing few boards having mcp51 chipset which causes a kernel panic.. xorg uses 100% cpu and system hangs.. only way is to manually reboot.. u hav 2 solutions

1. boot into rescue mode and change driver to vesa. wait for problem 2 be fixed
2. this problem no longer occurs on 32-bit kernels from driver 8.38.6/7.. u can try them out

and yaa.. u were wrong to mention that u hav no onboard graphics.. as per ur board spec u do hav a geforce 6150 which is what these nforce 430 boards come bundled with..

You can boot in recovery mode.. open ur xorg.conf and comment the Line load extmod in the modules section.. that may help

---

### Post by kingpico on 2007-07-03
right... 
i was using vesa drivers as long as i cant use fglrx.So i guess i ll stick with em and just wait until this bug is fixed....
tnx for your posts

---

