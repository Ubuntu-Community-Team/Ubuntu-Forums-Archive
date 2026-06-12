---
title: "Ubuntu 10.10 won't establish DSL connection"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by CrackerJack762 on 2010-11-24
What I have:
Computer: Dell XPS M1210
Modem: SpeedStream 51000   - It's SBCGlobal

I followed the pppoeconf setup instructions.
cracker@Jack:~$ sudo pppoeconf   Plugin rp-pppoe.so loaded.  
 RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5  
 

 I then asked it to start the connection.
  cracker@Jack:~$ sudo pon dsl-provider  
 Plugin rp-pppoe.so loaded.  
 RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5  
 

 

 Checked connection information and got this.

  cracker@Jack:~$ ifconfig eth0  
 eth0      Link encap:Ethernet  HWaddr 00:18:8b:dd:6e:cb   
           inet6 addr: fe80::218:8bff:fedd:6ecb/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:71 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:145 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:4878 (4.8 KB)  TX bytes:16904 (16.9 KB)  
           Interrupt:17  
 

I have no idea what the above means.:cry:

---

### Post by drdos2006 on 2010-11-24
I had the same problem with my hardware not connecting via an IPv6 address but connecting via an IPv4 address. You do not have an IPv4 address.

Try this.
From the terminal:
cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. Need to add extra commands to /etc/sysctl.conf

First copy sysctl.conf to a backup with :
sudo cp /etc/sysctl.conf   /etc/sysctl.conf.backup

Next type :
sudo gedit /etc/sysctl.conf
Highlight the commands below from your browser :

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Add the commands to the bottom of /etc/sysctl.conf, save and reboot.

From a terminal type : ifconfig
ifconfig should not mention an IPV6 address on any interface after you have rebooted and you should now have IPv4 address for your computer.

regards

---

### Post by CrackerJack762 on 2010-11-24
You sir are awesome. I'm online with it right now.
The network manager in the top right did manage to vanish though.

---

### Post by drdos2006 on 2010-11-24
No problem. Dont forget to mark your thread as [SOLVED] to help someone else.

regards

---

