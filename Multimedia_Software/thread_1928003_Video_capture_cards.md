---
title: "Video capture cards"
date: 2012-02-19
forum: Multimedia Software
---

### Post by Salbono on 2012-02-19
Having trouble getting video capture card to be recognized in Ubuntu and work. Why is this such a difficult thing??

 The computer with the capture card was setup as dual boot and has windows xp on it. From what I have read in the forums if you  boot with windows all will work fine.

Why hasn't somebody wrote code that will find the card in the machines structure, read the capture card contents and provide help with getting it setup??

I read one post about it and the member was told at the beginning that he should expect to spend two hours setting it up... it was a new card the person had just purchased a Haugen 250 or something like that. or just crawl back to microsoft....  what?

There are  A lot of things I want to do on my computers but spending hours setting up a capture card is not one of them. Although I probably have four into this one   lol

Again why the hard time setting up capture cards??

---

### Post by MartyBuntu on 2012-02-19
Which capture card do you have?

---

### Post by wolfen69 on 2012-02-19
Linux is coded mostly by volunteers. There is no one company that develops it. Device drivers are written by the companies that produce the devices, and given to microsoft and apple to use. If the company does not provide the drivers for linux, we are left to resorting to volunteers to write them.

Secondly, linux is a bit like mac, in the sense that you can't just buy any old hardware and expect it to work 100% of the time. (and I never hear mac users complain) You need to do a bit of research to find out what is compatible, and what is not. Google can take care of that for you. I myself, always make sure that I buy linux compliant hardware, and could not be happier.

Thirdly, let's find out what type of tv tuner card you have. Open a terminal and do:
```
lspci
```
Copy and paste the output here.

---

### Post by Salbono on 2012-02-19
> **MartyBuntu said:**
> Which capture card do you have?

The card Says falcon2. I recycled it from a 6 or 7 year old Gateway that somebody got rid of because the hard drive crashed.

I git it to work in MythTv once but then lost config file and it quite working.

Here is the printout from the command

  	 	 	 	 	 	   00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)  
 00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port  
 00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)  
 00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)  
 00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)  
 00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)  
 00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)  
 00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)  
 00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)  
 00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)  
 00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8400 GS] (rev a1)  
 02:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)  
 02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)  
 02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)

    Thank You

---

### Post by wolfen69 on 2012-02-19
You are in luck. It's IVTV based and well supported. See [my tutorial]("http://ubuntuforums.org/showthread.php?t=1734916") to get it working. Ask if you have any questions.

---

### Post by Salbono on 2012-02-20
I followed your instructions and everything worked great! Thank You.
Although I recorded some tv and when I viewed it the audio was still playing what was on the tv.
Again I thank you for your help.

---

### Post by pinelights on 2012-02-23
> **wolfen69 said:**
> You are in luck. It's IVTV based and well supported. See [my tutorial]("http://ubuntuforums.org/showthread.php?t=1734916") to get it working. Ask if you have any questions.

 Hi there - is your guide applicable for the HVR-3000 (analog tv + video capture) as well? I am thinking of moving to an Ubuntu 11.04 + MythTV and XBMC machine but the Live TV/Myth part is the hardest for me to figure out being a noob :confused:  Is there a noob-proof guide to set up MythTV say if one were to have the front/backend on the same machine?

Also there is a "Mythbox" addon for XBMC but i am unsure if one has to have a working mythtv set up before this add on could work in XBMC :confused:

Lastly can an Ubuntu + Myth machine share out the tv tuner so clients can view live tv? They may be windows or Mac machines

---

### Post by clarksonfisher on 2013-03-04
I wonder if you might be up for helping me also, wolfen69?

I'd love to be able to use TVTime which currently only tells me that it "Cannot open capture device /dev/video0"

Here's my lspci output:
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port B)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port H)
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
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde [Radeon HD 7700 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0
02:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
03:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV200 QW [Radeon 7500]
04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
06:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller



```

I appreciate very much any help that anyone might be able to give. The computer I am struggling with is my first Ubuntu computer. I had lots of trouble installing a driver for my primary vid card -- Radeon 7770 -- but eventually I found online enough documentation and discussion for me to eventually learn to make it work. Adding this 2nd video card is a different story though as it is very old and so there is way less documentation that I was able to find. Anyone happen to know what I need to do? THANKS!

---

