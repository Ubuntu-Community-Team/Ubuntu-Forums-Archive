---
title: "No Frontend GUI on Mythbuntu 10.10 Frontend."
date: 2011-02-18
forum: Mythbuntu
---

### Post by MythMuk on 2011-02-18
I am consistently encountering a problem with Mythbuntu 10.10 where the Mythfrontend GUI does not appear after booting the machine. Actually, the GUI never appears – even if Mythfrontend is restarted. A “ps ax | grep mythfrontend” command shows that mythfrontend is in fact running and did start up automatically after the boot process completed but the mythfrontend GUI is never displayed. The Mythbuntu desktop is displayed nicely and all the pull downs are there. I can stop Mythfrontend manually by using the kill command and then restart it using the desktop GUI pull downs but I get the same result – no Mythfrontend GUI. The /var/log/mythtv/mythfrontend.log shows everything normal:
 Starting mythfrontend.real..
 2011-02-06 14:15:55.503 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org]("http://www.mythtv.org")
 2011-02-06 14:15:55.504 Using runtime prefix = /usr
 2011-02-06 14:15:55.505 Using configuration directory = /home/steve/.mythtv
 2011-02-06 14:15:56.125 Empty LocalHostName.
 2011-02-06 14:15:56.125 Using localhost value of mythfe1
 2011-02-06 14:15:56.126 Testing network connectivity to '192.168.1.51'
 2011-02-06 14:15:56.160 New DB connection, total: 1
 

 This is on a Frontend only machine that successfully connects to a backend and the mysql db at 102.168.1.51.
 

 Mythfrontend is running on an Acer Revo AR3700-U3002 that has integrated Nvidia Ion graphics, Intel Atom D525(1.8GHz) processor, 64 bit Dual Core Processor, 1MB L2 Cache per processor, 2GB DDR3 memory and 250GB 5400RPM SATA.
 

 I have connected a Sony 43” LCD TV via HDMI as a monitor and am using the nvidia proprietary driver which displays the desktop nicely. I can open the NVIDIA X-server Settings application using the desktop pull downs and can see the GPU0 – (ION) configuration so I know the proprietary driver is being used.
 

 I have reinstalled Mythbuntu several times to make sure the install was done correctly and have researched this issue in several MythTv forums but have not found anyone with a similar problem.
 

 Background information:
 root@mythfe1:/# mythfrontend -v all
 xprop:  unable to open display ''
 

 (zenity:4669): Gtk-WARNING **: cannot open display:  
 

 (zenity:4670): Gtk-WARNING **: cannot open display:  
 

 root@mythfe1:/# lspci
 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
 00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
 00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
 00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
 00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
 00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
 01:00.0 VGA compatible controller: nVidia Corporation GT218 [ION] (rev a2)
 01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
 02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


See attached file for dmesg output.

 

 Can anyone give recommendations on what to check to find out why Mythfrontend starts up fine but does not display it's GUI on the monitor?
 

 Thanks - Steve

---

### Post by nickrout on 2011-02-19
> **MythMuk said:**
> 
 Background information:
 root@mythfe1:/# mythfrontend -v all
 xprop:  unable to open display ''
 

 (zenity:4669): Gtk-WARNING **: cannot open display:  
 

 (zenity:4670): Gtk-WARNING **: cannot open display:  
 

Why on earth are you trying to run mythfrontend as root? Try running it as the proper user, the one you set up when you installed mythbuntu

---

### Post by MythMuk on 2011-02-19
Oops, sorry. That's a bad habit of mine. Let's try again.

steve@mythfe1:~$ mythfrontend -v all
xprop:  unable to open display ''
mythfrontend.real: cannot connect to X server

Thank you for your reply.

---

### Post by MythMuk on 2011-02-19
The mythfrontend -v all command in the previous reply was done from an ssh session. When I did the command from a terminal window on the Acer, the result was quite different. Please see the attached file.

---

### Post by MythMuk on 2011-02-21
:D
Solved this myself.
When you are doing the initial install and are on the screen where it asks you to select a video driver, tvout, etc make sure you have the proper selections in there or the Mythfrontend GUI will not come up. For my hardware, I selected the following:

[COLOR=#000000][FONT=Tahoma, sans-serif][SIZE=2]Selected video driver:  Open source driver: Nvidia Graphics selected[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Tahoma, sans-serif][SIZE=2]TV-out:   component video out: HD1080p[/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Tahoma, sans-serif][SIZE=2]It works great now!
[/SIZE][/FONT][/COLOR]

---

### Post by nickrout on 2011-02-21
> **MythMuk said:**
> :D
Solved this myself.
When you are doing the initial install and are on the screen where it asks you to select a video driver, tvout, etc make sure you have the proper selections in there or the Mythfrontend GUI will not come up. For my hardware, I selected the following:

[COLOR=#000000][FONT=Tahoma, sans-serif][SIZE=2]Selected video driver:  Open source driver: Nvidia Graphics selected[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Tahoma, sans-serif][SIZE=2]TV-out:   component video out: HD1080p[/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Tahoma, sans-serif][SIZE=2]It works great now!
[/SIZE][/FONT][/COLOR]

That's great, I did spend some time puzzling over your logs and came to no conclusion - I'll pass on looking at it any more, log files are a great headache maker!

---

