---
title: "difficulty with wireless card Dell / Cisco / Aironet"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by pellicle on 2010-12-22
Hi

this has been a long and frustrating experience for me and it would be much appreciated if anyone can offer advice to solve this problem.

I had ubuntu 8 running on an IBM Thinkpad x20 and using ndiswapper on a netgear card for that. This has been fine as my 'guest' laptop at home for some time.

I then wanted to give this laptop to a friend but found (after a long trial) that the WiFi access to the internet where he lives uses **WPA2 TKIP protocol **and I believe that the Netgear does not support this.

So some research suggested that (among the candidates) a **Aironet PCCC4805LT PCMCIA card **would be a suitable card. ***This is badged Dell 4800LT***.

[COLOR=Red]**Before we go any further**[/COLOR] on this, does anyone know if this card will support  **WPA2 TKIP protocol **in Ubuntu 10.10?? If it does not then I will stop struggling and beg information on what card / usb device I can get which ***will*** work


Moving on ...

I tried all weekend reading posts such as [**this**]("http://ubuntuforums.org/showpost.php?p=6077792&postcount=72") one on how to possibly integrate the card.

In frustration I decided to pop in a spare 40Gig drive and install a fresh version of **Ubuntu 10.10 (netbook edition) **on the machine. It seems to run quite acceptably on the Thinkpad, **but again there is no wireless connection** available.

**The interesting thing is however that the card is in some ways recognized by the system**.

For example when I have no card placed in the slot and I enter ifconfig I see eth0 and lo. I believe that eth0 is the internal wired lan card.

When I insert the Aironet card I see: an additional interface of eth1

Additionally in the GUI System > Administration > Network Tools under Devices I see:
Loopback Interface (lo)
Ethernet Interface (eth0)
Ethernet Interface (eth1)
Unknown Interface (wifi0)

**both eth1 and wifi0 indicate information and statistics in the interface, and eth1 is State: Active while wifi0 is State: Inactive**.

This leads me to believe that I am somehow on the cusp of getting this going but some small thing stands between me and operation.

Ubuntu 10 looks very sweet and I'm eager to give my (poor and elderly) friend a Christmas present which allows him to be on the net at last

---

### Post by chili555 on 2010-12-22
Elderly? Well, I am a great-grandfather, so maybe I'm the best candidate to help you!

Some of these old PCMCIA cards don't support WPA because either the firmware just can't be bent to do so, or they're so old that the manufacturer is out of business or hasn't or won't update the firmware because they'de rather sell you a new card! Viz:> If it does not then I will stop struggling and beg information on what card / usb device I can get which will workSee, you are already in line with Cisco's marketing plan.

First, wifi0 is a dummy interface used by the system. We may safely ignore it, except to the extent that it indicates that wireless comes to life when you insert the card.

A great many things are faster, easier and quite a bit more informative in Ubuntu when done with the command line. Don't worry, we are not going to subject your recipient to the agony and ecstasy of the terminal; we are simply going to use it to query the system for diagnostics. My wife uses her Ubuntu computer every day and doesn't even know where the terminal is!

Please open Applications > Accessories > Terminal and do:```
sudo iwlist eth1 auth
```If your card does WPA, the output should read like:> $ sudo iwlist eth1 auth
[sudo] password for chili: 
eth1     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMPYou might or might not also get some clues with:```
dmesg | grep WPA
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Please post back if Grampy can help you further. I will be answering on one of my two Thinkpads!

---

### Post by pellicle on 2010-12-22
Dear Chilli555 (or do you prefer Grampy?)

> **chili555 said:**
> Elderly? Well, I am a great-grandfather, so maybe I'm the best candidate to help you!

could be ....

firstly thanks for all your kind and gently written assistance. To help you couch your replies I'm actually an old programmer, but for one reason or another while I started on assembly went through C to other languages my experience on Unix (solaris) was with the UNIX SYS ADMIN priesthood having charge of all the dirty stuff (with root and even sudo tightly controlled), thus much of the admin stuff is new to me.

While everything you wrote below worked and got results I'm actually testing the machine here at home and as a first step am attempting to attach to a test wireless lan which has no security.

My Ubuntu 8 with my ndiswrapped Netgear card can connect to that, but I have not tried with the ndis system since going to 10 ... I wanted to just get the Cisco going.

**I have tried multiple methods to get the card to see the SSID here but it just wont play ball - despite appearing tantalizingly close to doing so**

So, if there was additional information to what I wrote in the first post regarding getting this card going could you please hit me with those questions and I will reply as soon as I can with the results.

Interestingly iwlist scan returns:

lo    interface doesn't support scanning.
eth0  interface doesn't support scanning.
pan0  interface doesn't support scanning.
eth1  no scan results.
wifi0 no scan results.

as well the little icon for wireless just has a red ! in it and will not see anything around (including the unsecure ones)

thanks again

:-)
> 
Some of these old PCMCIA cards don't support WPA because either the firmware just can't be bent to do so, or they're so old that the manufacturer is out of business or hasn't or won't update the firmware because they'de rather sell you a new card! Viz:See, you are already in line with Cisco's marketing plan.

First, wifi0 is a dummy interface used by the system. We may safely ignore it, except to the extent that it indicates that wireless comes to life when you insert the card.

A great many things are faster, easier and quite a bit more informative in Ubuntu when done with the command line. Don't worry, we are not going to subject your recipient to the agony and ecstasy of the terminal; we are simply going to use it to query the system for diagnostics. My wife uses her Ubuntu computer every day and doesn't even know where the terminal is!

Please open Applications > Accessories > Terminal and do:```
sudo iwlist eth1 auth
```If your card does WPA, the output should read like:You might or might not also get some clues with:```
dmesg | grep WPA
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Please post back if Grampy can help you further. I will be answering on one of my two Thinkpads!

Hi

just a quick addition: when doing sudo lshw -C network I get information on the Wireless, but far fewer lines than the Ethernet.

I see
description: Wireless Interface
physical id: 1
logical name: eth1
serial: blah blah
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

---

### Post by chili555 on 2010-12-22
> Interestingly iwlist scan returns:

lo interface doesn't support scanning.
eth0 interface doesn't support scanning.
pan0 interface doesn't support scanning.
eth1 no scan results.
wifi0 no scan results.From *man iwlist*:> Triggering scanning is a privileged operation (root only) and normal users can only read left-over scan results. So what does this tell us? Errors, warnings and seemingly random things tell us clues:```
[COLOR="Red"]sudo[/COLOR] iwlist eth1 scan
```> description: Wireless Interface
physical id: 1
logical name: eth1
serial: blah blah
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS No driver or other description of the card in question? Ndiswrapper or what??

---

### Post by pellicle on 2010-12-22
Hi

> **chili555 said:**
> From *man iwlist*:So what does this tell us? Errors, warnings and seemingly random things tell us clues:```
[COLOR=Red]sudo[/COLOR] iwlist eth1 scan
```No driver or other description of the card in question? Ndiswrapper or what??

because the other machine is not running on the net, I am typing into this box what I see ... occasionally I abbreviate what I see my apology

indeed I am using sudo

> No driver or other description of the card in question? Ndiswrapper or  what??

correct, on this occasion I typed in all that was there ...  no ndiswrapper no this, I did as I said a clean install of 10.10 and tried to use the card

---

### Post by chili555 on 2010-12-23
> I did as I said a clean install of 10.10 and tried to use the cardThe Netgear or the Cisco? May I suggest, since we are trying to get the Cisco going, that we concentrate our efforts on it?

Please insert it and run and post:```
lspcmcia
```Let's figure out what driver it needs and if it exists on the system. You might also get some clues by running:```
sudo tail -f /var/log/messages
```Leave the terminal open as you insert the card and watch what new messages appear.

You can close the running *messages* terminal with Ctrl+c.

---

### Post by pellicle on 2010-12-23
> **chili555 said:**
> The Netgear or the Cisco?

the cisco ... its the only one I'm trying to work on
>  May I suggest, since we are trying to get the Cisco going, that we  concentrate our efforts on it?

certainly, sorry if I managed to confuse things with comparisons


> Please insert it and run and post:```
lspcmcia
```Let's figure out what driver it needs and if it exists on the system. 


Socket 0 Bridge: [yenta_cardbus] (bus ID: 000:00:08.0)
Socket 0 Bridge: [airo_cs] (bus ID: 0.0)
Socket 1 Bridge: [yenta_cardbus] (bus ID: 000:00:08.1)

You might also get some clues by running:```
sudo tail -f /var/log/messages
```Leave the terminal open as you insert the card and watch what new messages appear.

I'll leave out the dates n stuff but:
```
pcmcia_socket pcmcia_socket0: pccard: PCMCIA card insertied into slot 0
pcmcia 0.0 pcmcia: registering new device pcmcia0.0 (IRQ: 3)
airo(eth1): Firmware version 3.356.00
airo(eth1): WPA unsupported with firmware versions older than 5.3.0.17
airo(eth1): MAC enabled 00:40:xxxxxx <- my xxx here
airo_cs 0.0: index 0x05:, Vpp 5.0 irq3, io 0x011-0x013f

```

which answers one of the questions I was asking (the one about WEP)

however I'm not sure why it won't connect to my router here?

I managed to get it to try by going to System -> Administration -> Network Tools then choosing eth1 clicking Configure and then fiddling with the Network Connections under wireless tab

here I get the small icon to attempt searching but not connecting

I have data in the fields of:
Wireless Tab
SSID: myRouter
Mode: infrasstructure

and connect Automatically is checked

---

### Post by chili555 on 2010-12-23
> which answers one of the questions I was asking (the one about WEP)Which? Is the grind on these old trifocals a little off? I saw your question about WPA2. Is your router set to WPA2 or WEP? Unless you can manage to find and flash firmware at version 5.3.0.17
or newer, then WEP is where you are stuck.

---

### Post by pellicle on 2010-12-23
> **chili555 said:**
> Which? Is the grind on these old trifocals a little off? I saw your question about WPA2. Is your router set to WPA2 or WEP? Unless you can manage to find and flash firmware at version 5.3.0.17
or newer, then WEP is where you are stuck.

it answers the question about "will this card connect to WPA" but not the other question of why it will not connect to my vanilla router with no security at all

Merry Christmas :-)

---

### Post by chili555 on 2010-12-24
I suggest you set the router to no security, detach the ethernet cable, if any and click the Network Manager icon and see if you see your network. Click it and try to connect. Note the behavior: does it try to connect in any way? Does the little icon spin? What does this tell us?```
sudo cat /var/log/syslog | grep -i network
```There will likely be several hundred lines of output; look for the 8-10 lines that illustrate an attempt to connect and its failure and post then here.

---

### Post by pellicle on 2010-12-26
Hi chilli555


> **chili555 said:**
> I suggest you set the router to no security, detach the ethernet cable, if any and click the Network Manager icon and see if you see your network. 


I have been attempting this from the start, even my post before last said exactly that.


> 
Click it and try to connect. Note the behavior: does it try to connect in any way?
[QUOTE]

again, already described ...

Does the little icon spin?[/QUOTE]it has not got that sort of icon, it has what appears to be a "ripple of waves" expanding out in a fan ... 


>  What does this tell us?```
sudo cat /var/log/syslog | grep -i network
```There will likely be several hundred lines of output; look for the 8-10 lines that illustrate an attempt to connect and its failure and post then here.

Ok ... inserting and pulling the card I get this:

> Dec 26 19:15:37 block kernel: [  903.556204] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
Dec 26 19:15:37 block kernel: [  903.556472] pcmcia 0.0: pcmcia: registering new device pcmcia0.0 (IRQ: 3)
Dec 26 19:15:38 block kernel: [  904.883839] airo(): cmd:111 status:7f11 rsp0:2 rsp1:0 rsp2:0
Dec 26 19:15:38 block kernel: [  904.883865] airo(): Doing fast bap_reads
Dec 26 19:15:38 block kernel: [  904.884044] airo(): cmd:21 status:7f21 rsp0:4 rsp1:0 rsp2:0
Dec 26 19:15:38 block kernel: [  904.932493] airo(eth1): Firmware version 3.56.00
Dec 26 19:15:38 block kernel: [  904.932511] airo(eth1): WPA unsupported with firmware versions older than 5.30.17.
Dec 26 19:15:38 block kernel: [  904.932527] airo(eth1): MAC enabled 00:40:96:31:1b:ae
Dec 26 19:15:38 block kernel: [  904.944123] airo_cs 0.0: index 0x05: , Vpp 5.0, irq 3, io 0x0100-0x013f
Dec 26 19:15:38 block NetworkManager[670]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:08.0/0.0/net/eth1, iface: eth1)
Dec 26 19:15:38 block NetworkManager[670]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:08.0/0.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 26 19:15:38 block NetworkManager[670]: <error> [1293354938.760075] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 95)
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): driver does not support SSID scans (scan_capa 0x00).
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): new 802.11 WiFi device (driver: 'airo_cs' ifindex: 15)
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/7
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): now managed
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): bringing up device.
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): preparing device.
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): deactivating device (reason: 2).
Dec 26 19:15:38 block NetworkManager[670]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:08.0/0.0/net/wifi0, iface: wifi0)
Dec 26 19:15:38 block NetworkManager[670]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:08.0/0.0/net/wifi0, iface: wifi0): no ifupdown configuration found.
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): supplicant interface state:  starting -> ready
Dec 26 19:15:38 block NetworkManager[670]: <info> (eth1): device state change: 2 -> 3 (reason 42)
Dec 26 19:15:38 block kernel: [  905.193117] airo(eth1): cmd:103 status:7f03 rsp0:2 rsp1:148 rsp2:0
Dec 26 19:15:40 block avahi-daemon[669]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::240:96ff:fe31:1bae.
Dec 26 19:15:40 block avahi-daemon[669]: New relevant interface eth1.IPv6 for mDNS.
Dec 26 19:15:40 block avahi-daemon[669]: Registering new address record for fe80::240:96ff:fe31:1bae on eth1.*.
Dec 26 19:15:41 block kernel: [  908.192342] airo(eth1): cmd:21 status:7f21 rsp0:4 rsp1:170 rsp2:0
Dec 26 19:15:47 block avahi-daemon[669]: Interface eth1.IPv6 no longer relevant for mDNS.
Dec 26 19:15:47 block kernel: [  914.204256] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
Dec 26 19:15:47 block kernel: [  914.204410] airo(eth1): cmd:2 status:ffff rsp0:ffff rsp1:ffff rsp2:ffff
Dec 26 19:15:47 block kernel: [  914.204633] airo(eth1): cmd:21 status:ffff rsp0:ffff rsp1:ffff rsp2:ffff
Dec 26 19:15:47 block kernel: [  914.205375] airo(eth1): cmd:21 status:ffff rsp0:ffff rsp1:ffff rsp2:ffff
Dec 26 19:15:47 block avahi-daemon[669]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::240:96ff:fe31:1bae.
Dec 26 19:15:47 block avahi-daemon[669]: Withdrawing address record for fe80::240:96ff:fe31:1bae on eth1.
Dec 26 19:15:47 block avahi-daemon[669]: Withdrawing workstation service for eth1.
Dec 26 19:15:47 block NetworkManager[670]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:08.0/0.0/net/eth1, iface: eth1)
Dec 26 19:15:47 block NetworkManager[670]: <info> (eth1): now unmanaged
Dec 26 19:15:47 block NetworkManager[670]: <info> (eth1): device state change: 3 -> 1 (reason 36)
Dec 26 19:15:47 block NetworkManager[670]: <info> (eth1): cleaning up...
Dec 26 19:15:48 block avahi-daemon[669]: Withdrawing workstation service for wifi0.
Dec 26 19:15:48 block kernel: [  914.229075] airo(eth1): cmd:21 status:ffff rsp0:ffff rsp1:ffff rsp2:ffff
Dec 26 19:15:48 block NetworkManager[670]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 26 19:15:48 block NetworkManager[670]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 26 19:15:48 block NetworkManager[670]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:08.0/0.0/net/wifi0, iface: wifi0)
Dec 26 19:15:48 block wpa_supplicant[698]: Failed to disable WPA in the driver.
^C


within moments it says "not connected to the network" in a small "popup" from the network system

thanks for your assistance

thanks for your help

consider this case closed as I have purchased another NIC, a USB one which happily works

It was a D-Link DWA-125 ... plugged it in and it worked fine

:-)

---

### Post by rgonnering on 2011-01-07
I have 2 IBM T22 computers with Cisco 350 pcmcia cards. They both worked fine on 8.10 and 9.04. When I upgrade to 9.10, 10.04, or 10.10, there is no connection to the wireless network.

Are there any suggestions, to get this to work? Did something change between 9.04 and 9.10?

Someone abandoned the Cisco 350 pcmcia card. What device did you use? What version of Ubuntu did you use?

Thanks

---

### Post by chili555 on 2011-01-08
> I have 2 IBM T22 computers with Cisco 350 pcmcia cards. They both worked fine on 8.10 and 9.04. When I upgrade to 9.10, 10.04, or 10.10, there is no connection to the wireless network.

Are there any suggestions, to get this to work?If it is the card I believe it is, it is supposed to work with the driver module *airo*. Please insert the card, open Applications > Accessories > Terminal and do:```
sudo modprobe airo
iwconfig
lspcmcia ident
```Post the result and we'll proceed.

---

