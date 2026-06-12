---
title: "WAN Miniport (PPPOE)"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by damjan992 on 2011-11-09
Hi!

I had problem connecting to the internet on Ubuntu 9 and 10 and never  solved it. Now, I want to install Ubuntu 11.10 desktop i386 but as a  single OS.
I'm connecting trough **WAN Miniport (PPPOE)**. My wireless antenna is directly connected to a TP Lnk **WN-551g** 11b/g wireless adapter.
On Windows XP and 7 i have no problems. I only have to install drivers  and then type in my user name and password. In Linux I've tried a few  thing, including command sudo pppoeconf but it just wont work. ](*,)
Is this solved in Ubuntu 11 and if not, is there a way to connect to the internet using this type of connection?

---

### Post by dineshs on 2011-11-11
> In Linux I've tried a few thing, including command sudo pppoeconf but it just wont work.
Have you tried ```
sudo pppoeconf wlan0
```(Assuming that your wireless device is detected as wlan0)
Can you post the result of ```
sudo lshw -C network
```

---

### Post by damjan992 on 2011-11-11
Yes, I tried that too but something couldn't be found. I can't remember exactly. I even tried configuring wlan0 or something like that but even that it wouldn't work. I'll install Ubuntu, probably tonight, and try those codes.

Thanks!

---

### Post by damjan992 on 2011-11-11
I was running live OS but I hope that there is no difference.

I tried typing both

```
sudo pppoeconf
```and

```
sudo pppoecinf wlan0
```

On Ubuntu 9 and 10 there was the same error. Error that occurs when I type first code (see pics). It looks like that on 11 I can connect by typing second code but i didn't wanted to mess something up.

And here's what I get when I type

```
sudo lshw -C network
```

      =

```
  *-network               
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wlan0
       version: 01
       serial: 00:14:78:ee:0b:88
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-12-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dfef0000-dfefffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: 8c:89:a5:2c:dd:ff
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:defff000-deffffff memory:deff8000-deffbfff
```

---

### Post by dineshs on 2011-11-14
> It looks like that on 11 I can connect by typing second code but i didn't wanted to mess something up.
Please backup /etc/ppp/peers/dsl-provider using ```
sudo cp /etc/ppp/peers/dsl-provider /etc/ppp/peers/dsl
```
Proceed with ```
sudo pppoeconf wlan0
```
Then connect using```
sudo pon dsl-provider
```and disconnect using ```
sudo poff dsl-provider
```
> On Ubuntu 9 and 10 there was the same error
Does [COLOR="Blue"]sudo lshw -C network[/COLOR] look same in 9 and 10?

---

### Post by damjan992 on 2011-11-19
Sorry, but I gave up installing Ubuntu... for the third time. 

I actually couldn't manage to boot up Ubuntu. Screen starts to blink, flicker (don't know how to exactly express myself) so I've reinstalled it. Then, after booting that fresh installation I've left it that way for a couple of minutes and restarted computer. After trying to boot up again first my speakers started to bleep, sizzle (again, I hope I expressed myself correctly) and sound was on maximum, even if Hi-Fi wasn't. It lasted 2-3 seconds, and screen started to blink again. Tried booting couple times more but it blinks again and again and it wouldn't stop even after 5-10 minutes.

Good for hypnosis, though =P~

Anyway, I'll just wait for Ubuntu 12 :D



> Does [COLOR=Blue]sudo lshw -C network[/COLOR] look same in 9 and 10?

I don't have them on CD and neither do I have images on computer but I can download them again and see how it looks on them

---

### Post by damjan992 on 2011-11-21
Okay, I've installed Ubuntu again. It looks like it works without problems... for now :) I remembered that there was some boot problems with Ubuntu 9 but after installing updates it boots okay so I hope I won't be having any problems with that screen if I update Ubuntu

Anyway, I tried configuring internet connection how you told me to but with **no** success... ](*,)

So, here are some screenshots. Also, I didn't mentioned that I first connect to an wireless network and then start some kind of connection where username and password is (i think it's called dialer but you will see on screenshots). I asume that it's how PPPoE connection is but nevertheless it's good to tell.

Picture 1: First. I wait for that first picture. It has to connect to that network.

Picture 2: Then, I open Connect KingsNet (first window). After clicking connect i get that second window. Just follow those lines and you won't get lost ;-)

---

### Post by dineshs on 2011-12-03
Please connect from windows and post the result of ```
ipconfig /all
```
Also post the output of the following terminal commands from [COLOR="Red"]ubuntu[/COLOR]```
ifconfig -a
```and```
iwconfig
```
Did you try to configure the connection via *sudo pppoeconf wlan0*? Was there any error?

---

### Post by damjan992 on 2011-12-08
```
D:\Documents and Settings\Daljevic>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : hall-7k
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : TP-LINK 11b/g Wireless Adapter
        Physical Address. . . . . . . . . : 00-14-78-EE-0B-88
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.187.127
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter KingsNet:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : Err... No... You can't see this :)
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 10.184.26.242
        DNS Servers . . . . . . . . . . . : 172.22.0.10
                                            172.23.0.10
        NetBIOS over Tcpip. . . . . . . . : Disabled
```Ubuntu keep crashing so I couldn't give you those two last codes. If it's really important I'll reinstall it... again... but only if it's important! :D

> Did you try to configure the connection via *sudo pppoeconf wlan0*? Was there any error?Yes, I tried and I was unable to connect. There wasn't any error (although it asks many questions so I might did something wrong ???) I actually did tried about 4-5 times configuring in a different way but I couldn't connect.
I think that this isn't the problem. Problem is that I must be connected to a wireless network. Now, when I do that on Windows it says that I have limited or no connection but I stays that way. It's connected one way or the other. On Ubuntu, when I try to connect after a few second it disconnects and starting this connection that I made using sudo pppoeconf wlan0 is pointless because I'm not connected to that wireless network.

I hope I explained it right, cause English is not my native language. Luckily, we learn it school :)

---

### Post by dineshs on 2011-12-10
> There wasn't any error (although it asks many questions so I might did something wrong ???) I actually did tried about 4-5 times configuring in a different way but I couldn't connect.Please run ```
sudo pon dsl-provider
``` and then ```
ping 4.2.2.1 -c3
```(Pl post results)

---

### Post by damjan992 on 2011-12-10
Wow! I can connect to the internet for a few seconds :grin:
I never actually tried this but when a man is desperate he will try anything, no mater how stupid it may be :D
After configuring internet connection (I answered Yes to every question) and copying the results of codes you gave me, I tried to connect to a wireless network, and, while Ubuntu tried to connect to it, I opened Firefox and home page loaded. Then, I just randomly typed some letters in that search box and after hitting enter I actually got search results :D Of course, it disconnects after a few seconds :( Therefore, all I need, in order to use this type of internet connection with Ubuntu, is to have **constant** connection with that wireless network, no matter how that connection is - full or limited.

And about those results. I have a total of 6 results to post. Reason for this is that they are different depending on whether I'm offline or online. Since that connection to a wireless network is problem, and not configuration itself, and since those result's are [SIZE=2]**BIG**[/SIZE]... really [SIZE=4]**BIG**[/SIZE], I didn't posted them, but they are on my HDD, so if you do need them just say it :D

And yes, when Ubuntu is trying to connect to a wireless network, I can successfully ping 4.2.2.1. Btw, what is 4.2.2.1? Is it something like 127.0.0.1 or... ?

---

### Post by dineshs on 2011-12-12
> And yes, when Ubuntu is trying to connect to a wireless network, I can successfully ping 4.2.2.1. Btw, what is 4.2.2.1? Is it something like 127.0.0.1 or... ?4.2.2.1 is an open [DNS]("http://en.wikipedia.org/wiki/Domain_Name_System") server.You will get reply only if you are connected.
Please run ```
sudo gedit /etc/network/interfaces
```
Edit the file so that it reads only the following lines(you may backup the file before editing)
```
auto lo
iface lo inet loopback

```
Reboot and run ```
sudo pon dsl-provider
```to connect.
Any improvement?

---

### Post by damjan992 on 2011-12-12
It's still the same... :(

---

### Post by dineshs on 2011-12-13
I think the problem is with your wireless card.From your post#4 you have an Atheros AR2413 card.You may search for solved posts regarding this device. [Here]("http://ubuntuforums.org/showpost.php?p=10882161&postcount=109") is a similar case in Natty (Ubuntu 11.04).This may work for 11.10 too but I am not sure.Please also see postcount#8  [ here ]("http://ubuntuforums.org/showthread.php?t=1686282") .I think [chili555]("http://ubuntuforums.org/member.php?u=35909") can help you better.

---

### Post by damjan992 on 2011-12-13
But why is Ubuntu seeing my wireless card as Atheros AR2413 when it's TP-Link 551G? On wireless card itself is written TL-WN551G. I've searched for pictures of those two wireless cards and they are different... Or aren't they?

---

### Post by chili555 on 2011-12-13
Your TP Link identifies itself as an Atheros because that's the OEM manufacturer of the actual chipset. I also doubt the wireless card is at fault. It has grabbed a driver and created a wireless interface.:> *-network               
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: [COLOR="Red"]wlan0[/COLOR]
       version: 01
       serial: 00:14:78:ee:0b:88
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=ath5k [/COLOR]driverversion=3.0.0-12-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dfef0000-dfefffffDoes it scan?```
sudo iwlist wlan0 scan
```If it sees networks, specifically yours, the driver side of things is fine.

Are you connecting to a wireless router? If so, it's a whole lot easier to set up your details there. Please see attached.

If you are unable to do so, I'd suggest you use Network Manager to manage these details, instead of manual methods in the terminal which are often ineffective if NM is running. Please see attached.

---

### Post by damjan992 on 2011-12-15
> If it sees networks, specifically yours, the driver side of things is fine.

Yes. It sees more networks than in Windows so drivers are good :D

> Are you connecting to a wireless router?

Nope.


I don't quite understand what should I do with that Network Manager. Those configurations with ```
sudo pppoeconf wlan0
``` are working just fine. The main problem is that when I connect to a network (in Windows) it says that a connection is limited. I assume that Ubuntu sees that a connection to that network is limited and disconnects. I've called my ISP and they say that it's completely fine for a connection to be like that. It's actually supposed to be like that. So, we have to force Ubuntu to stay connected to a limited network...
Another problem is that I can use internet connection on Ubuntu for a very limited time. When I start connection with > sudo pon dsl-provider I then connect to a network, and while Ubuntu is trying to connect to it, I have connection to the internet bus as soon as Ubuntu disconnects that network (... probably because it's limited ???), I'm no longer connected to the internet. Therefore, I don't have enough time to download Network Manager...

---

