---
title: "Any ideas on how to get a Remote Control to work with a Zotac Box?"
date: 2013-04-11
forum: Mythbuntu
---

### Post by TheFuzz4 on 2013-04-11
Hey Everyone,

So I purchased this the other day [http://www.amazon.com/gp/product/B006HFVYUC/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1]("http://www.amazon.com/gp/product/B006HFVYUC/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1") and I got it yesterday, installed everything and got it all setup.  

For those of you who are wondering yes it does work great.  I have the latest AMD Graphics installed on it.  The only thing I had to do was adjust the overscaling of the card to get rid of the black boarders around the screen.  Oh and I also had to adjust the audio and graphic settings within the settings for the frontend as well.  No biggie here as I do this with each new frontend build out anyways.  

The only flaw I have is that its currently on my home G WiFi and if my other frontend in my living room is playing at the same time as this, this one suffers at the expense of the Living Room.  But I did run a cable to my bedroom last year but the wall jack is having an issue so I'll have to trouble shoot that and then I'll just hardwire this into my network and that should solve those problems.  

So anyways on with my question.

This little guy came with a remote control and I for the life of me cannot figure out how to set up the remote.  

Here is the output from LSUSB

```

myth@myth3:~$ lsusb
Bus 005 Device 002: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

and lspci
```

myth@myth3:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.3 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

In either of those outputs I don't see anything that stands out as the Infrared controller.  It is possible I'm just over looking something but I just don't see it.   I'm wondering if anyone else has purchased a unit similar to this one and might be able to perhaps shed some light on this.  For right now the wife and I are just using the Mythmote to control the box but we'd rather get the remote for this working and then setup our Logitech Harmony to work with the myth box.  Thank you all in advance for your help with this.

---

### Post by TheFuzz4 on 2013-04-11
Ok so after messing in the Bios (Which btw is the nicest bios I've ever seen on a box PC) The bios reported that the onboard IR was enabled but I disabled and renabled it for good measure.  After doing that I now have this in my lsusb output

```

Bus 004 Device 002: ID 099a:7202 Zippy Technology Corp. 

```

Not quite sure what Zippy is yet but I can only assume that this is the IR Receiver.  So now onto more troubleshooting with this silly thing.  BTW the PC did come with another IR Receiver for USB as well so I know that thing is going to go to another frontend for sure.

---

### Post by uteck on 2013-04-11
My Zotac worked without any fuss when I installed Mythbuntu and later with OpenElec.
You could try with another OS just to rule out a hardware problem, but if the problem persists it might be the hardware.

---

