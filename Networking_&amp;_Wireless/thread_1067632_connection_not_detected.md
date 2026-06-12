---
title: "connection not detected"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by kistopermak on 2009-02-12
Hi,

I just installed Ubuntu from the disk that I got through the mail. Everything has been installed but it is not detecting my internet connection.

I have a dual boot Windows XP/ Ubuntu with Globe Broadband and Windows is detecting the connection. 

I dont know how to classify my connection, Globe broadband uses wireless connections detected by a ZTE modem that is connected directly to the ethernet port on my computer. 

I tried the guide in ([https://help.ubuntu.com/8.10/internet/C/modems-adsl-pppoe.html](https://help.ubuntu.com/8.10/internet/C/modems-adsl-pppoe.html)) but it did not detect the network. 
I also tried following ([https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html)) but i got 0% succesful packets when i try to connect to 82.211.81.158 .

Anything else that I should do?

Your feedback is very much appreciated. Thanks

---

### Post by superprash2003 on 2009-02-12
go to the terminal and type **ifconfig** and post output here..

---

### Post by kistopermak on 2009-02-12
hi,

ifconfig shows :

eth0      Link encap:Ethernet  HWaddr 00:1e:90:e8:42:ed  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

ipconfig/all on windows shows

Windows IP Configuration

        Host Name . . . . . . . . . . . . : yesha-212bf00ea
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : local

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : local
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Eth
ernet NIC
        Physical Address. . . . . . . . . : 00-1E-90-E8-42-ED
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.20
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
       


I tried to ping the modem (192.168.0.1) and i got 0% succesful packets.

I don't know if the above information is necessary but i posted it anyway ^_^

Thanks for the reply !

---

### Post by StanleyJack123 on 2009-02-12
I had a similar problem recently.  This may be way off, but are you sure you have the correct drivers for the internet connection?

---

### Post by sleve on 2009-02-12
ive been having the same problem. ubuntu will automatically detect wireless connections but it sometimes has issues connect to my Wired connection.


if this is happening to more than us than im going to say its a bug.

if i reboot my pc i will have to shut off completely and hope that when i restart i have my wired connection. its very random as to when it wants to find it and when it doesnt. if someone has a solution please post :D

---

### Post by kistopermak on 2009-02-12
> **StanleyJack123 said:**
> I had a similar problem recently.  This may be way off, but are you sure you have the correct drivers for the internet connection?

I have an on-board ethernet.
I use one installer for windows, as for Ubuntu, i haven't installed anything yet. 

I have noticed that not all the lights on the modem are lit. So i suppose that means that no transfer of data is happening.

---

### Post by kistopermak on 2009-02-13
Hi,

Power Cycle did the trick!

Silly Me! HAHAHA,

Thanks for the replies.

---

