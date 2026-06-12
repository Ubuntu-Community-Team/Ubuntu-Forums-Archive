---
title: "Server 8.04.1 network connection problem"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by kaissa on 2009-01-12
Hello,


  I have installed Ubuntu Server 8.04.1 on a computer. I cannot ping the router or any other computer on the network. My original posts:

[http://ubuntuforums.org/showthread.php?t=1021356](http://ubuntuforums.org/showthread.php?t=1021356)

[http://www.linuxquestions.org/questions/linux-networking-3/beginner-ubuntu-server-8.04.1-network-problem-696053/](http://www.linuxquestions.org/questions/linux-networking-3/beginner-ubuntu-server-8.04.1-network-problem-696053/)

  The answers did not help me. While searching for more; I came up with this which looked quite similar:

[http://ubuntuforums.org/showthread.php?t=358546](http://ubuntuforums.org/showthread.php?t=358546)

  I followed the following advice:
[http://ubuntuforums.org/showpost.php?p=2143441&postcount=22](http://ubuntuforums.org/showpost.php?p=2143441&postcount=22)
  
  It gave a positive result with "bound to 192.168.1.16 -- renewal in X seconds". This somehow changed the manually give address of 192.168.1.19 to 192.168.1.16. After this I managed to ping 192.168.1.1 for the first time in weeks.

  Then I tried to ping a computer on the network. Both computers could not ping each other. After this try, it stopped pinging the router at 192.168.1.1.

  When I tried "# dhclient eth0" again, this time it keeps sending commands like "arp who-has 192.168.1.1 tell 192.168.1.16" for 32 minutes now. The output is "87 packets captured, 87 packets received by filter, 0 packets dropped by kernel".

  I have used Linux with GUI before and enjoyed. This is my first time in a Linux server with command line and had expected to learn about it. But spending almost two weeks to send one ping to the network has begun to take its toll on me. I hope you guys can help me in this.

Thank you for your time,

---

### Post by Iowan on 2009-01-12
I think I had to disable **ufw** on my Hardy server to get things started.

---

### Post by kaissa on 2009-01-15
> **Iowan said:**
> I think I had to disable **ufw** on my Hardy server to get things started.

  Unfortunately I am not as lucky as you were. It changed nothing.

  It looks like a DNS problem [https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-connection](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-connection) but even when I put in my isp DNS addresses and/or router address, nothing changes. I am stuck.

---

### Post by stefangr1 on 2009-01-15
Do you really need all that configuration in your /etc/networks/interfaces ?

I think you should use the default configuration:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by kaissa on 2009-01-15
OK, when I changed it your way; I first did "ifdown eth0", then "ifup eth0". It gave the following messages:
  Listening on LPF/eth0/...
  Sending on    LPF/eth0/...
  Sending on Socket/fallback
  DHCDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
  ""                                                 ""
  """                                                ""
   """                                             interval 8
 """"""""""""                                      interval 10
  """                                              interval 11
  ""                                               interval 12
  ""                                               interval 11
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.

  I wanted to have a static IP for the server.

---

### Post by stefangr1 on 2009-01-15
Yes but I suppoze (since other computers on the network are already connected) your router is the dhcp server right? If you would have multiple network interfaces, you would need extra configuration, but your setup is much simpler and thus might not need 'advanced' configuration. 

You can configure a static ip-address for your server in your router, which also simplifies troubleshooting.

---

### Post by cdtech on 2009-01-15
The way I run my Server is to have my "eth0" connected to the router using DHCP and my eth1 as the gateway to the network. My "eth1" is static using 192.168.1.1. I also use Shorewall as my frontend to "iptables". The following is my "interfaces" config file.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

# pre-up iptables-restore < /etc/iptables.up.rules


iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
```

---

### Post by kaissa on 2009-01-15
OK; I assigned the static IP from the router instead of the interface file which is dhcp as you said earlier. This time, I do not get an ip address for the computer after the ifconfig prompt.

---

### Post by kaissa on 2009-01-15
> **cdtech said:**
> The way I run my Server is to have my "eth0" connected to the router using DHCP and my eth1 as the gateway to the network. My "eth1" is static using 192.168.1.1.

Mine is not a server as yours. I have only one network card. I just wanted to install some programs on this "server" in order to learn more about them and improve myself. My "server" was supposed to be my playing field. My config files looks like they are OK. I get all the green lights, and even managed to ping the router once. So physical problem is out of the question.

---

### Post by stefangr1 on 2009-01-15
My configuration is similar to that of cdtech. I think your problem is misconfiguration of something that did not have to be configured in the first place. I'm now getting the impression that it is difficult to revert back to the default settings, which would allow you access to the network.

Maybe (you said you've been spending 2 weeks on this now?) doing a fresh install would be the most efficient solution... Then first you setup openssh-server and lookup the ip address of your machine with ifconfig, see if you can ssh into it from other machines, then you set a fixed ip address for your server in the router and reboot the server, see if ssh works again, etc...

---

### Post by kaissa on 2009-01-15
This was my 4th clean install :) I do not have access to the computer until Monday when I will format and install openssh-server and do what you told. I plan on setting LAMP as well. Thank you very much for your time.

---

