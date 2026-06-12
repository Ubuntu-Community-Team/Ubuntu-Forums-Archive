---
title: "limited connection to internet"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by Patggf on 2009-04-07
I have a Dell desktop 2400 with a direct wire dhcp ethernet connection to a sky router.
I'm running Ubuntu 8.04. When I start the computer sometimes I have no connection to the internet at other times it will work fine. I've tried reading the Absolute Beginners forumn and tried the following. I hope it helps.


/* first session */
-------------------------------------------------------------------
pat@pat-desktop:~$ sudo ifconfig eth0 down
[sudo] password for pat: 
pat@pat-desktop:~$ sudo ifconfig eth0 up
pat@pat-desktop:~$ ping google.com
ping: unknown host google.com
pat@pat-desktop:~$ ping 4.2.2.1
connect: Network is unreachable
pat@pat-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:54:27:5e  
          inet6 addr: fe80::20f:1fff:fe54:275e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4290 (4.1 KB)  TX bytes:984 (984.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49100 (47.9 KB)  TX bytes:49100 (47.9 KB)
pat@pat-desktop:~$ 
------------------------------------------------------------------------


Then I tried restarting the computer and had no connection either to the web with Firefox or with Synaptic Package manager. Then I tried sudo dhclient and was able to ping and connect with Firefox and Synaptic. I would have posted the dhclient and ping session but I did not know how to turn the ping off and so just closed the terminal window. On restarting the computer again I had no connection. Again typing sudo dhclient and I was able to connect with Firefox and Synaptic.


Any clues about what is happening here. If you need more information please ask. By the way I'm an absolute beginner and need a more or less step by step response with a bit of background as to why I need to try various possible solutions. Thanks in advance.

---

### Post by gui076 on 2009-04-07
Hello,

If you want to cancel a ping command or others type ctrl+C .

For your network problem you should be able with the graphic interface to solve it and put a dhcp on your interface.

your dhcpclient seems to be working because when you type it it works.

For the IP if your router provide a private IP it can be 10.X.X.X or 172.X.X.X or 192.X.X.X.

I think more about a module which is not loading during the start up.

I found on google the default address for a sky router is 192.168.0.1 so you should set or get(if dhcpclient works) an IP in this network.

---

### Post by Patggf on 2009-04-08
Thanks the problem is solved now. The /etc/network/interfaces file was corrupted. What I mean is the 'auto eth0' entry was at the bottom of the file and it should have been before some other code near the top of the file that was concerned with interface.

I used the terminal gksudo to run gedit and edit and save the file. It was a bit tedious sorting out how to edit the file as I needed root privileges. I'm very new to this.

---

### Post by Patggf on 2009-04-09
I thought this problem was solved because I restarted the computer three times and was able to get on the net, but I started the computer today and was unable to connect. In the past the problem has shown up most of the time: about seven times out of ten starts. I thought there was a regularity there. Anyway, below is the contents of my /etc/network/interface file as far as I can see it is already set for dhcp. Are there any other settings I should add? By the way after editing the interface file as described in a previous post I checked the file to see it was as it was when I edited it in case it had become corrupted again, but the contents are as below. I'm just going on hunches really as linux is very new to me.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by gui076 on 2009-04-13
Hi,

Maybe the Network Manager is playing a game with network configuration.
On my machine I just deactivated it. [I just renamed the script file NetworkManager in NetworkManager.old]

---

