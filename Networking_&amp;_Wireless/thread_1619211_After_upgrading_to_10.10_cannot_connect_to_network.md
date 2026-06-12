---
title: "After upgrading to 10.10 cannot connect to network through ethernet"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by DB90808 on 2010-11-11
I looked though the forum for an answer that would help me, but found none that were satisfactory. At start-up the computer will try to connect to my router, but will say after about 30 seconds that the network cable is disconnected. My computer is a Dell Inspiron 530, and has an Intel 82562V-2 Network Connector. I know nothing is wrong with the hardware because it was working fine using 10.04 . I don't know how to proceed. Please help.

---

### Post by drdos2006 on 2010-11-11
Use the terminal type in : ifconfig
Do you get an IPv4 address, such as 192.168.0.4...or 10.0.0.10 ?

regards

---

### Post by DB90808 on 2010-11-11
Here is what it says:

eth0      Link encap:Ethernet  HWaddr 00:1d:09:7f:8b:a7  
          inet6 addr: fe80::21d:9ff:fe7f:8ba7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:773 (773.0 B)  TX bytes:5065 (5.0 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by drdos2006 on 2010-11-11
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

### Post by grahammechanical on 2010-11-11
That ifconfig listing shows that eth0 is UP and it is also RUNNING. It seems that it is not connecting to the router/modem. Try this, please,

Right click the network manager icon. Select Edit Connections. Select Auto eth0 or eth0, if that is what is there. Select Edit. Go to the IPv4 Settings tab and make sure that Automatic (DHCP) has been chosen as the Method. You can also open the IPV6 Settings tab and make sure the Method is Ignore. If your IPV4 Settings Method is manual than you will have to insert the correct IP address for your router. Is it the correct address?

regards.

---

### Post by s_raiguel on 2010-11-12
Similar story here: I have a Dell with an Intel NIC on the motherboard. After going to 64-bit 10.10, had trouble connecting to wired router - it would connect maybe 1 out of 5 or 6 reboots. Yet, Windows, 10.04 AMD64 and 10.10-386i all connected reliably. 

Following some advice from this forum, I downloaded the latest driver directly from Intel. It comes in .tar.gz format, but there's an easy-to-follow readme file in it telling you step by step how to install the new driver, which consists of little more than typing "make install". With the new driver, 10.10-64 connects nearly every time, though it's still not quite perfect.

---

