---
title: "Install Modem Problems, IBM Thinkpad"
date: 2006-03-24
forum: Networking &amp; Wireless
---

### Post by Alij on 2006-03-24
Hi, I’ve been trying to install my modem drivers on a IBM Thinkpad 600x  PIII 500mhz 320MB RAM, this on Breezy 5.10. I’ve been following the guidance on the [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) . this seemed to be working well. I downloaded and ran scanModem and identified my modem as a Lucent/Agre DSP WinModem. I then followed the setup steps for this modem as set out in the Wiki DialupModemHowto, things seemed to be working well until I got an error “FATAL: module not found” Checking the Wiki setup instructions I saw this was a problem with 5.04 Hoary not Breezy 5.10, anyway the error seemed the same so I entered the fix as shown; adding *pci=routeirq*  in the /boot/grub/menu.lst . I then updated grub but no device   /dev/modem was created. I did this about 3 times to make sure that I covered everything but no luck.
I’m a bit lost at the moment, can anyone please give some help/ guidance? :-k 
Thanks.

---

### Post by towsonu2003 on 2006-04-14
I'd file a bug report after make sure you got this part covered:
> 
To check that the necessary package is installed, use your package manager, e.g. Synaptic or Adept. You need to look for a package, which is called linux-restricted-modules-ARCH, where ARCH is the last part of the $ uname -r output, i.e. your kernel flavor. If it is not installed yet, install it there.
[https://launchpad.net/malone/distros/ubuntu](https://launchpad.net/malone/distros/ubuntu)

I guess package to file under will be linux-restricted-modules. Also, try dapper when it got released, bc I see that developers don't fix breezy bugs too willingly.

---

