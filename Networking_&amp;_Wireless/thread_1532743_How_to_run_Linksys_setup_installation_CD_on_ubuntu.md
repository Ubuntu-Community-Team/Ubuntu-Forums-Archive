---
title: "How to run Linksys setup installation CD on ubuntu?"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by kbuntuu on 2010-07-16
Hello There, 

I just bought Linksys WAG160N ADSL 2+ Router and modem device. It came with an setup  installation CD which is not running on ubuntu. In the manual it is written that it will run only under windows and Mac OS. I have only Ubuntu on my laptop. 

I need to run the setup CD to go ahead. I searched more than three hours to find out how to run this CD so that I can complete the setup of my new modem-router but did not find any solution.

Any help will be highly appreciated. Hope to get some help.

Greetz

---

### Post by ieee488 on 2010-07-16
You don't need to run the installation CD.
Hook it up and go. You might need to connect to it and change some settings, but that is it.

I have never had to install any software for either the DSL modem or the cable modem.

---

### Post by kbuntuu on 2010-07-16
Hi ieee488

Thank you for your reply.

I think i can connect my laptop to modem-router using Ethernet cable to connect to internet. But I need to have wireless for that the setup will help to protect my connection so that nobody can access my connection.

Can you write me exactly what to do? Or do you have any links to direct me to?

Thanks once again.

---

### Post by ST3ALTHPSYCH0 on 2010-07-16
default linksys IP is 192.168.1.1 default UN& passw: admin & admin. If that doesn't work, plug it in and hold the reset button (I have to reset them out of the box to get webadmin working all the time).

---

### Post by 4hm on 2010-07-16
Yeah, I have never used the router install CDs.  In the future you can just google the IP address and standard username&password for your router. (this kind of goes without saying, but make sure you change the username and password)

---

### Post by kbuntuu on 2010-07-17
Thank you guys for all your replies.

---

### Post by v1ad on 2010-07-17
yea type the ip into a web browser when manually connected and then log in. you will be able to configure your router from there.

---

### Post by kbuntuu on 2010-07-17
Hi All
 
Thank you for all your replies.
 
I did configure my WAG160N ADSL Router using the web configuration interface through the web browser 192.168.1.1
 
But however I am not able to connect to internet neither through LAN(wired) nor through the wireless. As far as the wireless is concerned I am able to see the network connection and able to connect but even there not able to browse any websites.
 
I did try to ifconfig and also ping. By using the ifconfig command I got some ip addresses and so on. But with ping it didnt give result other than an error.
 
The output of the ifconfig command that i executed from the machine using wireless is below: (ofcourse connection is there but without able to browse any websites)
 
_________________________________________
C:\Documents and Settings\user1>ipconfig /all
Windows IP Configuration
        Host Name . . . . . . . . . . . . : Netbook
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Atheros AR8132 PCI-E Fast Ethernet Controller
        Physical Address. . . . . . . . . : 18-A9-05-DF-46-F2
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : 17 July 2010 13:36:34
        Lease Expires . . . . . . . . . . : 18 July 2010 13:36:34
Ethernet adapter Wireless Network Connection:
        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Réseau local Broadcom 802.11b/g
        Physical Address. . . . . . . . . : 90-4C-E5-B7-83-D3
_________________________________________
 
Could you please anyone help me to fix this problem and browse the internet using the WAG160N? If you want i can send the output of ifconfig command that has been ran from the machine using wired network.
 
Cant wait to fix this configuration stuff :-(
 
Thanks

---

### Post by TheStroj on 2010-07-17
Not really an 'ifconfig' =P

My guess would be your problem are the DNS servers, which might not be set.

If you can ping IPs and get a response than that's it.

Try this:
```
ping 74.125.43.104
```

If you don't set DNS servers, your browser can't change 'google.com' to it's IP and connect to it.

---

### Post by oomar on 2010-07-17
if you are connected to the router and you still cant even ping.... it means you arent connected to the internet. at all. check your router.... it should have something like STATUS to click on that might display its IP address (the real one, not LAN) if it has an IP address from your ISP then check the DNS servers. maybe change them to the openDNS servers. they work quite well. if both your IP address is there and DNS is configured properly then I have no idea :D

---

### Post by ieee488 on 2010-07-17
> **kbuntuu said:**
> Hi All
 
Thank you for all your replies.
 
I did configure my WAG160N ADSL Router using the web configuration interface through the web browser 192.168.1.1
 
But however I am not able to connect to internet neither through LAN(wired) nor through the wireless. As far as the wireless is concerned I am able to see the network connection and able to connect but even there not able to browse any websites.
 
I did try to ifconfig and also ping. By using the ifconfig command I got some ip addresses and so on. But with ping it didnt give result other than an error.
 
The output of the ifconfig command that i executed from the machine using wireless is below: (ofcourse connection is there but without able to browse any websites)
 
_________________________________________
C:\Documents and Settings\user1>ipconfig /all
Windows IP Configuration
        Host Name . . . . . . . . . . . . : Netbook
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Atheros AR8132 PCI-E Fast Ethernet Controller
        Physical Address. . . . . . . . . : 18-A9-05-DF-46-F2
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : 17 July 2010 13:36:34
        Lease Expires . . . . . . . . . . : 18 July 2010 13:36:34
Ethernet adapter Wireless Network Connection:
        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Réseau local Broadcom 802.11b/g
        Physical Address. . . . . . . . . : 90-4C-E5-B7-83-D3
_________________________________________
 
Could you please anyone help me to fix this problem and browse the internet using the WAG160N? If you want i can send the output of ifconfig command that has been ran from the machine using wired network.
 
Cant wait to fix this configuration stuff :-(
 
Thanks


Who is your ISP?

---

