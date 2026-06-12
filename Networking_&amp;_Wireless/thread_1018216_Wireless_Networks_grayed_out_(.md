---
title: "Wireless Networks grayed out :("
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by yigalm on 2008-12-21
Hi,

I installed Ubuntu 8.10 on my Windows XP machine. I am trying to connect to the Internet through my wireless router. It is not password-protected. The problem is that "Wireless Networks" is grayed out. Searching Google, I found advice that it may be because my user account doesn't have permission to connect to wireless networks. I found and enabled my user to use wireless networks, but it is still grayed out (on top right). 

What do I do now? :(

P.S. Why isn't the default user given full privileges upon installation anyway?

---

### Post by prshah on 2008-12-21
> **yigalm said:**
> The problem is that "Wireless Networks" is grayed out.

The Wireless networks option is just a heading, it is _supposed_ to be greyed out. Below that you will find listed detected wireless networks and/or options for adding custom (eg, hidden) wireless networks.

If you can't see those, it is likely that your wireless network card is not recognized, or not turned on (usually for notebooks).

In the second case, post back the output to the following terminal (Applications-Accessories-Terminal) commands```
lspci | grep -i -E wireless\|ethernet
iwconfig
sudo lshw -C network
```

---

### Post by yigalm on 2008-12-22
Thanks for the reply. No networks are showing under Wireless Networks. I ran the commands, and the response is below. TIA:popcorn:

yigi@ubuntu:~$ lspci | grep -i -E wireless\|ethernet
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
yigi@ubuntu:~$ 
yigi@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

yigi@ubuntu:~$ 
yigi@ubuntu:~$ sudo lshw -C network
[sudo] password for yigi: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:aa:81:99
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:8d:b3:62
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 2a:9f:5d:7f:f7:b4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
yigi@ubuntu:~$

---

### Post by prshah on 2008-12-22
> **yigalm said:**
> 
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


You're more than half-way there! The good news is that your wireless is recognized and active. Most people have a lot of trouble getting till this point!

If you are still not able to see wireless networks,

a) Check your "wireless kill switch" (ie, a switch that turns wireless on/off), and indicators thereof to see if it is turned on.

b) Turn off the wireless, wait 10 seconds, turn it back on, wait a further 10 seconds, and then check if any wireless networks show up.

c) Give the below command from the terminal to check if any wireless networks are detected```
iwlist wlan0 scan
``` If it detects any networks, check the wireless menu again, and if no networks are listed there, post back the output of the iwlist scan command here for instructions on how to manually (command-line) connect, and further troubleshooting.

---

### Post by yigalm on 2008-12-22
I don't have any switches on this laptop, so wireless is always on. That's how I'm online now with Win XP.

I ran "iwlist wlan0 scan" in Ubuntu, but it didn't find anything, and it's showing no networks under Wireless Networks.:(

P.S. I installed another copy from the same CD on a friend's desktop now, and his wireless is fine on the same network. It did something funny with his startup though.

What do I do now?:confused:

---

### Post by yigalm on 2008-12-22
Can anyone help me get online with Ubuntu? Or is it hopeless?

---

### Post by el generico on 2009-01-25
bump

---

### Post by splatr182 on 2009-03-07
I have spent weeks trying to get the broadcom card to work...
This guide solved it for me: :D
[http://blog.sampbar.com/2009/01/broadcom-bcm4318-ubuntu-intrepid/](http://blog.sampbar.com/2009/01/broadcom-bcm4318-ubuntu-intrepid/)

---

### Post by Forneus on 2009-06-27
> **prshah said:**
> 
a) Check your "wireless kill switch" (ie, a switch that turns wireless on/off), and indicators thereof to see if it is turned on.


](*,):oops: 

Forgot to check this on my laptop.

---

### Post by peppersteak on 2009-08-31
My problem is(was) that i booted Ubuntu with the wireless turned off already(did that in Windows).

Once Ubuntu was running the network was grayed out and no wireless networks were found. Turning on the wireless with the so called "kill switch" did not help.

but after doing the steps below it all works fine.
> a) Check your "wireless kill switch" (ie, a switch that turns wireless on/off), and indicators thereof to see if it is turned on.
 
 b) Turn off the wireless, wait 10 seconds, turn it back on, wait a further 10 seconds, and then check if any wireless networks show up.
So in short, once in Ubuntu i turn on my wireless, turn it off(10secs), turn it on again...network is UP.

Thanks!! although i would like to see that it works after the 1st time i turn it on.

Anyone?....

---

### Post by moodah on 2009-09-03
I have a sneaking suspicion that the list of wireless networks its dropping down is deselecting the networks because your network card firmware does not support WPA and your router is set to WPA-PSK authentication? This is just a guess..

Try changing it to WEP and see what happens after a rescan....

---

### Post by DEVMRS on 2010-04-14
I had the exact same problem. Wireless Network enable was grayed out. I looked on my Dell notebook and noticed that above the F2 key was a wireless antenna symbol. I pressed the Fn key and F2 and wireless came to life. I'm now able to unplug the ethernet connection and rely on the wireless connection.

---

### Post by shagen on 2010-04-28
My dell Inspiron mini is running ubutu 8.4 . it finds my home wireless network, but when I try to setup a new mobile broadband network by tethering my samsung blackjack the new network does not show in my list of available networks.

---

### Post by elasticsoul on 2010-07-23
Looks like [http://blog.sampbar.com/2009/01/broa...untu-intrepid/]("http://blog.sampbar.com/2009/01/broadcom-bcm4318-ubuntu-intrepid/") is no longer online. 
 
I have the problem where I can see the network I want to connect to, but it is grayed out.

---

### Post by xtrakt on 2010-07-27
> **elasticsoul said:**
> Looks like [http://blog.sampbar.com/2009/01/broa...untu-intrepid/]("http://blog.sampbar.com/2009/01/broadcom-bcm4318-ubuntu-intrepid/") is no longer online. 
 
I have the problem where I can see the network I want to connect to, but it is grayed out.

Me too. I installed the driver with ndiswrapper. I can see the two networks I'm supposed to see, but they are both greyed out.

---

### Post by Cloud_704 on 2010-10-31
*bump*

My guess is that the issue has something to do with the Network Manager applet itself -- all the troubleshooting procedures I read about indicate that everything should work fine. And yet, the "grayed out" problem.

---

### Post by sharo on 2011-06-11
[SIZE=3]@[prshah]("http://ubuntuforums.org/member.php?u=394709")  and yiglam
okay i love ubuntu 11.04 the problem i have it has caused me a bit of an headache. 

first of all i run a athero ar5007 win 7 ultimate and when i start up the win. wifi doesn't start automatically. bios has exclamation next to it

second in ubuntu my wireless networks are grayed out and my kill button is on it has blue light and its saying its on. i cant even turn it off no matter how long i hold it and it still has wireless networks grayed out so i am pretty sure you've got that similar problem.  

searching for fix will help when i find an answer to it my self [/SIZE]

________________________________________________________________________________________
[SIZE=4]ON Great Ubuntu path8-):-({|=:-({|=:-({|=:-({|=[/SIZE]

---

