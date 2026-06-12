---
title: "Ubuntu 10.04 LTS disconnected"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by ferrion on 2012-02-07
My Laptop is Asus F81Se and I install twin OS(Ubuntu 10.04 LTS/Windows XP).

When I log in XP OS, I can surf website. But while logging into Ubuntu, I cannot surf website.

My laptop connect to internet through a router, and the gateway IP is 192.168.1.1. While logging into XP, anything is OK. But when logging into Ubuntu, I cannot ping 192.168.1.1.

I doubt that The laptop is not assigned an IP by DHCP. Or this network access provided is not supported by DHCP? I consult ISP(internet service Provider) and the service engineer of ISP answered they cannot sure that it is supported by DHCP, maybe is supported by another protocol similar to DHCP.

However, why when logging into Windows XP, anything is OK?

Any help will be greatly appreciated!

---

### Post by ibrahimtawbe on 2012-02-07
did you checked the ip address assigned to your card 
```
iwconfig
``` if it's wireless or ```
ifconfig
``` if wired 
what's is the inet address you're getting for the interface ?

---

### Post by ferrion on 2012-02-15
My laptop access internet by wire, and I am a newbie at Linux. Thanks.
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:57:3a:96  
          inet addr:192.168.1.102  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe57:3a96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:34 dropped:0 overruns:0 frame:34
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58784 (58.7 KB)  TX bytes:20546 (20.5 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```

---

### Post by Iowan on 2012-02-15
Please add (post) results of **route -n**. 
You can also check contents of */etc/resolv.conf*. 
Have you tried connecting (or pinging) by IP address?

---

### Post by ferrion on 2012-02-16
Hi,

My laptop access internet by a wire connection, and I can ping 192.168.1.1.

```
$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.176 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.169 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.160 ms

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

The /etc/network/interfaces is as follows:
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```

The /etc/resolv.conf is as follows:
```
nameserver 192.168.2.2
nameserver 192.168.4.4
```

Thanks for your effort.

---

### Post by ibrahimtawbe on 2012-02-16
```
RX packets:140 errors:34 dropped:0 overruns:0 frame:34
TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
```[FONT=monospace]

This may be because the auto-negotiation failed and the card is running half-duplex 

check out this page and report back the results 
[http://www.johnnypez.com/linux/ifconfig-eth0-shows-packet-errors/](http://www.johnnypez.com/linux/ifconfig-eth0-shows-packet-errors/)
[/FONT]

---

### Post by Iowan on 2012-02-16
The nameserver list looks a li'l curious, but I don't know how your network is set up. Can you ping 74.125.225.110 (google.com) or 8.8.8.8?

---

### Post by ferrion on 2012-03-16
Hi Iowan,

It seems that my laptop cannot ping.

```
$ ping 74,125,225,110
ping: unknown host 74,125,225,110
$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=45 time=36.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=45 time=36.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=45 time=36.7 ms
```

---

### Post by ferrion on 2012-03-16
Hi ibrahimtawbe,

I have surfed the website you told me and noticed that I need to install ethtool. But I cannot install it online by ```
sudo apt-get install ethtool
```

because my networking is not working(We are resolving this problem).

I logged into Windows XP and downloaded ethtool-2.6.37.tar.gz from [http://linux.softpedia.com/get/System/Networking/ethtool-14252.shtml](http://linux.softpedia.com/get/System/Networking/ethtool-14252.shtml) 

However, I have no idea how to install it coz I am a newbie at ubuntu/Linux and cannot find any information by googling "how to install ethtool". 

I logged into Windows XP and extracted ethtool-2.6.37.tar.gz to ethtool-2.6.37. Then logging into Ubuntu, copy the extracted ethtool-2.6.37 to /tmp
```

cd /tmp/ethtool-2.6.37
./configure
sudo ethtool eth0

```

I got the following output:

```

sudo: ethtool: command not found

```


Would you please tell me how to install ethtool in detail? 
Thanks in advance.

---

### Post by ferrion on 2012-03-16
I knew how to install ethtool. After executing ./configure, I still have something to do. The following is what I should do:
```

./configure
make
sudo make install

```

After run ethtool command, I got the following output:
```

/tmp/ethtool-2.6.37$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000037 (55)
			       drv probe link ifdown ifup
	Link detected: yes

```

```

/tmp/ethtool-2.6.37$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok

```

I still cannot surf websites:(
I need help. Thanks

---

### Post by varunendra on 2012-03-16
I hope Iowan won't mind if, while he comes back, I answer what he would have answered.
> **ferrion said:**
> Hi Iowan,

It seems that my laptop cannot ping.

```
$ ping [COLOR=Red]**74,125,225,110**[/COLOR]
ping: unknown host 74,125,225,110
$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=45 time=36.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=45 time=36.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=45 time=36.7 ms
```
The first ping failed because there should have been dots (.), not commas in the address (that is- 74.125.225.110).

And since you are able to ping the google's dns servers (8.8.8.8 ), it almost certainly is a bad DNS issue. You should try changing it first before trying anything else. Try this-

Open the /etc/resolv.conf file as 'root' for editing:
```
gksu gedit /etc/resolv.conf
```replace the existing addresses with 8.8.8.8 and 8.8.4.4, such that the file now looks like:
> nameserver 8.8.8.8
nameserver 8.8.4.4proofread, save and close the file. Then try to browse internet and see if you can. If still not, do this:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```the retry and post back the results. I'm quite hopeful that a working DNS is all you need.

---

### Post by ferrion on 2012-03-16
Hi,

You are right! I make a mistake by input commas.
```

$ ping 74.125.225.110
PING 74.125.225.110 (74.125.225.110) 56(84) bytes of data.
64 bytes from 74.125.225.110: icmp_seq=1 ttl=40 time=374 ms
64 bytes from 74.125.225.110: icmp_seq=2 ttl=40 time=387 ms
64 bytes from 74.125.225.110: icmp_seq=3 ttl=40 time=378 ms

```

I modified /etc/resolv.conf as you told me:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

and do as follows:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

I got the following results:
```

$ ping www.msn.com
PING us.co1.cb3.glbdns.microsoft.com (207.46.140.34) 56(84) bytes of data.
^C
--- us.co1.cb3.glbdns.microsoft.com ping statistics ---
20 packets transmitted, 0 received, 100% packet loss, time 19153ms

$ ping www.alcatel-lucent.com
PING e782.b.akamaiedge.net (23.15.99.82) 56(84) bytes of data.
64 bytes from a23-15-99-82.deploy.akamaitechnologies.com (23.15.99.82): icmp_seq=1 ttl=44 time=315 ms
64 bytes from a23-15-99-82.deploy.akamaitechnologies.com (23.15.99.82): icmp_seq=2 ttl=44 time=299 ms
64 bytes from a23-15-99-82.deploy.akamaitechnologies.com (23.15.99.82): icmp_seq=3 ttl=44 time=307 ms
^C
--- e782.b.akamaiedge.net ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3000ms
rtt min/avg/max/mdev = 299.298/307.594/315.935/6.807 ms
$ ping www.ibm.com
PING www.ibm.com.cs186.net (129.42.58.216) 56(84) bytes of data.
^C
--- www.ibm.com.cs186.net ping statistics ---
20 packets transmitted, 0 received, 100% packet loss, time 18999ms

```

It seems I cannot ping all ip(s)
([www.msn.com:](www.msn.com:) fail
 [www.alcatel-lucent.com:](www.alcatel-lucent.com:) succeed
 [www.ibm.com:](www.ibm.com:) fail)

What can I do next? Do we need to ask internet provider for their DNS?
But I am very curious about because the initial namesevers(192.168.2.2 and 192.168.4.4 are got automatically) and logging into Windows XP, IP is also got automatically, but I can surf websites in windows xp mode.

---

### Post by ferrion on 2012-03-16
When I change the namesevers in /etc/resolv.conf file as you told me with 8.8.8.8 and 8.8.4.4, I will get the following result:

```
# Generated by NetworkManager
nameserver 192.168.2.2
nameserver 192.168.4.4
```

Very strange!:o

---

### Post by varunendra on 2012-03-16
> **ferrion said:**
> When I change the namesevers in /etc/resolv.conf file as you told me with 8.8.8.8 and 8.8.4.4, I will get the following result:

```
# Generated by NetworkManager
nameserver 192.168.2.2
nameserver 192.168.4.4
```Very strange!:o
Actually not so strange. The first line tells you the reason. It is network manager that is changing the values. The fix is easy. Just open network manager (right click on NM-Applet on the top panel > Edit connections) > double click your connection, goto "IPv4 Settings" tab then:

[LIST]
[*]If the "Method" is set to manual, just change the DNS server addresses as suggested ```
8.8.8.8, 8.8.4.4
```
[*]If the method is set to "Automatic (DHCP)", change it to "Automatic (DHCP) address only". Then enter the above dns addresses in the "DNS servers" field.
[/LIST]
Then restart or simply disable -> enable network manager to make change take effect, and see if you can browse now.

---

### Post by neo1691 on 2012-03-16
Hey folks!! I had faced a pretty much same problem while i was on Linux Mint and now on Ubuntu 10.04 LTS.

(As mint is based on ubuntu, the problem is same) 

Okay the problem was i was able to surf the internet on windows 7. I have a wired connection..
But on Ubuntu (or mint) the connection was always connected but i could never surf the internet.
The ip address, subnet and dns was all well set up in network connections.

[B][COLOR=Red][I]Here is the workaround:

[/I][/COLOR] [/B] 1) Boot from a live usb of ubuntu and **run ubuntu before installing.**

2)Set up all your ip adress and other settings by m**aking a new connection** in wired section of network connections.

3)Connect to the internet using mozilla. (it works perfectly) 

4)Reboot now into your [B]already installed ubuntu. 
[/B]
5) Do the same setup.

6) Surf the internet!! 

This is how i got it working!! 
I faced the same problem on two linux distros and got rid of it exactly the same way both times!! Hope it helps you too!!


I was going to start a new thread but then saw this thread and decided to post here~~

---

### Post by varunendra on 2012-03-16
Thanks for the input neo1691!

However, network issues are very subjective and almost always differ from person to person (even though many symptoms might seem to be same). Hence it is never recommended to blindly follow any set of instructions unless you are absolutely sure that it is meant for exactly the same problem (with exactly same reasons) that you have.

For example, an interface may sometimes pick an 'Ad-hoc' address which would make it look as connected, but actually you may not be able to connect to internet or even local network.

---

### Post by neo1691 on 2012-03-16
> **varunendra said:**
> Thanks for the input neo1691!

However, network issues are very subjective and almost always differ from person to person (even though many symptoms might seem to be same). Hence it is never recommended to blindly follow any set of instructions unless you are absolutely sure that it is meant for exactly the same problem (with exactly same reasons) that you have.

For example, an interface may sometimes pick an 'Ad-hoc' address which would make it look as connected, but actually you may not be able to connect to internet or even local network.
Yeah exactly! Hope that helps him!!

---

### Post by ferrion on 2012-03-16
After doing as follows:
> 
If the "Method" is set to manual, just change the DNS server addresses as suggested
Code:
8.8.8.8, 8.8.4.4
If the method is set to "Automatic (DHCP)", change it to "Automatic (DHCP) address only". Then enter the above dns addresses in the "DNS servers" field.
Then restart or simply disable -> enable network manager to make change take effect, and see if you can browse now.

surfing websites still cannot succeed!:confused:

I also tried the following way and hope to succeed(In fact, since we still do not find the exact reason why the laptop cannot connect to internet, I think it will hardly succeed), but cannot boot by live usb. I make live usb following Burn your CD or create a bootable USB stick([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)).

> 1) Boot from a live usb of ubuntu and run ubuntu before installing.

2)Set up all your ip adress and other settings by making a new connection in wired section of network connections.

3)Connect to the internet using mozilla. (it works perfectly) 

4)Reboot now into your already installed ubuntu. 

5) Do the same setup.

6) Surf the internet!! 

I have set removeable device boot at first then hardware boot, but my laptop still boot from hardware.

---

### Post by varunendra on 2012-03-17
If you connect through ethernet/wireless access-point and can ping an external DNS server (like 8.8.8.8 ), there are only three reasons I can think of that can stop you from browsing the internet:

[LIST=1]
[*]The DNS in computer is still not set correctly
[*]The browser is set to "Work offline" (in the "File" menu), or some other browser misconfiguration.
[*]A firewall or router policy is preventing you from accessing the internet.
[/LIST]
I am thinking about point 3 at the moment, although you should also check the other two. Your router itself is the gateway, and the computer is directly connected to it, right? Please correct and clarify if not so. Also, please post the outputs of these once again:
```
ifconfig -a
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
ping -c 4 8.8.8.8
ping -c 4 google.com

```

---

### Post by ferrion on 2012-03-17
Thanks for your time.

Today I called Internet Service Provider about their DNS and they told me DNS are 192.168.2.2 and 192.168.4.4.

I ping other websites and [www.msn.com](www.msn.com) and [www.ibm.com](www.ibm.com) still cannot succeed, but [www.google.com](www.google.com) can succeed.

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:18:57:3a:96  
          inet addr:192.168.1.102  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe57:3a96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170 errors:42 dropped:0 overruns:0 frame:42
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62156 (62.1 KB)  TX bytes:43475 (43.4 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:02:95:25  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

```
$ cat /etc/resolv.conf
nameserver 192.168.2.2
nameserver 192.168.4.4
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```

```
$ ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=41 time=46.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=41 time=48.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=41 time=47.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=41 time=45.7 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 45.795/46.964/48.385/0.931 ms
$ ping -c 4 google.com
PING google.com (74.125.128.139) 56(84) bytes of data.
64 bytes from hg-in-f139.1e100.net (74.125.128.139): icmp_seq=1 ttl=41 time=209 ms
64 bytes from hg-in-f139.1e100.net (74.125.128.139): icmp_seq=2 ttl=41 time=96.1 ms
64 bytes from hg-in-f139.1e100.net (74.125.128.139): icmp_seq=3 ttl=41 time=81.4 ms
64 bytes from hg-in-f139.1e100.net (74.125.128.139): icmp_seq=4 ttl=41 time=164 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 81.478/137.917/209.635/51.892 ms

```

> **varunendra said:**
> If you connect through ethernet/wireless access-point and can ping an external DNS server (like 8.8.8.8 ), there are only three reasons I can think of that can stop you from browsing the internet:

[LIST=1]
[*]The DNS in computer is still not set correctly
[*]The browser is set to "Work offline" (in the "File" menu), or some other browser misconfiguration.
[*]A firewall or router policy is preventing you from accessing the internet.
[/LIST]
I am thinking about point 3 at the moment, although you should also check the other two. Your router itself is the gateway, and the computer is directly connected to it, right? Please correct and clarify if not so. Also, please post the outputs of these once again:
```
ifconfig -a
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
ping -c 4 8.8.8.8
ping -c 4 google.com

```

My laptop access internet by connecting to a TP-LINK router and I have check my mozilla firefox browser in Ubuntu, it is indeed work online.

After your analyse, I am almost sure it is what you called "[COLOR="Red"]**a bad DNS issue**[/COLOR]". But I have no idea that why windows xp is quite OK( that get IP and DNS automatically as well) while ubuntu has so many problems. The packets by windows xp OS sends are different with by Ubuntu OS and DNS can identify the two type of packets(I think the two type of packets are the same)? This question puzzles me. So frustrated!

---

### Post by ferrion on 2012-03-17
BTW,maybe network driver has some problem? Because this laptop is windows xp/ubuntu 10.04 LTS twin operating systems and windows is quite OK.

```
$ sudo ethtool -i eth0
driver: sis190
version: 1.3
firmware-version: 
bus-info: 0000:00:04.0
```

---

### Post by neo1691 on 2012-03-17
there should be a boot menu or something while booting!! I press f9 while booting and select the removal media!! BTW how did you installed ubuntu? Can you somehow go into the live mode?? I mean can you run ubuntu live?

---

### Post by ferrion on 2012-03-17
Thank you first.
When rebooting only windows xp and ubuntu related hardware boot items. I have set removable device boot as first item in Bios.

I installed ubuntu at driver D and windows at Driver C by Grub4Dos.
I do not know how to go into the live mode because I am very new at ubuntu/linux. I almost believe my problem is caused by [COLOR="Red"]**a bad DNS**[/COLOR], but I'd like to try your proposal since any proposal is welcome now. Because I am almost drove to mad:mad: You know, if a os cannot support surf websites and download and upload, most people will give it up.

> **neo1691 said:**
> there should be a boot menu or something while booting!! I press f9 while booting and select the removal media!! BTW how did you installed ubuntu? Can you somehow go into the live mode?? I mean can you run ubuntu live?

---

### Post by neo1691 on 2012-03-17
> **ferrion said:**
> Thank you first.
When rebooting only windows xp and ubuntu related hardware boot items. I have set removable device boot as first item in Bios.

I installed ubuntu at driver D and windows at Driver C by Grub4Dos.
I do not know how to go into the live mode because I am very new at ubuntu/linux. I almost believe my problem is caused by [COLOR="Red"]**a bad DNS**[/COLOR], but I'd like to try your proposal since any proposal is welcome now. Because I am almost drove to mad:mad: You know, if a os cannot support surf websites and download and upload, most people will give it up.
Dont worry stick through it!!! You have windows, so first make a good bootable usb using universal usb installer.. You can get it from here 

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

Now after you make the USB then reboot with your usb plugged in.. 

Then you need to find out the way to select the boot device..

Its usually done by pressing ESC or some other key [the key is displayed at the time of boot, else refer your PC manual!]

---

### Post by ferrion on 2012-03-17
Wow! Thanks a lot! By Pressing ESC, I get into USB Device boot mode. 

But in live usb running mode, I still cannot access network. All things is the same with normal boot. It seems we have not find out the reason:(.

> **neo1691 said:**
> Dont worry stick through it!!! You have windows, so first make a good bootable usb using universal usb installer.. You can get it from here 

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

Now after you make the USB then reboot with your usb plugged in.. 

Then you need to find out the way to select the boot device..

Its usually done by pressing ESC or some other key [the key is displayed at the time of boot, else refer your PC manual!]

---

### Post by ferrion on 2012-03-17
Hi, firstly thank you all. 
In windows xp mode, I run the command:
```
ipconfig /all
```

and get the following result(you can find DNS Servers is 192.168.2.2 and 192.168.4.4):
```

Windows IP Configuration

        Host Name . . . . . . . . . . . . : MYPC
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter VMware Network Adapter VMnet8:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for
VMnet8
        Physical Address. . . . . . . . . : 00-50-56-C0-00-08
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.159.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter VMware Network Adapter VMnet1:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for
VMnet1
        Physical Address. . . . . . . . . : 00-50-56-C0-00-01
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.85.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : SiS191 Ethernet Controller
        Physical Address. . . . . . . . . : 00-26-18-57-3A-96
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.102
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
[COLOR="Red"][B]        DNS Servers . . . . . . . . . . . : 192.168.2.2
                                            192.168.4.4[/B][/COLOR]
        Lease Obtained. . . . . . . . . . : Sunday, March 18, 2012 1:35:17
        Lease Expires . . . . . . . . . . : Sunday, March 18, 2012 3:35:17

``` 


Since windows xp mode can access websites and is very OK. [COLOR="Red"]**That proves the DNS addresses are right**[/COLOR]. I guess the reason is the DNS servers not only can identify the operating system, but identify which operating system sends the data packets or different operating systems's data packets formats are different. But all these seem impossible, because TCP/IP data packets comply to a uniform data format.

> **varunendra said:**
> If you connect through ethernet/wireless access-point and can ping an external DNS server (like 8.8.8.8 ), there are only three reasons I can think of that can stop you from browsing the internet:

[LIST=1]
[*]The DNS in computer is still not set correctly
[*]The browser is set to "Work offline" (in the "File" menu), or some other browser misconfiguration.
[*]A firewall or router policy is preventing you from accessing the internet.
[/LIST]
I am thinking about point 3 at the moment, although you should also check the other two. Your router itself is the gateway, and the computer is directly connected to it, right? Please correct and clarify if not so. Also, please post the outputs of these once again:
```
ifconfig -a
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
ping -c 4 8.8.8.8
ping -c 4 google.com

```

---

### Post by varunendra on 2012-03-18
Sorry for the delayed response, I didn't get enough time to get back to you until now.

> **ferrion said:**
> 
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:18:57:3a:96  
          inet addr:192.168.1.102  Bcast:255.255.255.255  Mask:255.255.255.0
          **inet6 addr:** fe80::226:18ff:fe57:3a96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          **RX packets:170** [COLOR=Red]**errors:42**[/COLOR] dropped:0 overruns:0 [COLOR=Red]**frame:42**[/COLOR]
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62156 (62.1 KB)  TX bytes:43475 (43.4 KB)
          Interrupt:19 Base address:0xdead
..
..
..
$ ping -c 4 google.com
PING google.com (74.125.128.139) 56(84) bytes of data.
64 bytes from hg-in-f139.1e100.net (74.125.128.139): icmp_seq=1 ttl=41 time=[COLOR=Red]**209 ms**[/COLOR]
64 bytes from hg-in-f139.1e100.net (74.125.128.139): icmp_seq=2 ttl=41 time=**96.1** ms
64 bytes from hg-in-f139.1e100.net (74.125.128.139): icmp_seq=3 ttl=41 time=**81.4 **ms
64 bytes from hg-in-f139.1e100.net (74.125.128.139): icmp_seq=4 ttl=41 time=[COLOR=Red]**164 ms**[/COLOR]

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/**avg**/max/mdev = 81.478/[COLOR=Red]**137.917**[/COLOR]/209.635/51.892 ms

```
Notice those "errors" and "frame" in ifconfig? Usually (but not necessarily) those are symptoms of a bad cable or connector. But since you say you can browse normally on XP, there maybe another reason for that, but is definitely not good if this value is 42 for just 170 received packets.

Below that, while pinging the IP is okay, the same for "google.com" is not okay. The average replying time is almost thrice of what usual timings should be (around 50ms). So I still believe that you ISP's DNS is not as good as it should be, although considering the "frame" errors, this may not be the only reason, but 'seems' to be definitely adding to the problem.

> **ferrion said:**
> I guess the reason is the DNS servers not only can identify the operating system, but identify which operating system sends the data packets or different operating systems's data packets formats are different.
Nope! A DNS server does nothing more than resolving domain names to IP addresses. It does not analyze or interfere with transmitted data packets.

However, to be honest, at this point I am confused too. So it's best we eliminate the different possibilities one-by-one. Try one possible solution at a time, then post back the results. Let's do this in the following sequence:
[INDENT]1) Make sure you have changed the DNS to 8.8.8.8 and 8.8.4.4. Don't worry, it won't affect anything in XP, just do it in Ubuntu part. Even if it doesn't help, keep it same for the rest of our attempts.

2) Disable IPv6 using any of these methods:
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)
Keep it also disabled for the rest of attempts.

3) Change the MTU value in Network Manager from "automatic" to **1492**. It is the size of 'Max Transmission Unit' or 'Frame' which is 1492 in windows while 1500 by default in Ubuntu. Change it back to "automatic" if doesn't help improving "Frame" errors.

4) If you have a spare cable, try changing it with the current one.

[/INDENT]If none of this helps, please post the outputs of:
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```That's all I can think of right now with my tired brain. Please try and post back.

---

### Post by ferrion on 2012-03-18
Hi,

Thanks a lot.
I had followed what you told me(Just open network manager (right click on NM-Applet on the top panel > Edit connections) > double click your connection, goto "IPv4 Settings" tab. Since the method is set to "Automatic (DHCP)", change it to "Automatic (DHCP) address only", then enter 8.8.8.8, 8.8.4.4 in the "DNS servers" field), then restart. But when I do: cat /etc/resolv.conf, it shows the original namesever, not "8.8.8.8, 8.8.4.4".

Do I need do extra things to change DNS? Thanks you.

---

### Post by varunendra on 2012-03-18
Try:
```
sudo service network-manager restart
```
After changing DNS values in NM.

---

### Post by ferrion on 2012-03-19
do not have any effect and still cannot change it. So frustrated!:sad: 

varunendra, I guess you are very confused and frustrated just like me, right?
I am so sorry!

> **varunendra said:**
> Try:
```
sudo service network-manager restart
```
After changing DNS values in NM.

---

### Post by varunendra on 2012-03-19
> **ferrion said:**
> varunendra, I guess you are very confused and frustrated just like me, right?
Not at all..
There are so many things involved in networking that sometimes even obvious things get overlooked. So as I said, at this point I just want to eliminate the possibilities one-by-one. At least those we can think of right now. Once they seem to be in order, then we can go deeper if required.

In fact what's admirable is the patience of users like you who actually suffer such problems and yet don't give up.

Also, I tried that code in a 11.10 VM, it may be different in 10.04 but there are many ways to make it work. If in network manager it is still showing the changed DNS, try this one this time:
right-click on the NM-Applet > click "Enable Networking". This will remove the tick-mark beside it and disable it. Then, after waiting 4-5 seconds, redo the same thing to enable it again. This 'should' work. If even that doesn't work (although it would be a shock for me!;)), we may have to resort to manual methods - by disabling network manager.

By the way, I am more worried about those 'Frame' errors. A DNS issue can't do that. So changing DNS, as I said, is just a part of our 'elimination of culprits' procedure.

[B][U]
Edit[/U]:[/B]
I will be offline for a few hours, so may not reply immediately. Changing DNS is not an absolute requirement, especially if it is at least partially working (e.g, for google.com), so in the meanwhile, you may try the other steps to see if any of them resolves the 'frame' issue.

---

### Post by ferrion on 2012-03-19
> In fact what's admirable is the patience of users like you who actually suffer such problems and yet don't give up.
you are a real ubuntu experts and respectable person like a knight who always help others without any payment. I am greatly encouraged by you for your patience and knowledge:D

I have tried right-click  "Enable Networking" and redo the same thing to enable it again 4-5 seconds later. But things were not changed.
> right-click on the NM-Applet > click "Enable Networking". This will remove the tick-mark beside it and disable it. Then, after waiting 4-5 seconds, redo the same thing to enable it again. This 'should' work. If even that doesn't work (although it would be a shock for me!), we may have to resort to manual methods - by disabling network manager.

I will try the other steps to see if any of them resolves the 'frame' issue as you told me.

Thanks again.

---

### Post by ferrion on 2012-03-19
Thanks for your effort.

I have disable IPv6.

```
$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
1
```

I change the MTU value in Network Manager from "automatic" to 1492, but nothing happened. So I changed it back to "automatic"

$ uname -mr
2.6.32-33-generic i686
$ lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
	Kernel driver in use: sis190
	Kernel modules: sis190
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath9k
$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_hwdep               5412  1 snd_hda_codec
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                678735  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
ttm                    50103  1 radeon
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29329  1 radeon
soundcore               6620  1 snd
uvcvideo               57374  0 
ath9k                 306106  0 
videodev               34361  1 uvcvideo
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
sis190                 14852  0 
mac80211              205402  1 ath9k
sis_agp                 4015  0 
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162377  5 radeon,ttm,drm_kms_helper
psmouse                63677  0 
agpgart                31724  3 ttm,sis_agp,drm
mii                     4381  1 sis190
serio_raw               3978  0 
i2c_algo_bit            5028  1 radeon
ath                     7611  1 ath9k
cfg80211              126144  3 ath9k,mac80211,ath
asus_laptop            17008  0 
led_class               2864  2 ath9k,asus_laptop
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
sata_sis                3332  9 
mike@mike-laptop:~$ 

> 
1) Make sure you have changed the DNS to 8.8.8.8 and 8.8.4.4. Don't worry, it won't affect anything in XP, just do it in Ubuntu part. Even if it doesn't help, keep it same for the rest of our attempts.

2) Disable IPv6 using any of these methods:
[http://www.webupd8.org/2010/05/how-t...untu-1004.html](http://www.webupd8.org/2010/05/how-t...untu-1004.html)
[http://www.ubuntugeek.com/how-to-dis...in-ubuntu.html](http://www.ubuntugeek.com/how-to-dis...in-ubuntu.html)
Keep it also disabled for the rest of attempts.

3) Change the MTU value in Network Manager from "automatic" to 1492. It is the size of 'Max Transmission Unit' or 'Frame' which is 1492 in windows while 1500 by default in Ubuntu. Change it back to "automatic" if doesn't help improving "Frame" errors.

4) If you have a spare cable, try changing it with the current one.

If none of this helps, please post the outputs of:
Code:
uname -mr
lspci -nnk | grep -iA2 net
lsmod

---

### Post by varunendra on 2012-03-19
Firstly, thanks for your kind words. But you are obviously over-estimating my capabilities. Also, we do whatever we do here simply because we either enjoy it, or because it helps us to learn or polish our skills.

Now onto the problem-

Seems everything else is either ok (lspci, lsmod) or ineffective (IPv6, MTU). Only the DNS is still a mystery. I was wondering if you are 'editing' the correct 'connection' in NM (the one that appears in bold letters 'above' "**Disconnect**" in the left-click menu of nm-applet). Can you post screenshots of "Connection Information" (right-click on nm-applet > "Conn. Info....") and connection editing window where you've set the DNS in NM?

Since your pinging timings for IP addresses seem good, let's also try this:
Open the firefox browser (make sure it is NOT set to "Work Offline") then in the address bar, type (or copy-paste) this address:
**74.125.236.8**
or,
**74.125.225.110**
then press enter. See if this can open google's page in the browser.

---

### Post by ferrion on 2012-03-20
Thanks for your effort. I upload a screenshots.zip file including 2 screenshots.

Firefox can open [www.google.com](www.google.com) and I tried to browse other websites and cannot succeed.

Thanks again.

---

### Post by varunendra on 2012-03-20
Exactly what I suspected:> **varunendra said:**
> I was wondering if you are 'editing' the correct 'connection' in NM....
As per the "Connection info", you are using the "ifupdown (eth0)" connection, while the custom DNS entries are made for "Wired connection1" connection.

In short, you need to edit the "ifupdown (eth0)" connection. Put the 8.8.... DNS servers for that one. Then either reboot or simply do:
```
sudo service network-manager restart
```like before.

---

### Post by ferrion on 2012-03-20
Yeah, You are right.

But when I right-click "Edit Connections">left click "ifupdown (eth0)", net manager has no response while "Wired connection 1" connection" will pop up a dialog box.

I wonder why I have 2 ethernet card(ipupdown(eth0) and wired connection 1)? As I have known, I have only a ethernet card.

I will try to find out:
 
1) Why this happened(2 ethernet card)&#65311;
2) How to change my default network connection to "wired connceton    1" or make when double clicking "ifupdown(eth0)" and it pop up a dialogbox to set DNS.

---

### Post by varunendra on 2012-03-21
Let's take a look at:
```
cat /etc/NetworkManager/nm-system-settings.conf
```
This thread is certainly teaching me new things. I guess my next attempt would be to completely disable Network-Manager, and use the /etc/network/interfaces file instead to do the connection.

But please confirm this first-
What I have understood so far is that you do not need any kind of login or authentication procedures to get connected to internet. It is a normal Ethernet cable which has a permanently running broadband connection on it. You just have to plug it into the computer, and it gets connected, without requiring any extra steps (this is how it connects in the windows part, and is expected in Ubuntu too).

Please correct the above assumption as and if required.

As for your first question in above post, read the 'PS' below. For the second one, you should be able to connect to 'Wired Conn.1" by just clicking on its name in the drop-down menu of nm-applet. If you can't see it in the left-click menu of nm-applet, make sure it is set to use the "Device MAC Address" of your card in the first tab (that says 'Wired') of the connection editing box.

**_PS_:**
Just for clarification, those are not 'two' cards you see in the 'Connection' list. Those are just two different 'Profiles' having different configurations. You can create any number of connection profiles in that list. They may correspond to a single card/interface (or multiple, if available) as required. However, I didn't know that there can be profiles that you can't edit (the 'ifupdown' one in your case). I'm reading on it.

---

### Post by varunendra on 2012-03-21
Sorry for consecutive posts, but it is to avoid clutter. Please read the above one also.

Okay, I think I found out why you are unable to edit that connection and why the Manual entry in NM is ignored:
> **ferrion said:**
> The /etc/network/interfaces is as follows:
```
auto lo
iface lo inet loopback
[COLOR=Red][B]auto eth0
iface eth0 inet dhcp[/B][/COLOR]
```
Combined with this, I am 99% sure that [ifupdown] entry in nm-system-settings.conf file must have been set to "*managed=true*".

Accordingly, if you comment out the last two lines (by adding **#** before them) and/or set the [ifupdown] mode in nm-system-settings.conf file as ***false***, you should be either able to edit that connection, or it should get removed by itself.

If I'm correct, you need to do one or both of these:
1) comment out last two lines in /etc/network/interfaces file. To do so, open it as root by:
```
gksu gedit /etc/network/interfaces
```
then add # before last two lines so it looks like:
> auto lo
 iface lo inet loopback
 [COLOR=Red][B]# auto eth0
 # iface eth0 inet dhcp[/B][/COLOR][COLOR=Red][/COLOR] save and close file. It is equivalent to deleting them, but commenting-out is better in case you need them later.

2) Set the [ifupdown] mode as *false*. Same as above, open the file as root by:
```
gksu gedit /etc/NetworkManager/nm-system-settings.conf
```then look for **[ifupdown]** entry in it. Make sure the line below it is:
> managed=false save and close file. Then restart NM service as before. The new DNS should come into effect this time.

---

### Post by ferrion on 2012-03-22
Sorry for reply so late. I am on a biz trip.

```

mike@mike-laptop:~$ cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

mike@mike-laptop:~$ 

```

> Let's take a look at:
Code:
cat /etc/NetworkManager/nm-system-settings.conf

I upload 3 screenshort. From these screenshorts, you can see "Edit" button is not grayed when left clicking "Wired Conn.1", while "Edit" button is grayed when left clicking "ifupdown(eth0)".

Besides, "Device MAC Address" in the first tab (that says 'Wired') is not found.

---

### Post by ferrion on 2012-03-22
It seems you can forecast almost everything:o You are right.
> Combined with this, I am 99% sure that [ifupdown] entry in nm-system-settings.conf file must have been set to "managed=true".

Besides, you are very patient and list every step. Thank you:)
> If I'm correct, you need to do one or both of these:
1) comment out last two lines in /etc/network/interfaces file. To do so, open it as root by:
Code:
gksu gedit /etc/network/interfaces
then add # before last two lines so it looks like:
Quote:
auto lo
iface lo inet loopback
# auto eth0
# iface eth0 inet dhcp
save and close file. It is equivalent to deleting them, but commenting-out is better in case you need them later.

2) Set the [ifupdown] mode as false. Same as above, open the file as root by:
Code:
gksu gedit /etc/NetworkManager/nm-system-settings.conf
then look for [ifupdown] entry in it. Make sure the line below it is:
Quote:
managed=false
save and close file. Then restart NM service as before. The new DNS should come into effect this time.

I upload a attachment which show the configuration of Wired Connection 1. It seems everything is OK. In fact, access websites still not succeed.

---

### Post by varunendra on 2012-03-22
So what's the current situation?
```
ifconfig -a
route -n
cat /etc/resolv.conf
ping -c 4 74.125.236.6
ping -c 4 8.8.4.4
ping -c 4 google.com
```


**_PS_:**
I may get little or no time to reply until Monday, so if anybody looking at this thread has any ideas, please share it.

---

### Post by ferrion on 2012-03-23
Thank you!
I get the following results and post them back.
```
mike@mike-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:18:57:3a:96  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8226 (8.2 KB)  TX bytes:10102 (10.1 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:02:95:25  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mike@mike-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
mike@mike-laptop:~$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
mike@mike-laptop:~$ ping -c 4 74.125.236.6
PING 74.125.236.6 (74.125.236.6) 56(84) bytes of data.
64 bytes from 74.125.236.6: icmp_seq=1 ttl=43 time=273 ms
64 bytes from 74.125.236.6: icmp_seq=2 ttl=43 time=160 ms
64 bytes from 74.125.236.6: icmp_seq=3 ttl=43 time=158 ms
64 bytes from 74.125.236.6: icmp_seq=4 ttl=43 time=158 ms

--- 74.125.236.6 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 158.712/187.984/273.604/49.440 ms
mike@mike-laptop:~$ ping -c 4 8.8.4.4
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.
64 bytes from 8.8.4.4: icmp_seq=1 ttl=41 time=48.4 ms
64 bytes from 8.8.4.4: icmp_seq=2 ttl=41 time=49.0 ms
64 bytes from 8.8.4.4: icmp_seq=3 ttl=41 time=47.8 ms
64 bytes from 8.8.4.4: icmp_seq=4 ttl=41 time=49.8 ms

--- 8.8.4.4 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 47.897/48.809/49.823/0.718 ms
mike@mike-laptop:~$ ping -c 4 google.com
PING google.com (74.125.128.101) 56(84) bytes of data.
64 bytes from hg-in-f101.1e100.net (74.125.128.101): icmp_seq=1 ttl=41 time=71.0 ms
64 bytes from hg-in-f101.1e100.net (74.125.128.101): icmp_seq=2 ttl=41 time=62.8 ms
64 bytes from hg-in-f101.1e100.net (74.125.128.101): icmp_seq=3 ttl=41 time=68.7 ms
64 bytes from hg-in-f101.1e100.net (74.125.128.101): icmp_seq=4 ttl=41 time=60.6 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 60.659/65.826/71.054/4.218 ms
```

> Code:
ifconfig -a
route -n
cat /etc/resolv.conf
ping -c 4 74.125.236.6
ping -c 4 8.8.4.4
ping -c 4 google.com

You are almost right. But my laptop is connected with a router by category 5 cable(ethernet cable).
> But please confirm this first-
What I have understood so far is that you do not need any kind of login or authentication procedures to get connected to internet. It is a normal Ethernet cable which has a permanently running broadband connection on it. You just have to plug it into the computer, and it gets connected, without requiring any extra steps (this is how it connects in the windows part, and is expected in Ubuntu too).

Have a good weekend:D
> PS:
I may get little or no time to reply until Monday, so if anybody looking at this thread has any ideas, please share it.

---

### Post by varunendra on 2012-03-23
> **ferrion said:**
> You are almost right. But my laptop is connected with a router by category 5 cable(ethernet cable).That's fine. But since your pinging time for google.com looks good, have you tried to open it ([www.google.com](www.google.com)) in the browser? If it still fails, I'd suggest to install chromium and try it:
```
sudo apt-get install chromium-browser
```

Obviously, I'm doubting the browser (firefox??) again for some possible misconfiguration. Because other common factors seem all good to me now.

---

### Post by ferrion on 2012-03-23
I upload a screenshot about firefox's setting(click Edit menu > Preferences > Advance, then in the second tab, you can see "Network". Click "Settings" button)

I can open [www.google.com](www.google.com) in firefox but cannot open [www.msn.com:confused:](www.msn.com:confused:)&#65288;BTW: I have the same situation at my lab when access internet. My lab and home have different DNS&#65289;.

I installed chromium-browser you suggested. But after installation, I could not find it. I am afraid it failed, because I found error in the trace which I post it here(It seems installation need access networking). 
```
mike@mike-laptop:~$ sudo apt-get install chromium-browser
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-browser-l10n chromium-codecs-ffmpeg
The following NEW packages will be installed:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
0 upgraded, 3 newly installed, 0 to remove and 126 not upgraded.
Need to get 20.0MB of archives.
After this operation, 80.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  chromium-codecs-ffmpeg chromium-browser chromium-browser-l10n
Install these packages without verification [y/N]? y
[COLOR="Red"]Err[/COLOR] http://cn.archive.ubuntu.com/ubuntu/ lucid-updates/universe chromium-codecs-ffmpeg 15.0.874.106~r107270-0ubuntu0.10.04.1
  404  Not Found
[COLOR="Red"]Err[/COLOR] http://security.ubuntu.com/ubuntu/ lucid-security/universe chromium-codecs-ffmpeg 15.0.874.106~r107270-0ubuntu0.10.04.1
  404  Not Found [IP: 91.189.92.166 80]
[COLOR="Red"]Err[/COLOR] http://security.ubuntu.com/ubuntu/ lucid-security/universe chromium-browser 15.0.874.106~r107270-0ubuntu0.10.04.1
  404  Not Found [IP: 91.189.92.166 80]
[COLOR="Red"]Err[/COLOR] http://security.ubuntu.com/ubuntu/ lucid-security/universe chromium-browser-l10n 15.0.874.106~r107270-0ubuntu0.10.04.1
  404  Not Found [IP: 91.189.92.166 80]
[COLOR="Red"]Failed[/COLOR] to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg_15.0.874.106~r107270-0ubuntu0.10.04.1_i386.deb  404  Not Found [IP: 91.189.92.166 80]
[COLOR="Red"]Failed[/COLOR] to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser_15.0.874.106~r107270-0ubuntu0.10.04.1_i386.deb  404  Not Found [IP: 91.189.92.166 80]
[COLOR="Red"]Failed[/COLOR] to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser-l10n_15.0.874.106~r107270-0ubuntu0.10.04.1_all.deb  404  Not Found [IP: 91.189.92.166 80]
E: [COLOR="Red"]Unable[/COLOR] to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

> **varunendra said:**
> That's fine. But since your pinging time for google.com looks good, have you tried to open it ([www.google.com](www.google.com)) in the browser? If it still fails, I'd suggest to install chromium and try it:
```
sudo apt-get install chromium-browser
```

Obviously, I'm doubting the browser (firefox??) again for some possible misconfiguration. Because other common factors seem all good to me now.

---

### Post by varunendra on 2012-03-23
Hmm.. it's getting both mysterious and interesting. Failure of chromium installation suggests that the problem is not limited to firefox, but is effective system-wide.

What are the outputs of:
```
sudo ufw status
sudo iptables -L
```Although these are very-very unlikely to cause problems unless are manually (and exclusively) misconfigured, but I can't think of anything else because windows part is working fine (otherwise I could have blamed an external firewall ;)).

Also, can you open msn.com by typing this in the address bar of the browser: 65.55.206.203

---

### Post by ferrion on 2012-03-24
Thank you for your reply.
I post the results back. And when I type "65.55.206.203" in the firefox address bar, it quickly transform to "www.msn.com" - still cannot open it.

I almost forget tell you when I at my lab I access network not via a router. Access network at home via a router.

```
mike@mike-laptop:~$ sudo ufw status
Status: inactive
mike@mike-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

> **varunendra said:**
> Hmm.. it's getting both mysterious and interesting. Failure of chromium installation suggests that the problem is not limited to firefox, but is effective system-wide.

What are the outputs of:
```
sudo ufw status
sudo iptables -L
```Although these are very-very unlikely to cause problems unless are manually (and exclusively) misconfigured, but I can't think of anything else because windows part is working fine (otherwise I could have blamed an external firewall ;)).

Also, can you open msn.com by typing this in the address bar of the browser: 65.55.206.203

---

### Post by ferrion on 2012-03-28
bump!

---

### Post by pellyhawk on 2012-03-30
I have the same problem, Maybe I need some configuration.

---

### Post by varunendra on 2012-03-30
> **ferrion said:**
> bump!Sorry for not being able to reply. Reasons- firstly, this issue is getting over my head now, so I need enough time to look deeper into it; and secondly, the annual (fiscal year) closing exercises are keeping me on toes, so I'm not getting that time.. :(

So just a few things for now-

I believe MSN actually 'redirects' you to a closest/suitable server (depending on where you are located) immediately after a connection is established. And in this process, the redirected URL is different than just msn.com, so the DNS issue again strikes in, and since the new (redirected) URL doesn't get resolved, you can,t open the page.

The same thing 'may be' happening happening with the installation on chromium-browser. Obviously, if you can't resolve a URL, you can't fetch packages from it. But as I said, I'm not sure of anything at this point.

As for now, you may try to open as many URLs as possible by using their IP addresses (which you can get from XP part by just pinging them). However, this obviously isn't a solution, instead, it's just to confirm if DNS resolution is still a factor (and whether it is the only factor).

Also post the output of (from Ubuntu when you are connected):
```
sudo apt-get update
sudo apt-get upgrade
```

Unfortunately, I can't yet promise any consistency in my replies since my schedules are getting overwhelmingly busy with new and pending tasks every coming day.

> **pellyhawk said:**
> I have the same problem, Maybe I need some configuration.
@pellyhawk,
Please start a new thread of your own providing the details of your problem. Network issues are more than often differ from person-to-person even though they may seem similar.

---

