---
title: "Wired stopped working"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by qianian on 2012-04-09
Two weeks ago wired worked fine and now Network Manager tries to connect, then flags Wired Connection Disconnected. 

I tried making a Manual option in Network Connections from the page below, but though it sees the ethernet and displays Connected there's no pingback. Oddly, Network Tools shows occasional kilobytes received (89.6 Transmitted, 37.3 Received).

[http://askubuntu.com/questions/18311/wired-connection-not-working](http://askubuntu.com/questions/18311/wired-connection-not-working)

Here's the output:

```
~$ sudo ifconfig
[sudo] password for qian: 
eth0      Link encap:Ethernet  HWaddr 00:15:58:c8:c6:03  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fec8:c603/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21022 (21.0 KB)  TX bytes:61741 (61.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37921 (37.9 KB)  TX bytes:37921 (37.9 KB)

qian@Stonau:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:58:c8:c6:03  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fec8:c603/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21022 (21.0 KB)  TX bytes:61741 (61.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37921 (37.9 KB)  TX bytes:37921 (37.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:b0:cd:f8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

~$ ls -lrt /var/log
total 5680
drwx------ 2 speech-dispatcher root    4096 2011-06-06 10:29 speech-dispatcher
drwxr-xr-x 2 root              root    4096 2011-07-19 22:51 unattended-upgrades
drwxr-xr-x 2 root              root    4096 2011-10-01 03:09 samba
drwxr-xr-x 2 root              root    4096 2011-10-10 20:05 dist-upgrade
-rw-rw---- 1 root              utmp       0 2011-10-12 22:27 btmp.1
drwxr-xr-x 2 root              root    4096 2011-10-12 22:27 fsck
-rw-r----- 1 root              adm       31 2011-10-12 22:27 boot
-rw-r--r-- 1 root              root   49092 2011-10-12 22:27 bootstrap.log
-rw-r--r-- 1 root              root   24024 2012-03-31 00:43 faillog
-rw-rw-r-- 1 root              utmp  292292 2012-03-31 00:43 lastlog
drwxr-xr-x 2 root              root    4096 2012-03-31 00:52 installer
-rw-r----- 1 syslog            adm        0 2012-03-31 05:23 ufw.log
drwxr-xr-x 2 root              root    4096 2012-03-31 05:23 news
-rw-r----- 1 syslog            adm        0 2012-03-31 05:23 mail.log
-rw-r----- 1 syslog            adm        0 2012-03-31 05:23 mail.err
drwxr-xr-x 2 root              root    4096 2012-03-31 05:23 lightdm
-rw-r--r-- 1 root              root    2574 2012-03-31 08:28 fontconfig.log
-rw-r--r-- 1 root              root   31763 2012-03-31 16:18 pm-powersave.log.1
-rw-r--r-- 1 root              root   25912 2012-03-31 16:39 alternatives.log.1
-rw-r--r-- 1 root              root 1409472 2012-03-31 17:18 dpkg.log.1
-rw-rw-r-- 1 root              utmp   38400 2012-03-31 17:39 wtmp.1
-rw-r----- 1 syslog            adm   102261 2012-04-01 07:12 kern.log.2.gz
-rw-r----- 1 syslog            adm     3160 2012-04-01 07:30 auth.log.2.gz
drwxr-xr-x 2 root              root    4096 2012-04-01 08:02 apt
drwxr-xr-x 2 root              root    4096 2012-04-01 08:02 ConsoleKit
-rw-r----- 1 syslog            adm   139594 2012-04-01 08:02 syslog.4.gz
-rw-r--r-- 1 root              root   37789 2012-04-01 08:02 jockey.log.1
-rw-r--r-- 1 root              root       0 2012-04-01 08:02 jockey.log
-rw-rw---- 1 root              utmp       0 2012-04-01 08:02 btmp
-rw-r--r-- 1 root              root    1287 2012-04-01 09:42 wvdialconf.log
-rw-r--r-- 1 root              root    2986 2012-04-01 10:14 alternatives.log
-rw-r--r-- 1 root              root    6505 2012-04-01 10:14 dpkg.log
-rw-r----- 1 syslog            adm    35238 2012-04-03 07:35 syslog.3.gz
-rw-r----- 1 syslog            adm   208163 2012-04-07 12:50 syslog.2.gz
-rw-r----- 1 root              adm    17411 2012-04-08 11:06 dmesg.4.gz
-rw-r----- 1 root              adm    17537 2012-04-08 17:25 dmesg.3.gz
-rw-r----- 1 syslog            adm  1334723 2012-04-08 17:25 kern.log.1
-rw-r----- 1 syslog            adm    40702 2012-04-08 17:26 auth.log.1
-rw-r----- 1 syslog            adm   231887 2012-04-08 17:32 syslog.1
drwxr-xr-x 2 root              root    4096 2012-04-08 17:38 cups
-rw-r----- 1 root              adm    17239 2012-04-09 11:08 dmesg.2.gz
-rw-r----- 1 root              adm    17181 2012-04-09 11:27 dmesg.1.gz
-rw-r----- 1 root              adm    66377 2012-04-09 11:38 dmesg.0
-rw-r--r-- 1 root              root   30998 2012-04-09 12:11 Xorg.0.log.old
-rw-r--r-- 1 root              root  260898 2012-04-09 12:36 udev
-rw-r--r-- 1 root              root     414 2012-04-09 12:36 boot.log
-rw-r----- 1 root              adm    66345 2012-04-09 12:36 dmesg
-rw-r--r-- 1 root              root   31265 2012-04-09 16:41 Xorg.0.log
-rw-r--r-- 1 root              root   36678 2012-04-09 16:41 pm-suspend.log
-rw-r--r-- 1 root              root  116742 2012-04-09 16:44 pm-powersave.log
-rw-r----- 1 syslog            adm    11491 2012-04-09 17:02 auth.log
-rw-rw-r-- 1 root              utmp  110208 2012-04-09 17:02 wtmp
-rw-r----- 1 syslog            adm   429225 2012-04-09 17:03 kern.log
-rw-r----- 1 syslog            adm   687829 2012-04-09 17:03 syslog

~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0

~$ ping google.com
ping: unknown host google.com
```

/etc/network/interfaces displays the minimal lo interface lines.

I'm running 11.10 last updated about a week ago on a lenovo R61i. The cable LEDs are all blinking normally. 

Thanks for any suggestions.

---

### Post by Ms. Daisy on 2012-04-09
According to the netstat output, you might be missing the gateway.  

Can you ping 192.168.1.1? That's probably your router's address.

---

### Post by qianian on 2012-04-09
If so, how to address the problem?

~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.20 icmp_seq=1 Destination Host Unreachable
From 192.168.1.20 icmp_seq=2 Destination Host Unreachable
From 192.168.1.20 icmp_seq=3 Destination Host Unreachable
From 192.168.1.20 icmp_seq=4 Destination Host Unreachable
From 192.168.1.20 icmp_seq=5 Destination Host Unreachable
From 192.168.1.20 icmp_seq=6 Destination Host Unreachable
From 192.168.1.20 icmp_seq=7 Destination Host Unreachable
From 192.168.1.20 icmp_seq=8 Destination Host Unreachable
From 192.168.1.20 icmp_seq=9 Destination Host Unreachable
From 192.168.1.20 icmp_seq=10 Destination Host Unreachable
From 192.168.1.20 icmp_seq=11 Destination Host Unreachable
From 192.168.1.20 icmp_seq=12 Destination Host Unreachable
From 192.168.1.20 icmp_seq=13 Destination Host Unreachable
From 192.168.1.20 icmp_seq=14 Destination Host Unreachable
From 192.168.1.20 icmp_seq=15 Destination Host Unreachable
From 192.168.1.20 icmp_seq=16 Destination Host Unreachable
From 192.168.1.20 icmp_seq=17 Destination Host Unreachable
From 192.168.1.20 icmp_seq=18 Destination Host Unreachable
From 192.168.1.20 icmp_seq=19 Destination Host Unreachable
From 192.168.1.20 icmp_seq=20 Destination Host Unreachable
From 192.168.1.20 icmp_seq=21 Destination Host Unreachable
From 192.168.1.20 icmp_seq=22 Destination Host Unreachable
From 192.168.1.20 icmp_seq=23 Destination Host Unreachable
From 192.168.1.20 icmp_seq=24 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
27 packets transmitted, 0 received, +24 errors, 100% packet loss, time 26144ms
pipe 3
~$

---

### Post by Ms. Daisy on 2012-04-10
> **qianian said:**
> If so, how to address the problem?
I'm not sure yet.  We'll need some more information to determine that.

Let's set it back to default settings and see what we've got.

Go to the network manager applet --> edit connections
highlight wired connection **(if you have more than one option please post here)**
click the edit button
go to the IPv4 tab
change Method: to Automatic (DHCP)
click save

then open a terminal & type
```
sudo ifdown eth0 && sudo ifup eth0
```Then ping 8.8.8.8 and ping [www.google.com]("http://www.google.com")  Post the results here.

Also post the output of ifconfig

---

### Post by qianian on 2012-04-10
Under Network Connections, I have a second option which I added per my first post, "Manual." This is the option that connects at startup. 

Per your instructions I opened the default Auto Ethernet to edit but IPv4 was already set to Automatic (DHCP).

I disconnected "Manual" from the panel and ran the commands as follows.

~$ sudo ifdown eth0 && sudo ifup eth0
[sudo] password for qian: 
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.
~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:c8:c6:03  
          inet6 addr: fe80::215:58ff:fec8:c603/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9554 (9.5 KB)  TX bytes:17530 (17.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12618 (12.6 KB)  TX bytes:12618 (12.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:b0:cd:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

~$ ping 8.8.8.8
connect: Network is unreachable
~$ ping google.com
ping: unknown host google.com


Then I reconnected Manual and ran the same sequence, with the only difference being the output of ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:15:58:c8:c6:03  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fec8:c603/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12264 (12.2 KB)  TX bytes:21747 (21.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15901 (15.9 KB)  TX bytes:15901 (15.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:b0:cd:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Thanks for your help.

---

### Post by Ms. Daisy on 2012-04-11
Which one shows the box checked that says "connect automatically" ?  Make sure it's the automatic (DHCP) one.

It looks to me like DHCP quit working.  I've seen lots of people lose their wireless connections, but I've never seen anyone lose their wired connection like this.  So I may not be much more help.  I'll see what I can find and post back.

Maybe in the mean time you could give this a try (if you haven't already):
1. Shut down all the computers & printers & devices on the network
2. turn off your router & unplug it.  
3. if you've got a modem, unplug & turn it off (if it's got a battery take it out for a few seconds)
4. check all the cords & connections in the computer, router & modem again, make sure they're fully seated & not damaged
5. put the battery back in & restart the modem.  Wait until all the lights are back on (mine takes 5 - 10 minutes)
6. Turn the router back on. Wait for it to fully come up.
7. Turn your computer back on. Make sure it's using the Automatic DHCP wired connection.
8. ping google & 8.8.8.8

---

### Post by qianian on 2012-04-12
Thanks -- I'm going to restart as you suggest in a moment. I didn't think this was relevant before but the wire connects to a Windows laptop using a USB mobile broadband modem for internet. 

Before I made the "Manual" connection Auto Ethernet was trying to connect automatically. It always ended with the Disconnected flag, though.

---

### Post by qianian on 2012-04-12
Restarted and replugged everything. With Auto Ethernet the only "Connect automatically" option, it tries to connect but ends "Disconnected" again. Same unknown, unreachable pingbacks.

I tried playing with the IPv6 Settings and got nothing. It's possible the cable is damaged even though it's showing the usual LEDs. I'll look for another cable but it's pretty rural out here.

Any other ideas?

---

### Post by Ms. Daisy on 2012-04-12
AHA!!!!  Give this a try, it's a bit old but I believe it should still work.

[http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/](http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/)

In that tutorial they change the one existing wired connection. I recommend that you change the manual connection that you recently created instead. Leave the automatic (original) wired connection alone.  

Also make sure you click the "connect automatically" box in the modified connection.

It probably goes without saying but I'll say it anyway, the laptop needs to be booted up for this to work.

---

### Post by qianian on 2012-04-12
I changed the "Manual" option to Shared with other computers IPv4 with no effect -- it appeared connected on reboot but same unreachable/unknown pingbacks. 

Then I changed IPv6 back to Automatic, keeping the new IPv4 Shared, and on reboot Network Manager flags "Wired Network Disconnected" and "Connection Established" alternating every few seconds. The icon is statically disconnected, though. 

When I had a wired connection a couple weeks ago it was automatically connected through a second laptop. I didn't have to make any adjustments to Network Manager. 

Thanks again for your efforts.

---

### Post by dandnsmith on 2012-04-13
With the current state of the internet, I wonder whether that IPv6 address is proving to be the problem. I cannot see any sign of the IPv6 stuff in the routing table - but then I don't have any IPv6 usage PCs to check it against.
What I do know is that, at one point I had a problem when the IPv6 stuff was enabled, but neither my router nor my ISP were prepared to handle IPv6, so, following some advice, I disabled the IPv6 and everything seemed to start working (more or less) properly.

---

### Post by qianian on 2012-04-17
Derek - I did play with the IPv6 to no effect.

Do you think this thread may be worth a try, and if so, how what addresses should I set?

[http://serverfault.com/questions/264308/ubuntu-wired-network-disconnected](http://serverfault.com/questions/264308/ubuntu-wired-network-disconnected)

---

### Post by qianian on 2012-04-17
Derek - I did play with the IPv6 to no effect.

Do you think this thread may be worth a try, and if so, how what addresses should I set?

[http://serverfault.com/questions/264308/ubuntu-wired-network-disconnected](http://serverfault.com/questions/264308/ubuntu-wired-network-disconnected)

---

### Post by Ms. Daisy on 2012-04-17
You have to know the addresses of the other computers on your network, plus that's essentially what you said you did already in post #1.

Up until now I assumed that everything between the internet and your ethernet cable was just dandy.  But that was a bad assumption.  Let's check it all out.

What is the name and model of the USB mobile broadband modem?  Is it the same one as a few weeks ago when everything worked?

Let's look at the Windows computer. It can connect to the internet, correct? Open a command prompt and type ```
ipconfig
```  Post the output here.  

Give this a try on the Windows computer (directions are for Vista but I'm fairly certain it's the same for Windows 7):
[http://windows.microsoft.com/en-US/windows-vista/Using-ICS-Internet-Connection-Sharing](http://windows.microsoft.com/en-US/windows-vista/Using-ICS-Internet-Connection-Sharing)

Come back and tell me whether network sharing was enabled before, and if it wasn't- is it now?

---

### Post by qianian on 2012-04-18
Both the modem and the Windows machine are different. I don't have access to any other.

ipconfig returns the command line with no output.

I did follow the instructions on that page to the best of my ability. I don't have a "Manage network connections" option but enabled sharing from the dialog box for "Local Area Connection" and set IPv4 to automatic. When I enable sharing from the "Venus Mobile" broadband modem dialog box, though, I get a popup

The user name and password for this connection cannot be saved for use by all users. As a result, Internet Connection Sharing can only dial this connection when you are logged on. To enable automatic dialing, you should create a new connection for all users, save your user name and password for all users, and then enable sharing for the new connection. 

I didn't think this mattered at first pass because I am always logged in as this user on the Windows machine. I cleared the boxes according to the ICS settings page.

It also appears only one connection can be enabled for sharing -- I take it that should be the Venus modem. I re-enabled that last, reconnected,  and disconnected and reconnected the Ubuntu from Network Manager. Still unknown/unreachable pingbacks.

---

### Post by Ms. Daisy on 2012-04-18
I found [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing"), which states > there is a bug which turn off and on the share connection. The  workaround for now is to set IPv6 options to Ignore and then sudo  killall dnsmasq. Reconnect and it should work.  Try that on the Ubuntu computer and see if it can connect. If not, then that means the Windows computer hasn't been set up properly to share its connection.  Answer the following questions if that didn't fix it:

1. What version of Windows is this computer running?

2. The Windows computer can access the internet, correct?

3.Right click on command prompt (before you open it) and run it as an administrator.
Then try ipconfig again.

4. Please post the model of your Venus USB broadband modem (for instance LG Venus VX8800). We need to find out if that specific type of modem will allow sharing of the connection.

---

### Post by dandnsmith on 2012-04-19
Let's hope it isn't Win7 - just found the opportunity to check on a Win7 PC, and found that, despite the help throwing up the same sequence as in the link you (Ms. Daisy) posted, there is no tab (for me) allowing for ICS.

---

### Post by Ms. Daisy on 2012-04-19
If you have Windows 7, use this

[http://answers.microsoft.com/en-us/windows/forum/windows_7-networking/how-to-enable-internet-connection-sharing-on/5a3e34ec-f0af-4a02-a588-e9f091711095](http://answers.microsoft.com/en-us/windows/forum/windows_7-networking/how-to-enable-internet-connection-sharing-on/5a3e34ec-f0af-4a02-a588-e9f091711095)

---

### Post by qianian on 2012-04-20
The problem must be with the Windows machine. It is Win 7.

I don't get an Admin option when I right-click on command. 

I followed the instructions to enable internet connection sharing. Then, under Network Connections, I saw the modem share box was unchecked again and re-checked it and specified sharing for LAN. I don't know why this keeps getting unchecked. 

I reconnected, made sure the wired option was set to Ignore IPv6, and got the same pingbacks.

I keep getting a "Windows Shell Common Dll" crash when I'm working on this. The details:

Problem signature:
  Problem Event Name:	APPCRASH
  Application Name:	rundll32.exe_shell32.dll
  Application Version:	6.1.7600.16385
  Application Timestamp:	4a5bc637
  Fault Module Name:	ntdll.dll
  Fault Module Version:	6.1.7600.16385
  Fault Module Timestamp:	4a5bdadb
  Exception Code:	c00000fd
  Exception Offset:	00046bd2
  OS Version:	6.1.7600.2.0.0.256.1
  Locale ID:	1057
  Additional Information 1:	7075
  Additional Information 2:	70759f0b794678fd767d3cfb0ad9069a
  Additional Information 3:	e23d
  Additional Information 4:	e23da38b8a3c5c35de97d53eb3eeac80

Read our privacy statement online:
  [http://go.microsoft.com/fwlink/?linkid=104288&clcid=0x0409](http://go.microsoft.com/fwlink/?linkid=104288&clcid=0x0409)

If the online privacy statement is not available, please read our privacy statement offline:
  C:\Windows\system32\en-US\erofflps.txt

---

### Post by Ms. Daisy on 2012-04-20
You have to be an admin to make the change permanent I imagine.  Are you logged in as the admin user?  

When  you right click command prompt you get the choice of "run as". Click that and you should get a window where you choose which rights.  Choose the admin.  You may need a password if you set one up.

---

### Post by dandnsmith on 2012-04-21
I think I may be getting confused by some of the detail but, if you're trying to perform ICS with the Win7 box as the one doing the sharing, and also the one which connects to the internet through the modem, is it reasonable to expect the modem to be sharable?
After all, all the traffic will be under the control of the Win7 box, which will take care of the routing to and from the internet.

---

### Post by Ms. Daisy on 2012-04-21
Not sure where you're going...

---

### Post by qianian on 2012-04-21
I don't have any admin options. There's only one user at logon and when I right-click command there's no option Run as...

btw I don't have the factory packaging for the modem so no more info about it for now. Sorry I'm so limited here.

---

### Post by Ms. Daisy on 2012-04-22
OK, I've got to tell you.  I feel like I'm wandering aimlessly in the woods here.  We're all over the place and we're not really getting anywhere.  I need some clarity on a few things. 

First, can you access the internet on the Windows computer right now, with the Venus USB broadband modem connected to the Windows computer?

---

### Post by dandnsmith on 2012-04-22
Good question to clear the ground Ms. Daisy.

I suggest he also check whether he is an administrator on the Win7 box, as I'm beginning to wonder - can do this via Control Panel | User Accounts and Family Safety |User accounts where the account will show its status.

---

### Post by qianian on 2012-04-22
I've been there all along, Ms Daisy... sorry to drag you in. 

Yes, I am using the Win 7 laptop with Venus Mobile modem for internet. I couldn't get the Linux laptop to see it when I try to plug it in directly, thus the effort to fix wired.

The only user is logged in and listed as Administrator under User Accounts.

---

### Post by Ms. Daisy on 2012-04-22
Unfortunately we have reached the far edges of my abilities. Plus I think my inexperience has kind of made a mess of this thread.  Here's what we need to do.  I've talked it over with several folks much more experienced than I.

Qianian, start a new thread titled *connection sharing: Win 7 to Ubuntu.* Give as much detail as possible, like "I have a Windows 7 laptop (toshiba satellite BS6900 or whatever yours is) that successfully connects to the internet using a Venus USB Broadband modem (model number BS6969 or whatever) that is plugged directly into the machine.  I have a separate Ubuntu 11.10 laptop (Acer BS69 or whatever it is).  When I plugged the modem into the Ubuntu laptop, the modem is not recognized, so I cannot connect to the internet on the Ubuntu computer.  What is the best way to connect both computers to the internet using the Venus USB Broadband modem?  And how do I achieve that?"

 (Add the model info for the Venus modem if you can find it, you'll get much better responses. Open Device Manager in Windows 7 and see if it's listed under "network adapters" or "universal serial bus controllers").

---

### Post by qianian on 2012-04-23
[http://ubuntuforums.org/showthread.php?p=11865985#post11865985](http://ubuntuforums.org/showthread.php?p=11865985#post11865985)

Thanks again, Ms Daisy.

---

### Post by Ms. Daisy on 2012-04-23
Sorry I couldn't be of more help. Looks like you've got one good response already.

---

