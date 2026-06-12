---
title: "Ubuntu 10.04 cannot network"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by pellyhawk on 2012-12-04
Hi, I am a newbie for Linux and installed a dial booting OS(Windows XP and Ubuntu 10.04). Windows XP runs very well, but Ubuntu cannot visit websites except [www.google.com](www.google.com).

Especially, while starting Ubuntu, "init; ureadahead main process (***) terminated with status 5" emerged, and *** is a number. Every time, this number is different. I noticed that 386, 306, 293, 297, 280 etc ever emerged.

```
mike@mike-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:57:3a:96  
          inet addr:192.168.179.205  Bcast:192.168.179.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe57:3a96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21459 errors:257 dropped:0 overruns:0 frame:257
          TX packets:7880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000 
          RX bytes:16052319 (16.0 MB)  TX bytes:588923 (588.9 KB)
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
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mike@mike-laptop:~$ 
mike@mike-laptop:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=66.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=51.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=46 time=51.5 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=46 time=64.8 ms
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 51.173/58.432/66.151/7.082 ms
mike@mike-laptop:~$ ping www.ibm.com
PING www.ibm.com.cs186.net (129.42.60.216) 56(84) bytes of data.


``` 

Any help is welcome. Thanks in advance.

---

### Post by mörgæs on 2012-12-04
10.04 had several problems with ureadahead. I would recommend a fresh install of 12.04 or 12.10.

---

### Post by pellyhawk on 2012-12-04
> **mörgæs said:**
> 10.04 had several problems with ureadahead. I would recommend a fresh install of 12.04 or 12.10.

But, why I cannot network? I can access to network at my home, but cannot at my office.

---

### Post by varunendra on 2012-12-05
I don't think the ureadahead bug is related with the network problem, but I concur with *mörgæs* about switching to 12.04 or 12.10. Lucid (10.04) will reach its EOL ([end of life]("https://wiki.ubuntu.com/Releases")) in April next year, so it make sense to upgrade now, especially if you are facing any OS dependent problems.

As for the current problem -
> **pellyhawk said:**
> Ubuntu cannot visit websites except [www.google.com](www.google.com).
Google.com is a very light page, opens quickly on even extremely slow connections. But heavy pages may not load and open if the connection speed is too slow or has physical errors.

I can't say why XP is working better but this doesn't look right to me -
> **pellyhawk said:**
> 
```
mike@mike-laptop:~$ ifconfig
..
          RX packets:**21459** **errors:[COLOR="Red"]257[/COLOR]** dropped:0 overruns:0 **frame:[COLOR="Red"]257[/COLOR]**
```

Check your cable, connectors and ports. If you can, try replacing the cable with a fresh, tested one. If that doesn't help, you may try setting **MTU** to a lower value, like 1492 using **NM applet > Edit Connections**, or by the command -
```
sudo ifconfig eth0 mtu 1492
```
but try this only after double-checking your physical connections.

Also -
> **pellyhawk said:**
> ```

mike@mike-laptop:~$ ping **[www.ibm.com](www.ibm.com)**
PING [www.ibm.com.cs186.net](www.ibm.com.cs186.net) (129.42.60.216) 56(84) bytes of data.

```
I just tried pinging ibm.com myself and didn't get any replies. So I guess it doesn't support ping requests. How about -
```
ping -c4 www.ubuntu.com
```

And can you successfully run an update in terminal? -
```
sudo apt-get update
```
does it return any errors?

However, if the physical connection is okay and setting MTU to a lower value doesn't help, I would once again recommend to switch to 12.04 for any further troubleshooting. Although we can proceed with 10.04 if you wish so.

---

### Post by pellyhawk on 2012-12-06
My OS is decided by my company's IT administrator, so I cannot upgrade:( 

I almost forget tell you that I can visit websites very well at my home.

I have checked my cable and it is OK. Then I followed your suggestion and got these results
```

mike@mike-laptop:~$ ping -c4 www.ubuntu.com
PING www.ubuntu.com (91.189.89.88) 56(84) bytes of data.
64 bytes from privet.canonical.com (91.189.89.88): icmp_seq=1 ttl=44 time=304 ms
64 bytes from privet.canonical.com (91.189.89.88): icmp_seq=2 ttl=44 time=304 ms
64 bytes from privet.canonical.com (91.189.89.88): icmp_seq=3 ttl=44 time=313 ms
64 bytes from privet.canonical.com (91.189.89.88): icmp_seq=4 ttl=44 time=303 ms

--- www.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 303.958/306.575/313.798/4.208 ms
mike@mike-laptop:~$ sudo apt-get update
[sudo] password for mike: 
Hit http://dl.google.com stable Release.gpg
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US                                                                                     
Hit http://dl.google.com stable Release                                                                                                                      
Get:1 http://cn.archive.ubuntu.com lucid Release.gpg [189B]                                                                                       
Hit http://dl.google.com stable/main Packages                                                                                                          
Get:2 http://security.ubuntu.com lucid-security Release.gpg [198B]       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://deb.opera.com stable Release.gpg                               
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US         
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://deb.opera.com stable Release                                   
Ign http://deb.opera.com stable/non-free Packages                         
Ign http://deb.opera.com stable/non-free Packages   
Hit http://deb.opera.com stable/non-free Packages   
51% [1 Release.gpg 0B/189B 0%] [Waiting for headers]                 

```

I tried to reconfigure MTU in NM applet, but the buttons of "Edit" and "Delete" is grayed. Thus I cannot modified MTU. Why they are grayed? (I upload the screenshot)

And I found the network speed is not very high while accessing to network via Windows XP. I guess company's IT limit our network speed. Will MTU affect my access and why MTU will affect it? It seems MTU does not affect my access but my network speed while logging on by Windows XP.

Thanks a lot.

---

### Post by varunendra on 2012-12-06
> **pellyhawk said:**
> I almost forget tell you that I can visit websites very well at my home.
Then my first doubt is firewall settings in your workplace, meaning - maybe your employer has blocked access to certain websites on purpose. But if you can access the same sites on XP, then maybe there is something else affecting Ubuntu. Your ping and update outputs look normal.

> **pellyhawk said:**
> I tried to reconfigure MTU in NM applet, but the buttons of "Edit" and "Delete" is grayed. Thus I cannot modified MTU. Why they are grayed? (I upload the screenshot)
Your screenshot suggests that the network is not managed by Network Manager, but most probably by /etc/network/interfaces file instead. That's why NM can not edit or change the settings and that's why the edit button is greyed out. To change settings we would have to edit the "interfaces" file. For now, let's just take a look at it. Please post the output of -
```
cat /etc/network/interfaces
```

> **pellyhawk said:**
> Will MTU affect my access and why MTU will affect it? **[COLOR="Navy"]It seems MTU does not affect my access but my network speed while logging on by Windows XP.[/COLOR]**
I'm not sure I understand correctly the part highlighted in Blue above. Do you mean you tried changing MTU in XP? Please explain it for me.

MTU is the maximum size of packets that can be transmitted over the network ([more info]("https://en.wikipedia.org/wiki/Maximum_transmission_unit")). If it is larger than the size any of your network devices like router, firewall etc. can handle, it will cause malformed packets and thus slow speeds, sometimes even a total blackout! It is usually set to '1492' in Windows (XP, and I believe in others too), and since Windows is usually the standard for most of the vendors, that value is supposed to be more promising if such bottleneck with MTU exists on the network.

---

### Post by pellyhawk on 2012-12-06
> **varunendra said:**
> 
Will MTU affect my access and why MTU will affect it? It seems MTU does not affect my access but my network speed while logging on by Windows XP.


I meant while logging on Windows XP, I have not set MTU, and networking is very good. I guess MTU will not affect access but speed. But after you clarified MTU, I knew I make a big mistake.

I input:
```
cat /etc/network/interfaces
```
and got:
```

auto lo
iface lo inet loopback



auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```

I replaced these with my VMWare Ubuntu 10.04 /etc/network/interfaces's content
```
auto lo
iface lo inet loopback
```
Then, reboot Ubuntu 10.04 and this time I can edit or delete this connection. I deleted it and Network Manager create an connection itself(I did not do it manually). But I still cannot access to network until I modified MTU by "1492" as you told me before. I succeed at last. However, I did not understand why modify the /etc/network/interfaces which is what I need to study later. Are what I modified right? 

I also found I can access to network by wireless, but I do not know how to set which is the first access and which is the second(Surprisedly, wireless connection is created automatically, just like wired connection. Why wired and wireless are created aumatically without my permission to create them?).

---

### Post by varunendra on 2013-01-11
I don't think such a late reply would mean anything to you, but since your questions are still unanswered, I'll try to explain them in short-
> **pellyhawk said:**
> I succeed at last. However, I did not understand why modify the /etc/network/interfaces which is what I need to study later. Are what I modified right?
The /etc/network/interfaces file is the traditional way of settin up network connections in Linux, still used in all GUI-less versions (like server installations), and modern applications like Network Manager are designed to respect that tradition.

By default, if an interface is listed in 'interfaces' file, NM will not manage it. In order to have NM control it, either you need to delete (which you did) or 'comment out' the interface(s) in that file *(by adding a **#** at the start of lines)*, or you'll have to change the default setting of NM (by changing 'Mode' managed=False to managed=True in /etc/NetworkManager/NetworkManager.conf file).

In order to aviod conflict over an interface's control, resulting in possible errors, it is always recommended to use either NM or the 'interfaces' file, but not both at the same time.

> I also found I can access to network by wireless, but I do not know how to set which is the first access and which is the second(Surprisedly, wireless connection is created automatically, just like wired connection. Why wired and wireless are created aumatically without my permission to create them?).
Usually, the wired interface is given priority over wireless interface. As far as I know, there is a way to change the order of priority, but don't remember how.

NM creates the connections automatically because it is designed that way. As soon as you give the control of an interface to NM, it assumes that you want it to create a logical connection and connect it automatically if possible (that is, if DHCP is enabled on your network).

If you do not want it to create automatic connections for you, simply 'un-tick' the "Enable Wireless" or even "Enable Networking" option itself (disabling NM altogether) in the drop-down menu of nm-applet. If you only want it to stop connecting automatically, edit the desired connection ("Edit connections" in drop-down menu > double-click the desired connection) and 'Clear' the checkbox that says - "Connect Automatically".

Hope this answers your curiosity if you haven't already found the answers yourself.

If your original problem was permanently solved, please mark this thread as [Solved] to help others too.

---

### Post by pellyhawk on 2013-01-12
Thank you for your reply:D

---

