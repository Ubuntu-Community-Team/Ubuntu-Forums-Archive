---
title: "network connection but no Internet"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by LePeache on 2010-08-15
Hello,

I've just installed ubuntu 10.04 onto my laptop. I have managed to connect to my network but it seems to have limited internet connection (I can ping google, yahoo, etc) the computer tells me I have an Internet connection but Firfox will not load any pages, ubuntu software centre won't download anything, and I can't seem to get anything from update. When firefox starts, it seems to get an intial response from web sites but not enough to load the page.

I have a Netbook running UNR and the connection settings are exactly the same, but the Netbook works fine. I have
DHCP set to Auto
My router is set as the gateway.

Is there something I could be looking at?
The Laptop is HP Pavilion and the netbook an ACER Aspire one


Cheers
Leon

---

### Post by Kerubu on 2010-08-15
It's not clear from your post exactly what components you have in your system:

1. What provides your internet connection? e.g. adsl modem, cable modem etc

2. What provides your LOCAL network eg ethernet or wireless router or hub or do you have a combined modem/wireless base/thernet hub?

3. how many computers do you have connected on you LOCAL network ? which ones work ok and what OS do they each have.

---

### Post by LePeache on 2010-08-15
Thanks for the reply

My local network has a Thomson router/ADSL modem supplied by Telstra.  There are four computers connected an iMac desktop, Apple Laptop, Acer aspire one netbook, and a HP pavilion Laptop.
All computers are connected to the network by wireless. No other computer seems to be having difficulties. The Netbook is running a dual boot with UNR 9.10 and Windows XP and in both systems I can connect to the Internet.
The laptop originally had Vista installed but I've just reformatted the drive in installed ubuntu 10.04

---

### Post by Kerubu on 2010-08-15
First try issuing the command :

ifconfig

in a terminal window, on both the machine that is slow and a machine that works (assuming is has *nix on a working one)

Look for the value of 'MTU=' and see if there is an difference between the value for a working machine and the one that is slow

---

### Post by LePeache on 2010-08-15
both MTU are set at 1500..

---

### Post by Kerubu on 2010-08-15
from the slow machine, can your ping a website?

ping -c 5 [www.yahoo.com](www.yahoo.com)

---

### Post by Kerubu on 2010-08-15
And also, post the output from ifconfig, executed on the slow machine.

---

### Post by lovinglinux on 2010-08-15
> **LePeache said:**
> both MTU are set at 1500..

Set it as 1492 then disable ipv6.

Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

This should fix your problem.

---

### Post by LePeache on 2010-08-15
My ifconfig is as below:

leon@leons-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:9b:75:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x6000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480.0 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:a0:af:6f  
          inet addr:10.0.0.13  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fea0:af6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:828746 (818.7 KB)  TX bytes:151721 (151.7 KB)

root@ubuntu:/home/leon# 

I also tried the advice above regarding changing the MTU and Firefox but still have no joy. I have found another problem, even though the router can see the laptop (it has it listed when I go to the routers admin page) I can not load the external drive that the router is connected to. The netbook can connect though.

---

### Post by LePeache on 2010-08-15
I also could ping successfully, [www.yahoo.com](www.yahoo.com), [www.google.com](www.google.com), and [www.facebook.com](www.facebook.com).
each time I got 5 packets sent, 5 recieved, 0% lost and time was between 4004/6ms

---

### Post by LePeache on 2010-08-16
ok, so I've been playing with not much changing, except, I right clicked on the network icon and clicked on "about". This opened a window giving version details of "NetworkManager Applet 0.8".
From there I clicked on "NetworkManager Website" and it loaded, this is the only page to open. "http://projects.gnome.org/NetworkManager/" was the page that opened but no others, including links on that page opened.
The only other page that remotely looked like opening was Facebook, which stalls waiting for static.ak.fbcdn.net and the tab changes title to "Welcome to Facebook" but that is all that happens.

This must be something simple but I'm having trouble finding it. As I mentioned in my original post, the netbook seems to have the network setup the same and it works fine.

---

### Post by rcchume on 2010-08-16
Is there any chance that the ip addresses of the hosts on which you pinged are already maintained in hosts file? The slowness could be with hostname resolution.

---

### Post by lovinglinux on 2010-08-16
Are you able to update your system and install software from the Software Center or Synaptic Package Manager?

---

### Post by lovinglinux on 2010-08-16
Are you able to update your system and install software from the Software Center or Synaptic Package Manager?

---

### Post by wanwarlock on 2010-08-16
> **lovinglinux said:**
> Set it as 1492 then disable ipv6.
 

Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
This should fix your problem.
 
 
i had the same issue and this fixed it. but having issues with email & chat for some reason...

---

### Post by lovinglinux on 2010-08-16
EDIT: nevermind, the OP is using another program for mail.

---

### Post by LePeache on 2010-08-17
Thanks for all the help so far, but I still have had no luck. Software centre, update manager, Synaptic Package Manager all come up with errors and won't download anything.

I still can't understand why two computers appear to have the same settings, but one will work and the other won't.

What should I do to check the Host file?

---

### Post by lovinglinux on 2010-08-17
Try method #3 of [this tutorial]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html").

---

### Post by LePeache on 2010-08-18
Ok, so I've now narrowed it down to being something to do with the wireless setup. The computer works great when connected to the LAN just not when using wireless.

---

### Post by Elmer Fudd on 2010-08-18
> **LePeache said:**
> Ok, so I've now narrowed it down to being something to do with the wireless setup. The computer works great when connected to the LAN just not when using wireless.

I have seen this problem in mixed (Wintel,apple,linux) environments. Though usually with linksys routers. Disabling ipv6 in the apple and linux boxes fixed the problem in those cases.

Probably not the case here if it works when wired and the apple products are running.

Did you notice if the DHCP gave you the same ip address for both wireless and wired connections?

---

### Post by fraict on 2010-08-19
i just installed ubuntu 9.10 in vaio e series but when i connect my lan its not getting connected....but when i use in window7 its getting detected....so if any1 can help....

---

### Post by LePeache on 2010-08-24
I'm still getting no joy, IPV6 isn't being used and DHCP is giving different IP addresses to all the computers connected. The only thing noticable is the driver indicated when I review the active connections is different on the netbook "ath9k" while the laptop has "iwlagn" I'm not sure if this is important and if it is I don't know how to fix it.
Incidentally, the laptop does connect to the HDD connected to the router. and appears to make fisrt contact with the internet, just not enough to load the pages. I also note that when I ping internet sites, I get through successfully
Could this be a firefox problem?

---

### Post by Elmer Fudd on 2010-08-25
Eliminate the question of "is it a Firefox problem" by trying Opera,Chromium or Midori.

---

### Post by LePeache on 2010-08-25
I tried to download a new browser but alias, neither wireless or cable are working now. The LAN connection and wireless have totally different IP setup, though both are connecting to the same router and using DHCP? I can't remember changing anything on the Router or LAN setup. But even though I can ping internet sites, the ubuntu software centre would only download the first 5% of Midori and then freeze. Similar to what happens when I try to open a page, initially looks like the browser communicates but then stops.

I'm thinking due to the software centre not downloading that perhaps its something different to just a browser problem.

Could it be my drivers? and if so how and what should I do to replace or update them? Sorry I'm still learning Linux and still learning the simple things.

Thanks for all the help so far

Leon

---

### Post by LePeache on 2010-08-25
OK :-D

Checking the other network connections and the other computers were using 10.0.0.138 as the gateway (and is the routers address) and the computers were using addresses between 10.0.0.1 to 10.0.0.22. I know the router also uses 192.168.1. so I set the laptop to 192.168.1.10 with the gateway set as 192.168.1.254.

Restarted the network adn instantly connected to the internet ..... I'm using thr Laptop to write this message.

Can any explain to me why this computer needs to use a totally different IP address to the other computer which share the internet connection?

Either way it all works now, thanks for all the help.

Cheers
Leon.

---

### Post by Bob99 on 2010-08-25
> **LePeache said:**
> My ifconfig is as below:

leon@leons-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:9b:75:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x6000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480.0 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:a0:af:6f  
          inet addr:10.0.0.13  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fea0:af6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:828746 (818.7 KB)  TX bytes:151721 (151.7 KB)

root@ubuntu:/home/leon# 

I also tried the advice above regarding changing the MTU and Firefox but still have no joy. I have found another problem, even though the router can see the laptop (it has it listed when I go to the routers admin page) I can not load the external drive that the router is connected to. The netbook can connect though.
I am having the same problem. Unable to connect to the network using wireless. If I use a hard wired connection everything is fine, I can ping and be pinged. I noticed that in your ifconfig that you do not have a valid IP address on your wireless. It is my understanding that the IP address should be in area of 192.168.1.xxx for the router to identify your computer.

---

### Post by dineshs on 2010-08-25
If you have problem with wireless please start a new thread with the results of the following commands 
```
sudo lshw -C network
```and
```
iwconfig
```

---

