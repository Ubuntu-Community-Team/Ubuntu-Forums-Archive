---
title: "Unable to read EDID"
date: 2008-11-25
forum: Multimedia Software
---

### Post by swordfishRU on 2008-11-25
Hi all!

please, help me configure xorg and find EDID information about my LCD display.

xorg write in /var/log/Xorg.0.log warning:
"Unable to read EDID for display device CRT-0 "

??? why ???

I have this hardware: 
mainboard: Asus M2N-MX SE Plus 
video: on-board NVIDIA GeForce 6100/nForce 430 
cpu: 2-head 64-bit AMD
[http://www.asus.com/products.aspx?modelmenu=2&model=1870&l1=3&l2=101&l3=345&l4=0]("http://www.asus.com/products.aspx?modelmenu=2&model=1870&l1=3&l2=101&l3=345&l4=0")
monitor: Asus VW193D
[http://www.asus.com/products.aspx?modelmenu=2&model=1688&l1=10&l2=87&l3=545&l4=0]("http://www.asus.com/products.aspx?modelmenu=2&model=1688&l1=10&l2=87&l3=545&l4=0")

I use:

root@m-art:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

root@m-art:~# cat /proc/version
Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008

root@m-art:~# Xorg -version
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux m-art 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present

root@m-art:~# cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
GCC version:  gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11)

root@m-art:~# cat /proc/driver/nvidia/cards/0
Model:           GeForce 6150SE nForce 430
IRQ:             11
Video BIOS:      05.61.32.25.00
Card Type:       PCI
DMA Size:        39 bits
DMA Mask:        0x7fffffffff
Bus Location:    00.0d.0


root@m-art:~# ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: Build    061010.3
product: MCP61 - mcp61-80 Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid:
edidfail

attached: lshw.log, xorg.conf, Xorg.0.log


thank you very much!

---

### Post by swordfishRU on 2008-11-26
up

---

### Post by eeried on 2008-11-26
From wikipedia> Extended display identification data (EDID) is a data structure provided by a computer display to describe its capabilities to a graphics card. It is what enables a modern personal computer to know what kind of monitor is connected. EDID is defined by a standard published by the Video Electronics Standards Association (VESA). The EDID includes manufacturer name, product type, phosphor or filter type, timings supported by the display, display size, luminance data and (for digital displays only) pixel mapping data.

With the new Xorg you shouldn't have to configure anything.

What's important is does your screen display your desktop, does it work normally?

I'm considering buying this screen for our LUG but tell us if it works at all. This is not clear from your post.

---

### Post by swordfishRU on 2008-11-26
Hi, eeried!

I can't setup supported resolution in my monitor without adding 
"HorizSync" and "VertRefresh" keywords in "Monitor" subsection of xorg.conf configuration file. But this information - HorizSync, VertRefresh (and others) must be read from monitor directly. And I don't understand - why xorg can't read this automatically? 


yours faithfully...

---

### Post by eeried on 2008-11-27
So you're saying Xubuntu boots and loads normally but the login screen doesn't show up and instead an ugly screen tells you Xorg needs to be configured.

Or is it that you can get to the desktop but the resolution isn't right?


And are you saying you have added the right values for "HorizSync" and "VertRefresh" and still Xorg doesn't read the file?


Please let us know exactly.

I find Xorg a bit tricky to configure but you need to add the desired modeline too. Look up the info on the forum and on the Ubuntu documentation.

But Xorg should be able to deal with LCD screens.

Can you check if the screen works on another computer or even on a MS box?

Could there be some anti-Linux stuff in this Asus screen?

---

### Post by stoobers on 2009-08-24
> **swordfishRU said:**
> Hi all!

please, help me configure xorg and find EDID information about my LCD display.

xorg write in /var/log/Xorg.0.log warning:
"Unable to read EDID for display device CRT-0 "

??? why ???




I had this same problem, and I solved like this:
First, EDID is some sort of configuration coming out of the monitor.  In the nvidia config, you can ask the monitor to produce the monitor EDID.

Then, you save the monitor EDID somewhere, such as in:
/home/myname/x/my_edid.bin

Then (and here is the magic) you need to tell xwindows to use your particular edid.  Here is the section of my xorg.conf that refers to my edid file.


.
.
.
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option "CustomEDID" "CRT-0:/home/whitestone/x/small_edid.bin"
EndSection


This Section "Device" was generated automatically when I deleted my xorg.con file, then ran the nvidia driver installer under ubuntu (kubuntu, actually).

I had to add the Option "CustomEDID"

I needed to do this because I bought a monitor splitter so I could use my small monitor or my large monitor.  But the monitor splitter (sort of like a kvm) was blocking the edid from both monitors.  So I plugged in the small monitor directly to the graphics card, and captured the EDID.  Then I plugged in the large monitor and captured its EDID.

I can just switch the xorg.conf that contains the proper EDID file, and restart the xserver.  :P

---

