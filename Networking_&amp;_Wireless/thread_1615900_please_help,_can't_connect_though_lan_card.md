---
title: "please help, can't connect though lan card"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by Pralay on 2010-11-07
Hi there,
I am very much new to ubuntu, was using windows this far, but really thinking about shifting to ubuntu ( I still have dual booting in my pc). Anyway, I have a lan card installed in my pc which connect to a dsl modem for broadband connection. some days ago I tried ubuntu 8.04 LTS. I tried sudo pppoeconf and just followed the steps and it easily got connected to internet. Then couple of days ago, I freshly installed ubuntu 10.10. But since then I havn't been able to connect to internet.
I tried sudo pppoeconf and followed the same steps, but to no avail.
When I tried ifconfig -v it gave me following output,

eth0      
Link encap:Ethernet  HWaddr 00:a1:b0:60:51:29             
inet6 addr: fe80::2a1:b0ff:fe60:5129/64 Scope:Link           
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
RX packets:197 errors:0 dropped:0 overruns:0 frame:0           
TX packets:199 errors:0 dropped:0 overruns:0 carrier:0           
collisions:0 txqueuelen:1000            
RX bytes:11880 (11.8 KB)  TX bytes:10839 (10.8 KB)           
Interrupt:18 Base address:0x8c00   

lo        
Link encap:Local Loopback             
inet addr:127.0.0.1  Mask:255.0.0.0           
inet6 addr: ::1/128 Scope:Host           
UP LOOPBACK RUNNING  MTU:16436  Metric:1           
RX packets:1016 errors:0 dropped:0 overruns:0 frame:0           
TX packets:1016 errors:0 dropped:0 overruns:0 carrier:0           
collisions:0 txqueuelen:0            
RX bytes:78576 (78.5 KB)  
TX bytes:78576 (78.5 KB) 

I just can't connect. Like I said, I am a novice, so please help me out. I am really planning to scrap windows, but unless i can connect, this is not gonna happen. anyone out there an help? :confused:

---

### Post by grahammechanical on 2010-11-07
From the listing that you give eth0 is not only UP but also RUNNING. This usually means that you are connected by ethernet cable to the modem. Do you see the network manager icon in the top panel? For wired connection it is two arrows pointing in opposite directions. For wireless it is a wedge of rings radiating upwards. 

If you left click you should get a menu listing your network connections. Auto eth0 should be there with Disconnect underneath. If you right click you should see a tick against Networking. Clicking this will switch networking on and off. You can also use this menu to Edit Connections and set eth0 to connect automatically and be available to all users.

If you see these things listed as I have described the you should get access to the internet. Perhaps the router settings are incorrect.

Regards.

---

### Post by grahammechanical on 2010-11-07
I have just compared your listing with my setup and underneath
> Link encap: Ethernet etc., and > above inet addr:fe::2a1 etc.,
you should see something like > inet addr: 192.168.1.64

This is the IP address of my modem. It tells me that I am connected to the modem. Your listing does not show this. Your modem will have a similar address. In fact if I change the number 64 into 254 and put the group of numbers as a http:// address in the web browser, then I can access the setup program of the modem. Can you do this with your modem? Do you have any instructions on the modem available? I am directing your attention to the modem and not the setup of 10.10.

regards.

---

### Post by Pralay on 2010-11-08
Thanks a lotgrahammechanical for your quick reply.
To answer your questions, when I first started Ubuntu right after installing, I saw the icon of wedge of rings radiating upwards you mentioned, in the top right menu bar. Then I tried  "sudo pppoeconf" and setup my lan card there. After that, when I restarted My pc, i haven't seen that very icon up in the menu bar. But problem is, I haven't seen the icon of two arrows pointing in opposite directions either.:confused:

As fas ar the ip address is concerned, you are right, I am also thinking that my ip should be something similar to what you have got. My modem does not come with any instructions. Moreover I can easily connect from windows. In windows, I just power it on and connect through lan card and I am connected to internet.

I am really confused that if ubuntu can detect the lan card, why it is not picking up the IP? Why is it showing this weird thing (fe80::2a1:b0ff:fe60:5129/64) as inet6 addr?

I must be missing something. Can you please guide me what to do now? Are there any other settings? If I need to make change in the modem, how should I make it?

Please reply.

---

### Post by dineshs on 2010-11-08
Please try this
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by Pralay on 2010-11-08
Hi dineshs,
I tried exactly what you have instructed, but yet to get the desired result.

What is most striking, even after following your steps, my NM in top menu bar still showing icon for wireless connection instead of 2 arrows one up, one down. This is really confusing. When I click on NM icon and select dsl connection, it tries to connect, but icon does not change to the icon for wired connection. Somehow I feel, this is where the main problem is. I don't have any wireless setup. But ubuntu might be trying to connect using wireless device even though I select dsl connection.

This is really weird. Can you please guys help me to make step forward? I really need this and I look forward to your help.

I am attaching screenshot.

Please help.

---

### Post by dineshs on 2010-11-09
> When I click on NM icon and select dsl connection, it tries to connect, but icon does not change to the icon for wired connection
Dont worry about the icon.The exclamation mark means disconnected
Please post the results of```
sudo dhclient eth0
```then```
sudo lshw -C network
```By the way Do you use a PPPoE dialler in windows? What does ```
ipconfig /all
``` say in[COLOR="Red"] windows[/COLOR]

---

### Post by Pralay on 2010-11-09
Hi dineshs,
Thanks a lot for your help.
The result of sudo dhclient eth0 is 
> 
Internet Systems Consortium DHCP Client V3.1.3

Copyright 2004-2009 Internet Systems Consortium.

All rights reserved.

For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)



Listening on LPF/eth0/00:a1:b0:60:51:29

Sending on   LPF/eth0/00:a1:b0:60:51:29

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14

And output of sudo lshw -C network is,

> *-network               

       description: Ethernet interface

       product: VT6105/VT6106S [Rhine-III]

       vendor: VIA Technologies, Inc.

       physical id: 2

       bus info: pci@0000:01:02.0

       logical name: eth0

       version: 8b

       serial: 00:a1:b0:60:51:29

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s

       resources: irq:18 ioport:d800(size=256) memory:ff8ffc00-ff8ffcff

I have attached the screenshot of the windows ipconfig /all result.

Thanks again for your effort.
Please get me out of this trouble. :(

---

### Post by Pralay on 2010-11-09
Hi dineshs,
Just to let you know, I use BSNL broadband service and a PPPoE dialler.
They provided me a Dataone UT300RTU Modem and I bought a lan card myself. All i did was to attach the lan card in my pc, installed the driver, attached it with modem with the cord given.

Then from windows network and internet connection manager, created a new connection with username password for my broadband connection. Every time I need to connect to internet, i click on that icon, provide password and its connected.


I know these are very simple information, but thought might help you to track down the problem.

Thanks again. :)

---

### Post by grahammechanical on 2010-11-09
Hi Pralay

I did not think that my post would be of much help, except to remove the feeling that no one is helping and it did get the attention of someone more experienced than I. As Dinesh says, do not worry about the icon. The wedge of rings with a red exclamation mark is the standard icon to show that networking is disconnected. I get it when I disable networking. The red exclamation mark will disappear if a wireless connection is made and the icon itself will change to the two arrows when the connection is by wire. So, the system is not trying to use wireless.

Regards

---

### Post by Pralay on 2010-11-09
Hi grahammechanical and dineshs,

Please accept my gratitude as you are paying so much attention to a novice like me.
I am still not out of the trouble. :(
Just help me to start using ubuntu. And I can't do that unless I can get connected to internet.

Regards,

---

### Post by grahammechanical on 2010-11-09
Pralay

When  you right click the network manager icon does Enable Networking have a tick mark to the left of it? Is it the same for Enable Wireless? If they do not then click on them. Also from the same menu you can select Edit Connections. Choose the wireless tab. Select your wireless connection and click Edit. Confirm that you have the right password. It is under wireless security. You can click Show Password to see what the actual password is. This is not your login password. I have made that mistake before. It is the wireless key or WPA-PSK password. 

I have never used ppoeconf. So, I do not know how that works. Does not your modem dial the ISP as part of its startup procedure? I used to use a dial up modem then I got broadband and now it is connected to the ISP from startup until I switch it off. I do not use DSL in network manager. If the modem connects to the ISP then all we need to do is connect to the modem. And network manager does this automatically as part of the boot process.

When I had a dial up modem I had to issue a command for the modem to dial the ISP telephone number. With Ubuntu 7.04 I could use network manager to do this. But over the years this ability has been removed from network manager. I think that the developers assume that everyone has an always on broadband connection. And this from company based in Africa. So, we may be trying to solve the wrong problem. Sorry for the long post.

Regards.

---

### Post by dineshs on 2010-11-10
UT300R2U is a DHCP enabled modem and you should get an IP when you run *sudo dhclient*(Assuming  you havent disabled DHCP in modem or edited  /etc/dhcp3/dhclient.conf by hand)So I think (not sure)it is a LAN driver issue and I am not an expert to suggest a remedy for that.
> product: VT6105/VT6106S [Rhine-III]
vendor: VIA Technologies, Inc.

---

### Post by chili555 on 2010-11-10
> **Pralay said:**
> Hi dineshs,
Thanks a lot for your help.
The result of sudo dhclient eth0 is 


And output of sudo lshw -C network is,



I have attached the screenshot of the windows ipconfig /all result.

Thanks again for your effort.
Please get me out of this trouble. :(The screenshot says the driver is r8139. Your lshw above says it's via-rhine. What explains this? Do you have more than one ethernet adapter? Please post:```
lspci -nn
dmesg | grep eth
```I wonder if we have a mis-configuration.

---

