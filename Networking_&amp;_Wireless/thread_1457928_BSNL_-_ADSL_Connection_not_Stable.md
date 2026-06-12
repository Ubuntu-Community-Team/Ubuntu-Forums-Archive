---
title: "BSNL - ADSL Connection not Stable"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by abanmitra on 2010-04-19
Hi,
I am new ubuntu user :) . I installed - ubuntu desktop v9.10 32bit. 
I have BSNL (Indian Telephone service) broadband connection. In Windows 7, BSNL broadband connection is working fine. 

Now in ububtu I try to establish ADSL connection using following command: 
"**sudo pppoeconf**". It open a console based wizard and I'm able to create the connection. But this connection is sustain hardly 4~3 minute, after that it is disconnected. So, Again i have go through the same process again and again. :confused:
Can anyone help regarding this issue...please :(

Thanks in advance.

Regards,
aban

---

### Post by dineshs on 2010-04-19
You are using Bridge mode which requires something similar to a dialler in the operating system.In linux you can do this via pppoeconf command.The advantage is that you can connect or disconnect as and when required.The modem is set in BRIDGE mode for this.
But I suggest you use PPPoE mode .For this set your modem in PPPoE mode(and store username and password given by ISP in the modem itself).This results in an always on internet connection irrespective of the OS used. 
Configuring modem for always on internet is explained here
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)

If you find any difficulty,open a terminal and post the result of 
```
ifconfig -a
```
```
cat /etc/resolv.conf
```
Pl let us know which modem you are using ie the model name say UT300R2U,DNA 211 etc.

Also make sure that the ADSL/DSL/LINK lamp is stableand your phone is connected via splitter(no parellel phone connection)

---

### Post by abanmitra on 2010-04-19
Hi dineshs,

Thank you very much for your prompt replay.

As per your instruction i try to configure the modem. Now my modem directly connect to internet [store username and password given by ISP in the modem itself].
Then I try try to run the command "**sudo pppoeconf**", but it gives the error. I attach the image serially as it comes in the screen. like "sh1,sh2,sh3 and sh4"
As per your request I ran the command and the following information is displayed:

bappa@ubuntu:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:1d:60:fc:4d:e5  
          inet6 addr: fe80::21d:60ff:fefc:4de5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:480 (480.0 B)  TX bytes:1156 (1.1 KB)
          Interrupt:25 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

bappa@ubuntu:~$ **cat /etc/resolv.conf**
nameserver 218.248.255.193
nameserver 218.248.240.180

My modem Information as follow:
Modem: SmartAX MT882
Model Name: MT882
Firmware Version: V200R001C01B021SP03 Jun 20 2005

Now I reset the modem to give you my feedback :)...

After reset the modem, I run the command "**sudo pppoeconf**" and connection is behaved as previous it was.

So, i don't know what to do !!!

---

### Post by dineshs on 2010-04-20
Your modem is MT882.So do the following
1.Set a static IP to the ethernet as follows
Right-click on the nm-applet and then click on Edit Connections.
Select the tab, wired 
select the connection and click edit(you can add the ethernet connection if not listed)
select ipv4
method-manual
click add
address 192.168.1.100
mask 255.255.255.0
gateway 192.168.1.1
then hit enter
DNS 4.2.2.1
then click apply

2.Now open firefox and configure modem as follows
 Type 192.168.1.1 in Address bar. click GO
Enter both Username and Password as admin
Click OK
Click the + sign left to home
Click WAN settings 
select PPP as WAN type
Enter  Username and Password as allotted by BSNL in the respective fields 
Select max idle time Always on
Apply the settings
The system will ask for reboot . Tick no and Click OK.
Click DHCP under home (left)
Enable DHCP and apply
The system will ask for reboot . Tick no and Click OK.
Click DNS on the left
Enable DNS and make all zeros (0.0.0.0)
Apply
Tick Yes and Click OK.
Wait till reboot complete (3 minutes).

After 3 minutes if the ADSL link is red/orange in color you are done!
Just open firefox and try browsing .NO pppoeconf or anything

---

### Post by ganesh_thevar on 2010-07-12
Hi there, 

My ISP is MNTL and the router is DLINK GLB 502 T. I am about to install ubuntu 10.04 on my second system and was scouting for information on setting up the internet. 
 
On the Ubuntu documentation site ([https://help.ubuntu.com/10.04/internet/C/connecting-dsl.htmlthe](https://help.ubuntu.com/10.04/internet/C/connecting-dsl.htmlthe)) direction of setting up DSL connection was very brief. This is reproduced below 
 
Ubuntu Documentation > Ubuntu 10.04 > Internet and Networks > Ways of Connecting > DSL

DSL
Right click the Network Manager icon in the system notification area and click Edit Connections...
Click DSL.
Click Add.
 
Is that all? once I follow this bare instructions will the system be connected to the internet? Those fortunate who have already been through this please enlighten me.

---

### Post by dineshs on 2010-07-14
If your modem is set in bridge mode try DSL connection as follows
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections.
Select the DSL tab- click add - Enter username and password as given by MTNL-tick available to all users- apply(connection name =DSL connection 1 by def)

To connect DSL click on NM icon click `DSL connection'Pl see the attachments

---

