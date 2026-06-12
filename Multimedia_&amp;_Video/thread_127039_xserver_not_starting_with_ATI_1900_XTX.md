---
title: "xserver not starting with ATI 1900 XTX"
date: 2006-02-08
forum: Multimedia &amp; Video
---

### Post by Toube on 2006-02-08
Hi,

I've installedUbuntu about 3 times allready but I still can't get the xserver to start.. :confused: 

I also tried to configure it again in safe mode with the command sudo dpkg-reconfigure xserver-xorg, but I'm pretty new to linux so I really don't know what to configure there..

Here's the last part from the Xorg.0.log file:

(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATIRadeon 1900 XTX".
(WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.

Fatal server error:
no screens found

I would really like to work with Linux... anyhelp is welcomed!

Thanks,

Toby

---

### Post by stangbang on 2006-02-08
use cat to check to look at your xorg.conf file. write down the parts having to do with the video driver. It should be in the section "ATIRadeon 1900 XTX" from what I can see in your log file. use this to look at your xorg file (cat /etc/X11/xorg.conf | less). also do a lspci -v and copy in what it says for your video card.

---

### Post by Toube on 2006-02-08
[QUOTE=stangbang]use cat to check to look at your xorg.conf file. write down the parts having to do with the video driver. It should be in the section "ATIRadeon 1900 XTX" from what I can see in your log file. use this to look at your xorg file (cat /etc/X11/xorg.conf | less). also do a lspci -v and copy in what it says for your video card.[/QUOTE]

Thanks for your reply,

I will try what you mentioned.

-Toby

---

### Post by stangbang on 2006-02-08
just copy the information into the forum. dont actualy replace your xorg file with anything the lspci says

---

### Post by Toube on 2006-02-08
[QUOTE=stangbang]just copy the information into the forum. dont actualy replace your xorg file with anything the lspci says[/QUOTE]

Ok, this is probably a newbie question but how do I get the lspci -v output to file an copied to a floppy disk:-k 

-Toby

---

### Post by Toube on 2006-02-08
Ok, I got the xserver to sart using the VESA driver..

Here's the output from the file lspci -v:

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
        Subsystem: Asustek Computer, Inc.: Unknown device 8194
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: c7f00000-c7ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:1a.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: c8000000-ceffffff
        Capabilities: <available only to root>

0000:00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c7efc000 (32-bit, non-prefetchable) [size=4K]

0000:00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c7efd000 (32-bit, non-prefetchable) [size=4K]

0000:00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at c7efe000 (32-bit, non-prefetchable) [size=4K]

0000:00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
        Memory at c7effc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1e.0 ISA bridge: ALi Corporation: Unknown device 1575
        Subsystem: ALi Corporation: Unknown device 1575
        Flags: bus master, medium devsel, latency 0

0000:00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Asustek Computer, Inc.: Unknown device 8056
        Flags: medium devsel

0000:00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c8) (prog-if fa)
        Subsystem: Asustek Computer, Inc.: Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        I/O ports at ff00 [size=16]
        Capabilities: <available only to root>

0000:00:1f.1 RAID bus controller: ALi Corporation: Unknown device 5288 (rev 10)
        Subsystem: Asustek Computer, Inc.: Unknown device 8056
        Flags: bus master, 66MHz, medium devsel, latency 128, IRQ 19
        I/O ports at c800 [size=16]
        I/O ports at c400 [size=8]
        I/O ports at c000 [size=16]
        I/O ports at b800 [size=8]
        I/O ports at b400 [size=32]
        Memory at c7eff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7249 (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 0b12
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c7fe0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at d000 [size=256]
        Expansion ROM at c7fc0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 7269
        Subsystem: ATI Technologies Inc: Unknown device 0b13
        Flags: bus master, fast devsel, latency 0
        Memory at c7ff0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <available only to root>

0000:02:12.0 Multimedia audio controller: Creative Labs: Unknown device 0005
        Subsystem: Creative Labs: Unknown device 0023
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at e800 [size=32]
        Memory at cee00000 (64-bit, non-prefetchable) [size=2M]
        Memory at c8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:02:14.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 14)
        Subsystem: Asustek Computer, Inc.: Unknown device 811a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
        Memory at cedfc000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at e400 [size=256]
        Expansion ROM at cedc0000 [disabled] [size=128K]
        Capabilities: <available only to root>


The second problem is that Ubuntu doesn't recognize the Marvell Yukon ethernet card.. so I have no internet connection..

Should i download ATI linux drivers and install them or?

Thanks

-Toby

---

### Post by stangbang on 2006-02-08
if you want to output any command to a file you can do so by using the ">" minus the quotes. just tye in the command followed by > then type in the location you want to put the file in, and the file name.

for instance:

lspci -v > /home/lspcioutput.text


Dont worry we all have to start somwhere.

---

### Post by newuser111 on 2006-02-08
i have an x700 pro pcie card and it also doesn't work with the open source "ati" drivers ubuntu installs by default

however run sudo dpkg-reconfigure xserver-xorg, and select vesa, then use this guide [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by stangbang on 2006-02-08
you can try the fglrx driver. It may work, but since the ati driver didnt im not so sure it will. I dont believe that card is supported under it, but I can always be wrong. As for your NIC you need to install the driver for it. check out this thread for instructions on how to do that. [http://ubuntuforums.org/showthread.php?t=47615](http://ubuntuforums.org/showthread.php?t=47615)

---

### Post by gmc on 2006-02-08
Hi Toube,

I hate to rain on your parade, but the current ATI drivers do not support the 1900 XTX (at least at this time). However if it make you feel better, I'm in the same boat with my X1400.

Watch for ATI to release new drivers at some time in the future. In the meantime, you can use the vesa drivers for Xorg.

G.

---

