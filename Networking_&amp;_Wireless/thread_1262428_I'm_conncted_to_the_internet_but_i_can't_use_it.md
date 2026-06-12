---
title: "I'm conncted to the internet but i can't use it ??"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by NawafLol on 2009-09-09
Hey i'm having a problem with my internet connection !

i have installed ubuntu 9.04 for about one week and the internet was ok
nothing was wrong

i'm using a Acer Aspire 5738 G

but for some reason  i can't connect :confused:  ... can't surf can't login to my msn nothing .... it just my ubuntu my windows XP is working great surfing and all !

by the way i'm using LAN and wireless ... tried to restart didn't help 

i'm using speedtouch router 

Please can any one help me :)

and thanks !

P.S : Sorry for my Bad English

---

### Post by RedSingularity on 2009-09-09
Type this in terminal

ping -c 5 [www.google.com](www.google.com)

And post the output.

---

### Post by NawafLol on 2009-09-10
its says : ping :unknown host [www.google.com](www.google.com) 

and i typed /etc/resolv.conf
and it said : bash : /etc/resolv.conf

and thanks :)

---

### Post by RedSingularity on 2009-09-10
Post the output of 

lspci

---

### Post by NawafLol on 2009-09-10
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 06ec (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
 i hope that helps :)

---

### Post by RedSingularity on 2009-09-10
So what happened when you go to the network manager?  Do you see any networks at all?  

And look in System>admin>Hardware drivers to see if there is a driver to activate for WiFi.

---

### Post by NawafLol on 2009-09-10
no there's nothing .... i only say my Nvidia graphics card

can i like reinstall my ubuntu without losing data or do like a backup ??

i have a full bar signal with my wireless but can't use the internet
 
this happened after i left it overnight downloading some apps

---

### Post by RedSingularity on 2009-09-10
If you do 

sudo apt-get update

Does it update or no?

---

### Post by RedSingularity on 2009-09-10
It sounds to me like a problem with Network Manager configuration.  Look into WICD.  I have found that solves many other problems similar to your own.  And its a very nice easy to use interface.  

If you want you could remove network manager and reinstall it.  I think you would be fine with WICD though.

---

### Post by NawafLol on 2009-09-10
sudo apt-get update didn't work !

and how can i get the the WICD 

thanks i feel like rather a noob :)

---

### Post by NawafLol on 2009-09-11
i tried sudo apt-get install wicd didn't work !

---

### Post by cariboo on 2009-09-11
If networking doesn't work, you're not going to be able to download anything.

Try this right clcik on the network-manager icon and select edit connection. Highlight wlan0, or whatever your wireless device is, then click edit. 

Click the IPv4 Settings tab, next click the Method dropdown and select Automatic (DHCP) adresses only. 

Finally in DNS servers enter 208.67.222.222 and click Apply, next click Close. Now try and connect.

---

### Post by NawafLol on 2009-09-11
i know that ... and i tried the DNS Server didn't work i even tried 208.67.220.220 ... this is weird ... i feel hopeless

maybe i'm missing something

---

### Post by megamania on 2009-09-11
> **NawafLol said:**
> i know that ... and i tried the DNS Server didn't work i even tried 208.67.220.220 ... this is weird ... i feel hopeless

maybe i'm missing something
Try connecting the computer to a wired network, then install Wicd (which will in turn uninstall Network Manager). 

That could solve your problems (it solved the same problem with Karmic for me).

---

### Post by NawafLol on 2009-09-11
Nope couldn't connect to the internet same problem full signal bar but i can't use the internet 

i'm using my windows working great but ubuntu nothing

---

### Post by NawafLol on 2009-09-11
my ifconfg -a is :

eth0      Link encap:Ethernet  HWaddr 00:1d:72:fb:1c:50  
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
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr de:45:d1:42:f9:21  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:d0:39:4a  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fed0:394a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2301 (2.3 KB)  TX bytes:1921 (1.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-6B-D0-39-4A-39-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

i hope this helps !

or i have to Reinstall My Ubuntu

---

### Post by NawafLol on 2009-09-11
did anyone figure it out ??

please guys

---

### Post by RedSingularity on 2009-09-11
[Here]("http://sourceforge.net/projects/wicd/files/wicd-stable/wicd-1.5.9/wicd_1.5.9_all.deb/download") is a .deb of wicd.  Put it on a stick and bring it to your ubuntu computer.  It will install very easy.  If you cant install due to conflicts with Network-Manager do a 

sudo apt-get autoremove --purge network-manager-gnome

and try again.

---

### Post by NawafLol on 2009-09-11
i removed network manager as you said 

but it still says conflict with the installed package "network-manager"

thanks really thanks but can you help in this one :)

---

### Post by RedSingularity on 2009-09-11
sudo apt-get autoremove network-manager

---

### Post by NawafLol on 2009-09-11
got Wicd Up and running restarted my ubuntu but its all fail

connected but with no internet !

can you ask someone who had this problem

maybe its my wicd configuration

---

### Post by RedSingularity on 2009-09-11
Enter this then....

sudo dhclient wlan0 (or **eth0** if you are wired at the moment)

Post output

---

### Post by NawafLol on 2009-09-11
here we go :

There is already a pid file /var/run/dhclient.pid with pid 4087
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
parse_option_param: Bad format a
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:6b:d0:39:4a
Sending on   LPF/wlan0/00:21:6b:d0:39:4a
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.67 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.67 from 192.168.1.254
bound to 192.168.1.67 -- renewal in 37014 seconds.

---

### Post by RedSingularity on 2009-09-11
Go to system>Preferences>Network Proxy.  Make sure it is "direct Internet connection."

---

### Post by NawafLol on 2009-09-11
It Is !

---

### Post by RedSingularity on 2009-09-11
Ummmm..........have you tried to restart the router at all?  I mean a full reset not just turning it off.

---

### Post by NawafLol on 2009-09-11
I will try that in come back to you !

---

### Post by NawafLol on 2009-09-12
Nothing !

---

### Post by RedSingularity on 2009-09-12
How about in firefox.  Preferences>Advanced>Network Tab>Settings.  Make sure you have No Proxy in use.

---

### Post by NawafLol on 2009-09-12
it says "use system proxy settings"

this is getting rather boring is it hahah

---

### Post by RedSingularity on 2009-09-12
Not boring at all, I am just running out of ideas.  :(

Did you try turning the proxy off completely?

---

### Post by RedSingularity on 2009-09-12
Ping your router to make sure we are fully connected.  

ping -c 5 192.168.1.1

---

### Post by inspired on 2009-09-12
Hi there,
I just want to chip in here and say that I may well be experiencing the same thing, and it may have started happening around the same time. Did you run any updates in the past week?

I have a thread here: [http://ubuntuforums.org/showthread.php?t=1263995](http://ubuntuforums.org/showthread.php?t=1263995)
But in a nutshell... I connect to my Wifi (or wired, makes no difference) and the connection happens just fine. BUT I can't ping nor access anything on the internet. I also can't ping the router (I can from other computers on the network). Basically domain name resolution has bombed out. If I set up IP / domain name pairs in the /etc/hosts file then I can connect to those sites. So the connection to the net is there... just no resolution. I can also ping IP addresses on the internet... just not the IP of my router, nor the domain names of any sites (unless I have them in the hosts file).

Are you able to ping IP addresses on the internet?
Try to ping 70.109.235.96 for instance. Or 216.239.51.99 (a Google IP). Does that work?

Based on the info in this thread I have removed network-manager and network-manager-gnome, and I have installed wicd. I like the wicd interface. Sadly, it does not fix the situation. It connects and has the same issue.

I am keen to determine if we have exactly the same issue. Seems slight coincidental that we both started to experience this at about the same time.

Regards,
Jonathan

---

### Post by NawafLol on 2009-09-13
Shadow it came out like that:

Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination

inspired :

i don't really know as i said i left it over night downloading some stuff and my bit torrent working :)

i really hope we figure this out cause i miss using my internet in ubuntu

---

### Post by RedSingularity on 2009-09-13
You typed in an invalid option for the ping command.  Make sure it looks like this exactly:

ping -c 5 192.168.1.1

---

### Post by NawafLol on 2009-09-13
here you go 

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4000ms

---

### Post by RedSingularity on 2009-09-13
192.168.1.1 is your router, the packet losses mean they are not reaching their destination.  It would seem you are not "fully" connected to the access point even though it is showing you are.  

And just to confirm, you said you have tried to plug an Ethernet cord in?

---

### Post by NawafLol on 2009-09-13
Yes !

so how can i fix this

---

### Post by RedSingularity on 2009-09-13
It sounds like a bug that inspired mentioned.  It may have come with an update.  Unfortunately i think you will have to do a reinstall.  Have you contacted anyone in IRC chat about this?  They may be able to offer a few more suggestions that i cant think of.  You can also file a bug report on Launchpad.

---

### Post by inspired on 2009-09-13
> **NawafLol said:**
> 
inspired :

i don't really know as i said i left it over night downloading some stuff and my bit torrent working :)

i really hope we figure this out cause i miss using my internet in ubuntu
Well... how do you do your updates? Manually with Synaptic or Update Manager, or automatically with Update Manager?
If you use Synaptic then there will be a record of any recent updates in the History log, found in the File menu (first on the left... might be called something else) in Synaptic.
If you use Update Manager that too might have a log of updates. Can't check just now... please take a look. It would be helpful if we manage to pin this down to a cause.

I have now tried using mine on another network. Same scenario. It seems to connect... receives an IP, etc., but no access to the router or internet... do domain name resolution.

Yes, it would be nice to sort this out!!

---

### Post by inspired on 2009-09-13
I have posted a bug report here:
[https://bugs.launchpad.net/bugs/429128](https://bugs.launchpad.net/bugs/429128)

---

### Post by HalfCrackedTech on 2009-09-13
I am having the same issues.  hope all this helps thank you!!

---

### Post by RedSingularity on 2009-09-13
Well it would seem this is becoming a popular problem.

---

### Post by inspired on 2009-09-13
> **HalfCrackedTech said:**
> I am having the same issues.  hope all this helps thank you!!
Hi there,
Thanks for saying so.
Have you run any updates (automatically or manually) in the past week or so?

Regards,
Jonathan

---

### Post by NawafLol on 2009-09-13
i updated tow days before i lost my connection so i don't think that was it :)

i tried to make a new user ... that was pointless !

so have any ideas guys .... that ubuntu install cd looks so good :P

hope we fix this fast !

---

### Post by zman58 on 2009-09-13
> **NawafLol said:**
> i updated tow days before i lost my connection so i don't think that was it :)

i tried to make a new user ... that was pointless !

so have any ideas guys .... that ubuntu install cd looks so good :P

hope we fix this fast !

Can you use the wire connection on your Router? Will that work?

---

### Post by HalfCrackedTech on 2009-09-14
Have you added any new apps?

Cause I did I added a ndis wrapper app and then I removed it trying to figure out what it was and then I got my Internet back.

---

### Post by NawafLol on 2009-09-14
tried using a wire didn't work .... i even tried wireless usb !

and it would be weird if an app causing my internet to go off but i will try

---

### Post by inspired on 2009-09-14
> **NawafLol said:**
> i updated tow days before i lost my connection so i don't think that was it :)

I did too. I didn't update everything that had updates available though... just a few things. I shall post a list of those apps here. Would you take a look through your update history log and see if any of those apps are some that you updated?

I don't have my laptop with my just now (it's not much use when I can't get on the internet with it!!) so I will post the list soon.

---

### Post by inspired on 2009-09-14
> **HalfCrackedTech said:**
> Have you added any new apps?

Cause I did I added a ndis wrapper app and then I removed it trying to figure out what it was and then I got my Internet back.

I updated a few apps, but didn't install anything new. I am wishing it was that simple! I've happily remove any app to get my networking back.

---

### Post by inspired on 2009-09-14
> **zman58 said:**
> Can you use the wire connection on your Router? Will that work?
This issue affects all network connections, as far as I can tell. Wired, wifi, whatever.
It also does not appear to be network-manager specific, as I have completely removed that and installed wicd in place of it. Issues still exists.

---

### Post by RedSingularity on 2009-09-14
Did anyone file a bug report on launchpad?

---

### Post by NawafLol on 2009-09-14
i removed some apps ! 

still nothing tried to make a static ip no go ... Open DNS didn't work ...... getting rather hopeless

---

### Post by NawafLol on 2009-09-14
did anyone file a bug report ... i don't know and my English is bad enough !

---

### Post by inspired on 2009-09-14
> **Shadow121 said:**
> Did anyone file a bug report on launchpad?

Sure did. Refer to:
[http://ubuntuforums.org/showthread.php?t=1262428&page=5&p=7944811](http://ubuntuforums.org/showthread.php?t=1262428&page=5&p=7944811)

---

### Post by inspired on 2009-09-14
As promised, here is a list of the updates I have done in the past week:

> Commit Log for Tue Sep  8 20:12:54 2009
Upgraded the following packages:
autokey (0.60.4-0~jaunty) to 0.60.5-0~jaunty
sip-communicator (1.0-alpha3-nightly.build.2008) to 1.0-alpha3-nightly.build.2023
ttf-opensymbol (1:3.1.0-5ubuntu1~jaunty1) to 1:3.1.1-1ubuntu1~jaunty1
wine (1.1.28~winehq0~ubuntu~9.04-0ubuntu1) to 1.1.29~winehq0~ubuntu~9.04-0ubuntu2

It is possible that when this issue arose, it was the first time I had rebooted and connected to a network... so it is possible (not sure how likely though) that this issue arose as a result of these updates. I can't see anything in there, though, that I can imagine would overly mess with my network configuration.

UPDATE: As of today I can now access websites via my browser. I had been adding to my hosts file the IPs of the sites (such as this forum, and launchpad) I needed to access for resolving this bug. So I have been able to access those sites. But today I discovered I can now access any site.
I still can't ping anything that's not in the hosts file, nor can evolution access any mail servers I don't have in the hosts file, such as the imap.gmail.com server, which changes IP constantly, so I've not added it to the hosts file.

---

### Post by tony_wh on 2009-12-27
I know this thread is a bit old but I've had exactly the same problem.  I was visiting relatives an trying to hook to their router (which I had done before but on Jaunty not Karmic) via DHCP.  Interestingly, I could use Skype without problem but either browser (firefox or opera) would fail at the look up website as did apt-get.  Using IP addresses also failed.  I could ping my own IP address and 127.0.0.1 but not that assigned as the DNS gateway, nor the routers own assigned setup page.

The solution was on page two of this thread post #12.  I set the network to 'Automatic DHCP (addresses only)' and put 208.67.222.222 as the DNS server (I'm going to experiment with openDNS IP next).  It works. I am most grateful to cariboo907 - I know little of what this did but am thankful that it got things going.

---

### Post by inspired on 2010-01-06
> **tony_wh said:**
> I know this thread is a bit old but I've had exactly the same problem.  I was visiting relatives an trying to hook to their router (which I had done before but on Jaunty not Karmic) via DHCP.  Interestingly, I could use Skype without problem but either browser (firefox or opera) would fail at the look up website as did apt-get.  Using IP addresses also failed.  I could ping my own IP address and 127.0.0.1 but not that assigned as the DNS gateway, nor the routers own assigned setup page.

The solution was on page two of this thread post #12.  I set the network to 'Automatic DHCP (addresses only)' and put 208.67.222.222 as the DNS server (I'm going to experiment with openDNS IP next).  It works. I am most grateful to cariboo907 - I know little of what this did but am thankful that it got things going.

As far as I can tell it is mostly a DNS issue. The connection is made but no domain name resolution takes place. It's as if the DNS server IPs are not established after the connection is made. I have checked the file where these DNS settings are set each time a connection is made and the details are there. But they don't resolve through to an IP.
Adding the OpenDNS server IPs seems to work.
Not always though. I also find this issue has another side to it, on my machine at least. I will be connected but domain name resolution will die at some point and I have to disconnect and connect again. This happens on many different routers I connect to in my travels... so it is not router specific.
Services like Skype are not affected because they connect directly to an IP address, thus are not reliant on DNS servers.

**UPDATE**: When access to the net is lost after having had successful access (actually, domain resolution is lost), as mentioned above, it too is a DNS issue. I can ping IPs but not domain names. They don't resolve. Disconnecting and reconnecting fixes this, for a while. Often it fixes itself. I just have to hit refresh a few times on the browser and it might start working again,,, but it appears to get progressively worse, until reconnecting becomes necessary.

---

