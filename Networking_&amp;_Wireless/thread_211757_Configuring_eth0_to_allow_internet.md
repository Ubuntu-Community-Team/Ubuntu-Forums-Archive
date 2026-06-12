---
title: "Configuring eth0 to allow internet"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by The Doughnut Man on 2006-07-08
Hi There,

I'm new to Linux and have just installed Ubuntu Dapper Drake 6.06.  I am dual booting with Windows XP.  At the moment I am having a great deal of trouble configuring my eth0 ethernet connection to allow me to use the internet.  

I have an ADSL connection - and it's working fine in windows.

My windows network settings are:
IP 10.0.0.10
Subnet 255.0.0.0
Gateway (ADSL modem via switch) 10.0.0.138 (Alcatel Speedtouch)
DNS 1 218.214.17.1
DNS 2 202.154.92.35

I've tried configuring the eth0 card through System->Administration->Networking with the above settings many times.

From firefox I am unable to load the modem setup via 10.0.0.138

My NIC is a 3Com 3C900B-TPO2

Any ideas as to what I am doing wrong?  Is there any other information I can provide to help solve the problem?

Cheers

Greg

---

### Post by raldz on 2006-07-08
if you are able to access your modem/router via firefox, then your NIC is working properly.. have you tried to ping "64.233.189.104" <<Google.. if you could ping that IP address with no packet loss, then it's probably just a DNS error..

---

### Post by The Doughnut Man on 2006-07-09
In firefox on Ubuntu I have tried to load 10.0.0.138 - which brings up the modem setup (in windows anyway).

I will try pinging 64.233.189.104, however I doubt anything will happen as I have tried loading several web pages.

we'll see. :)

---

### Post by raldz on 2006-07-09
We are just trying to isolate the problem by doing the easy methods first.. if you could ping Google's IP, it means that you have internet connection, but the problem is the name-to-ip translation that should be provided by your DNS server.. but if you could not ping the IP, then the problem is in your system.. and that is where we would start..

---

### Post by The Doughnut Man on 2006-07-10
Thanks Raldz.  On Pinging 64.233.189.104 I get:

PING 64.233.189.104 (64.233.189.104) 56(84) bytes of data.
From 10.0.0.14 icmp_seq=2 Destination Host Unreachable
From 10.0.0.14 icmp_seq=3 Destination Host Unreachable
etc, etc

Had to CTRL C to stop the process.

112 packets transmitted, 0 received, +84 errors, 100% packet loss, time 111009ms, pipe 3.

What does this mean?

---

### Post by raldz on 2006-07-10
I am able to ping the IP with no errors, now we know that the problem is internal or wrong settings.. could you please post your ifconfig? execute in the terminal "ifconfig" you should get an output alsmost similar to this:

eth0      Link encap:Ethernet  HWaddr 00:11:5B:96:39:83
          inet addr:192.168.0.151  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe96:3983/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2816599 (2.6 MiB)  TX bytes:747991 (730.4 KiB)
          Interrupt:193 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:340 (340.0 b)  TX bytes:340 (340.0 b)

We will try to check if there is a wrong setting.. sorry if in any case that my replies are late.. but you could turn off the firewalls first just to establish that it is not a firewall issue too..

---

### Post by The Doughnut Man on 2006-07-11
no problems about the timeliness of your replies...you have been a great help...as you can see I am hardly on time either!

This is what I got:

eth0      Link encap:Ethernet  HWaddr 00:10:4B:1A:DD:9F
          inet addr:10.0.0.14  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::210:4bff:fe1a:dd9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:7668 (7.4 KiB)
          Interrupt:177 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4890 (4.7 KiB)  TX bytes:4890 (4.7 KiB)

---

### Post by The Doughnut Man on 2006-07-18
So Does anyone have any ideas about what is going on?  It seems that on the forums that people do have problems connecting to the internet with Ubuntu....

I have previously installed Fedora Core and it was terribly straightforward...

---

### Post by macogw on 2006-07-18
I'm having problems with it right now.  eth0 is active, enabled, and set for DHCP.  When I tried to set eth0 for the default gateway, the terminal said:

** (network-admin:10427): CRITICAL **: gst_xml_element_set_content: assertion 'node != NULL' failed

And I have no idea what that means.  I can't get to the internet though, that's all I know.

---

### Post by Draky on 2006-07-24
got the same modem : speedtouch (530) with ethernet connexion.
same "ifconfig" result.
can't join "10.0.0.138" :(
dhcp = auto in "network"

---

### Post by mips on 2006-07-24
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by kaumochan on 2006-07-24
hv been facing similar problem. still not able to fix or know the actual problem.
However interestingly I am able to access internet when i open firefox as root or ping as root. Also as normal user, i can connect to websites if i put ip address instead of the www. name

is this to do with permissions to drivers or devices?

---

### Post by Draky on 2006-07-24
Ok.

Let's post :

I have an asus motherboard, with a nforce2 chipset. My network controller is included on the motherboard.
My ADSL modem is a speedtouch (alcatel-thomson) 530.

Here is the results of what you asked :

```
1. Please post output of ifconfig eth0 (Depends on your interface number)
2. Please post output of lspci | grep Eth
3. Please post output of route -n
4. Please post output of cat /etc/resolv.conf
5. Please post output of cat /etc/network/interfaces
6. Please post output of cat /etc/dhcp3/dhclient.conf
7. Please copy entire output of windows ipconfig /all command here

1)
eth0      Lien encap:Ethernet  HWaddr 00:0C:6E:0D:CC:1D
          adr inet6: fe80::20c:6eff:fe0d:cc1d/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 b) Octets transmis:2862 (2.7 KiB)
          Interruption:177 Adresse de base:0x8000

2)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)

3)
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface

4)
search lan
nameserver 10.0.0.138

5)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

6)
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

7)
Configuration IP de Windows

        Nom de l'hôte . . . . . . . . . . : ordinathan
        Suffixe DNS principal . . . . . . :
        Type de noud . . . . . . . . . . : Inconnu
        Routage IP activé . . . . . . . . : Non
        Proxy WINS activé . . . . . . . . : Non
        Liste de recherche du suffixe DNS : lan

Carte Ethernet Connexion au réseau local:

        Statut du média . . . . . . . . . : Média déconnecté
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Adresse physique . . . . . . . . .: 00-0C-6E-0D-CC-1D

Carte Ethernet Connexion au réseau local 2:

        Suffixe DNS propre à la connexion : lan
        Description . . . . . . . . . . . : Alcatel SpeedTouch(tm) USB ADSL RFC1
483
        Adresse physique . . . . . . . . .: 00-0E-50-2C-A5-41
        DHCP activé. . . . . . . . . . . : Oui
        Configuration automatique activée . . . . : Oui
        Adresse IP. . . . . . . . . . . . : 10.0.0.1
        Masque de sous-réseau . . . . . . : 255.255.255.0
        Passerelle par défaut . . . . . . : 10.0.0.138
        Serveur DHCP. . . . . . . . . . . : 10.0.0.138
        Serveurs DNS . . . . . . . . . .  : 10.0.0.138
        Bail obtenu . . . . . . . . . . . : lundi 24 juillet 2006 15:43:07
        Bail expirant . . . . . . . . . . : lundi 24 juillet 2006 17:43:07

```

Sorry, I'm french so my ubuntu is with "locales fr" and my Windows XP is in french ;)

Thanks in advance :)

---

### Post by mips on 2006-07-24
Draky,

Your DHCP is not working. Try a static config and see if you can connect, can always try dhcp later again. Just need to establish the cause first.

Also disable IPv6 while you are at it.

---

### Post by mips on 2006-07-24
> **The Doughnut Man said:**
> Hi There,
My windows network settings are:
IP 10.0.0.10
Subnet 255.0.0.0
Gateway (ADSL modem via switch) 10.0.0.138 (Alcatel Speedtouch)


Can you ping 10.0.0.14 , 10.0.0.138 ???

---

### Post by Draky on 2006-07-24
tried to disable ipv6 and a static eth0
no difference, except that now, instead of displaying a "standard" error page, firefox keeps looking for the domain i'm asking (I tried google.com).

---

### Post by mips on 2006-07-30
?

---

### Post by Draky on 2006-07-30
solved the problem for me

changed to a tecom modem
2 eth port, both working :)

---

