---
title: "sharing wi-fi connecntion problem on jaunty"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by spazio73 on 2009-05-16
My pc has two network adapter: wlan0 connected to internet by an access point (ip: 192.168.0.3 gw: 192.168.0.1), and eth0 connected to my private network (10.0.0.3). 
If i use only wifi connection everything works fine and i can surf on internet but when i plug ethernet cable surfing quit to work.
It seems like if all routing goes to eth0 instead wlan0. I 'm using jaunty's default network manager instead /etc/network/interfaces.
Can i force wlan0?

Also i would like to share wifi internet connection to othen pc on my lan. I've tried:

iptables -A FORWARD -i wlan0 -o eth0 -s 10.0.0.0/24 -m state --state NEW -j ACCEPT    
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT                    
iptables -A POSTROUTING -t nat -j MASQUERADE                                          
sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"                                        

Is it correct?

---

### Post by Adina on 2009-05-16
You need to save the ip tables rules, or else you have to do all the configuration all over again after you reboot you computer.

look a bit down the page:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by spazio73 on 2009-05-16
This configuration work never, neither the first time. Do you think that is NetworkManager that force all traffic routing to wired connection first?
Maybe i should disable NM and config everything manually in /etc/network/interfaces?

---

### Post by Peter09 on 2009-05-16
CAn you post the output of the terminal command

```
 route 
```

for both your machines

---

### Post by Adina on 2009-05-16
I think that somehow you didn't manage to configure the 2 interfaces to be on separate networks. You can not have two interfaces on the same network (192.168.0.0). I think that is why your internet connection get rejected when you connect both interfaces.

---

### Post by spazio73 on 2009-05-16
This is all my system stats:
------------------------------------------------------
**~$ route**
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
linux1.local    *               255.255.255.255 UH    0      0        0 eth0
172.16.85.0     *               255.255.255.0   U     0      0        0 vmnet8
10.0.0.0        *               255.255.255.0   U     1      0        0 eth0
192.168.213.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         linux1.local    0.0.0.0         UG    0      0        0 eth0

~$ 

**:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"JERICHO"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1F:33:87:6F:42   
          Bit Rate=48 Mb/s   Tx-Power=6 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=74/100  Signal level:-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.

~$ 

**~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:18:f3:d8:c7:2c  
          inet indirizzo:10.0.0.3  Bcast:10.0.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::218:f3ff:fed8:c72c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:13253 (13.2 KB)
          Interrupt:20 Indirizzo base:0xe800 

lo        Link encap:Loopback locale  
          inet indirizzo:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:4576 (4.5 KB)  Byte TX:4576 (4.5 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet indirizzo:192.168.213.1  Bcast:192.168.213.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet indirizzo:172.16.85.1  Bcast:172.16.85.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:af:00:a4  
          inet indirizzo:192.168.0.3  Bcast:192.168.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::215:e9ff:feaf:a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:19009 (19.0 KB)  Byte TX:8639 (8.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-AF-00-A4-30-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

~$ 

**~$ sudo vi /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

# Restore Routing Rules
pre-up iptables-restore < /home/libreria/.iptables

---

### Post by Peter09 on 2009-05-16
Your routing table does not show a link between 10.xxx and 192.168.xx

You will need to add a route,
try

```
sudo route add 10.0.0.0 mask 255.255.255.0 192.168.213.0
```

You also seem to have some other routes defined as well!

---

### Post by Peter09 on 2009-05-16
Also your default gateway is on eth0, so when it is connected all traffic to the internet will go that way.

---

