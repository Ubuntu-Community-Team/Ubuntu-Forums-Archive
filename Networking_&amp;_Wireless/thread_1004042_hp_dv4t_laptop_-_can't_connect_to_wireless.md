---
title: "hp dv4t laptop - can't connect to wireless"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by rajasekhar on 2008-12-06
I have hp dv4t laptop with Intel Pro/Wireless 5100 AGN. I recently installed Intrepid Ibex. I cannot connect to my wireless network! wlan doesn't even show up in iwconfig listings...


Here are the results of commands lshw and iwconfig. Please help me! Appreciate it!

 sudo lshw -C Network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:ef:86:99
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.6 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 42:b0:04:92:20:7d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



-----------------


$iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by albinootje on 2008-12-06
Please try : 
sudo update-pciids ; sudo update-usbids
Then post the output of : lspci|grep net

---

### Post by rajasekhar on 2008-12-07
thanks for the reply. Here is the result of your suggestion!

$ lspci|grep net
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by rajasekhar on 2008-12-08
bump!

---

### Post by rajasekhar on 2008-12-10
anybody help!

---

### Post by rajasekhar on 2008-12-11
The issue is resolved. I installed intrepid ibex rather than upgrading from hoary. That solved it. The wireless is up and running. wooohoooooo!!

---

### Post by stickman51 on 2008-12-15
> **albinootje said:**
> Please try : 
sudo update-pciids ; sudo update-usbids
Then post the output of : lspci|grep net

Hello from a former Nederlander, albinootje; I have almost the identical problem. Any chance you can help me? Ubuntu 8.10 just installed on a new laptop; will not recognize ANY WLANs here. If i boot it into Vista, NO problem. Thanks. ken

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> Hello from a former Nederlander, albinootje; I have almost the identical problem. Any chance you can help me? Ubuntu 8.10 just installed on a new laptop; will not recognize ANY WLANs here. If i boot it into Vista, NO problem. Thanks. ken

Hi fellow dutchman stickman51 :) (Goeiemiddag ;-).

I think it's a good idea to start a new thread about this. Then it will be under new posts, and it will show up in the RSS-feed of the Ubuntu-forums.

Regarding your question. If Ubuntu doesn't see any wifi-card then you might need to try Ndiswrapper.

Can you post (in the new thread) the output of :
lspci
and 
lsusb ?

Good luck!
(Succes ermee alvast!)

---

### Post by stickman51 on 2008-12-15
Thanks for the quick reply, albinootje; Bedankt! I'm afraid to start a THIRD thread on this one for fear of getting flamed or worse........... maybe you can reply to the last time I started a new thread? That thread is at [http://ubuntuforums.org/showthread.php?p=6369508#post6369508](http://ubuntuforums.org/showthread.php?p=6369508#post6369508) and I can post all the long text from entering those 3 little codes; I was able to move it from the troubled computer to THIS one with a flash drive.

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> Thanks for the quick reply, albinootje; Bedankt! I'm afraid to start a THIRD thread on this one for fear of getting flamed or worse........... maybe you can reply to the last time I started a new thread? That thread is at [http://ubuntuforums.org/showthread.php?p=6369508#post6369508](http://ubuntuforums.org/showthread.php?p=6369508#post6369508) and I can post all the long text from entering those 3 little codes; I was able to move it from the troubled computer to THIS one with a flash drive.

Okay, good :)
Can you post the output of lspci and lsusb there ?
Also the output of :
sudo lshw -C Network

Thanks in advance!
Dank alvast.

---

### Post by albinootje on 2008-12-15
By the way, trouwens.. I just found this :
[http://www.linlap.com/wiki/HP+Pavilion+dv4t](http://www.linlap.com/wiki/HP+Pavilion+dv4t)
See the comments, one poster claims that wireles works out of the box using the 8.10 installation cdrom.

This looks even better :
[http://lindajane.wordpress.com/2008/11/02/installation-tips-for-hp-dv4t-laptop-on-ubuntu-810-intrepid-ibex/](http://lindajane.wordpress.com/2008/11/02/installation-tips-for-hp-dv4t-laptop-on-ubuntu-810-intrepid-ibex/)

It talks about enabling the restricted driver for the wireless card.
Which Ubuntu release were you using ?
(I missed a bit of the previous postings).

I'm off to do some shopping,
GL! :)

---

### Post by stickman51 on 2008-12-15
Here is what I got yesterday after somebody told me HOW to bring all this up; I'll have to still try the one you listed:

lspci
ifconfig
iwconfig 

THIS is ALL the text that appeared:

kenlaninga@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
kenlaninga@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:dc:85:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

kenlaninga@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

kenlaninga@ubuntu:~$

---

### Post by stickman51 on 2008-12-15
Hmmm; I may have replied in the wrong thread here so here it is again:

Here is what I got yesterday after somebody told me HOW to bring all this up; I'll have to still try the one you listed:

lspci
ifconfig
iwconfig

THIS is ALL the text that appeared:

kenlaninga@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
kenlaninga@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1d:72:dc:85:f3
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:16

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:246 errors:0 dropped:0 overruns:0 frame:0
TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:15408 (15.4 KB) TX bytes:15408 (15.4 KB)

kenlaninga@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

kenlaninga@ubuntu:~$


I did the one you said: sudo lshw -C Network but have to move it to this computer so will do that in a minute or two. THANKS!

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> 
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

That's your wifi-card.
You're using 8.10 ? Can you go -> System -> Admin -> Hardware Drivers
and see whether the Atheros driver is mentioned there ?

And i got a little confused, i assumed you also had a HP dv4t laptop.
But perhaps you don't. Correct ?

---

### Post by stickman51 on 2008-12-15
Here is the other one you asked for:

kenlaninga@ubuntu:~$ sudo lshw -C Network
[sudo] password for kenlaninga: 
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:1d:72:dc:85:f3
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:10:04:4d:45:16
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
kenlaninga@ubuntu:~$

---

### Post by stickman51 on 2008-12-15
> **albinootje said:**
> That's your wifi-card.
You're using 8.10 ? Can you go -> System -> Admin -> Hardware Drivers
and see whether the Atheros driver is mentioned there ?

And i got a little confused, i assumed you also had a HP dv4t laptop.
But perhaps you don't. Correct ?

Sorry, I should have mentioned that my new laptop is an eMachines running Vista (and now, Ubuntu) and I can give you all the info you need on that too.

Yes, in the Hardware Drivers box I see with a green dot, "Support for Atheros 802.11 wireless LAN cards." and with a black dot, "ATI/AMD proprietary FGLRX graphics driver"

and below that, under "Support for Atheros 802.11 wireless LAN cards." I see:
Tested by the Ubuntu developers
License: Free"

and at the very bottom, with green dot, "This driver is activated and currently in use."

That any good to you?

---

### Post by stickman51 on 2008-12-15
And, yes, I'm running Ubuntu 8.10 just downloaded and installed Friday.

---

### Post by stickman51 on 2008-12-15
will it help if I post a picture of the "Hardware Drivers" box?

---

### Post by stickman51 on 2008-12-15
albinootje, in my netbook running Linux Debian (I think) all I did was right-click the WIFI icon, pick my own WLAN from the several it found, and enter my 10-digit security code and it was online. I tried it here but am not sure where to enter that 10-digit code nor what to enter in the other lines: here is a pic of what I'm looking at:

---

### Post by albinootje on 2008-12-15
Okay, thanks for the information. 
That is clear, no need for a screenshot.

Can you also name the type of the eMachines that you have.
Here are a few mentioned : [http://www.linux-on-laptops.com/emachines.html](http://www.linux-on-laptops.com/emachines.html)

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> albinootje, in my netbook running Linux Debian (I think) all I did was right-click the WIFI icon, pick my own WLAN from the several it found, and enter my 10-digit security code and it was online. I tried it here but am not sure where to enter that 10-digit code nor what to enter in the other lines: here is a pic of what I'm looking at:

Okay, but if the iwconfig command is not showing any wifi, then it's pretty likely that the network-manager (where you attached the screenshot from) also cannot produce a wifi-connection. :(

Can you also post the output of :
lsmod | grep -i ath

---

### Post by stickman51 on 2008-12-15
This is most of the specs of the machine I am using for Ubuntu:

Emachines 14.1"  Laptop (EMD620-5772) Model MS2257
OS: Vista Home Basic
Hard Drive Speed/Capacity    120GB 5400RPM
Mfr. Part Number:   LX.N230Y.041
Optical Drive    Dual Layer 8X DVD+/-RW With DVD-RAM
Processor Speed    1.6GHz
Processor Type    AMD Athlon 2650E
RAM  1024MB
Expandable Video Memory    Yes - Up To 1919MB
Graphics Chipset  ATI Radeon X1200
Integrated Video Memory  Yes
Native Screen Resolution  1280 x 800
Audio Chipset    AMD RS690MC
Audio Output  Stereo
USB 2.0   2
Ethernet Port    10/100
Integrated Bluetooth  No
Integrated WiFi  802.11 b/g/Draft-N
Processor Cache    512KB L2
System Bus  800MHz

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> This is most of the specs of the machine I am using for Ubuntu:

Emachines 14.1"  Laptop (EMD620-5772) Model MS2257

Okay, thanks.

---

### Post by albinootje on 2008-12-15
Do you have experience with Ndiswrapper ? Or are you kind of new to Linux ?

You might want to glance this through already :
[http://en.wikipedia.org/wiki/NdisWrapper](http://en.wikipedia.org/wiki/NdisWrapper)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by stickman51 on 2008-12-15
Hehehehe; I am so new to Linux, I can't even spell it  ;-) On Thursday I d/l it. No, have not heard of that Ndiswrapper; will check out those URLs.

---

### Post by albinootje on 2008-12-15
Okay :)

Since you have an Atheros based Wifi-card take a look at this too :
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by stickman51 on 2008-12-15
Well, that is "over my head" but shall I (try to) do what it suggests? If I use Alt - F2 then the "Run Application" dialog box does come up fine.

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> Well, that is "over my head" but shall I (try to) do what it suggests? If I use Alt - F2 then the "Run Application" dialog box does come up fine.

Yes, that's good, and there's no harm in blacklisting your wifi-drivers for the moment since they don't work anyway

Can you continue with step 1 and 2 ?
It's recommended to use copy&paste

---

### Post by stickman51 on 2008-12-15
Well step 1 gave me a lot of text, the last line of it was 
blacklist snd_pcsp

so below that I added the other two lines starting with "blacklist" and now I'm rebooting as indicated....


Yikes, this is getting geeky................

---

### Post by stickman51 on 2008-12-15
After the reboot, and Alt-F2 again, I entered gksudo nautilus and that brought up a window where I clicked the File System and from there to a folder called "etc" and from there to a folder called "modprobe.d and found 1 folder and 15 files; four of the files starting with "blacklist-" but not one of the "blacklist" folders had a line in it called "blacklist ath5k."

I think my head just exploded.

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> After the reboot, and Alt-F2 again, I entered gksudo nautilus and that brought up a window where I clicked the File System and from there to a folder called "etc" and from there to a folder called "modprobe.d and found 1 folder and 15 files; four of the files starting with "blacklist-" but not one of the "blacklist" folders had a line in it called "blacklist ath5k."

I think my head just exploded.

:) It is OK when that line is not there. 
Let's continue trying the next step.

---

### Post by albinootje on 2008-12-15
And if you think it's really getting scary or too geeky, why not find a local Linux Users Group where people can help you in real life.

Definition :
[http://en.wikipedia.org/wiki/Linux_User_Group](http://en.wikipedia.org/wiki/Linux_User_Group)

Here you search for one in your area :
[http://www.linux.org/groups/](http://www.linux.org/groups/)

---

### Post by stickman51 on 2008-12-15
Darn; all 3 groups in Alberta are at least 500 km from here.

---

### Post by albinootje on 2008-12-15
I just looked at this :
[http://www.firehazrd.com/ubuntu/using-windows-wireless-drivers-on-ubuntu-](http://www.firehazrd.com/ubuntu/using-windows-wireless-drivers-on-ubuntu-)
ndiswrapper-utility

which is old, but looks promising for your situation.

You can run this in a terminal ( -> Applications -> Accessories -> Terminal) :

sudo apt-get install ndisgtk

And then use the graphical Ndiswrapper installer.

The only thing you need is to locate the Windows driver for your wifi-card.

---

### Post by stickman51 on 2008-12-15
OK, I now have ndiswrapper-1.53.tar.gz  sitting on the desktop of the new laptop. And in the Terminal I now have:
kenlaninga@ubuntu:~$ sudo apt-get install ndisgtk
Hitting Enter asked for my password. Maybe I should have double-clicked the ndisw.... file first? I now got:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndisgtk
kenlan...............

Should I have double-clicked the d/l file before doing the Terminal thing?

---

### Post by stickman51 on 2008-12-15
Also, after I typed that, i shut it down, booted into Vista, found "Network Adapters" and that shows 2 items:
Atheros AR007EG Wireless Network Adapter
Generic Marvell Yukon 88E8040 PCI-E Ethernet Controller.

Then I booted back into ubuntu

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> OK, I now have ndiswrapper-1.53.tar.gz  sitting on the desktop of the new laptop. And in the Terminal I now have:
kenlaninga@ubuntu:~$ sudo apt-get install ndisgtk
Hitting Enter asked for my password. Maybe I should have double-clicked the ndisw.... file first? I now got:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndisgtk
kenlan...............

Should I have double-clicked the d/l file before doing the Terminal thing?

Hmm, that is a bit strange, because according to this :
[http://packages.ubuntu.com/search?keywords=ndisgtk](http://packages.ubuntu.com/search?keywords=ndisgtk)

the package ndisgtk is included in Ubuntu Intrepid Ibex.

Can you do the following in a terminal :

sudo apt-get update

(And let's forget about the downloaded tar.gz file for the moment).

---

### Post by stickman51 on 2008-12-15
Did that; got a loooong list of text, the bottom line is:
"W: You may want to run apt-get update to correct these problems"

??

Do you want to see the whole list?

BTW, it must be getting late for you; almost 10 PM; need to quit for the night?

---

### Post by albinootje on 2008-12-15
Can you try this ?

(From here [http://ubuntuforums.org/archive/index.php/t-766169.html](http://ubuntuforums.org/archive/index.php/t-766169.html))

this post is for people who may have the same problem as i had.

i've a Toshiba a201 with Atheros AR5007EG (named AR5006EG in gusty) now name AR242x in hardy.

anyway, to make it work:

- disable both restricted drivers in System > Adminstration > Hardware drivers

- install ndiswrapper in the add/remove window

- download the .inf from the XP driver at : [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)

- open a terminal and type this command : sudo ndisgtk

- select the net5211.inf file and "enter"

- it should now work

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> 
Do you want to see the whole list?

No, thanks. Unless you think there were errors in it.

> 
BTW, it must be getting late for you; almost 10 PM; need to quit for the night?

It's OK, let try to solve this problem soon :)

---

### Post by stickman51 on 2008-12-15
"- install ndiswrapper in the add/remove window"

means to just double-click the file, which then shows it in a window with New, Open, Extract, Add Files, Add Folder etc in it? If I Double-click it in there I get 2 folders (driver and utilities) and 8 files; then what?

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> "- install ndiswrapper in the add/remove window"

means to just double-click the file, which then shows it in a window with New, Open, Extract, Add Files, Add Folder etc in it? If I Double-click it in there I get 2 folders (driver and utilities) and 8 files; then what?

No, it means to go to -> Applications -> Add/Remove
In there type "ndis" (without the " ") in the search-field,
and press <enter>.
Mark it for installation (the small white box in front of the description).
And then press "apply changes".

---

### Post by stickman51 on 2008-12-15
Hmmmm; I tried to put the checkmark in front of:
Windows Wireless Drivers
Ndiswrapper driver installation tool

but I get a popup: The list of applications is not available
Click on "Reload" to load it. To reload the list you need a working internet connection."

And the buttons are REFRESH and Close

If I try Refesh, I get an error.

Looks like I'm screwed here.

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> Hmmmm; I tried to put the checkmark in front of:
Windows Wireless Drivers
Ndiswrapper driver installation tool

but I get a popup: The list of applications is not available
Click on "Reload" to load it. To reload the list you need a working internet connection."

Hmm, I assumed you had a working wired internet connection with your Ubuntu-install. Is that not the case ?

If so, then that makes things a little bit (even ;-) more complicated...

Let's think it over and continue next time ?

---

### Post by stickman51 on 2008-12-15
Sent emails to all 3 Linux Groups in Alberta and got replies from 2 already. One of the guys is actually in MY TOWN!! Told him I'd buy him dinner if he can fix me up.

Maybe we should leave this for tonight; getting late for you.

---

### Post by stickman51 on 2008-12-15
> **albinootje said:**
> Hmm, I assumed you had a working wired internet connection with your Ubuntu-install. Is that not the case ?

If so, then that makes things a little bit (even ;-) more complicated...

Let's think it over and continue next time ?

Yes, later is better. No, I have not used a cable from that 'puter to the modem at all; I am trying to get it going on the WLAN but probably CAN plug it in.

---

### Post by albinootje on 2008-12-15
> **stickman51 said:**
> Sent emails to all 3 Linux Groups in Alberta and got replies from 2 already. One of the guys is actually in MY TOWN!! Told him I'd buy him dinner if he can fix me up.

Wow, awesome !! :)

---

### Post by stickman51 on 2008-12-15
I plugged that 'puter into the modem and then I could click that little box and download 28 files. Next time we look at this I can show you a picture of the resulting window. LOOKS ok.

---

### Post by stickman51 on 2008-12-15
Here is what I got:

---

### Post by stickman51 on 2008-12-15
> **albinootje said:**
> Wow, awesome !! :)

And whether or not YOU are able to help me fix this, I'll buy YOU dinner for sure, next time you come to western Canada. I was back in Holland in 1982 and have no plans to go again.

---

### Post by albinootje on 2008-12-16
> **stickman51 said:**
> And whether or not YOU are able to help me fix this, I'll buy YOU dinner for sure, next time you come to western Canada. I was back in Holland in 1982 and have no plans to go again.

Thanks for the offer, i'm not much of a traveller, but i appreciate the gesture! :)

And nice that the wired internet works now.

Did you already make an appointment with the LUG guy in your town ?

---

### Post by stickman51 on 2008-12-16
Well, probably it *would* have been online long ago IF I had wanted to plug it into the modem but that is no good to me. I did notice that as soon as I plugged it in, it wanted to download and install 189 updates! And I only downloaded Ubuntu on Thursday! So, of course, I did. The local fellow said he would try by email, but he is not really into wireless stuff. A fellow in Calgary also asked me to enter some Terminal stuff and give him the resulting data which I did.
This "Terminal" seems to be about the Linux equivalent of the Windows Registry; am I correct in that assumption?

BTW Goede morgen!

kees

---

### Post by stickman51 on 2008-12-16
Lots of emails from the group this morning! SO MANY helpful people (such as yourself!) out there. I just now replied:

Gord, I downloaded the Ubuntu 8.10 on Thursday and burned the Image CD and installed it on the new laptop. It runs 100% except that it cannot, apparently find my WIFI card.

And last night I plugged it into my modem (no router anymore; the modem does it all) and it was online instantly and downloaded and installed 189 updates no problem.

SO, it appears that Ubuntu 8.10 needs a driver for my wireless card. As John Jardine pointed out, it is:

05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg 
Wireless PCI Express Adapter (rev 01)
 Subsystem: AMBIT Microsystem Corp. Device 0428
 Flags: fast devsel, IRQ 17
 Memory at f0200000 (64-bit, non-prefetchable) [disabled] [size=64K]
 Capabilities: <access denied>
 Kernel modules: ath_pci

I'd prefer *not* to get a dongle; maybe I should just wait until some genius comes along and writes the driver? I'm sure I'm not the only user who would be very happy if somebody could do that.

---

### Post by stickman51 on 2008-12-16
Albinootje, I started a new thread, basically asking for some genius out there to write the driver needed.

This is a heck of a way to run a railroad, imho. If Ubuntu is not ready to use, why release it. I'm very disappointed with Linux but sure am impressed with all the good people who tried so hard to help. Not their fault Ubuntu is faulty.

We might as well drop this thread; I've taken too much of your time as it is anyway. THANK YOU VERY MUCH though, and if you change your mind about traveling, I owe you dinner. As it happens, my cousin from here is visiting over there right now; people travel back and forth a LOT!

---

### Post by K3N8 on 2008-12-16
> **stickman51 said:**
> 05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg 
Wireless PCI Express Adapter (rev 01)
Hi,

I have the same wireless card and I use the backport kernel modules:```
apt-get install linux-backports-modules-intrepid-generic
```

After that go to the hardware section and disable the default driver and activate the 5xxx driver. reboot and you are set!

Gegroet,

Alexander

---

### Post by stickman51 on 2008-12-16
> **K3N8 said:**
> Hi,

I have the same wireless card and I use the backport kernel modules:```
apt-get install linux-backports-modules-intrepid-generic
```

After that go to the hardware section and disable the default driver and activate the 5xxx driver. reboot and you are set!

Gegroet,

Alexander

K3N8, thanks for that; looks like very similar to this answer which I am in the middle of trying now, wouldn't you say?
[http://www.webdigity.com/index.php/topic,8202.0.Ubuntu+8.10+-+Atheros+AR242x+problems.html](http://www.webdigity.com/index.php/topic,8202.0.Ubuntu+8.10+-+Atheros+AR242x+problems.html)
now I'm waiting to hear how to get to that "Settings" window.

---

### Post by albinootje on 2008-12-16
> **stickman51 said:**
> 
This is a heck of a way to run a railroad, imho. If Ubuntu is not ready to use, why release it. I'm very disappointed with Linux but sure am impressed with all the good people who tried so hard to help. Not their fault Ubuntu is faulty.

First of all :  

I'm helping you for the Love of Linux.

And the ones who are to blame are the hardware companies amongst others
(and also Microsoft, but i'll try not to start a MS-rant here).

I've started with Linux around 1995, i remember the day i read about Win-modems and Win-printers, which made me very angry. Linux has had to struggle a lot through the years. Some programmers even have produced drivers by tapping the data the device and a computer because the hardware-company refused to give more details about the device.

I'm happy that Linux is getting better and better at the desktop.
Unfortunately you still need to be careful what you buy, and yes, you might have to invest time to make some things work.

But the big difference is that you are now part of the Linux community, you can communicate with others, and your voice can be heard, and can be taken serious. (See e.g. [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)).

Quite some months ago i read that some Microsoft spokes person said that the new Internet Explorer was not gonna have tabs because customers didn't want that... (cough,cough). :)

---

### Post by albinootje on 2008-12-16
> **stickman51 said:**
> 
We might as well drop this thread; I've taken too much of your time as it is anyway. THANK YOU VERY MUCH though, and if you change your mind about traveling, I owe you dinner. As it happens, my cousin from here is visiting over there right now; people travel back and forth a LOT!

You're welcome!

And you're right, i should do some more travelling :)
Actually, the upcoming january i'm gonna be abroad for a few days, looking forward to that very much.

---

### Post by stickman51 on 2008-12-16
GOT IT!! All fixed. Will start a new thread with the detail, subject "SOLVED: Ubuntu wireless" so others might benefit.

THANKS TO ALL OF YOU!!
ken

---

### Post by albinootje on 2008-12-16
> **stickman51 said:**
> GOT IT!! All fixed. Will start a new thread with the detail, subject "SOLVED: Ubuntu wireless" so others might benefit.

THANKS TO ALL OF YOU!!
ken

Cool, congrats!! :)

---

### Post by stickman51 on 2008-12-16
> **albinootje said:**
> Cool, congrats!! :)

But I still want to buy you dinner if you come out west!

Enjoy your trip in January!

---

### Post by albinootje on 2008-12-16
:) Thank you!

---

