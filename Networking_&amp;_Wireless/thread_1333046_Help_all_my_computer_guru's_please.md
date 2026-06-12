---
title: "Help all my computer guru's please"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by helloamhere8702 on 2009-11-21
i know its a million questions out there about wireless but i have to ask mine.      CAN SOMEONE HELP ME GET WIRELESS CONNECTIONS? PLEASE      I just installed ubuntu 9.10 on my laptop its a acer aspire 3620, but for some reason its not picking up no wireless connections, and its a whole bunch of them in my area.       I installed ubuntu on my brothers laptop yesterday and his works fin and he has an acer aspire 5100 a little newer than mine, but his works perfect.      IF ANY ONE OF YOU KIND COMPUTER GURU'S OUT HERE CAN HELP ME SOLVE MY PROBLEM THAT WOULD BE GREAT, I REALLY LOVE UBUNTU.  i dont have my own network i just use the local wireless connections.

---

### Post by Iowan on 2009-11-21
Wireless still isn't my strong suit, but I'll ask the openers: From a terminal (Applications>Accessories>Terminal) check **lshw -C network** - post results. The opener would be - "What is the chipset, and is it being recognized?"

---

### Post by helloamhere8702 on 2009-11-21
> **Iowan said:**
> Wireless still isn't my strong suit, but I'll ask the openers: From a terminal (Applications>Accessories>Terminal) check **lshw -C network** - post results. The opener would be - "What is the chipset, and is it being recognized?"

i copy that command and paste to terminal and this is what i get:

No command 'check' found, did you mean:
 Command 'icheck' from package 'icheck' (universe)
 Command 'chuck' from package 'chuck' (universe)
 Command 'acheck' from package 'acheck' (universe)
 Command 'vcheck' from package 'vcheck' (universe)
 Command 'mcheck' from package 'mtools' (main)
 Command 'fcheck' from package 'fcheck' (universe)
check: command not found

????????? i dont know whats going on with it??????

---

### Post by bkratz on 2009-11-21
> **helloamhere8702 said:**
> i copy that command and paste to terminal and this is what i get:

No command 'check' found, did you mean:
 Command 'icheck' from package 'icheck' (universe)
 Command 'chuck' from package 'chuck' (universe)
 Command 'acheck' from package 'acheck' (universe)
 Command 'vcheck' from package 'vcheck' (universe)
 Command 'mcheck' from package 'mtools' (main)
 Command 'fcheck' from package 'fcheck' (universe)
check: command not found

????????? i dont know whats going on with it??????



He didn't mean to put in the word check it should just be

[B]lshw -C network


[/B]

---

### Post by helloamhere8702 on 2009-11-21
> **bkratz said:**
> He didn't mean to put in the word check it should just be

[B]lshw -C network


[/B]

i tried that too and it says:

no command Ishw found, did you mean: 
command 'Ishw' found, did you mean:
command 'Ishw' from package 'Ishw' (main)
Ishw command not found
  
thats what am getting when i type that

---

### Post by bkratz on 2009-11-21
> **helloamhere8702 said:**
> i tried that too and it says:

no command Ishw found, did you mean: 
command 'Ishw' found, did you mean:
command 'Ishw' from package 'Ishw' (main)
Ishw command not found
  
thats what am getting when i type that


That is a little L as in little, not an I

---

### Post by Iowan on 2009-11-21
Try again: ```
lshw -C network
```
That's a lower case "L" (ell), not a "one" or " capital eye" ;)
Sorry about the confusion...

---

### Post by helloamhere8702 on 2009-11-21
> **Iowan said:**
> Try again: ```
lshw -C network
```That's a lower case "L" (ell), not a "one" or " capital eye" ;)
Sorry about the confusion...


Oh ok cool, now i got it this is what it says a really long message and towards the end it says network DISABLED

---

### Post by bkratz on 2009-11-21
> **helloamhere8702 said:**
> Oh ok cool, now i got it this is what it says a really long message and towards the end it says network DISABLED



That is what he wanted you to paste in so he could see it ; and probably lspci also ( again a little L)

---

### Post by helloamhere8702 on 2009-11-21
> **bkratz said:**
> That is what he wanted you to paste in so he could see it ; and probably lspci also ( again a little L)

OK I DID THAT AND I GOT:
 
32 maxl at ency=64 mi ngnt=32 mulicast= yes
    resources: irg: 20 i oport: 3000( size=256) memory: b0102000-b01020ff
    network DISABLED
    description: Wireless interface
    physical id: 1
    logical name: wi an0
    serial: 00: 14: a4: 82: b1: 0f
    capabilities: Ethernet physical wireless 
    configuration: broadcast=yes multicast=yes wireless= IEEE 802. 11bg

---

### Post by steveneddy on 2009-11-21
Simple question:

Did you right click the Network Manager applet and check "Enable Wireless" ?

---

### Post by bkratz on 2009-11-21
> **helloamhere8702 said:**
> OK I DID THAT AND I GOT:
 
32 maxl at ency=64 mi ngnt=32 mulicast= yes
    resources: irg: 20 i oport: 3000( size=256) memory: b0102000-b01020ff
    network DISABLED
    description: Wireless interface
    physical id: 1
    logical name: wi an0
    serial: 00: 14: a4: 82: b1: 0f
    capabilities: Ethernet physical wireless 
    configuration: broadcast=yes multicast=yes wireless= IEEE 802. 11bg


Is that all you got?
please copy and paste the output rather than typing it. You can use the third symbol from the right (the #) to condense the posting and make it readable.  This is where it says "wrap code tags around selected text"

Also include lspci

---

### Post by helloamhere8702 on 2009-11-21
> **steveneddy said:**
> Simple question:

Did you right click the Network Manager applet and check "Enable Wireless" ?

yes i did, thats check off

---

### Post by helloamhere8702 on 2009-11-21
> **bkratz said:**
> Is that all you got?
please copy and paste the output rather than typing it. You can use the third symbol from the right (the #) to condense the posting and make it readable.  This is where it says "wrap code tags around selected text"

Also include lspci

am actually using a different laptop to be on the forum, so i cant copy and paste....
but thats not the only thing i got its a really long message but i just typed out the message at the end. thats the whole issue is that my other laptop is not picking up internet connection so i have to use this computer for the forum....

---

### Post by bkratz on 2009-11-21
Do you have a usb thumb drive to transfer the files?  We really need to find out what your network card is.  It is probably listed in the output of lspci or lsusb  ( if it is a usb dongle), or can you find it in the listings?

---

### Post by helloamhere8702 on 2009-11-21
> **bkratz said:**
> Do you have a usb thumb drive to transfer the files?  We really need to find out what your network card is.  It is probably listed in the output of lspci or lsusb  ( if it is a usb dongle), or can you find it in the listings?


OK. thats what am going to do transfer it

---

### Post by helloamhere8702 on 2009-11-21
> **bkratz said:**
> Do you have a usb thumb drive to transfer the files?  We really need to find out what your network card is.  It is probably listed in the output of lspci or lsusb  ( if it is a usb dongle), or can you find it in the listings?

OK. this is what came up:

  	 	 	 	 	 	  jermaine@ubuntu:~$ lshw -C network  
 WARNING: you should run this program as super-user.  
   *-network:0              
        description: Network controller  
        product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller  
        vendor: Broadcom Corporation  
        physical id: 5  
        bus info: pci@0000:06:05.0  
        version: 02  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master  
        configuration: driver=b43-pci-bridge latency=32  
        resources: irq:21 memory:b0100000-b0101fff  
   *-network:1  
        description: Ethernet interface  
        product: RTL-8139/8139C/8139C+  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 7  
        bus info: pci@0000:06:07.0  
        logical name: eth0  
        version: 10  
        serial: 00:0a:e4:f2:fe:5a  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes  
        resources: irq:20 ioport:3000(size=256) memory:b0102000-b01020ff  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 1  
        logical name: wlan0  
        serial: 00:14:a4:82:b1:0f  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 



 jermaine@ubuntu:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)  
 00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)  
 00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)  
 00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)  
 00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)  
 00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)  
 00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)  
 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)  
 00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)  
 00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)  
 00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)  
 00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)  
 06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)  
 06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)  
 06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)  
 jermaine@ubuntu:~$  
 

THATS WHAT IT SAYS

---

### Post by bkratz on 2009-11-21
The wireless is the BCM4318 the other (RTL-8139....) is the ethernet controller.  There are a lot of threads for all of us to read!  Here is a start for the wireless

[http://ubuntuforums.org/search.php?searchid=67146069](http://ubuntuforums.org/search.php?searchid=67146069)

Look at the most recent ones first and one that either have a lot of postings or say solved first.

Also, is there a switch that needs to be turned on on the laptop? Secondly check the menu
System-administration--hardware drivers  at the top of the screen and see if it gives any information and directions.

It will take a while to go through all the threads, so I will subscribe to the thread and check back later (after sleeping!)

---

### Post by bkratz on 2009-11-21
This one looks promising

[http://ubuntuforums.org/showthread.php?t=1312325&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1312325&highlight=BCM4318)

---

