---
title: "Wired Connection Problem"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by tusharg1993 on 2012-03-03
Hello
I am a new user to ubuntu.
I have installed ubuntu 11.10 along with windows 7 64 bit by wubi installer.
Now i am n=very upset about the internet in ubuntu the lan just hangs up many times and there is no response to connections.
Also the speed is very throttled.
Please ask for the info needed..as i am new i dont know what info to post.

---

### Post by tusharg1993 on 2012-03-03
no reply!!!!!
Please Help.....

---

### Post by Iowan on 2012-03-03
One bump every 24 hours is generally adequate.Your discription is a little confusing. Are you talking about wired or wireless (or both)?  What do you mean by "no response to connections"? I don't know if it has anything to do with the wubi install - I've never tried it.

---

### Post by tusharg1993 on 2012-03-04
I mean both for wired and wireless.
The wireless connection just doesn't connect....
In case of wired it is very unresponsive....
The connection times out many times...
In case of detection to it loops to detecting and wired network disconnected whereas it is working really fine in windows.

---

### Post by tusharg1993 on 2012-03-04
[http://ubuntuforums.org/showthread.php?t=1896636](http://ubuntuforums.org/showthread.php?t=1896636)

From the post #6 of this thread i got the wireless working but still having problem in the wired connection...

---

### Post by vidtek on 2012-03-04
> **tusharg1993 said:**
> Hello
I am a new user to ubuntu.
I have installed ubuntu 11.10 along with windows 7 64 bit by wubi installer.
Now i am n=very upset about the internet in ubuntu the lan just hangs up many times and there is no response to connections.
Also the speed is very throttled.
Please ask for the info needed..as i am new i dont know what info to post.

Tu-

The info we need:
Ubuntu version
Network hardware type (is it internal to motherboard ?)

There was a bug in later kernels which installed the wrong driver for some Realtek network cards, this gave the faults you describe.

If you make a signature similar to mine it will give us a lot of the info we need.  Go to your CP (control panel) when you log into the forum and edit signature.

Best wishes, Tony.

Tony

---

### Post by tusharg1993 on 2012-03-04
The out put of $ lspci

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

```

Ubuntu Version Ubuntu 11.10

---

### Post by tusharg1993 on 2012-03-04
> **vidtek said:**
> Tu-

The info we need:
Ubuntu version
Network hardware type (is it internal to motherboard ?)

There was a bug in later kernels which installed the wrong driver for some Realtek network cards, this gave the faults you describe.

If you make a signature similar to mine it will give us a lot of the info we need.  Go to your CP (control panel) when you log into the forum and edit signature.

Best wishes, Tony.

Tony


The out put of $ lspci

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

```

Ubuntu Version Ubuntu 11.10

---

### Post by vidtek on 2012-03-04
Tu-

You have the same issue as I did.  see my post here:

 [http://ubuntuforums.org/showthread.php?t=1865423](http://ubuntuforums.org/showthread.php?t=1865423)

and here: 

[http://ubuntuforums.org/showthread.php?t=1880597](http://ubuntuforums.org/showthread.php?t=1880597)
Tony.

---

### Post by tusharg1993 on 2012-03-05
> **vidtek said:**
> Tu-

You have the same issue as I did.  see my post here:

 [http://ubuntuforums.org/showthread.php?t=1865423](http://ubuntuforums.org/showthread.php?t=1865423)

and here: 

[http://ubuntuforums.org/showthread.php?t=1880597](http://ubuntuforums.org/showthread.php?t=1880597)
Tony.

Can't it be solved..?????:(:(:(

---

### Post by Neill_R on 2012-03-05
Tony

I assume that you are complaining about access and connections to the Internet. I am also going to assume that you have an ADSLwireless router modem. 

First things first disable the wireless network interface on your PC (laptop) and concentrate on using a wired connection to the router. 

Do you know about NetworkManager? Have you ensured that the connection is set up okay?

---

### Post by vidtek on 2012-03-05
> **Neill_R said:**
> Tony

I assume that you are complaining about access and connections to the Internet. I am also going to assume that you have an ADSLwireless router modem. 

First things first disable the wireless network interface on your PC (laptop) and concentrate on using a wired connection to the router. 

Do you know about NetworkManager? Have you ensured that the connection is set up okay?

Neil-

Earlier kernels worked with the RTL 8168 card and used the correct driver.
They now install the RTL 8111 driver which causes problems.  The correct driver has to be d/l from the Realtek site and manually installed, hard to do with no network connection.
Tony

---

### Post by tusharg1993 on 2012-03-05
> **vidtek said:**
> Neil-

Earlier kernels worked with the RTL 8168 card and used the correct driver.
They now install the RTL 8111 driver which causes problems.  The correct driver has to be d/l from the Realtek site and manually installed, hard to do with no network connection.
Tony

if i download the proper driver from realtek would it work properly????

---

### Post by vidtek on 2012-03-05
> **tusharg1993 said:**
> if i download the proper driver from realtek would it work properly????

Tu-

Yes, I got my system working with this driver.
The driver included in newer kernels works intermittently and has dropout and speed issues, the d/l version works well. 

use these instructions:

Debian Lenny / Ubuntu 9.04/up
After installing the driver, update the module dependencies. 
depmod -a
First the r8169 network driver needs to be blacklisted in order to prevent the kernel from loading it. Note If additional NICs are installed in the server, the module must not be blacklisted. 
Ubuntu:
echo "blacklist r8169" >> /etc/modprobe.d/blacklist.conf
Debian:
echo "blacklist r8169" >> /etc/modprobe.d/blacklist
Then we force the kernel to include the driver in the initrd. This also ensures, that the new r8168 module is loaded before the r8169 module. 
echo "r8168" >> /etc/initramfs-tools/modules
And rebuild the initrd 
update-initramfs -v -u -k `uname -r`
Now you can reboot to activate the driver. 
After a kernel update the driver might need to be recompiled.]] 
Retrieved from "http://wiki.hetzner.de/index.php/Installation_of_r8168_network_driver"

Best of luck Tony.

---

### Post by tusharg1993 on 2012-03-06
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

From the above address i downloaded the driver source and run the autorun.sh script for the install.
I restarted the laptop and now the wired connection seems fine.

Thanxx everybody For your valuable support.
Thumbs Up for Tony.:p:pDude You Rock.

---

