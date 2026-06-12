---
title: "How to manually configure the Nic"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by avender on 2006-01-19
Hi,

I have broadband connected through a ADSL router. The ADSL router is connected to Ethernet card.

My problem is that network setup using GUI is not working. It is not allowing me to change the settings there, So I want to manually configure the internet. How to do it in Kubuntu 5.10 ?
```

C:\Documents and Settings\Administrator>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : g-x6qev4tqaz9wy
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : D-Link DFE-538TX 10/100 Adapter
        Physical Address. . . . . . . . . : 00-08-A1-92-40-7D
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.11.17
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter Data One:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 59.92.242.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 59.92.242.5
        DNS Servers . . . . . . . . . . . : 218.248.255.145
                                            61.1.96.69
        NetBIOS over Tcpip. . . . . . . . : Disabled

```

I already tried DHCP, but it is not working... :(

---

### Post by bobyang on 2006-01-19
edit /etc/network/interfaces file directly
everytime you changed this file, remember to restart networking service:
sudo /etc/init.d/networking restart

---

### Post by avender on 2006-01-20
Hi, All. Finally I got connected to internet in Linux. :razz:  Thank you UBUNTU FORUM. Now I going to Remove Windows. After that I can proudly say that **"User of LINUX, No more SLAVE to Windows"**. :)

Also, I think that Ethernet card which I brought is worth.

Thank you once again to all those who helped me.

Have a nice day...

Here is the method which I used in Kubuntu 5.10 to connect to DataOne using ADSL.
```

$sudo eth0 192.168.1.100 netmask 255.255.255.0
$sudo pppoeconf

```

Note : You need to download the **pppoeconf** from Ubuntu website at [http://packages.ubuntu.com](http://packages.ubuntu.com)

This information may help those who use DataOne in India.

---

