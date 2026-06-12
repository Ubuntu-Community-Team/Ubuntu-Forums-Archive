---
title: "IPN 2220 wireless netcard"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by newparrot on 2012-08-28
Hi
 
I cant set up my wireless connection, can you help please? 
 
I have managed to pull up the box that has network connections on and can click on wireless, and manually input data, but cant see available connections/ I dont know how to configure it manually.
 
Brand new to ubuntu so baby steps if possible please :) 
 
Tried disconnecting wired and rebooting, didnt work.

---

### Post by irv on 2012-08-28
What is your wifi card? If it is a pci card you can do this to see what it is. Type in a terminal:
```
lspci
```
Then post your out put.

---

### Post by newparrot on 2012-08-28
Sorry...VERY new to ubuntu...
 
terminal?

---

### Post by newparrot on 2012-08-28
adrian@adrian-TravelMate-2200:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI Radeon 9100 IGP AGP Bridge
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI OHCI USB Controller #1 (rev 01)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI OHCI USB Controller #2 (rev 01)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI EHCI USB Controller (rev 01)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SMBus (rev 1a)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI Device 434c
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: Advanced Micro Devices [AMD] nee ATI IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: Advanced Micro Devices [AMD] nee ATI IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS300M AGP [Radeon Mobility 9100IGP]
02:02.0 Ethernet controller: InProComm Inc. IPN 2220 802.11g
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
adrian@adrian-TravelMate-2200:~$

---

### Post by RichardTree on 2012-08-28
> **newparrot said:**
> Sorry...VERY new to ubuntu...
 
terminal?

Press Ctrl+Alt+T. It's like the command prompt in Windows.

---

### Post by newparrot on 2012-08-28
Thank you is the above thing right then?

Do you know I had no idea how much windows had taken a hold of my brain until I installed Ubuntu..... its like moving to a different country its so different! I seem to be picking it up.... I think ;)

---

### Post by newparrot on 2012-08-29
Any ideas?
 
Or am I going to have to replace my wireless LAN?

---

### Post by steeldriver on 2012-08-29
Hi the IPN 2220 is a bit of an oddball I think - but folks have certainly go them working

Can you open a terminal and post the output of

```
sudo lshw -C network
```

which will let us see the driver / firmware configuration

---

### Post by newparrot on 2012-08-30
SOrry for the delay in reply.

I have downgraded to xubuntu due to the laptop not coping with ubuntu(just so you know)

Here is the output from above

adrian@adrian-TravelMate-2200:~$ sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:a400(size=32) memory:e8200800-e820081f memory:e8200000-e82007ff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:5e:ba:9e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.5 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:a000(size=256) memory:e8200c00-e8200cff
adrian@adrian-TravelMate-2200:~$

---

### Post by newparrot on 2012-08-30
This is driving me mad! I have read that I can install drivers using a command but I really am a newbie to Linux and am struggling!

---

### Post by steeldriver on 2012-08-30
I *think* I'm correct in saying there is no native Linux support for that device - only ndiswrapper

[http://ubuntuforums.org/showpost.php?p=12154806&postcount=4](http://ubuntuforums.org/showpost.php?p=12154806&postcount=4)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

You should confirm you have the same PCI-ID before going ahead, e.g. using

```
lspci -vnn | grep -iA2 'InProComm'
```and looking for the number in brackets [17fe:2220]

---

### Post by newparrot on 2012-08-30
adrian@adrian-TravelMate-2200:~$ lspci -vnn | grep -iA2 'InProComm' 02:02.0 Ethernet controller [0200]: InProComm Inc. IPN 2220 802.11g [17fe:2220]     Subsystem: AMBIT Microsystem Corp. Device [1468:0305]     Flags: bus master, medium devsel, latency 64, IRQ 11   Is this the right one? *confused :(   Also      When I type in the command given in the links I get this  adrian@adrian-TravelMate-2200:~$ sudo apt-get install ndisgtk [sudo] password for adrian:  Reading package lists... Done Building dependency tree        Reading state information... Done ndisgtk is already the newest version. The following packages were automatically installed and are no longer required:   linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic Use 'apt-get autoremove' to remove them. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. adrian@adrian-TravelMate-2200:~$

---

### Post by newparrot on 2012-08-30
I have found a driver that matches card and have downloaded and extracted but dont know what to do next...

---

### Post by chili555 on 2012-08-30
Ndisgtk is correct for your device. Download the file I've attached to your desktop. Right-click it and select Extract Here. Open a terminal and do:```
sudo ndisgtk
```When the window opens, point to Desktop > Winxp > neti2220.inf. Your wireless should spring to life. Post back if you need more help.

---

### Post by newparrot on 2012-08-30
It pops up a window saying root or sudo priviledges required.... when i have done a sudo command before it asks for password which I type into terminal but there seems no option to do this?

---

### Post by chili555 on 2012-08-30
Please type:```
sudo ndisgtk
```For security purposes, your password is not echoed back to you; not even ****. Just type it in and press Enter.

---

### Post by newparrot on 2012-08-30
Thank you thank you thank you thank you thank you :D  If i could blow virtual kisses at you I would, works like a dream thank you so so much :)

---

### Post by chili555 on 2012-08-30
You're very welcome! Please use thread tools at the top and mark Solved.

Have fun!

---

### Post by AndyOpie150 on 2012-08-30
EDIT: oops

---

### Post by chili555 on 2012-08-30
> **AndyOpie150 said:**
> what's the output of: 
lsusb
ndiswrapper -lIt's not a USB device and I think he's all set.

---

### Post by AndyOpie150 on 2012-08-30
Sorry, was posting based on info in first page (just trying to help draw out more info). Didn't see there was a second page with your great advice. Duh! 
 
My brain is overloaded from trying to research and try everything having to do with getting a internet connection on Ubuntu (can't seem to even get a wired connection straight from the modem).

---

### Post by chili555 on 2012-08-30
> **AndyOpie150 said:**
> Sorry, was posting based on info in first page (just trying to help draw out more info). Didn't see there was a second page with your great advice. Duh! 
 
My brain is overloaded from trying to research and try everything having to do with getting a internet connection on Ubuntu (can't seem to even get a wired connection straight from the modem).Do you have a thread? Can we help you?

---

### Post by AndyOpie150 on 2012-08-30
I think I will start a thread after reading and trying a few more things (I hate to start a new thread if the info has already been posted).

---

### Post by frederik1975 on 2013-02-07
Hi,

I did had same problem with mine installed ubuntu 12.10. The wireless device didn't work. But it seems I did found solution.

First I did downloaded the ndiswrapper-1.58rc1 (Download link earlier post above)
Then I did downloaded the Winxp driver for mine IPN2220 (Download link earlier post above)

Then I did unzip both downloaded documents in mine folder Downloads

Then I did followed steps in the konsole or terminal:
1. sudo make uninstall
2. sudo make
3. sudo make install
     "This was giving troubles" I did had some errors with that command.. see errors:
     mkdir: kan map ‘/lib/modules/3.5.0-23-generic/misc’ niet aanmaken: Toegang 
     geweigerd
     It seems it couldn't build this map misc and it didn't had correct rights?
4. Open a second Terminal and make that map manual: 
    
     cd /lib/modules/3.5.0-23-generic/

      sudo mkdir misc

5. now try again ==>    sudo make install
6. no go to the extracted map where your driver is and type:  ndiswrapper -i neti2220.inf
7. sudo ndiswrapper -l
    (This will give you something like below)
    neti2220 : driver installed
    device (17FE:2220) present
8. sudo modprobe ndiswrapper


After this it was working :D
It seems there were troubles with access rights, I put for every command "sudo" and the directorys he fails to make automatic I did create with sudo mkdir..........

Maybe it can be done more easy or pro... but it works fine now for me;)

Thanx for the post of the WindowsXP drivers

Best Regards,
):P

---

### Post by mörgæs on 2013-02-07
Thanks for the advice. Am I correct assuming it was a 32 bit installation?

---

