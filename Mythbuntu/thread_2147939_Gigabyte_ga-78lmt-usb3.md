---
title: "Gigabyte ga-78lmt-usb3"
date: 2013-05-23
forum: Mythbuntu
---

### Post by marduk201 on 2013-05-23
Hello all i don't like to open a new post but i hit the end. I build a new HTPC using the Gigabyte GA-78LMT-USB3. i frist had it runing with windows 7 MC and everything worked fine. then i found Myth box and downloaded and installed mythbuntu. here is were verything when wrong. Im using the HDMI output to the TV and i cant for the live of me get the sound to come out. i found a forum that had the some problem with the same borad but the user was runing Ubuntu 13. i tryed what the forum said but nothing happen. the video seem to work fine in menu and on the deck top but when i try to play a 1080adp the looks like s@#t (on a side note that same video plays great on my Rasbarry Pi) I found that the mother borad has Integrated ATI Radeon HD 3000 graphics. but it don't same to find it on the new hardware program. here are the full spec of the board. 

[http://www.gigabyte.com/products/product-page.aspx?pid=4305#ov](http://www.gigabyte.com/products/product-page.aspx?pid=4305#ov)     

any help would be great.

---

### Post by gordintoronto on 2013-05-23
I have never used Mythbuntu. Is there a Sound Settings program? What options does it show for output?

Can you open Terminal and enter this somand: lspci
It shoulkd produce 15 to 20 lines of output, and a couple of them should include Audio device, such as this:
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)

If you were to copy/paste those lines into your response, it might help.

Also, the output from uname -a so we can see how up to date your Mythbuntu is.

---

### Post by marduk201 on 2013-05-23
this is what pop out

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS780 HDMI Audio [Radeon HD 3000-3300 Series]
02:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
03:00.0 Multimedia video controller: Device 1b7c:0004 (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
05:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)

---

### Post by gordintoronto on 2013-05-23
OK, you answered 25% of my questions, what about the other ones?

If Sound Settings is available, it sure looks like it would solve the problem, by selecting:
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS780 HDMI Audio [Radeon HD 3000-3300 Series]

---

### Post by PhilWig on 2013-06-24
That board looks great apart from the ATI graphics which seems to have issues under Linux.

I'm not sure of your expertise level so forgive me if I'm teaching grandma to suck eggs.  A few very basic things which gave me grief with sound:
1.  With my Nvidia graphics, I needed to upgrade the driver (in Mythbuntu control centre).  Perhaps you need to do so for your ATI?
2.  Start a terminal session, run alsamixer, enable all three 958 channels; set master and front volumes to maximum.  
It's not very intuitive until you find that H gives help.
3.  In frontend > setup > audio try different settings and use the test facility.  You have the right one if you get a hiss.
  
Possible other avenues:  add an Nvidia graphics board?   Might (mumble) XBMC frontend be better?

HTH
Phil

---

