---
title: "need to understand another old post?"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by gordon33 on 2010-08-22
My HP laptop is not seeing or connecting to any wire less routers.  I came across what sounds like a simple fix at the following post.  I quoited the part I do  not understand.  What did he do and how did he do it.  

Network connection?   Does he mean the icon at on the top panel?
Adding a notification area to the task bar.”?  How would you do that and how would it help?


[http://ubuntuforums.org/showthread.php?t=1552609&highlight=troubleshoot](http://ubuntuforums.org/showthread.php?t=1552609&highlight=troubleshoot)

“The problem was that I had disabled the network connections and lost the network manager icon to enable it.
The odd thing was that I was able to get the network manager back by adding a notification area to the task bar.”

thanks

gordon33

---

### Post by bkratz on 2010-08-22
> **gordon33 said:**
> My HP laptop is not seeing or connecting to any wire less routers.  I came across what sounds like a simple fix at the following post.  I quoited the part I do  not understand.  What did he do and how did he do it.  

Network connection?   Does he mean the icon at on the top panel?
Adding a notification area to the task bar.”?  How would you do that and how would it help?


[http://ubuntuforums.org/showthread.php?t=1552609&highlight=troubleshoot](http://ubuntuforums.org/showthread.php?t=1552609&highlight=troubleshoot)

“The problem was that I had disabled the network connections and lost the network manager icon to enable it.
The odd thing was that I was able to get the network manager back by adding a notification area to the task bar.”

thanks

gordon33

Where he/she was referring to (bad English) is the icon on the top panel. Left clicking on it should show available networks and right clicking on it is how to enable disable both the wired and wireless connections.  The op in the post had deleted that icon and had to right click on the top panel>>select "add to panel" and select notification area to be added. If yours is there don't worry about it.

---

### Post by gordon33 on 2010-08-22
Hello bkratz

Thank you for the reply.  I was hoping their was a little more to that post.

My computer has the wifi icon and it is marked as enabled. But, none of the wire less routers are showing when I left click on the wifi icon.  can not wake up the Wireless Networks en I left click on the wifi icon.

---

### Post by HeadHunter00 on 2010-08-22
First of all make sure that your wireless card is turned on. And then type this command```
sudo ifconfig wlan0 up
```

---

### Post by gordon33 on 2010-08-22
Hello HeadHunter00

Thank you for the reply.

How can I check to see if my wireless card is turned on?  I have a HPG60t laptop.  As far as I know their are no external switches for wifi.

Would the code "sudo ifconfig wlan0 up" turn my wifi card on?

Gordon33

---

### Post by bkratz on 2010-08-22
> **gordon33 said:**
> Hello HeadHunter00

Thank you for the reply.

How can I check to see if my wireless card is turned on?  I have a HPG60t laptop.  As far as I know their are no external switches for wifi.

Would the code "sudo ifconfig wlan0 up" turn my wifi card on?

Gordon33

we really need to know what the wireless card is. If you go to the terminal (Applications>>Accessories>>Terminal) and copy/paste the outputs from the following:  Use "code" tags (#) to make the output pretty (and shorter) for the following:

```
lspci -nn
lshw -C Network
sudo iwlist scan
```


Commands that start with "sudo" will require your password which will not be echoed back to you during typing, just enter the password and press "enter"

also add

rfkill list

to that list above

---

### Post by gordon33 on 2010-08-22
Hello bkratz

I am not sure how to use "code" tags (#) to make the output pretty (and shorter) for the following:

I did get the full out put for the codes you listed.  

gordon@gordon-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
gordon@gordon-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:76:dc:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.6 latency=0 multicast=yes
       resources: irq:26 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:af:c5:33
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d2600000-d260ffff
gordon@gordon-laptop:~$ sudo iwlist scan
[sudo] password for gordon: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

gordon@gordon-laptop:~$

---

### Post by bkratz on 2010-08-22
Well the good news is that your wireless card is the
AR5001 Wireless Network Adapter [168c:001c] (rev 01)
and seems to have the ath5k driver. The bad news is that is not one of the ones I know alot about, I will googlubuntu for it and see what I can find.
Also did you get an output for
rfkill list 
that I edited in later. You may not have sometimes nothing is returned.
Back later, hopefully an AR5001 expert will jump in

---

### Post by gordon33 on 2010-08-22
Hello bkratz

That is a code I saw a while back and could not remember.  I am thinking "Hard blocked Yes" is a bad thing?


gordon@gordon-laptop:~$ rfkill list 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

Thank you 

gordon33

---

### Post by bkratz on 2010-08-22
Ran into this thread about code tags

[http://ubuntuforums.org/showthread.php?t=855096](http://ubuntuforums.org/showthread.php?t=855096)

for info only, still  looking

---

### Post by bkratz on 2010-08-22
> **gordon33 said:**
> Hello bkratz

That is a code I saw a while back and could not remember.  I am thinking "Hard blocked Yes" is a bad thing?


gordon@gordon-laptop:~$ rfkill list 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

Thank you 

gordon33

Unless your laptop is having a problem talking to Ubuntu about the switch or you simply have to find it and turn it on. Hard blocked is the wireless switch.

---

### Post by bkratz on 2010-08-22
By the way, what is the model number of your laptop, maybe we can find something on the web.

---

### Post by gordon33 on 2010-08-22
Hello bkratz

I have a HPG60t-200 laptop. 

Gordon33

---

### Post by bkratz on 2010-08-22
> **gordon33 said:**
> Hello bkratz

I have a HPG60t-200 laptop. 

Gordon33

I downloaded the manual from this location
[http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&lang=en&product=3837660&#](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&lang=en&product=3837660&#)

and it talks about a wireless "button" is there one someplace?  It gives no other details or pictures that I see.  If there is one what color is it displaying, is it blue?

---

### Post by gordon33 on 2010-08-22
Hello bkratz

Their is a blue (some times orange) wireless icon light/button at the top center of the key board.  It is orange during boot up and turns blue once the computer is running.  Pushing it or holding it in seems to make no difference.


gordon33

---

### Post by bkratz on 2010-08-22
> **gordon33 said:**
> Hello bkratz

Their is a blue (some times orange) wireless icon light/button at the top center of the key board.  It is orange during boot up and turns blue once the computer is running.  Pushing it or holding it in seems to make no difference.


gordon33

Blue supposedly indicates some wireless device is on--it doesn't specify what others there are.  Anyway, we can try

```
sudo rfkill unblock all
rfkill list

```

and see if the hardblock disappears. It may not help, but it can't hurt either!

---

### Post by HeadHunter00 on 2010-08-22
> **gordon33 said:**
> Hello HeadHunter00

Thank you for the reply.

How can I check to see if my wireless card is turned on?  I have a HPG60t laptop.  As far as I know their are no external switches for wifi.

Would the code "sudo ifconfig wlan0 up" turn my wifi card on?

Gordon33
You see the power button. There should be a button right beside it that looks like a radio tower. Make sure that it's blue or white, not orange. If it's orange, then press it. After that use my command.

---

### Post by HeadHunter00 on 2010-08-22
> **gordon33 said:**
> Hello bkratz

That is a code I saw a while back and could not remember.  I am thinking "Hard blocked Yes" is a bad thing?


gordon@gordon-laptop:~$ rfkill list 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Thank you 

gordon33
BTW, hardblocked isn't a bad thing. That just means you have to turn your wireless signal on by pressing the wifi button.

---

### Post by bkratz on 2010-08-22
> **HeadHunter00 said:**
> BTW, hardblocked isn't a bad thing. That just means you have to turn your wireless signal on by pressing the wifi button.

Yes, see post 11-- I have seen several cases recently where Ubuntu can't seem to "read" the switch though.  Especially with Dells!

---

### Post by gordon33 on 2010-08-22
Hello HeadHunter00 and,  bkratz

SOLVED

The downloaded manual talked about "wlan" being important.  So I went to System/ administration/ Synaptic Package Manager and clicked on the linux-wlan-ng-doc and linux-wlan-ng came up as a needed pair.  Rebooted and the wifi worked.

Thank you HeadHunter00 and, exspecially bkratz

It's great to have wifi again.

gordon33

---

### Post by bkratz on 2010-08-22
> **gordon33 said:**
> Hello HeadHunter00 and,  bkratz

SOLVED

The downloaded manual talked about "wlan" being important.  So I went to System/ administration/ Synaptic Package Manager and clicked on the linux-wlan-ng-doc and linux-wlan-ng came up as a needed pair.  Rebooted and the wifi worked.

Thank you HeadHunter00 and, exspecially bkratz

It's great to have wifi again.

gordon33

Sure am glad to hear that!  I was running out of ideas.  I am going there and seeing exactly what you are referring to now.

---

