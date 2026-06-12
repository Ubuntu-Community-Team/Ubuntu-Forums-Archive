---
title: "trouble with wireless on an old computer"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by ebodnaruk on 2009-08-16
I just installed Ubuntu 9.04 on an old computer of mine to see if that would improve its performance.  I however am having trouble getting the wireless to work.  It definitely still worked before.  I am still a newbie at ubuntu so I would appreciate some help. (I have a new computer and wireless worked just fine.) I am pasting the results of the following commands:  

  	 	 	 	 	 	   Code:
 sudo lshw -c network lspci iwconfig ifconfig I assume it's because this computer has an older wireless card, but don't really know. 

Thanks so much!

  	 	 	 	 	 	   *-network:0 UNCLAIMED    
        description: Ethernet controller 
        product: 88w8335 [Libertas] 802.11b/g Wireless  
        vendor: Marvell Technology Group Ltd.  
        physical id: 9  
        bus info: pci@0000:01:09.0  
        version: 03  
        width: 32 bits  
        clock: 66MHz  
        capabilities: pm bus_master cap_list  
        configuration: latency=64  
   *-network:1  
        description: Ethernet interface  
        product: NC100 Network Everywhere Fast Ethernet 10/100  
        vendor: ADMtek  
        physical id: b  
        bus info: pci@0000:01:0b.0  
        logical name: eth0  
        version: 11  
        serial: 00:03:6d:15:c7:f6  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes  
   *-network DISABLED  
        description: Ethernet interface  
        physical id: 1  
        logical name: pan0  
        serial: 56:b5:d3:52:3c:8c  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes  
 

 

 

 LSPCI command
 

 user@user-desktop:~$ lspci  
 00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)  
 00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)  
 00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)  
 00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)  
 00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)  
 00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)  
 01:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)  
 01:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)  
 01:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)  
 

 

 user@user-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 eth0      no wireless extensions.  
 pan0      no wireless extensions.
 

 

 user@user-desktop:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:03:6d:15:c7:f6   
           inet6 addr: fe80::203:6dff:fe15:c7f6/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:5 dropped:0 overruns:0 carrier:10  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:9 Base address:0xd800  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by Metaljaz on 2009-08-16
Follow this thread:

[http://art.ubuntuforums.org/showthread.php?t=1136959](http://art.ubuntuforums.org/showthread.php?t=1136959)

---

### Post by ebodnaruk on 2009-08-16
Thanks, I'll give it a try tomorrow and see what happens!

---

### Post by ebodnaruk on 2009-08-17
Ok, I followed the thread above which basically tells me that I need to use ndiswrapper and a driver for my internet card.  I downloaded the driver mentioned from drivers.softpedia.com and it came as a file called 8335_3.2.1.3.exe

Now I have no clue how to run an .exe file in Ubuntu, and how to use ndiswrapper.  I don't see it in any of my program files, etc.  Can you please help?  I did the whole make install thing for ndiswrapper-1.55 and that seemed to work just fine.

Thanks!
Ethan

---

### Post by kerry_s on 2009-08-17
you need to extract that, try **right clicking-> extract here**

or

in a terminal:
**unzip -a 8335_3.2.1.3.exe**

---

### Post by ebodnaruk on 2009-08-17
I tried extracting the 8335_...exe file but there was an error message.  In brief:

"end of central directory signature not found.  Either this file is not a zipfile...  file may be a plain executable, not an archive.  cannot find zipfile directory in one of 8335...exe or .exe.zip" and so on...

---

### Post by kerry_s on 2009-08-17
here use this driver:
[ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)

follow the instructions here:
[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

---

### Post by ebodnaruk on 2009-08-18
> **kerry_s said:**
> here use this driver:
[ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)

follow the instructions here:
[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

Wow, it works!  Thanks!  I got a little confused on step 5 of the instructions in the link above, where you are supposed to edit the file wpa_supplicant.conf.  I was confused because I had no such file, but then I realized by editing it, you create the file and add the text to it according to the instructions!  So that was good.  

I don't really understand a lot of the directions but i could follow them blindly!  It's funny - i'm used to being pretty good with computers, but this stuff is just crazy!  

Thanks again,
Ethan

---

