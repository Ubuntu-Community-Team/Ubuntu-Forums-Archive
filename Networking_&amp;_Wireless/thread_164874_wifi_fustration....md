---
title: "wifi fustration..."
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by el duderino on 2006-04-23
First off I'm at work..Don't tell my Boss!
So I don't have my PC handy, but here's my story....

I've got a Gateway Solo 5150 which Ubuntu installed almost perfectly on, sound card not detected or setup propely- not too worried about that yet.

My problem, my PCMCIA wifi card. Its a SMC 2635W "B" PCMCIA card. It worked with the evil OS beautifally, both with wep and open. 

After installing Ubuntu 5.10, investigated wifi card. It was dectected as a ralink 2400? comes up as ra0.
I ran through this forum for setup/troubleshooting. Did the iwconfig, iwlist and checked all the *.opt files that looked like they had something to do with my wifi card. Still no joy.
Card lights up, I can set it to my router's channel, set a wep key, set the ESSID all that good stuff. 
In network admin activated and deactivated after changes. Rebooted did the same(yeh I know windows has me "trained")

Question1: It's a PCMCIA but is being detected as a PCI card. Is this a problem? Could it not be running the right "ifup" script/thing?

Question2: Any suggestions?

I'll post what I can from laptop when I can get my hands on it...


regards...

---

### Post by kyoushu on 2006-04-23
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?")
Follow this.  It really helps, unless you can't find your wireless driver on the list.  Anyways, to have it work best you should somehow install wine, because some of the drivers are exe's that you then install somewhere on your Ubuntu and then find the inf file or the file specified in the directions.

---

### Post by el duderino on 2006-04-24
ah yes! That was one of my last resorts. To go and do a ndiswrapper. I wanted to learn how to setup/install a wifi card. 

here's some terminal output:

> lspci |less

0000:00:0a.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
        Flags: bus master, medium devsel, latency 168, IRQ 9
        Memory at 0c001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 0cc00000-0cfff000 (prefetchable)
        Memory window 1: 0d000000-0d3ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:01:00.0 Network controller: RaLink Wireless PCI Adpator RT2400 / RT2460
        Subsystem: Accton Technology Corporation: Unknown device ee07
        Flags: bus master, slow devsel, latency 64, IRQ 9
        Memory at 0c800000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>


pete@craptop:~$ sudo iwconfig ra0
ra0       RT2400PCI  ESSID:"different"
          Mode:Managed  Channel=1  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:128bit key and off   Security mode:restricted
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

giving ndiswrapper a go...

---

### Post by el duderino on 2006-04-24
just some quick info, the SMC 2635W's drivers aren't in an exe they are one of the folders in the zip file you can download, just exract the XP ones. 
The windows driver's for it can support WPA now...

---

### Post by el duderino on 2006-04-26
ok update...
The drivers at the ndiswrapper site didn't work. I used the drivers from the manufacturer and now my link light blinks like its looking for an ESSID. I found a log showing it was looking for what I set it for, then my neighbors and another ESSID. After it ran through those it went for "any" essid. 
On the iwconfig with the Manufacturer's drivers it had a value for signal stregnth. 
I turned off my WEP and removed the key from ra0's settings. Still no joy. 

I need to do some more reading on installing stuff. I think I need to do the modprobe thing now.

---

### Post by el duderino on 2006-05-05
Ok I'm good to go with my Wireless card (PCMCIA SMC 2635W).

Here's what I did, almost like cheating...

I have a USB hardwire NIC. I used it to connect to my router and updated everything. I even went for a newer kernel. I used the Synaptic Package Manager. I'm a gui addict that dabbles with the command line. I guess the update/new kernel did the trick. 


> his_dudeness@craptop:~$ uname -r
2.6.12-10-386

I have not fully tested my Wifi, no wep or WPA yet but will do so and give you guys some output.

---

