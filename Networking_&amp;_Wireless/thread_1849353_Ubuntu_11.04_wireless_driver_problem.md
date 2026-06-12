---
title: "Ubuntu 11.04 wireless driver problem"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by Goranm on 2011-09-24
Hello! 
 
I am new to the forum, and to Linux OS. I have **Ubuntu 11.04,** dual boot with Windows 7. 
I want to switch to using Ubuntu, but can't seem to install drivers for my wireless network! As a matter of fact I can't install any drivers at all! I know Unix commands and I use the terminal and Ubuntu normally but cannot install any drivers nor programs. Both, Linux and Windows. I can't install Wine either. I know I need ndiswrapper in order to install Windows programs, but... :p
I would appreciate if someone could guide me through installing and setting up my wireless connection. I'll take it from there. 
 
My wireless card is** RALINK RT61 Turbo Wireless LAN Card**. Ubuntu recognizes it, I can see available networks but can't use it. Also,*** I need*** to make ***an internet connection with my username and password. ***
 
Thanks in advance!
 
Goran

---

### Post by varunendra on 2011-09-29
Helo Goranm, and welcome to the forums!

Ndiswrapper is meant for using only windows wireless drivers, not 'any' windows program. It is 'Wine' for that purpose.

If you can see wireless networks, then you already have a working driver for your wifi, so most probably you don't need ndiswrapper. Whether you need a better driver or not depends upon the kind of problem you are facing while trying to connect to the available networks. Is it that it asks for a pass-phrase but doesn't accept when supplied? If so, open Network Manager and make sure the correct security type is selected in the "Wireless Security" tab. If the problem is different than this, please explain in detail.

---

### Post by Goranm on 2011-10-11
> **varunendra said:**
> Helo Goranm, and welcome to the forums!
 
Ndiswrapper is meant for using only windows wireless drivers, not 'any' windows program. It is 'Wine' for that purpose.
 
If you can see wireless networks, then you already have a working driver for your wifi, so most probably you don't need ndiswrapper. Whether you need a better driver or not depends upon the kind of problem you are facing while trying to connect to the available networks. Is it that it asks for a pass-phrase but doesn't accept when supplied? If so, open Network Manager and make sure the correct security type is selected in the "Wireless Security" tab. If the problem is different than this, please explain in detail.
 
Hi varunendra!
 
Thanks for shedding some light on the "issues" about installing programs in Ubuntu. 
But, my main problem here is setting up the VPN connection, with my username and password. So that I could connect to my network. Ubuntu does recognize my network but I just can't make my VPN connection work. 
 
Thanks,
Goran

---

### Post by varunendra on 2011-10-11
> **Goranm said:**
> 
But, my main problem here is setting up the VPN connection, with my username and password. So that I could connect to my network. Ubuntu does recognize my network but I just can't make my VPN connection work.
So should I assume that you are otherwise able to connect to and browse Internet normally? If so, then _please explain in detail everything you have done so far to configure VPN, and the problem you are facing_.

I have never configured or used a VPN connection myself, so may not be able to help with VPN specific issues, but if the problem you are having is related with drivers or normal network configuration, then a detailed description may give us some clues that may help troubleshooting it.

If you haven't already been through the guides, here are some links that may be useful:
[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)
[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

Some advanced topics:
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by Goranm on 2011-10-25
> **varunendra said:**
> So should I assume that you are otherwise able to connect to and browse Internet normally? If so, then _please explain in detail everything you have done so far to configure VPN, and the problem you are facing_.
 
I have never configured or used a VPN connection myself, so may not be able to help with VPN specific issues, but if the problem you are having is related with drivers or normal network configuration, then a detailed description may give us some clues that may help troubleshooting it.
 
If you haven't already been through the guides, here are some links that may be useful:
[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)
[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)
 
Some advanced topics:
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
 
Hello varunendra! 

Sorry it took me awhile to come back. But, I had to do some digging and I finally know what I need! :) It's not VPN, it's PPPOE! I have it installed, but I cannot make a dial up connection! Please, if you could guide through installing of PPPOE and setting up the connection with my user name and password. 
Thank you!
 
Goran

---

### Post by varunendra on 2011-10-25
If you have an 'Unlimited' connection plan, it is best to configure PPPoE in the modem/router itself (refer to its user-manual for doing so, or post its model no. so I could try to search it for you). Else, you may either configure it within the Network Manager or through commandline console.

I'm not sure on this, but I think if you wish to configure it in Network Manager, you will have to uninstall pppoe with its configuration files first (sudo apt-get purge pppoe) to avoid any conflicts with network manager settings.

In network Manager, you have to save the ID-Password in a DSL connection, as shown in this video: [http://www.youtube.com/watch?v=J4XhbQhCIhQ](http://www.youtube.com/watch?v=J4XhbQhCIhQ)

For the console method, this guide may be what you need: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by Goranm on 2011-10-26
> **varunendra said:**
> If you have an 'Unlimited' connection plan, it is best to configure PPPoE in the modem/router itself (refer to its user-manual for doing so, or post its model no. so I could try to search it for you). Else, you may either configure it within the Network Manager or through commandline console.
 
I'm not sure on this, but I think if you wish to configure it in Network Manager, you will have to uninstall pppoe with its configuration files first (sudo apt-get purge pppoe) to avoid any conflicts with network manager settings.
 
In network Manager, you have to save the ID-Password in a DSL connection, as shown in this video: [http://www.youtube.com/watch?v=J4XhbQhCIhQ](http://www.youtube.com/watch?v=J4XhbQhCIhQ)
 
For the console method, this guide may be what you need: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
 
I've had a DSL connection made for some time now, but it doesn't work. 
You know those two little arrows from the you tube video you posted...well, I don't have them at all. That's the problem. The connection is there, but for some reason it does not work. 
Also, I have a PPPoE installed, I checked it. But, when I tried to use the console method you also posted, and tried to connect I got this:
Error: "Only members of the 'dip' group can use this command."
What does that mean? What's the 'dip' group?
 
Man, I wouldn't want to have to give up on Ubuntu because of this. If I make that connection work, everything else is a piece of cake. But, for some reason there are problems with this. 

Maybe I'm wrong, but everything is set up good, but the connection is still the problem. The network card works, the PPPoE is installed, the username and password are correct...
 
Thanks for your help! I appreciate it!

---

### Post by varunendra on 2011-10-26
> **Goranm said:**
> ....tried to connect I got this:
Error: "Only members of the 'dip' group can use this command."
What does that mean? What's the 'dip' group?....
Wow! That may be the core of the issue I was completely missing. "Dip" user group is the group whose members have the permission to connect to internet using a modem ([see here]("https://wiki.ubuntu.com/Security/Privileges#Connect_to_the_Internet_using_a_modem")). I think you should have already been its member (assuming yours is the first user created on that machine). But anyways, please follow this and retry with the Network Manager method first:

The shortest way to add yourself in the dip group is a single line command:
```
sudo adduser *<your username here>* dip
```(for example, if my user name is varun and I want to add myself to the dip group, the command will be: *sudo adduser varun dip*)

To do the same thing via GUI:
Press Alt+F2 to bring up "Run Application dialogue box. Then type **users-admin**  and press 'Enter'. This will open Users Settings dialogue box. Click on  "Manage Groups" button, then search "dip" in the list and click  "Properties" button. Put a tick-mark against your username > click OK  > supply your password and close everything.

You may have to restart  to see if it automatically fixes things. If not, at least we found and  fixed one problem, time to find and fix the next one :).

---

### Post by Goranm on 2011-10-26
> **varunendra said:**
> Wow! That may be the core of the issue I was completely missing. "Dip" user group is the group whose members have the permission to connect to internet using a modem ([see here]("https://wiki.ubuntu.com/Security/Privileges#Connect_to_the_Internet_using_a_modem")). I think you should have already been its member (assuming yours is the first user created on that machine). But anyways, please follow this and retry with the Network Manager method first:
 
The shortest way to add yourself in the dip group is a single line command:
```
sudo adduser *<your username here>* dip
```(for example, if my user name is varun and I want to add myself to the dip group, the command will be: *sudo adduser varun dip*)
 
To do the same thing via GUI:
Press Alt+F2 to bring up "Run Application dialogue box. Then type **users-admin** and press 'Enter'. This will open Users Settings dialogue box. Click on "Manage Groups" button, then search "dip" in the list and click "Properties" button. Put a tick-mark against your username > click OK > supply your password and close everything.
 
You may have to restart to see if it automatically fixes things. If not, at least we found and fixed one problem, time to find and fix the next one :).
 
 
Ok! I'm now in the dip group. And I got this:
***pppd[1716]: pppd 2.4.5 started by goran, uid 1000 ***
***pppd[1716]: Serial connection established. ***
***pppd[1716]: Using interface ppp0 ***
***pppd[1716]: Connect: ppp0 <--> /dev/pts/1 ***
 
But, it still doesn't work. And I did restart the computer.
***Wireless network-Disconnected***
***You are now offline***

I guess your wish came true! :) "...We found and fixed one problem, time to find and fix the next one." :)
 
Oh, one more question while you're here. 
Will using the same modem or wireless card on, both, Windows 7 and Ubuntu 11.04 interfere with one another? In other words, can using it with Ubuntu, then restarting the computer and using it with Windows 7, have any undesirable or negative effect?
I bought this new computer a month ago with Windows 7 and I installed Ubuntu 11.04., so I have a dual boot system, so I am the first user created on this machine.

---

### Post by varunendra on 2011-10-27
Let's clear up some basic things before going further.

In order to get connected to a pppoe connection via wireless you first need to get connected to your modem/router. If this connection is established, you will be able to ping your modem/router from your computer. Then comes the stage when you have to establish a PPPoE connection.

By your description so far, it seems you are unable to connect to your router in the first place (even though you can see the network in the available networks' list). So let's make sure you get that connection established first. Accordingly, please give a detailed description of all the devices, connections and methods involved in your network. For now I am assuming you have an ADSL modem which is connected to your ISP through a cable. You get connected to that modem via wifi, and then dial pppoe to get connected to internet.

As for using same modem/router with both windows/ubuntu, theoretically there should be no problems. However practically, in some rare cases, I have seen problems with ubuntu IF you boot into it immediately after closing windows. It happens due to the fact that the firmware loaded in the network interface card's memory does not get completely removed before the next one (ubuntu's) is loaded. A crude workaround in those problems was to leave the computer completely powered of for 10-20 min before booting into ubuntu (if you were using windows previously). But as I said, those are rare cases and I still haven't understood them properly.

As a quick check to whether or not you are connected to your modem/router, please post outputs of:
```
ifconfig -a
iwconfig
```Please wrap these outputs in 'code' tags (by using the **#** symbol at the top of edit box) just like you are using 'quote' tags so far. It preserves the formatting of the output and makes it more readable.

---

### Post by Goranm on 2011-10-27
> **varunendra said:**
> Let's clear up some basic things before going further.
 
In order to get connected to a pppoe connection via wireless you first need to get connected to your modem/router. If this connection is established, you will be able to ping your modem/router from your computer. Then comes the stage when you have to establish a PPPoE connection.
 
By your description so far, it seems you are unable to connect to your router in the first place (even though you can see the network in the available networks' list). So let's make sure you get that connection established first. Accordingly, please give a detailed description of all the devices, connections and methods involved in your network. For now I am assuming you have an ADSL modem which is connected to your ISP through a cable. You get connected to that modem via wifi, and then dial pppoe to get connected to internet.
 
As for using same modem/router with both windows/ubuntu, theoretically there should be no problems. However practically, in some rare cases, I have seen problems with ubuntu IF you boot into it immediately after closing windows. It happens due to the fact that the firmware loaded in the network interface card's memory does not get completely removed before the next one (ubuntu's) is loaded. A crude workaround in those problems was to leave the computer completely powered of for 10-20 min before booting into ubuntu (if you were using windows previously). But as I said, those are rare cases and I still haven't understood them properly.
 
As a quick check to whether or not you are connected to your modem/router, please post outputs of:
```
ifconfig -a
iwconfig
```Please wrap these outputs in 'code' tags (by using the **#** symbol at the top of edit box) just like you are using 'quote' tags so far. It preserves the formatting of the output and makes it more readable.
 
 
 
 
 
 
 
 
 
 

Ok! As requested, the outputs:
[LIST]
[*]ifconfig - a
[/LIST]```
eth0 Link encap:Ethernet HWaddr 1c:6f:65:54:8b:45 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:41 Base address:0x2000 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:148 errors:0 dropped:0 overruns:0 frame:0 
TX packets:148 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:11416 (11.4 KB) TX bytes:11416 (11.4 KB) 
 
wlan0 Link encap:Ethernet HWaddr 00:fd:07:95:24:ec 
inet6 addr: fe80::2fd:7ff:fe95:24ec/64 Scope:Link 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:480 errors:0 dropped:0 overruns:0 frame:0 
TX packets:28 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:6720 (6.7 KB) TX bytes:8343 (8.3 KB) 

```

[LIST]
[*]iwconfig
[/LIST]```

lo no wireless extensions. 
 
eth0 no wireless extensions. 
 
wlan0 IEEE 802.11bg ESSID:off/any 
Mode:Managed Frequency:2.447 GHz Access Point: Not-Associated 
Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off 
Power Management:off 

```
 
I hope that can help!
 
The reason I asked about possible problems with two OS using the same modem is because it happened once or twice to me. When I tried to connect to the internet in Ubuntu, then restarted the computer, Windows couldn't recognize, or reported that, the wireless card was disconnected. But, I didn't have to wait 10-20 minutes, just restarted the computer again and no problems reappeared. But, that happened from Ubuntu to Windows. Either way, I feel better now because it's nothing serious. 
 
Ok! My wireless card is **RALINK RT61 Turbo Wireless LAN Card**. Yes, it is connected through a cable, so I presume everything you assumed about my network is correct. 
As you can see, I am not really into setting up networks, so I don't know much about it. So far I didn't have to know, but now this is a good excersize. :D 
 
Thanks for the tip on how to use the "code wrapping".

---

### Post by varunendra on 2011-10-27
> **Goranm said:**
> ```
 
wlan0 Link encap:Ethernet HWaddr 00:fd:07:95:24:ec 
inet6 addr: fe80::2fd:7ff:fe95:24ec/64 Scope:Link 

```
[LIST]
[*]iwconfig
[/LIST]
```
 
wlan0 IEEE 802.11bg ESSID:off/any 
Mode:Managed Frequency:2.447 GHz Access Point: **Not-Associated **
Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off 
Power Management:off 

```
So your wifi is currently NOT connected to any networks. Do you see any available networks in the drop-down menu of Network manager? If you do, what happens when you click on one?

In case you can't find any available networks, or can't connect to it, please post outputs of:
```
lspci -nnk | grep -iA2 net
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```(Please note that it is 'piping' symbol between "-nnk" and "grep", not a small 'L' in the first command. If unsure, just copy-paste the commands)

> **Goranm said:**
> Thanks for the tip on how to use the "code wrapping".No problems with that :). Here's another one - It is not necessary to quote everything from one's post (or quote it at all). It is done to express which part of the post you are responding/referring to. So if you quote a long post (like my previous one), it is a good idea to delete its irrelevant parts and leave only those which you are going to respond/refer to. If not necessary, don't quote at all as it makes a post unnecessarily longer and wastes space on forum-servers.

---

### Post by Goranm on 2011-10-27
Outputs: 
[LIST]
[*]**lspci -nnk | grep -iA2 net**
[/LIST]```
 00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2) 
Subsystem: Giga-byte Technology Device [1458:e000] 
Kernel driver in use: forcedeth 
-- 
01:07.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301] 
Subsystem: Ralink corp. EW-7108PCg [1814:2561] 
Kernel driver in use: rt61pci 

```
 

[LIST]
[*]**cat /etc/network/interfaces**
[/LIST]```
auto lo 
iface lo inet loopback 
 

```
 

[LIST]
[*]**cat /etc/NetworkManager/NetworkManager.conf**
[/LIST]```
 # This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default. To override, specify: '--config file' 
# during NM startup. This can be done by appending to DAEMON_OPTS in 
# the file: 
# 
# /etc/default/NetworkManager 
# 
[main] 
plugins=ifupdown,keyfile 
[ifupdown] 
managed=false 

``` 
 
 
>  Do you see any available networks in the drop-down menu of Network manager? If you do, what happens when you click on one?

 
Yes, I can see networks. When I choose mine, it tries to connect and it says: ***Wireless network: disconnected. ***
 
> ...It is not necessary to quote everything from one's post...
 
Don't worry. I'm not new to forums, I'm just new to this one. :D 
But, before I was replying to your whole post. 
Thanks for the tips, though. I like learning new stuff. That "code" thing is good stuff. :D
 
What I don't understand is why this is so complicated on my machine. It makes me wonder. :D

---

### Post by varunendra on 2011-10-27
It gets me wondering too, because everything in the outputs seems to be fine so far.

When you try to connect, it tries and eventually disconnects, please post the output of the following command afterwards:
```
dmesg | grep -iE "rt61|wlan"
```Some more questions:

[LIST=1]
[*]What is the brand and model of your wireless router/modem (the device which is connected to your ISP via cable)
[*]Is your wireless network secured? If it is, try to turn off the security in the router (just for testing purpose) and retry to connect.
[*]Have you tried to connect to any other network successfully (in Ubuntu)?
[/LIST]

---

### Post by Goranm on 2011-10-28
> **varunendra said:**
> It gets me wondering too, because everything in the outputs seems to be fine so far.

When you try to connect, it tries and eventually disconnects, please post the output of the following command afterwards:
```
dmesg | grep -iE "rt61|wlan"
```Some more questions:

[LIST=1]
[*]What is the brand and model of your wireless router/modem (the device which is connected to your ISP via cable)
[*]Is your wireless network secured? If it is, try to turn off the security in the router (just for testing purpose) and retry to connect.
[*]Have you tried to connect to any other network successfully (in Ubuntu)?
[/LIST]


Hey Varun! I called my provider and they told me that all I had to do was to install PPPoE! And that that was going to fix all my problems with internet connections! I'm glad you got me through this, man! Because it works! :D I don't know how, because the network I am using right now is not my provider's network! :D You told me to try other networks and this one is the only one that works! I will copy this whole thread and save it in case of some future problems with network. I hope there will be no more problems! :D 
But, before I mark this thread "Solved", I need a couple of more things! :D
First of all, I can't install anything! Except updates! And I need to install a graphics drivers ASAP because I don't like the letters at the moment. :) Bad! Everything's good except the letters. Hurts my eyes. 
I have the drivers downloaded, for Linux, but it says that I have to check if it's a binary file and that **"gedit has not been able to detect character encoding."** And it says that for everything I want to install. I also have Wine installed but I can't install any of the Windows drivers either. Man, my machine is really something, isn't it! 

Thanks!

---

### Post by varunendra on 2011-10-28
> **Goranm said:**
> 
I have the drivers downloaded, for Linux, but it says that I have to check if it's a binary file and that **"gedit has not been able to detect character encoding."** And it says that for everything I want to install. I also have Wine installed but I can't install any of the Windows drivers either. Man, my machine is really something, isn't it!Hi,
Your machine is normal, don't worry about that :)
Gedit is a text editor while the drivers/application packages are binary files, hence gedit or any other 'text editor' can not open them. In order to install them, you need to make then 'executable':
```
chmod +x <filename>
```(the GUI method is to right-click on the file > goto 'Permissions' tab > check "Allow executing..." > close)

Anyway, for your graphics related questions, you'd be better off creating a separate thread with a relevant title. Although I'd like to follow that one too, so you may put a link to it here.

As for the current problem, glad it is working 'somehow', but I don't see how it is solved if you still are unable to connect to your own network. I still believe we are missing something. As I said previously, IF it is indeed a router which is connected to your ISP and IF you have an unlimited plan, at least one possible level of complexity/problem could be eliminated by enabling PPPoE in the router itself. In that case, it automatically gets connected to the ISP as soon as you turn it on. You don't need to do any setting in the computer, just connect it to your access point, and start browsing internet. But configuring PPPoE within the OS also isn't any difficult. It just adds one more level where errors may occur.

So currently I doubt there is some inconsistency between the driver/firmware of your wifi card and the router/access-point. It is not very rare and there are workarounds for most of them. I was expecting to get some relevant hint regarding this from the output I asked for. But I also know that not all the people have time for such irritating problems. Besides, it could have been much more easier and straightforward had you been helped by an expert here who has first-hand experience with such issues (which I clearly don't have) :)

So if you think you are done with it, you may just leave it open as it is. But I really don't think it can be said to be 'solved' at this stage.

---

### Post by Goranm on 2011-10-28
> 
I was expecting to get some relevant hint regarding this from the output  I asked for. But I also know that not all the people have time for such  irritating problems. Besides, it could have been much more easier and  straightforward had you been helped by an expert here who has first-hand  experience with such issues (which I clearly don't have) :smile:

So if you think you are done with it, you may just leave it open as it  is. But I really don't think it can be said to be 'solved' at this  stage.Well, I don't find these problems irritating at all, simply because I have to learn everything about Linux and you have helped a lot. And I also love computers, so... Don't worry, you're doing a great job, so no "experts" are needed. If you think I should continue with searching and fixing the problem, then I shall do it, because I do not want to have the same problem in near future. Since this is the opportunity for me to learn more, we'll continue. It's great you have the will to continue. :D I appreciate that! Thanks again!

Output:

[LIST]
[*]**dmesg | grep -iE "rt61|wlan"**
[/LIST]
```
 
[   11.494598] rt61pci 0000:01:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   11.536029] Registered led device: rt61pci-phy0::radio
[   11.536047] Registered led device: rt61pci-phy0::assoc
[   12.996331] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.892264] wlan0: authenticate with 00:80:48:67:54:59 (try 1)
[   18.927180] wlan0: authenticated
[   18.927265] wlan0: associate with 00:80:48:67:54:59 (try 1)
[   18.973029] wlan0: RX AssocResp from 00:80:48:67:54:59 (capab=0x421 status=12 aid=16383)
[   18.973034] wlan0: 00:80:48:67:54:59 denied association (code=12)
[   18.973090] wlan0: deauthenticating from 00:80:48:67:54:59 by local choice (reason=3)
[   30.032166] wlan0: authenticate with 00:80:48:67:54:59 (try 1)
[   30.045774] wlan0: authenticated
[   30.045858] wlan0: associate with 00:80:48:67:54:59 (try 1)
[   30.056539] wlan0: RX AssocResp from 00:80:48:67:54:59 (capab=0x421 status=12 aid=16383)
[   30.056544] wlan0: 00:80:48:67:54:59 denied association (code=12)
[   30.056593] wlan0: deauthenticating from 00:80:48:67:54:59 by local choice (reason=3)
[   35.892406] wlan0: authenticate with 00:24:d2:54:05:d1 (try 1)
[   35.893787] wlan0: authenticated
[   35.893817] wlan0: associate with 00:24:d2:54:05:d1 (try 1)
[   35.896424] wlan0: RX AssocResp from 00:24:d2:54:05:d1 (capab=0x401 status=0 aid=1)
[   35.896428] wlan0: associated
[   35.896920] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.256031] wlan0: no IPv6 routers present

```Whatever you think is necessary to enable my own network, let me know. I think this thread will be helpful to those with similar problems. 

> In order to install them, you need to make then 'executable':
```
chmod +x <filename>
```(the GUI method is to right-click  on the file > goto 'Permissions' tab > check "Allow executing..."  > close) I tried it, it doesn't work. I guess I did make it executable, because I get options to choose. When I click "Run" nothing happens. But, when I open it in Terminal, it says I have to be root to install it. But, when I am root, it doesn't want to open the driver. I'll keep on trying. For now, at least I have internet connection so I don't have to restart the computer all the time to get back to the forum. 
Oh yeah! You forgot to tell me the command for installing in terminal. If there is such a thing. Maybe that's the problem. 

> Anyway, for your graphics related questions, you'd be better off creating a separate thread with a relevant title.I'll post the link if I decide to make another thread. For now I think everything's ok.

---

### Post by varunendra on 2011-10-28
To eliminate some doubt I have right now, can you please post the brand and model code of your wifi device which is connected via cable to your ISP? (and to which your laptop is unable to connect via wifi).

Also, the output of:
```
iwlist scan
```(while you are within close range of your wifi router/access point)


**_EDIT_:**
As for executing those binaries from terminal, it depends upon what kind of packages those are. If they are .deb, you just need to double-click on them to initiate installation. If they tarballs (.tar/.gz) you need to first extract them using archive manager, then run some installation script found in the extracted files. For example, if there is a file named install.sh in the extracted files, and the readme says that is the file to run, the command in terminal would be something like *sudo sh ./install.sh* or just *sudo ./install.sh*. Some other binary packages need successful execution of a three-step sequence of .*/configure, make, make-install*. But unless we know what is your card and whether the driver is correct one for it, suggesting anything can worsen things. That's why I suggest to start a new thread so that it can be discussed separately in detail.

---

### Post by Goranm on 2011-10-28
> 
the output of:
```
iwlist scan
```(while you are within close range of your wifi router/access point)
 
 

[LIST]
[*]**iwlist scan**
[/LIST]```

lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wlan0 Scan completed :
Cell 01 - Address: 00:80:48:62:F9:40
Channel:8
Frequency:2.447 GHz (Channel 8)
Quality=46/70 Signal level=-64 dBm 
Encryption key:off
ESSID:"BEOTELNET - Melenci - S1"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Mode:Master
Extra:tsf=000000543a1636c2
Extra: Last beacon: 3820ms ago
IE: Unknown: 001842454F54454C4E4554202D204D656C656E6369202D205331
IE: Unknown: 010482040B16
IE: Unknown: 030108
IE: Unknown: DD2A000C42000000011E0000000000661E030000303038303438363246393430000000000000000005028F09
Cell 02 - Address: 00:1B:9E:F5:04:5D
Channel:10
Frequency:2.457 GHz (Channel 10)
Quality=30/70 Signal level=-80 dBm 
Encryption key:off
ESSID:"HG520s"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000002e8be9572
Extra: Last beacon: 3696ms ago
IE: Unknown: 0006484735323073
IE: Unknown: 010482848B96
IE: Unknown: 03010A
IE: Unknown: 2A0104
IE: Unknown: 32080C1218243048606C
Cell 03 - Address: B4:82:FE:A1:AC:7C
Channel:7
Frequency:2.442 GHz (Channel 7)
Quality=30/70 Signal level=-80 dBm 
Encryption key:off
ESSID:"HG520c"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000079efdd1d7
Extra: Last beacon: 3880ms ago
IE: Unknown: 0006484735323063
IE: Unknown: 010482848B96
IE: Unknown: 030107
IE: Unknown: 2A0104
IE: Unknown: 32080C1218243048606C
Cell 04 - Address: 00:80:48:67:54:8C
Channel:5
Frequency:2.432 GHz (Channel 5)
Quality=32/70 Signal level=-78 dBm 
Encryption key:off
ESSID:"BEOTELNET - Melenci - S8"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Mode:Master
Extra:tsf=0000002d10e3c181
Extra: Last beacon: 3992ms ago
IE: Unknown: 001842454F54454C4E4554202D204D656C656E6369202D205338
IE: Unknown: 010482040B16
IE: Unknown: 030105
IE: Unknown: DD2A000C42000000011E00100000006600050000303038303438363735343843000000000000000005028009
Cell 05 - Address: 00:80:48:67:54:59
Channel:5
Frequency:2.432 GHz (Channel 5)
Quality=34/70 Signal level=-76 dBm 
Encryption key:off
ESSID:"BEOTELNET - Melenci - S3"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Mode:Master
Extra:tsf=00000054395762e5
Extra: Last beacon: 3996ms ago
IE: Unknown: 001842454F54454C4E4554202D204D656C656E6369202D205333
IE: Unknown: 010482040B16
IE: Unknown: 030105
IE: Unknown: DD2A000C42000000011E00100000006605050000303038303438363735343539000000000000000005028009
Cell 06 - Address: 00:80:48:69:46:8F
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=42/70 Signal level=-68 dBm 
Encryption key:off
ESSID:"BusMelenci2.4GHz-4"
Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s
Mode:Master
Extra:tsf=0000017105bd2181
Extra: Last beacon: 4216ms ago
IE: Unknown: 00124275734D656C656E6369322E3447487A2D34
IE: Unknown: 0103848B96
IE: Unknown: 030102
IE: Unknown: 050400010000
IE: Unknown: DD2A000C42000000011E0000000000660B040000303038303438363934363846000000000000000005027109
Cell 07 - Address: 00:24:D2:54:05:D1
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=28/70 Signal level=-82 dBm 
Encryption key:off
ESSID:"Gaja"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001c7e1a3f30
Extra: Last beacon: 4272ms ago
IE: Unknown: 000447616A61
IE: Unknown: 010482848B96
IE: Unknown: 030101
IE: Unknown: 2A0104
IE: Unknown: 32080C1218243048606C

```
 
 
>  To eliminate some doubt I have right now, can you please post the brand and model code of your wifi device which is connected via cable to your ISP? (and to which your laptop is unable to connect via wifi).  
 
I don't have a laptop, I have a desktop PC. 
As for my wifi device, this is all I know about it: **REink Jet**, **Wireless-G PCI Adapter**, **model WL-150G-C. Manufacturer: Ralink Technology. **
**Driver: Ralink RT61 Wireless LAN Network. **
 
 
> ...I suggest to start a new thread so that it can be discussed separately in detail.
 
I will start a new thread about installing applications in Ubuntu. I'll post you a link here.

---

### Post by Goranm on 2011-10-28
Link to the new thread:
[http://ubuntuforums.org/showthread.php?p=11403861#post11403861](http://ubuntuforums.org/showthread.php?p=11403861#post11403861)

---

### Post by varunendra on 2011-10-29
> **Goranm said:**
> I don't have a laptop, I have a desktop PC.
Yeah, I was doubtful about that (didn't search for the card's model you described earlier). Good it's clear now.

> **Goranm said:**
> As for my wifi device, this is all I know about it: **REink Jet**, **Wireless-G PCI Adapter**, **model WL-150G-C. Manufacturer: Ralink Technology. **That is the PCI card plugged-in your computer. I was interested in the box from where it is getting the signal. Usually it is a small box with a number of LEDs on it and maybe some empty cable-connection ports on its back. The internet cable that comes into your house, from the service provider, is directly connected to it.

Also, among the 7 cells detected by *iwlist scan*, can you identify your own connection (the "ESSID" is the name by which each connection appears in the "Available Networks" list)? Which one is it?

---

### Post by Goranm on 2011-10-29
> 
I was interested in the box from where it is getting the signal. Usually it is a small box with a number of LEDs on it and maybe some empty cable-connection ports on its back. The internet cable that comes into your house, from the service provider, is directly connected to it. 
 
Oh that! :) That's exactly why I didn't understand what you were asking me about, because I do not have that box, there are not LEDs. I have an antenna which resembles a "net" TV antenna. My brother has the box you're talking about. 
We have different providers, so different equipment altogether. My antenna is simple, with the cable going straight through it and is connected to the "head". Forgot what it's called. So, no bells and whistles here. :) Also, the cable is not plugged into the card in the computer, but screwed in. Maybe that helps.
 
> 
can you identify your own connection. Which one is it?
 
Yes, my network is **BEOTELNET - Melenci - S1.**

---

### Post by varunendra on 2011-10-30
So as you might have already guessed, I'm out of ideas now. You can connect to one of those available networks (to "Gaja" it seems from your dmesg), so the driver is working. But can't connect to your own access point, suggests a possible mutual inconsistency at authentication level. Whatever, it seems beyond my level of expertise (which is already too low when it comes to wifi). So here are the last arrows in my quiver (try one at a time):

[LIST]
[*]Open Synaptic Package Manager, and make sure wpasupplicant is installed.
[/LIST]

[LIST]
[*]If you have option to change the password, try changing it to something else, preferably, a simple combination of normal alpha-numeric characters. If you can also change the security type, try different ones (wep is easiest, but most vulnerable)
[/LIST]

[LIST]
[*]Try the only parameter available for your driver:
[/LIST]
```
sudo rmmod -f rt61pci
sudo modprobe rt61pci nohwcrypt=1
```

[LIST]
[*]Try installing **wicd** from software center, and remove **Network-Manager**. It often works better with wireless interfaces. You will need to connect to internet though. Although you can also download it manually from here: [http://packages.ubuntu.com/natty/net/](http://packages.ubuntu.com/natty/net/) , it may give you troubles with dependencies (you'll have to download and install each dependency manually), and with no guarantee of success, it may not be worth all that trouble.
[/LIST]

[LIST]
[*]Try this guide to manually connect (without any network management tool): [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[/LIST]

As far as I know, you can use pppoe ONLY when you get connected to the access point first. If your connection behaves otherwise (since your ISP said you need only pppoe, although I can't think how it is possible), it will be more than interesting for me to know.

---

### Post by Goranm on 2011-11-02
> **varunendra said:**
> 

Open Synaptic Package Manager, and make sure wpasupplicant is installed.
[LIST]
[*]If you have option to change the password, try changing it to something else, preferably, a simple combination of normal alpha-numeric characters. If you can also change the security type, try different ones (wep is easiest, but most vulnerable)
[/LIST]
[LIST]
[*]Try the only parameter available for your driver:
[/LIST]```
sudo rmmod -f rt61pci
sudo modprobe rt61pci nohwcrypt=1
```

[LIST]
[*]Try installing **wicd** from software center, and remove **Network-Manager**. It often works better with wireless interfaces. You will need to connect to internet though. Although you can also download it manually from here: [http://packages.ubuntu.com/natty/net/](http://packages.ubuntu.com/natty/net/) , it may give you troubles with dependencies (you'll have to download and install each dependency manually), and with no guarantee of success, it may not be worth all that trouble.
[/LIST]
[LIST]
[*]Try this guide to manually connect (without any network management tool): [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[/LIST]
 
I've been reading and trying to make it work, so couldn't reply before seeing if there were any results. No results whatsoever. :guitar::)
 
Ok! From the guide for manually connecting, and because my RT61 wireless card is on the list for this kind of setting, aka ***Wpa-PSK with Ra Based Chipsets***[SIZE=2], [/SIZE]I tried this:
```

[COLOR=black][FONT=Courier New]sudo ifconfig wlan0 down[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo dhclient -r wlan0[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo ifconfig wlan0 up[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo iwconfig wlan0 essid "BEOTELNET-MELENCI-S1"[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo iwpriv wlan0 set AuthMode=WPAPSK[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo iwpriv wlan0 set EncrypType=TKIP[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo dhclient wlan0[/FONT][/COLOR]
 

```
 
And got this:
 
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "BEOTELNET-MELENCI-S1"
sudo iwpriv wlan0 set AuthMode=WPAPSK
***wlan0 no private ioctls.***
sudo iwpriv wlan0 set EncrypType=TKIP
**wlan0 no private ioctls.**

```
 
Ok! As you can see I never got to use my WPA PSK key. Which, as you might guess I do not know. :) But, after some googling I found that there are ways of finding that key. 
First, I need these outputs **wlan0 no private ioctls **interpreted.
 
PS Got rid of *Network Manager*, so I can't connect in Ubuntu now. But, I have Windows until I make it work. :D *Wicd* installed but other than that nothing happened. I don't know how to connect using *wicd*.

---

### Post by Goranm on 2011-11-03
Hey Varun! :D

I have upgraded from 11.04 to 11.10...thinking it could help solve my problems with connection...and I think I know what the problem is! There's no PPPoE installed at all! Tried to install it again and got this:
```
                                                          &#9474;          
          &#9474; Sorry, I scanned 2 interfaces, but the Access            &#9474;          
          &#9474; Concentrator of your provider did not respond. Please    &#9474;          
          &#9474; check your network and modem cables. Another reason for  &#9474;          
          &#9474; the scan failure may also be another running pppoe       &#9474;          
          &#9474; process which controls the modem.  
```

Any ideas on how to "fix" that? 
I like this Ubuntu 11.10! :D

Thanks!

Goran

---

### Post by 0121computers on 2011-11-03
Hi there this can be a problem especialy using certain laptops There are a couple of ways to fix this conect a hardline and instail the right drivers for the WILLAN or the easyest way is get yourself a BELKIN USB wireless adaptor instail the drivers and the card then when working re boot take out the usb stick and your wirless should work normaly I hope this helps good luck

---

### Post by Goranm on 2011-11-03
> **0121computers said:**
> Hi there this can be a problem especialy using certain laptops There are a couple of ways to fix this conect a hardline and instail the right drivers for the WILLAN or the easyest way is get yourself a BELKIN USB wireless adaptor instail the drivers and the card then when working re boot take out the usb stick and your wirless should work normaly I hope this helps good luck

Hello! 

I read about BELKIN USB adaptor. But, I think I should stick to what I have for now. 
I don't have a laptop, I have a desktop PC.
I would try to install the drivers for the WILLAN if I knew what it was. You mean wlan? 
Some further explanation will be appreciated. 

Thanks!

Goran

---

### Post by varunendra on 2011-11-04
> **Goranm said:**
> Hey Varun! :D

I have upgraded from 11.04 to 11.10...thinking it could help solve my problems with connection...and I think I know what the problem is! There's no PPPoE installed at all! Tried to install it again and got this:
```
                                                          &#9474;          
          &#9474; Sorry, I scanned 2 interfaces, but the Access            &#9474;          
          &#9474; Concentrator of your provider did not respond. Please    &#9474;          
          &#9474; check your network and modem cables. Another reason for  &#9474;          
          &#9474; the scan failure may also be another running pppoe       &#9474;          
          &#9474; process which controls the modem.  
```Any ideas on how to "fix" that? 
Sorry for a late reply, but I got 'unexpectedly' busy and will be for next couple of days. After that I may not even be able to access internet until 29th of this month as will be away where I may not get access to it. A summary of my recent and forthcoming involvements can be read on RASA's profile page in my visitor's message: [http://ubuntuforums.org/member.php?u=1029120](http://ubuntuforums.org/member.php?u=1029120)


The message you got is normal when you are either physically disconnected, or another pppoe client is already functional on the same connection as the message suggests. For example, when I configure pppoe in my adsl router, I get this message when attempting to run it from within ubuntu. But when I disable it in the router, it works as smooth as can be expected. So I don't think it can be a problem with its installation or functioning. But I am currently unable to suggest a possible solution. Firstly because my mind is still jumbled up with all the tasks in my hand, and secondly because I don't think I am understanding your whole ISP to client network properly (yeah, even after getting so much details from you..). Although I firmly 'believe' I theoretically understand it, I just not am sure since I have so far seen or read no practical examples of it. If I go with my theory, you need to get 'physically' connected first with your access point. A PPPoE connection can be established 'only' after that (by supplying your ID-Password after your wifi shows you are connected). But I may be wrong.... new knowledge and examples keep coming to me all the time, and my current knowledge about "pppoe over wifi" is definitely inadequate... :)

I think you can get the most precise and accurate help from either [chili555]("http://ubuntuforums.org/member.php?u=35909"), [praseodym]("http://ubuntuforums.org/member.php?u=1411497"), or [wildmanne39]("http://ubuntuforums.org/member.php?u=508533")

I personally have seen chili555 helping with similar problem, but he seems to be away from forums for a few days (actually many days). But trying to contact any of them won't hurt :).

Sorry again for not being able to help, but I think I have reached the limit of my current knowledge, and am too short of time to do any more research before 29th, when I'd return from home.

With hopes to keep visiting in the meanwhile, whenever I get access to internet.., see you all later.
-Varunendra

---

### Post by Goranm on 2011-11-04
PPPoE is installed. And re-installed, and checked that it's the newest version.  But, I'm having problems configuring it. 

Tried and got this:
```
Oh, dear, I don't see the file '/etc/ppp/pppoe.conf' anywhere.  Please
re-install the PPPoE client.

```Re-installation didn't fix the problem.

---

