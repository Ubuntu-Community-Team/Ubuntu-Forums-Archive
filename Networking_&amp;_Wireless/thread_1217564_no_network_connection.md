---
title: "no network connection"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by bearcreek10 on 2009-07-19
Just installed 9.04 and cant connect to internet. I am completely new to Ubuntu, so bear with me. I believe  I am missing the driver for the network adapter because when I get no devise found when I run different commands in the terminal window. How do I fix this. I am using lan, not wireless. Thanks for any replies.

---

### Post by philcamlin on 2009-07-19
what internet card do you have? 8)

---

### Post by bearcreek10 on 2009-07-19
Dont know, it is on a computer that was given to me, just wanted to try out Ubuntu. No name on the computer, it may be built. The mother board is Foxconn, I believe. The number on the board is E210882. The ethernet card is on the motherboard. If you have any suggestions, please go step by step as I know nothing about linux. Thank you for the fast reply.

---

### Post by bearcreek10 on 2009-07-19
The command I put into the terminal was ifconfig ethl.
Response was : error fetching interface information : Device not found

---

### Post by dlmarti on 2009-07-19
run "lspci" from the command line and post the relevant lines here (the ones about the ethernet card).

---

### Post by ugm6hr on 2009-07-19
Give output from:
```
lspci
lshw -class network
```

---

### Post by ghettocounsler on 2009-07-19
sorry wrong thread. :(

---

### Post by Whiffle on 2009-07-19
Looks like its detected and given an interface, what is the output of:


ifconfig eth1

---

### Post by ghettocounsler on 2009-07-19
sorry wrong thread :(

---

### Post by dlmarti on 2009-07-19
my guess would be their is no DHCP server on your network and you didn't setup a static IP.

What steps have you done to get networking up and running?

Your network card is detected, its just waiting for an IP address.

---

### Post by bearcreek10 on 2009-07-20
What do I need to do, everything worked when it had windows on it. So, what is my next step? I really dont want to use a static IP. 
 
Thanks for all the responses.

---

### Post by dlmarti on 2009-07-20
> **bearcreek10 said:**
> What do I need to do, everything worked when it had windows on it. So, what is my next step? I really dont want to use a static IP. 
 
Thanks for all the responses.

You still need to answer this post: [http://ubuntuforums.org/showpost.php?p=7643121&postcount=6](http://ubuntuforums.org/showpost.php?p=7643121&postcount=6) for us to continue.

---

### Post by ugm6hr on 2009-07-20
You haven't replied to my request for information.

That is your next step.

EDIT: too slow - see above.

---

### Post by bearcreek10 on 2009-07-20
Sorry about that. Just ran the scripts, but I do not know how to put them on a windows computer. I have a flash drive, how do I transfer it or what format do I need?

---

### Post by dlmarti on 2009-07-20
Flash drives normally come preformatted with FAT32, or some such, Ubuntu will automatically recognize it when you plug it in.  Once plugged in it appears on your desktop similar to other OS's.

Under Linux you can "pipe" to output of programs to a file.

For example:
1. open a console window (applications->accesories->terminal).
2. change your current directory to your desktop "cd Desktop"
3. type "lspci > lspci.txt"
4. type "sudo lshw -class network > lshw.txt"
[FONT=monospace]5. drag and drop the lspci.txt file to the usb dongle
6. drag and drop the lshw.txt file to the usb dongle.
7. right click the usb dongle and select "unmount"
8. unplug the dongle

I might have missed a step, but you get the idea I hope.
[/FONT]

---

### Post by bearcreek10 on 2009-07-20
Sorry for the dumb questions, I am super new to Linux.

Here is what I got for the lspci:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)



Here is the lshw:

*-network

       description: Ethernet interface

       product: 82562EZ 10/100 Ethernet Controller

       vendor: Intel Corporation

       physical id: 8

       bus info: pci@0000:01:08.0

       logical name: eth0

       version: 01

       serial: 00:11:11:2f:aa:22

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A 
latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 2a:93:a0:07:40:dd

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by dlmarti on 2009-07-20
> **bearcreek10 said:**
> Sorry for the dumb questions, I am super new to Linux.


I don't consider a question that you don't know the answer too dumb.  Better to ask.

> **bearcreek10 said:**
> 
Here is what I got for the lspci:
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)


I've never used this chip, but everything I see says this is 100% supported without problems.

> **bearcreek10 said:**
> 
Here is the lshw:
*-network
description: Ethernet interface
product: 82562EZ 10/100 Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:01:08.0
logical name: eth0
version: 01
serial: 00:11:11:2f:aa:22
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A 
latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 2a:93:a0:07:40:dd
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I don't have a lot of experience with  lshw, I'm a little concerned about the line that says "*-network DISABLED" not sure what that means  :)

I know you said that "ifconfig eth1" didn't work for you, but what is the output of "ifconfig"???  My guess is the chip is working and we just need to configure it.

---

### Post by dlmarti on 2009-07-20
Also not that this chip is supposedly supported by Intel also [FONT=Arial][SIZE=2]"linux.nics@intel.com".

Not sure how good their support is, you might be better sticking with us.
[/SIZE][/FONT]

---

### Post by bearcreek10 on 2009-07-20
ifconfig yields:

eth0      Link encap:Ethernet  HWaddr 00:11:11:2f:aa:22  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
 
         inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:40 errors:0 dropped:0 overruns:0 frame:0

          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:3184 (3.1 KB)  TX bytes:3184 (3.1 KB)



ifconfig eth1 yields:

ethf1: error fetching interface information: Device Not Found

---

### Post by dlmarti on 2009-07-20
> **bearcreek10 said:**
> 
ifconfig eth1 yields:

ethf1: error fetching interface information: Device Not Found

Thats because you don't have an eth1, when you used the gui tool did you specify eth0 or eth1?

---

### Post by bearcreek10 on 2009-07-20
ifconfig eth0 yields:

eth0      Link encap:Ethernet  HWaddr 00:11:11:2f:aa:22  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by dlmarti on 2009-07-20
This means your network card is working and ready, you just need to configure it.
Go to system->Preferences->network connections and setup the card.

---

### Post by bearcreek10 on 2009-07-20
Thank you for all of you help. I have been there and not sure what to do. I tried alot of the settings, and no go. I am using a router/modem from verizon.
It also says "never" at the end of the row on Auth0.

---

### Post by dlmarti on 2009-07-20
> **bearcreek10 said:**
> Thank you for all of you help. I have been there and not sure what to do. I tried alot of the settings, and no go. I am using a router/modem from verizon.
It also says "never" at the end of the row on Auth0.

Don't give up, a couple more posts is all we need to get this fixed.

This is what my network setup looks like:
[IMG]http://www.terabytecode.com/stuff/network.png[/IMG]

You need to find out what your network parameters are, and enter in your stuff.

---

### Post by bearcreek10 on 2009-07-20
Do I have to use a static IP? Using a static IP dont I have to set up the router for that. My router has new firmware on it from verizon and they made it very difficult to navigate.

---

### Post by dlmarti on 2009-07-21
I use a static IP, but you can use a dynamic one if that is what you want.
I was just indicating that you could do this for a test.

---

### Post by bearcreek10 on 2009-07-21
I tried using the static, but it didnt work. I think you have to set the router for static and dhcp, and I am unsure on how to do this because I just got this modem/router. It is branded with verizon firmware and they did there best to keep you from changing anything (not very user friendly). I would use static but I have alot of different things to come and go on my network and I do not want to have to set up a static ip address everytime. Lazy?, yes. But it cuts down on the issues if the router assigns an address. 
 
Sorry for the rambling, so do I need to choose dhcp instead of manual? I have done this with no success. Maybe I am entering the wrong numbers?
 
 
Side note: I called them to see how to port forward because I could not find it in the gui of the router. I was told that I had to pay an extra monthly fee to be able to do this! Unbelievable!

---

### Post by dlmarti on 2009-07-21
try this:
1. "sudo -s"  + password
2. "/etc/init.d/networking stop
3. "ifconfig"  Make sure that eth0 does not have an ip address assigned to it, if it does type "ifconfig eth0 down.
4. "dhclient eth0"  (record the output of this)

5. check your networking and see if its working, if not send me the output of the dhclient program.

I'll be a away for a little bit, but I will continue to debug with you later on.

---

### Post by bearcreek10 on 2009-07-21
Thank you, I am at work, so I will not be able to try this until later.

---

### Post by dlmarti on 2009-07-21
> **bearcreek10 said:**
> Thank you, I am at work, so I will not be able to try this until later.

lol, so am I.
Damn work getting in the way!

---

### Post by toudai on 2009-07-21
I am having kind of same problems with my computer (HP Vectra) which with the Network Manager at first did not find any ethernet connection. 

By using ifconfig I found out macaddress and by checking my other laptop (which is using Windows vista) I got info of gateway and mask settings. I made new connection in Network Manager - manual settings but was not sure what ip address to use. Anyway, the ethernet connection (eth0) is getting connected now and when I check the connection with network tools, I can see TX packages are being sent but RX packages getting errors. Still can not use the internet..

I am not really sure what to change further as I also tried dual boot with my other laptop using Ubuntu and there it works straight out of the box without changing any settings so I guess this is not a problem with the router.

Any help very much appreciated.

---

### Post by dlmarti on 2009-07-21
> **toudai said:**
> I am having kind of same problems with my computer (HP Vectra) which with the Network Manager at first did not find any ethernet connection. 

By using ifconfig I found out macaddress and by checking my other laptop (which is using Windows vista) I got info of gateway and mask settings. I made new connection in Network Manager - manual settings but was not sure what ip address to use. Anyway, the ethernet connection (eth0) is getting connected now and when I check the connection with network tools, I can see TX packages are being sent but RX packages getting errors. Still can not use the internet..

I am not really sure what to change further as I also tried dual boot with my other laptop using Ubuntu and there it works straight out of the box without changing any settings so I guess this is not a problem with the router.

Any help very much appreciated.

You need to create a new thread, it sounds like your issue is different.

---

### Post by toudai on 2009-07-21
I dont know what criteria you use to say that this is a different problem. Reading this post I think that I am just one step further with this by manually entering a configuration for eth0.

Anyway, I will create a new post and hopefully will get some more positive feedback ...

---

### Post by dlmarti on 2009-07-21
> **toudai said:**
> I dont know what criteria you use to say that this is a different problem. Reading this post I think that I am just one step further with this by manually entering a configuration for eth0.

Anyway, I will create a new post and hopefully will get some more positive feedback ...

because your see RX errors, its a different problem.

---

### Post by bearcreek10 on 2009-07-22
Here are the results of everything:

root@bill-desktop:~# /etc/init.d/networking stop

 * Deconfiguring network interfaces...                                   [ OK ] 

root@bill-desktop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:xxxxxxxxxxxx  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:0 


          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


root@bill-desktop:~# ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:xxxxxxxxxxxxxxx  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


root@bill-desktop:~# ifconfig eth0 down

root@bill-desktop:~# dhclient eth0

Internet Systems Consortium DHCP Client V3.1.1

Copyright 2004-2008 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/eth0/00:xxxxxxxxxxxxxxx
Sending on   LPF/eth0/00:xxxxxxxxxxxxxxx
Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12

No DHCPOFFERS received.

No working leases in persistent database - sleeping.
root@bill-desktop:~#

---

### Post by dlmarti on 2009-07-22
> **bearcreek10 said:**
> 
No DHCPOFFERS received.

This is saying you don't have a DHCP server on your network, does that sound right?
Its pretty rare now-a-days to not have one.  I've even seen them on networks where they are never even used.

---

### Post by bearcreek10 on 2009-07-22
I am confused. When I hook up something new, computer or xbox, it automatically gets and ip from the router. If it is not seeing a dhcp server it is because there is no connection, true? Everything works fine, I can use this computer to tap into my xbox with no issues threw the router.

---

### Post by bearcreek10 on 2009-07-22
Just got off the phone with verizon's marvelous non-english speaking tech. After 2 minutes of I cant hear or understand you, I asked if verizon had something in the firmware that would keep Ubuntu from connecting to the internet. After another 2 minutes of do you know what Ubuntu is, I finally got the response of "it is an operating system, which we do not have support for".  I then asked why does the automated system ask if I am running an alt. operating system and then send me here if you do not support it? She replied, " We do not have support for linux", after every question I asked.  I finally asked is the router/modem compatible with linux, she said she would check. When she came back on she said, no it is not, only windows xp and vista are supported. Could this be true?

If this is true, could this be an intentional block? I would have to believe so due to the hackability of linux.

Sorry for the ramblings, I am just angry from the phone conversation with verizon.

---

### Post by bearcreek10 on 2009-07-22
Well I should not post this because this is the most embarrassing thing ever and you are going to hate me for all the trouble I caused you. It was the ethernet cord. I got thinking, what if the ethernet cord was bad, so I plugged in one that I knew worked and that fixed it. That is not the worst part. I went to the router and looked, I ran the ethernet cord but forgot to plug it in or it fell out somehow. That deserses a big fat DOH!


Sorry about that, if you are going to be dumb, you may as well be good and dumb. It is always the dumbest thing you never think of. At least I learned alittle about the terminal box and that VERIZON LIES!!!!!!

Thank you for all of your help and time. I am sure I will be back with more dumb questions, and when I do start with the easiest, dumbest, thing I could have missed.

Thanks

---

### Post by dlmarti on 2009-07-22
> **bearcreek10 said:**
> Just got off the phone with verizon's marvelous non-english speaking tech. After 2 minutes of I cant hear or understand you, I asked if verizon had something in the firmware that would keep Ubuntu from connecting to the internet. After another 2 minutes of do you know what Ubuntu is, I finally got the response of "it is an operating system, which we do not have support for".  I then asked why does the automated system ask if I am running an alt. operating system and then send me here if you do not support it? She replied, " We do not have support for linux", after every question I asked.  I finally asked is the router/modem compatible with linux, she said she would check. When she came back on she said, no it is not, only windows xp and vista are supported. Could this be true?

If this is true, could this be an intentional block? I would have to believe so due to the hackability of linux.

Sorry for the ramblings, I am just angry from the phone conversation with verizon.

Ignore Verizon, they are completely clueless.  I know lots of people using Linux on the Verizon FIOS system.  In fact I set one of them up last week.

Its not the router, its something else we are missing.
This is what I don't understand:
> root@bill-desktop:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:mad:xxxxxxxxxxxxxx  
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Why is the MAC address all zeros?

I have a development system that I will test on tomorrow, and see if I can recreate this.

---

### Post by dlmarti on 2009-07-22
> **bearcreek10 said:**
> Well I should not post this because this is the most embarrassing thing ever and you are going to hate me for all the trouble I caused you. It was the ethernet cord. I got thinking, what if the ethernet cord was bad, so I plugged in one that I knew worked and that fixed it. That is not the worst part. I went to the router and looked, I ran the ethernet cord but forgot to plug it in or it fell out somehow. That deserses a big fat DOH!


Sorry about that, if you are going to be dumb, you may as well be good and dumb. It is always the dumbest thing you never think of. At least I learned alittle about the terminal box and that VERIZON LIES!!!!!!

Thank you for all of your help and time. I am sure I will be back with more dumb questions, and when I do start with the easiest, dumbest, thing I could have missed.

Thanks

lol, no problem.
Good luck on Ubuntu, you'll like it.

---

