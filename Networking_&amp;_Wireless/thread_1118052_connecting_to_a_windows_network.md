---
title: "connecting to a windows network"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by Bensky5012 on 2009-04-06
Hi all I am new to ubuntu, have been a windows user for quite sometime.  I'm trying to set up a connection on my laptop through Ubuntu.  My network is set up so that my desktop which is running Windows XP is where the connection is coming through.  I am trying to get access through a wireless router and I can see the Windows Network in Places/Network, however I cannot connect to it.  

Thanks in advance.
Ben

---

### Post by cosine352 on 2009-04-06
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Bensky5012 on 2009-04-06
I've installed samba, but still having trouble.  What do I have to set up with Samba to be able to access the network?

---

### Post by MockY on 2009-04-06
Browsing windows shares via nautilus is broken, and has been for a very long time. You have to access the share directly.
In nautilus (open any folder, click the notepad icon to the left of the location bar) type ```
smb://ipnumbertoxpmachine/folderthatisshared
```

---

### Post by Bensky5012 on 2009-04-06
I'm not trying to share a folder, I am just trying to access the internet.

---

### Post by MockY on 2009-04-06
> **Bensky5012 said:**
> I am trying to get access through a wireless router and I can see the Windows Network in Places/Network, however I cannot connect to it
That led me to believe that you were in fact trying to access a Samba share, which I was not alone in thinking.
What is the outcome of the ifconfig command in terminal?

---

### Post by cosine352 on 2009-04-06
> **Bensky5012 said:**
> I'm not trying to share a folder, I am just trying to access the internet.

What is your problem?

---

### Post by Bensky5012 on 2009-04-06
Output of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:18:8b:ce:af:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)


When I click on the connection icon in the upper right corner next to the clock, nothing is showing up in Wireless connection.  I click on connect to hiden wireless network and pick the connection I setup then click connect. A message pops up that "The network has been disconnected".

---

### Post by Bensky5012 on 2009-04-06
up

---

### Post by cosine352 on 2009-04-07
[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html)

---

### Post by Bensky5012 on 2009-04-07
Still havent figured out what to do...

I go to Places->Network, right click the windows network icon and go to properties.  There is nothing that says enable this connection.

Edit: Is there a reason the connection shows up as hidden wireless connection?

---

### Post by Bensky5012 on 2009-04-07
up

---

### Post by gtr32 on 2009-04-07
> **Bensky5012 said:**
> My network is set up so that my desktop which is running Windows XP is where the connection is coming through.

Easiest way would be to set your router to handle the connection instead of Windows. Any specific reason why Windows is the gateway?

---

### Post by Bensky5012 on 2009-04-07
The software for the wireless router was run on the Windows XP computer and so I set up the network through that.

edit: I'm not sure if the connection is set up through Windows XP or through the router itself.  All I know is that it shows up as a windows network on ubuntu and I can't connect to it.

---

### Post by gtr32 on 2009-04-07
> **Bensky5012 said:**
> The software for the wireless router was run on the Windows XP computer and so I set up the network through that.

What kind of router? Set it as the gateway + DHCP server for local network and you save yourself a lot of headache.

---

### Post by Bensky5012 on 2009-04-07
The wireless router is Netgear 54 Mbps Wireless Router WGR614v7

How do I set the router as the gateway + DHCP server for the local network?

---

### Post by lisati on 2009-04-07
If connecting to the internet is the issue, then it might be easier to go through a router. Another option is to enable internet connection sharing at the Windows end.

For sharing files (which is what I first thought) there are plenty of tutorials e.g. [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by lisati on 2009-04-07
> **Bensky5012 said:**
> The wireless router is Netgear 54 Mbps Wireless Router WGR614v7

How do I set the router as the gateway + DHCP server for the local network?

ah yes, that's the model I have, with a wired connection to the ADSL modem. Once it was setup  to work with Windows using the setup CD, and tweaked to have WPA security, all I had to do was click on the networking icon in Ubuntu, choose my wireless network, put in the passphrase when requested, and it worked.

To configure the router, a wired connection is sometimes easier while you're setting things up. Open up a browser and go to [http://routerlogin.net](http://routerlogin.net) - you will be asked for a user name and password. The default username is "admin" and the default password is "password" (change a.s.a.p.)

EDIT: **I forgot:** I meant the router setup CD not the Windows setup CD

---

### Post by gtr32 on 2009-04-07
[ftp://downloads.netgear.com/files/wgr614v7_setup_manual_21apr06.pdf](ftp://downloads.netgear.com/files/wgr614v7_setup_manual_21apr06.pdf)

I am assuming your router is connected to your DSL/Cable/Fiber/etc modem. If not, that's where it needs to go.

You need to contact your service provider if you don't know your username and password for your account (assuming you need it). Many people forget it or never knew it if someone else installed it for them.

---

### Post by Bensky5012 on 2009-04-07
What do I have to setup in ubuntu to be able to use this connection?  Should it automatically work when I provide my key and network name?  Because I have this already setup, but when I click connect it says the network has been disconnected.

---

### Post by gtr32 on 2009-04-07
Can you try wired connection to rule out wireless issue?

So to clarify...is this your connection setup 

1) ISP -> Router -> LAN/Wireless?

Or is it 

2) ISP -> Windows -> Router -> Wireless? 

You mentioned you are sharing the connection in your Windows machine which you should not do and your route should be #1 setup.

How is your wireless card setup? Static IP or dynamic? 

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

---

### Post by Bensky5012 on 2009-04-07
I'm not sure whether it is:

1) ISP -> Router -> LAN/Wireless?

Or it is

2) ISP -> Windows -> Router -> Wireless? 

How can I find this out?  How can I find out whether I'm using static or dynamic IP?

---

### Post by lisati on 2009-04-07
> **Bensky5012 said:**
> What do I have to setup in ubuntu to be able to use this connection?  Should it automatically work when I provide my key and network name?  Because I have this already setup, but when I click connect it says the network has been disconnected.

Once mine was set up, all I had to do was click on the network manager icon, choose my network, and provide my key when prompted.

I'm not sure of the OP's intent: my setup is laptop->Netgear router(both wireless and wired)->Thomson ADSL router/modem->internet

---

### Post by Bensky5012 on 2009-04-07
Okay, the network is setup, I click on the network icon, click connect to hidden wireless network.  Pick my connection where my SSID and Key are saved to and then click connect.  When I do this it says "the connection to the network has been disconnected"

Anyone else have some suggestions?

---

### Post by stchman on 2009-04-07
> **Bensky5012 said:**
> Hi all I am new to ubuntu, have been a windows user for quite sometime.  I'm trying to set up a connection on my laptop through Ubuntu.  My network is set up so that my desktop which is running Windows XP is where the connection is coming through.  I am trying to get access through a wireless router and I can see the Windows Network in Places/Network, however I cannot connect to it.  

Thanks in advance.
Ben

Let me get this straight, your XP machine is acting as your router?

If yes then obviously you have 2 ethernet cards in your XP PC.  Do you have ICS enabled in Windows XP?  Do you have the wireless access point (WAP) hooked up to the 2nd ethernet card.

If yes to all the above then you shoulc be able to connect to the WAP.

---

### Post by Bensky5012 on 2009-04-07
I don't think I have two ethernet cards in my XP machine.  Im not sure if the connection is coming through the windows pc or the router.  And I'm not sure what ICS is or if I have it enabled but I would assume not.

edit: I think that the connection is set up through the router, but I can not connect to it from ubuntu.  Im dual booting ubuntu and windows on my laptop and I can connect from the windows partition but not the ubuntu.

---

### Post by gtr32 on 2009-04-07
> **Bensky5012 said:**
> edit: I think that the connection is set up through the router, but I can not connect to it from ubuntu.  Im dual booting ubuntu and windows on my laptop and I can connect from the windows partition but not the ubuntu.

Since you're dual booting I think you're connected to a router, good. You can check this by looking your cabling. Where does the cable from your modem go to? Router most likely. Have you tried wired connection yet? Have you double checked wireless password settings if they are correct?

Could you do this:

1) Open terminal, type command: sudo tail -f /var/log/messages
2) Try to connect wireless again

What do you see in terminal? 

> **Bensky5012 said:**
> How can I find this out? How can I find out whether I'm using static or dynamic IP? 

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

---

### Post by Bensky5012 on 2009-04-07
ben@ben-laptop:~$ sudo tail -f /var/log/messages
[sudo] password for ben: 
Apr  7 21:14:40 ben-laptop kernel: [  137.432920] type=1503 audit(1239153280.039:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6228 profile="/usr/sbin/cupsd"
Apr  7 21:14:40 ben-laptop kernel: [  137.432942] type=1503 audit(1239153280.039:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6228 profile="/usr/sbin/cupsd"
Apr  7 21:14:40 ben-laptop kernel: [  137.432957] type=1503 audit(1239153280.039:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6228 profile="/usr/sbin/cupsd"
Apr  7 21:14:40 ben-laptop kernel: [  137.432972] type=1503 audit(1239153280.039:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6228 profile="/usr/sbin/cupsd"
Apr  7 21:14:40 ben-laptop kernel: [  137.432987] type=1503 audit(1239153280.039:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6228 profile="/usr/sbin/cupsd"
Apr  7 21:14:40 ben-laptop kernel: [  137.433002] type=1503 audit(1239153280.039:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6228 profile="/usr/sbin/cupsd"
Apr  7 21:14:40 ben-laptop kernel: [  137.433022] type=1503 audit(1239153280.039:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6228 profile="/usr/sbin/cupsd"
Apr  7 21:14:40 ben-laptop kernel: [  137.433037] type=1503 audit(1239153280.039:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6228 profile="/usr/sbin/cupsd"
Apr  7 21:14:40 ben-laptop kernel: [  137.433153] type=1503 audit(1239153280.039:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6228/net/dev" pid=6228 profile="/usr/sbin/cupsd"
Apr  7 21:14:56 ben-laptop kernel: [  153.985495] CE: hpet increasing min_delta_ns to 113904 nsec

---

