---
title: "https://answers.launchpad.net/ubuntu/+source/yelp/+question/26631"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by labinnsw on 2009-06-07
> ee, When I boot from CD Ubuntu 8.10, I can connect to internet instantly. Even it does not ask my details of services provider. It even do not ask me usename and password of broadband service provider.

My connection icon on right top bar, when I right click it it shown "connection information" and "edit connection"
In connection information it shows Auto eth0 as default and shows its information.
If I click edit connection , i get a window in which "Wired" tab I select "autoeh0" and click edit to see details. It shows MAC address as 00:24:8c:0C:29:8C. ALL OTHE TABS HAVE NOTING IN IT.
When I left click connection icon on right top bar, I can see a radio button (selected) with Auto eth0 .

Now when (from cd booting mode itself) I go to System - administration - networking tool - I get device networking tool.
There are two 1) Loop back and 2) Ethernet Interface eth0 .
In ethernet interface, there are two protocol Ipv4 and ipv6

Now when restart my system and remove cd and book from my hard disk ubuntu 8.10 and right click connection icon on right top bar, I do not see connection information. Also it has only lo and no mac address.

When I click system - administration - networking tool - device ntetworking tool there is loop back with all details and in ethernet interface I DO NOT FIND IPV4 AND ITS DETAILS.

I think this is the problem due to I can not connect while booting from my hard disk.
My computer was with Window xp with 4 partitions. I installed ubuntu 8.10 on saparate partition. This time I was not having zte modem and broadband connection.
After a week I purchased ZTE modem and broadband connection and started it in windows. But when i booted my machine from bunutu, i found it is not connection to internet.
I tried to boot Ubuntu from CD and I found that without any setting every time I can connect to internet.
I do not have hart to reinstall Ubuntu as I am scared I may mess up with everything.

CAN ANYONE SHOW ME WHERE I AM DOING MISTAKE IN SETTING?
From where can I set my interent connection?
Hasit

I have posted this here so that Hasit can benefit from the expertise of the entire community. [The original can be found here.]("https://answers.launchpad.net/ubuntu/+source/yelp/+question/26631")

---

### Post by labinnsw on 2009-06-07
> Up to manual formating opotion I did everything as per your guidance.
Even what image you sent is also available.
Then I selected my sda8 and ext 3 and mount point /
then I clicked forward.
It showed me a window with a warning that all my data will be removed for
**selected** partiting.
I do not want this. I want my windowxp as it is .
Will my other partitions be removed? Will my other data lost or just sda8
ext3 and swap will be over written?
( I selected Format check box after selecting my drive in which ubuntu is
installed and edited it while selecting / and ext 3 )
Am I doing everything right?
Hasit

If you had contiunued and not selected your Windows partition, it would not be formatted. Since only the Ubuntu partition was selected, only the Ubuntu partition would be formatted. All other partitions would remain untouched.

---

### Post by Hasit on 2009-06-07
When I boot my PC (installed with winxp and ubuntu 8.10 on two different partitions) from CD Ubuntu 8.10, I can connect to internet instantly. Even it does not ask my details of services provider. It even do not ask me usename and password of broadband service provider. IT does not ask any details at all and when I click Firefox it connect to ineternet.

My connection icon on right top bar, when I right click it it shown "connection information" and "edit connection"
In connection information it shows Auto eth0 as default and shows its information.
If I click edit connection , i get a window in which "Wired" tab I select "autoeh0" and click edit to see details. It shows MAC address as 00:24:8c:0C:29:8C. ALL OTHE TABS HAVE NOTING IN IT.
When I left click connection icon on right top bar, I can see a radio button (selected) with Auto eth0 .

Now when (from cd booting mode itself) I go to System - administration - networking tool - I get device networking tool.
There are two 1) Loop back and 2) Ethernet Interface eth0 .
In ethernet interface, there are two protocol Ipv4 and ipv6

Now when restart my system and remove cd and book from my hard disk ubuntu 8.10 and right click connection icon on right top bar, I do not see connection information. Also it has only lo and no mac address.

When I click system - administration - networking tool - device ntetworking tool there is loop back with all details and in ethernet interface I DO NOT FIND IPV4 AND ITS DETAILS.

I think this is the problem due to I can not connect while booting from my hard disk.
My computer was with Window xp with 4 partitions. I installed ubuntu 8.10 on saparate partition. This time I was not having zte modem and broadband connection.
After a week I purchased ZTE modem and broadband connection and started it in windows. But when i booted my machine from bunutu, i found it is not connection to internet.
I tried to boot Ubuntu from CD and I found that without any setting every time I can connect to internet.
I do not have hart to reinstall Ubuntu as I am scared I may mess up with everything.

CAN ANYONE SHOW ME WHERE I AM DOING MISTAKE IN SETTING?
From where can I set my interent connection?
Hasit

---

### Post by cariboo on 2009-06-07
I would suggest you boot from the LiveCD and then open a Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

and either print out the result, or copy them to your hard drive. Then do that same thing when you boot your Ubuntu installation normally, and compare the results, because it sounds like the nic driver isn't loading when booting normally.

---

### Post by Hasit on 2009-06-08
> **cariboo907 said:**
> I would suggest you boot from the LiveCD and then open a Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```and either print out the result, or copy them to your hard drive. Then do that same thing when you boot your Ubuntu installation normally, and compare the results, because it sounds like the nic driver isn't loading when booting normally.
************************

THANKS A LOT ,,,,, I AM NEAR TO SOLUTION IT SEEMS......

**************************

   THIS IS THE INFO WHEN I BOOT FROM CD AND I CAN CONNECT TO INTERNET.
   
   
  To run a command as administrator (user "root"), use "sudo <command>".
  
  See "man sudo_root" for details.
  
   
   
  ubuntu@ubuntu:~$ sudo lshw -C network
  
    *-network               
  
         description: Ethernet interface
  
         product: L2 100 Mbit Ethernet Adapter
  
         vendor: Attansic Technology Corp.
  
         physical id: 0
  
         bus info: pci@0000:02:00.0
  
         logical name: eth0
  
         version: a0
  
         serial: 00:24:8c:0c:29:8c
  
         size: 100MB/s
  
         capacity: 100MB/s
  
         width: 64 bits
  
         clock: 33MHz
  
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  
         configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.0.4 duplex=full firmware=L2 ip=192.168.1.2 latency=0 link=yes module=atl2 multicast=yes port=twisted pair speed=100MB/s
  
    *-network DISABLED
  
         description: Ethernet interface
  
         physical id: 1
  
         logical name: pan0
  
         serial: 3a:a9:c2:62:04:f6
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  
  ubuntu@ubuntu:~$ 



*****************
NOW


    THIS IS MESSAGE WHEN I BOOT FROM UBUNTU 8.10 FROM MY HARD DRIVE (CAN NOT CONNECT TO INTERNET)
   
  hasit@hasit-desktop:~$ sudo lshw -C network
  
  [sudo] password for hasit: 
  
    *-network               
  
         description: Ethernet interface
  
         product: L2 100 Mbit Ethernet Adapter
  
         vendor: Attansic Technology Corp.
  
         physical id: 0
  
         bus info: pci@0000:02:00.0
  
         logical name: eth0
  
         version: a0
  
         serial: 00:24:8c:0c:29:8c
  
         size: 100MB/s
  
         capacity: 100MB/s
  
         width: 64 bits
  
         clock: 33MHz
  
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  
         configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.0.4 duplex=full firmware=L2 latency=0 link=yes module=atl2 multicast=yes port=twisted pair speed=100MB/s
  
    *-network DISABLED
  
         description: Ethernet interface
  
         physical id: 1
  
         logical name: pan0
  
         serial: 4e:c6:84:69:b8:65
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


**************** 

I CAN SEE THERE ARE SOME DIFFERENCES, BUT I DO NOT KNOW HOW TO EDIT IT. I AM TOTALLY NEW.... PLEASE GUIDE ME STEP BY STEP....
I AM NEAR TO SOLUTION.


THANKS. ALL

---

### Post by Hasit on 2009-06-08
ip and serial is different on my hard drive installation. how to change it?

---

### Post by cariboo on 2009-06-08
Don't worry about pan0, it has nothing to do with your no connection problem.

If you open an Application-->Accessories-->Terminal and type:

```
sudo dhclient eth0
```

what is the output?

BTW you can copy the output of any commands you type in a terminal, by just highlighting the text, then to paste just press the middle mouse button if you have a wheel mouse, if you don't, just press both mouse buttons at once.

---

### Post by Iowan on 2009-06-08
> **cariboo907 said:**
> BTW you can copy the output of any commands you type in a terminal, by just highlighting the text, then to paste just ress the middle mouse button if you have a wheel mouse, if you don't, just press both mouse buttons at once.HEY... there's a new trick to file away.
THANKS =D>

---

### Post by Hasit on 2009-06-09
> **cariboo907 said:**
> Don't worry about pan0, it has nothing to do with your no connection problem.

If you open an Application-->Accessories-->Terminal and type:

```
sudo dhclient eth0
```what is the output?

BTW you can copy the output of any commands you type in a terminal, by just highlighting the text, then to paste just ress the middle mouse button if you have a wheel mouse, if you don't, just press both mouse buttons at once.


************
I get following thing when I type above mentioned command.

   hasit@hasit-desktop:~$ sudo dhclient eht0
  [sudo] password for hasit: 
  Internet Systems Consortium DHCP Client V3.1.1
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
  SIOCSIFADDR: No such device
  eht0: ERROR while getting interface flags: No such device
  eht0: ERROR while getting interface flags: No such device
  Bind socket to interface: No such device
  hasit@hasit-desktop:~$ 



**************
I tried to cut one line from terminal window, but could not.
When I tried to paste something from clipboard, it paste at bottom.
*************


PLEASE HELP

---

### Post by cariboo on 2009-06-09
> sudo dhclient eht0

You have a spelling error that should be:

```
sudo dhclient eth0
```

not eht0

Edit: you can copy the command directly from the web page to a terminal by using the method I suggested for copying and pasting.

---

### Post by Hasit on 2009-06-09
> **cariboo907 said:**
> You have a spelling error that should be:

```
sudo dhclient eth0
```not eht0

Edit: you can copy the command directly from the web page to a terminal by using the method I suggested for copying and pasting.


***********

I will post it now only.
Thanks.

---

### Post by Hasit on 2009-06-09
> **cariboo907 said:**
> You have a spelling error that should be:

```
sudo dhclient eth0
```not eht0

Edit: you can copy the command directly from the web page to a terminal by using the method I suggested for copying and pasting.
*****************

now i corrected my spelling mistake and found following thing:-

hasit@hasit-desktop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 6302
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:24:8c:0c:29:8c
Sending on   LPF/eth0/00:24:8c:0c:29:8c
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 39549 seconds.
hasit@hasit-desktop:~$ 

******************

AND SURPRISING... MY CONNECTING IS WORKING.
ON RIGHT HAND CONNECTION ICON IT SHOWS LO AND NO ETH0
IT DOES NOT HAVE EDIT BUTTON. (when I right click)
My INTERNET is working now , but if i restart , I do not know what will happen.

---

### Post by Hasit on 2009-06-09
> **cariboo907 said:**
> You have a spelling error that should be:

```
sudo dhclient eth0
```not eht0

Edit: you can copy the command directly from the web page to a terminal by using the method I suggested for copying and pasting.

********************

When I rebooted my computer , I could not connect to internet. So I typed sudo dhclient eth0 and entered my password. 

after screen data appeared, I tried to click Firefox, and I can connect to internet...My network connection icon on right side top panel shows network connection lo and when I right click there is no edit item.

what is wrong?

Even I have upgraded just now to 9.04 through internet. When I rebooted everything is fine but If I have to connect to Internet , I have to write sudo dhclient eth0  command after booting then and then only I can connect to Internet. Connection icon on the right top panel also shows Network Connection : lo and when I right click it, it do not have edit button.
Please help.

---

### Post by Iowan on 2009-06-09
Either I'm missing something, or there's something amiss... "lo" is the loopback device. How did it end up as a connection option???

Have you tried adding a connection via Network Manager? Ordinarily, NM is *very* intent on providing "auto eth0". If that option is unavailable (maybe it just got renamed), you should be able to build a DHCP connection.  You will need to have the MAC address for eth0 (00:24:8c:0c:29:8c).

---

### Post by Hasit on 2009-06-10
> **Iowan said:**
> Either I'm missing something, or there's something amiss... "lo" is the loopback device. How did it end up as a connection option???

Have you tried adding a connection via Network Manager? Ordinarily, NM is *very* intent on providing "auto eth0". If that option is unavailable (maybe it just got renamed), you should be able to build a DHCP connection.  You will need to have the MAC address for eth0 (00:24:8c:0c:29:8c).


In network tools and in network configuration, I can  enter details but it goes off when I again open it to see.
Network connection only showl lo and it does not have edit menu.

---

### Post by Iowan on 2009-06-10
As I recall, I had some problems getting the settings to take - I don't remember if I had to click in each box separately, use <ENTER>, or click on [APPLY].

---

