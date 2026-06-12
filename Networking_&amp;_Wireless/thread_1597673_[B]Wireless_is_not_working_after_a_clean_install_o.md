---
title: "[B]Wireless is not working after a clean install of Ubuntu 10.10[/B]"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by iokara08 on 2010-10-15
Good evening to everyone out there....:)

Yesterday I upgraded to Ubuntu 10.10 by a clean install. My laptop is an **acer aspire 5050** with a **IEEE 802.11 b/g** Wlan wireless card. 
I am using only Ubuntu in my laptop.

Today I noticed that wireless is dead. The indicator is off and I can see that there is not detection of any wireless networks in the "Wireless Networks" menu. 
In this point I must inform you that I didn't experience any wireless problems with the two previous versions of Ubuntu (9.10 & 10.04).

Below you can see the outputs (in italic format) of some commands that I peformed in terminal:

*1st command 
sudo ifconfig -a:

[I]eth0      Link encap:Ethernet  HWaddr 00:1b:24:6b:03:1d  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe6b:31d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6345102 (6.3 MB)  TX bytes:979493 (979.4 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:24:8a:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/I]

*2nd Command
[I]lakis@lakis-Aspire-5050:~$ sudo ifconfig wlan0 up
lakis@lakis-Aspire-5050:~$[/I] 
(It looks that wireless is on.....)

*3rd command
sudo lspci

[I]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[/I]


Please let me know if you need some more information. I hope that there will be a solution about this problem.:confused:
Thank you for your time:!:):P
:popcorn:

---

### Post by SteveDee on 2010-10-15
Run the following & post the output:-
```

iwconfig

```

...also:-
```

sudo iwlist scanning

```

---

### Post by iokara08 on 2010-10-15
SteveDee good evening.
Thank you for the fast reply,

Below you can see the output of the two commands that you asked for:

[I]lakis@lakis-Aspire-5050:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lakis@lakis-Aspire-5050:~$ sudo iwlist scanning
[sudo] password for lakis: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results[/I]

As a last step to inform you that my wireless laptop external switch is broken but this never caused any problems since my wireless it is always activated on the startup.

Thank you in advance.

---

### Post by iokara08 on 2010-10-15
I am posting again the output due to the emoticons......


[I]lakis@lakis-Aspire-5050:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          
lakis@lakis-Aspire-5050:~$ sudo iwlist scanning
[sudo] password for lakis: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results[/I]

---

### Post by SteveDee on 2010-10-15
Given your comments regarding the wifi switch on your laptop, I wonder if you now have a hardware problem. If you still have a LiveCD for an earlier version of Ubuntu, I suggest you boot from this and double check your wifi.
I don't think physical wifi switches (that are set to OFF) can be over-ridden by the software.

---

### Post by laimigrante on 2010-10-15
i having problems too with a laptop too, works on windows partition but not ubuntu, so i write on terminal the same thing u say to him and got the same output, but in the live cd i use before on this laptop and do not work, but  i will try again.

---

### Post by iokara08 on 2010-10-15
Hi again SteveDee,

Well I think I got what you mean. I have a live cd of an earlier version. So as I have understood there should not be any drivers problem but hardware...is this the conclusion that you get seeing my output results?

Just to mention that just a couple of weeks ago I had to re-format my laptop installing the same software and after completing the installation the wireless switch was "on".
Furthermore, it might be also very informative the below fact:
Once I was using my laptop including two softwares Ubuntu 10.04 & Windows Vista. In the case of booting primarily in Vista wireless was not working. The solution was Restart->Choosing ubuntu-> and then I could restart again and use Windows vista with wireless open.
So...I really don't know why now is not "fire up" my wireless:confused:

I will check your solution and I will reply here.:)
Thanks again for your interest.

---

### Post by iokara08 on 2010-10-15
Hi again SteveDee,
The solution has reached[-o<.

Following your instructions I used the live cd of 10.04. When I reached the "live desktop" wireless was working.
Straight after I tried to connected to one of the wireless networks. I succeeded and thus I restarted my laptop by removing the live CD in order to enter to Ubuntu 10.10.
Wireless was operating successfully.....
It seems that by using the live CD I made to turn on the wireless switch.
I did not have to do this process through the previous versions of Ubuntu.

Thank you a lot for your help and your time SteveDee.
Have a nice night and take care!:-D

---

### Post by SteveDee on 2010-10-16
> **iokara08 said:**
> .....It seems that by using the live CD I made to turn on the wireless switch....


This is very odd! Are you saying you have to run the LiveCD each time you boot your computer before you can restart in 10.10 with wireless? Or has this initial operation now completely fixed wireless in 10.10?

---

### Post by iokara08 on 2010-10-16
Good evening SteveDee,

Now wireless is always turned on. I don't have to re-use the Live CD anymore for turning on the wireless.=D>

In one of my previous post I just explained what was happening regarding my wireless when I had installed on my HD drive two different softwares, Vista & Ubuntu. 
I had a strange "wireless issue" using Vista while in Ubuntu wireless was fully operating. In few words when I was primarily booting in Vista, wireless was not operating. In order to make it work, in Vista, I had to boot in the Ubuntu partition and then restart again in order to boot in Vista. After the latter procedure I could make wireless work in Windows Vista.

Anyway this belongs to past....since Vista has gone):P!!! Actually I had to install Vista in one of my partitions due to some engineering software which I could not use by running Ubuntu.

Thank you once more SteveDee.
Take care.

---

### Post by johnnytm on 2010-10-16
I think what happened here is that when you inserted the live cd it actually installed your wireless driver. IEEE 802.11 b/g is not a wireless card. that is the international electronics standard code for all  wireless cards in the b and g range. The wireless card you are using is *Atheros Communications Inc. AR5001 Wireless Network Adapter *[SIZE=1][FONT=Arial]that was listed in your lspci output.[/FONT][/SIZE]

---

### Post by iokara08 on 2010-10-18
Good afternoon Johnnytm,

Thank for the information about my wireless card data.
I am wondering why my wireless drivers were not activated automatically after the clean install of the Maverick Meerkat:-k.
As I wrote through my previous posts I did not have this issue with Ubuntu 9.10 & 10.04.
Of course it is not a big trouble for me since now wireless has an adequate operation.

Have a nice day.

---

### Post by iokara08 on 2010-10-26
Good evening again,

The problem remains. For a couple of days when I was opening my laptop wireless was turned on automatically.
The last days every time that I am turning on my laptop wireless is off and if I want to turn on the wireless device I must always use the live cd of of Ubuntu 10.04.

Is there any way to turn on the wireless device from the desktop interface since my external switch is broken? I tried to use the "rfkill" tool but I did not succeed.

Is it possible to adjust Ubuntu 10.10 in order to keep always my wireless device on (like it was in the previous versions of Ubuntu)?

Thak you in advance!

---

### Post by johnnytm on 2010-10-26
Can you post the output of ```
rfkill list
``` and ```
sudo lshw -C network
```

---

### Post by DirtyPC on 2010-10-26
I'm curious, when you say the wireless switch is broken, is it literally a switch? I too have a Acer, similar to yours, and to activate my wireless i have to press FN + 3.

---

### Post by johnnytm on 2010-10-26
Thats why the rfkill output would be important. It can block both the switch and the driver from activating

---

### Post by iokara08 on 2010-10-26
Hi again,

"harrylucas1" I have an Acer Aspire 5050 series:5052AWXMi. In order to activate my wireless I have to use an external switch. It is not the same as in your case. I know what you mean but it is not the same. 
 
"johnnytm"
Below you can see the output results of the commands that you asked for: 

-----------------------------------------------------------------
[I]rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


sudo lshw -C network
[sudo] password for lakis: 
  *-network DISABLED      
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:26:24:8a:31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:b0200000-b020ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:6b:03:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:a000(size=256) memory:b0301c00-b0301cff[/I]
----------------------------------------------------------------

---

### Post by iokara08 on 2010-10-26
In order to give you a better understanding of the problem I run the live cd of Ubuntu 9.10 and then I restarted and boot again to Ubuntu Maverick Meerkat, here is my output results of the terminal commands "rfkill" and "sudo lshw -C network":

-----------------------------------------------------------------

[I]~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

~$ sudo lshw -C network
[sudo] password for lakis: 
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:26:24:8a:31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.2.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:b0200000-b020ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:6b:03:1d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:a000(size=256) memory:b0301c00-b0301cff[/I]
-----------------------------------------------------------------

Just to mention that as you can see also from the above output the wireless now is working:confused:

Have a nice night.

---

### Post by iokara08 on 2010-10-28
Hi again,

The problem of course remains....
What I have found is that when I am activating the switch (using a live CD of a previous Ubuntu version and then boot again in Ubuntu 10.10) internet as we already know is working. If I restart or shut down without unplug my laptop from the electricity again no problem occurs...but when I am unplugging my laptop and then I am booting again then wireless switch is off.

That means that when I am not unplugging my laptop (After I have switch on wireless) I can continuously using wireless.
On contrary if I unplug my laptop then in order to use wireless again I must boot firstly from Live CD in order to active the switch.......

---

### Post by iokara08 on 2010-11-15
Good afternoon,

As I have described using Maverick Meerkat my Wireless was not activated on each start up. Thus I had to do it manually, and since my external switch was broken problematic situations were appearing....
Actually the solution came using the option "save of my session" before turn off my laptop.
I have to confess that I have tried this solution before but somehow it did not work out.
Anyway now wireless is always turned on and apart of it also power settings, like brightness, are from default set to maximum.
Actually, the latter gave me the solution because it made me think again about using "save of my session" since whenever I was restarting my laptop the power settings were set to default values(brightness was in dim mode).

Have a nice day.

---

### Post by grahammechanical on 2010-11-15
May I add a comment. I am not a laptop user but it seems to me that a laptop will power down the wireless hardware in order to save battery power when the laptop is running on batteries. It does not need to do this when the laptop is plugged in the mains power supply. This is why the laptop is provided with some kind of physical switch or combination key press to re-activate the wireless hardware when re-starting the computer.

It would explain why wireless stays activated when 1) it has been switched on by the live CD and 2) it is left on powered by the mains supply. The power saving features are not needed. As the external switch is broken you will need some kind of software switch to activate the wirelesss device when running on batteries as the device is being powered off by both the laptop and the OS as a power-saving feature.

This is just my thoughts on this problem.

Regards.

---

### Post by docfred on 2010-11-15
Hi all,

Hope someone can help me.I have done a clean install of ubuntu10.10 on my acre aspire 1683 wlmi.Now as per network manager wireless is disabled and I am not able to scan for wireless networks.It works fine when wired.Please let me know how to fix this.
iwconfig - 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by docfred on 2010-11-15
Heres th out put for lshw -C Network
network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:5e:94:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.39 latency=64 multicast=yes
       resources: irq:6 memory:d0204000-d0205fff memory:24000000-24003fff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:88:62:a0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:d0208000-d0208fff
fred@cedric:~$ 

the wireless is disabled but it doest give me the option to enable it.The physical button on the comp has no effect.

---

### Post by iokara08 on 2010-11-15
Hi docfred,

Well I don't know if it is gonna be a usefull help but let me know the following:

1) Have you installed previously Ubuntu in your laptop? 
2) If yes, was your wireless operating using the previous versions?
3) Have you checked/installed any additional drivers?(System>Administration>Additional Drivers)
4) Have you installed any other software, e.g. Windows, on your hard disk (dual boot)?

---

### Post by iokara08 on 2010-11-15
Hi grahammechanical,

Thank you for your information

I got your meaning but I would like to make some more comments on it. 

Unfortunately my battery is broken...since my laptop was unlucky to be provided with.... Vista!
Of course in case of buying a battery I will have to verify your comment.
Moreover, just to state that in the 2 last versions of Ubuntu my wireless was always open automatically without need to use at all the external switch even when I was operating my laptop on battery mode (a little amount of battery which was made to survive...).
What is more, a strange issue :confused: under Maverick Meerkat, was that when I was activating wireless (using live cd) I could always use it as long as my laptop was not unplugged since the last activation. If for some reason I had to transfer my laptop, thus turn off and unplug it, then I had to use live CD again.
As I posted the solution have found using the save my current session. 

Have a nice night.

---

### Post by grahammechanical on 2010-11-15
Hi iokara08

I was thinking. A lot of laptop uses have problems with wireless and hibernation/suspend. Your solution of "save current session" might also be a solution for them as well as for you.

regards.

---

