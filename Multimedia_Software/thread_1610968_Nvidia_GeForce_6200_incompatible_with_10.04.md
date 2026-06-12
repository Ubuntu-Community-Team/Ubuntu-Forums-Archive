---
title: "Nvidia GeForce 6200 incompatible with 10.04?"
date: 2010-11-01
forum: Multimedia Software
---

### Post by lupulin on 2010-11-01
Hey all, maybe someone can make a recommendation for me. I am pretty much a total linux/ubuntu newb. I got an Nvidia GeForce 6200 video card as a hand me down from someone else and I can't seem to get any driver to work with it. When I go to Hardware Drivers from the system menu, any of the drivers that I activate from there create an error and kick me into low resolution mode when I restart the computer. Is this driver compatible with 10.04?

This is what lspci tells me if it helps:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

---

### Post by makins on 2010-11-01
Have you tried the drivers off the nvidia website? 

[http://www.nvidia.co.uk/object/linux-display-ia32-260.19.12-driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-260.19.12-driver-uk.html")

---

### Post by azc on 2010-11-01
I have an Nvidia GeForce 6200 AGP that is working with 10.04.

The card:
[http://www.evga.com/products/moreInfo.asp?pn=256-A8-N401-LR&family=GeForce%206%20Series%20Family](http://www.evga.com/products/moreInfo.asp?pn=256-A8-N401-LR&family=GeForce%206%20Series%20Family)

```

$ lspci|grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
$ 

```
To get it working, I followed this page:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

And installed **173.14.22**. NOT the recommended version-current.

I did take an extra step, after running "sudo nvidia-xconfig", which was to run:
```

$ sudo nvidia-settings

```
Edit: And then saved the settings to "/etc/X11/xorg.conf"

The 173 series supports the 6200 just fine. For my needs anyway.

[http://www.nvidia.com/object/linux_display_ia32_173.14.22.html](http://www.nvidia.com/object/linux_display_ia32_173.14.22.html)

---

### Post by lupulin on 2010-11-01
> **azc said:**
> I have an Nvidia GeForce 6200 AGP that is working with 10.04.

The card:
[http://www.evga.com/products/moreInfo.asp?pn=256-A8-N401-LR&family=GeForce%206%20Series%20Family]("http://www.evga.com/products/moreInfo.asp?pn=256-A8-N401-LR&family=GeForce%206%20Series%20Family")

```

$ lspci|grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
$ 

```To get it working, I followed this page:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

And installed **173.14.22**. NOT the recommended version-current.

I did take an extra step, after running "sudo nvidia-xconfig", which was to run:
```

$ sudo nvidia-settings

``` Edit: And then saved the settings to "/etc/X11/xorg.conf"

The 173 series supports the 6200 just fine. For my needs anyway.

[http://www.nvidia.com/object/linux_display_ia32_173.14.22.html](http://www.nvidia.com/object/linux_display_ia32_173.14.22.html)

Thanks for the tip. I will give that driver a whirl. A couple questions though. 1) Do I need to do anything to save the settings to /ect/X11/xorg.conf or does hitting save automatically save it there?

2)After running 
```

$ sudo nvidia-settings

```it tells me "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." Do I need to edit my X configuration? Not sure how to do that. 

[edit] I ran ```
nvidia-xconfig
``` and it said 
"WARNING: Unable to locate/open X configuration file.


ERROR: Unable to write to directory '/etc/X11'."

---

### Post by captaintrav on 2010-11-01
should use:

> sudo nvidia-xconfig

---

### Post by lupulin on 2010-11-01
> **captaintrav said:**
> should use:

Duh. That did something. I tried to run it and then restart X by hitting Right Alt + Print Screen + k which kicked me right back into low graphics mode with an error. I restarted the computer with the default settings, tried to run sudo nvidia-xconfig again and it says 
"Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'"

Seems like I'm going in circles here. Wish it was a bit more straight forward. 

Any ideas?

---

### Post by marl30 on 2010-11-01
I don't know what issue you're having but my 6200 worked flawlessly with 10.04 and is still working just as well with 10.10.

---

### Post by marl30 on 2010-11-01
By they way, my current driver is 260.19.12. Tell you what... to get this driver installed... install Ubuntu Tweak. Then go to applications> source center > desktop. Scroll down and check X Updates, then hit sync. This will install the latest Nvidia driver from x.org. After it installs, you can restart. If it still doesn't work... maybe you should check to make sure that graphics are is working properly.

---

### Post by captaintrav on 2010-11-01
there is some annoying behavior trying to get the right version of the kernel module needed for older drivers.

try to install nvidia-173-modaliases if that's not installed, that might do it

>  lsmod | grep nvidia to see if any nvidia module is loaded.  Also check /var/log/Xorg.0.log.old (I think) to see if you have anything about the kernel module being the wrong version.

---

