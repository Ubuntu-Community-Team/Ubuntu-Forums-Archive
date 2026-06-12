---
title: "Lost internet connection??"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by lucifuge on 2009-05-30
When i installed Ubuntu, it automatically detected my router and its settings and the internet had been working fine for last month or so. My girlfriends attached notebook also works hassle free.

Tonight, for some reason, i lost the internet connection (ADSL) on Ubuntu...said it couldn't connect in the network icon. I initially thought the internet service was down. I entered the 192.168.2.1 in my Firefox to access the Belkin settings, but it wouldnt let me!  To my complete shock my girlfriends notbook was totally unaffected. Also, I can get into the router settings  no probs on her machine. Now being somewhat of a Ubuntu noob I dabbled here and there and cannot for the life of me get Ubuntu to "see" the ADSL connection. Can someone suggest what I need to do (exactly) to get me back in business?? :(

---

### Post by Chris_no on 2009-05-30
Need some info to help you.

What version of ubuntu? (9.04, 8.10 or 8.04)

Then open a terminal window and post the result of ifconfig.

You might want to access your router from your girlfriends computer to
see if the router can see your computer.

---

### Post by lucifuge on 2009-05-30
9.04

---

### Post by lucifuge on 2009-05-30
It's like something critical has been removed or deleted maybe?

anyway  here's result of ifconfig:

---------------------------------------

   [SIZE=2]brett@brett-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:c6:5b:5a  
          inet6 addr: fe80::211:2fff:fec6:5b5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4815 (4.8 KB)  TX bytes:3500 (3.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:114740 (114.7 KB)  TX bytes:114740 (114.7 KB)

pan0      Link encap:Ethernet  HWaddr a6:6a:00:80:39:b6  
          inet6 addr: fe80::a46a:ff:fe80:39b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:2f:da:95:3a  
          inet6 addr: fe80::211:2fff:feda:953a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:11560 (11.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-2F-DA-95-3A-35-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

brett@brett-desktop:~$ 

[/SIZE]

---

### Post by Chris_no on 2009-05-30
Are you connecting through the wired or the wireless card to internet? 

Will need output of iwconfig as well if it is wireless.

Copy the content of /etc/network/interfaces file also, but remove any passkeys.

---

### Post by lucifuge on 2009-05-30
Im using a network cable from the router as Im not sure my older PC has wireless functionality.

---

### Post by lucifuge on 2009-05-30
content of /etc/network/interfaces file
----------------------------------------
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

---

### Post by Chris_no on 2009-05-30
If I gather this correctly you had a direct connection from your computer
to your ADSL.

Your computer also have a wireless card of somekind built in.
I'm no good at PPP stuff, but we might get your wireless card up
and running. I'm assuming that your router supports that.

What is the output of iwconfig?

PS: This is about PPP in ubuntu if it's any help. [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by lucifuge on 2009-05-30
The strange thing is, i jsut treid to connect to my wireless network.  and it connected!!   but i cant access the internet or email????  Fireofex doesnt like it  nor thunderbird.  Im going nuts

---

### Post by Chris_no on 2009-05-30
Firefox doesn't need to like it nor Thunderbird . ;)

Some of your settings may not be correct, eighter on your machine or the router.

It would be helpful to see output of iwconfig and ifconfig now.

---

### Post by Iowan on 2009-05-30
Your problem sounds [familiar]("http://ubuntuforums.org/showthread.php?t=1156441") ...  [This]("http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html") article goes more in-depth.

---

### Post by Chris_no on 2009-05-30
No I think this is a bit different since he hasn't enabled dhcp in the first
place, but enabling it just might do the trick.

I'm assuming that PPP doesn't use dhcp in some way.

---

### Post by lucifuge on 2009-05-30
OK

I've completely reinstalled Ubuntu 9.04. I reset the router which is wired to my PC and wireless to my girlfriends notebook.  After the router reinitialized, I can view the router settings on my gf's notebook and it CAN see my PC!   The internet works fine on her notebook, but still Auto Eth0   won't work on mine!    What can have changed??  This is a fresh install. I've also replaced the LAN cable, no luck!??   What hell is going on.  Last installation of Ubuntu it ofudn the internet asap.  What can have changed???

---

### Post by tommah04 on 2009-05-31
did you lose connect after a certain auto update? 

I know this maybe be a simple solution, but never hurts to ask.....

if you did, you might need to just restart your computer.

same thing happened to me, internet worked for a little while, updated, lost internet..... started pulling hairs out trying to figure it out.....restarted.....felt stupid

---

### Post by lucifuge on 2009-05-31
****update*****

dirty LAN port on the PC!!!!!!!!!!!!

it's fine now, at least Win XP is, I'm yet to re-install Ubuntu as a dual boot.

---

