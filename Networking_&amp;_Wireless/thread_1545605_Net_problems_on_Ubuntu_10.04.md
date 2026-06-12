---
title: "Net problems on Ubuntu 10.04"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by piyush.neo on 2010-08-04
i recently installed Ubuntu 10.04 and here are few problems i am facing....
1. Net is not working properly. I can access many sites perfectly but i don't know what problem it has with Gmail.
> The server at [www.google.com]("http://www.google.com") is taking too long to respond.Same problem with Chromium web browser(Its working fine from windows...)

2.Whenever i am trying to install any package from synaptic manager,after installing it is initiating some  tts-msscorefonts-installer (dont know why)  which never get connected to its server. Finally i need to kill synaptic, clear the /var/lib/dpkg/updates/* or restart my system in order to use synaptic again as killing it didn't leave locks on some file perhaps.....here is detail of synaptic
```

Preconfiguring packages ...
Selecting previously deselected package libcap2-bin.
(Reading database ... 125269 files and directories currently installed.)
Unpacking libcap2-bin (from .../libcap2-bin_1%3a2.17-2ubuntu1_i386.deb) ...
Selecting previously deselected package liblua5.1-0.
Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.4-5_i386.deb) ...
Selecting previously deselected package libsmi2ldbl.
Unpacking libsmi2ldbl (from .../libsmi2ldbl_0.4.8+dfsg2-2_i386.deb) ...
Selecting previously deselected package libc-ares2.
Unpacking libc-ares2 (from .../libc-ares2_1.7.0-1_i386.deb) ...
Selecting previously deselected package wireshark-common.
Unpacking wireshark-common (from .../wireshark-common_1.2.7-1_i386.deb) ...
Selecting previously deselected package wireshark.
Unpacking wireshark (from .../wireshark_1.2.7-1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for python-support ...
Setting up ettercap-common (1:0.7.3-1.4ubuntu1) ...
Setting up libnet1 (1.1.4-2) ...

Setting up ettercap-gtk (1:0.7.3-1.4ubuntu1) ...

Setting up ttf-mscorefonts-installer (3.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-08-04 14:16:47--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-08-04 14:17:09--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... 

```
:(

---

### Post by dineshs on 2010-08-04
May be problem with MTU.How do you connect to internet? DSL?

---

### Post by piyush.neo on 2010-08-04
i have a wired LAN connection(broadband)

---

### Post by dineshs on 2010-08-04
Can you set MTU as 1492 in eth
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you use for broadband
under wired set MTU as 1492
Also pl post the output of
```
ifconfig -a
```

---

### Post by piyush.neo on 2010-08-04
> 
	 		Can you set MTU as 1492 in eth
Right-click on the NM icon(two opposite arrows on top right) and then  click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you use for broadband
under wired set MTU as 1492
Also pl post the output of

i have changed mtu and here is the output
```

piyush@piyush-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:38:0e:40:5f  
          inet addr:172.31.73.159  Bcast:172.31.73.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe0e:405f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13693190 (13.6 MB)  TX bytes:1074142 (1.0 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:bc:f4:89  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by Iowan on 2010-08-04
Changes don't appear to have taken - you may need to restart Network Manager...

---

### Post by piyush.neo on 2010-08-04
here is new o/p...still no change in net...:(
```

piyush@piyush-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:38:0e:40:5f  
          inet addr:172.31.73.159  Bcast:172.31.73.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe0e:405f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:701 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:377555 (377.5 KB)  TX bytes:54532 (54.5 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:bc:f4:89  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

piyush@piyush-laptop:~$ 


```

---

### Post by dineshs on 2010-08-04
Let us first set an open DNS to ensure that there is no DNS issue
Right-click on the NM icon and then click on Edit Connections.
Select the tab, wired
select eth0 - click edit
select ipv4
method-automatic DHCP addresses only (if you have set IP manually you may continue with`manual')
Give DNS as 4.2.2.1
apply.
Restart the PC and see if there is change
If not set MTU as 1482,1472,or 1464 and see(refer [http://ubuntuforums.org/showthread.php?t=1376506](http://ubuntuforums.org/showthread.php?t=1376506))

---

### Post by piyush.neo on 2010-08-04
i am sure its not a DNS problem. i am behind a college proxy.My friends have same setting as mine. Also many other sites are working properly.I have also tried other MTU but in vein...i think i need to switch back to 9.10.. :(

---

### Post by dineshs on 2010-08-05
Not sure if this is related
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by piyush.neo on 2010-08-13
Reinstalled it....now working fine..

---

### Post by Iowan on 2010-08-13
I always hesitate to suggest a re-install - even if it seems the "easiest" way. Glad you found a solution. If problem is fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

---

### Post by piyush.neo on 2010-08-14
> **Iowan said:**
> I always hesitate to suggest a re-install - even if it seems the "easiest" way. Glad you found a solution. If problem is fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

It was freshly installed so i found no harm in reinstalling it, also my lot of work was stuck due to this...so finally have to take this decision.

---

