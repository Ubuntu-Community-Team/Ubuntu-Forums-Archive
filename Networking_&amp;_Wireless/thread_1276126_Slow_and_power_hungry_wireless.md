---
title: "Slow and power hungry wireless"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by artg@cs.nyu.edu on 2009-09-26
Hello 

  	 	 	 	 	 	  I'm running Ubuntu 8.04 on a laptop.    	 	 	 	 	 	  
It's a MICRO-STAR INT'L, MS-1029, with an American Megatrends Inc. BIOS     	 	 	 	 	 with an AMD Turion(tm) 64 Mobile Technology MT-40 running at 2200MHz. The    	 	 	 	 	Wireless interface is a 

	RT2500 802.11g Cardbus/mini-PCI. (More info below.)


1. should I run a 64-bit OS on it?


2. The wireless runs slow, inconsistent and hot. Data rates peak at 50 KB/sec, but often stall. All transfers rev the fan and heat the box. How should I debug this?


   	 	 	 	 	BR
A


More extensive info:



It's a MICRO-STAR INT'L, MS-1029, with an American Megatrends Inc. BIOS with capabilities: 	isa eisa pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int14serial int10video acpi usb agp smartbattery biosbootspecification
 

 the CPU is an AMD Turion(tm) 64 Mobile Technology MT-40
 running at 2200MHz
 width: 	64 bits
 capabilities: 	fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
 with L1-Cache 128KiB with pipeline-burst internal varies data
 System Memory 2GiB
 and Host bridge from Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge
 vendor: 	ATI Technologies Inc
 description: 	Ethernet interface
 product: 	RTL-8139/8139C/8139C+
 vendor: 	Realtek Semiconductor Co., Ltd.
 

 description: 	Wireless interface
 product: 	RT2500 802.11g Cardbus/mini-PCI
 vendor: 	RaLink
 physical id: 	
 9
 bus info: 	
 pci@0000:02:09.0
 logical name: 	
 wmaster0
 version: 	01
 serial: 	00:13:d3:67:40:f3
 width: 	32 bits
 clock: 	33MHz
 capabilities: 	pm bus_master cap_list logical ethernet physical wireless
 configuration:	
 broadcast	=	yes
 driver	=	rt2500pci
 ip	=	192.168.1.4
 latency	=	64
 module	=	rt2500pci
 multicast	=	yes
 wireless	=	IEEE 802.11g

---

### Post by spd106 on 2009-09-27
1. I don't have a 64-bit compatible PC, so I can't really advise you. But I hear that most of early issues have been resolved now. You even use flash on 64-bit now.


2.I would recommend upgrading to a newer version of Ubuntu as it will have a better version of the RT2x00 driver that you are using.

See [http://www.linux.com/archive/feature/132701](http://www.linux.com/archive/feature/132701)

Try downloading the Ubuntu 9.04 live CD and see if it improves your wireless performance, you don't really have anything to lose. Might want to grab the 64-bit edition too.

---

### Post by artg@cs.nyu.edu on 2009-09-28
Thanks spd106

I've since noticed that the laptop runs much more slowly than I'd expect. For example, with only one user logged in, and only two user applications -- Firefox (with just 6 tabs using 130 MB RAM) and SystemMonitor -- CPU usage ranges between 20% and 80 %. Much slower than I'd expect from a 2 GHZ CPU with 2 GB RAM.

I'll try 64-bit ubuntu 9.04, unless someone suggests otherwise.

BR
A

---

