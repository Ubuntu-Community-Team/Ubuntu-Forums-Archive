---
title: "Internet (ISP: @home) not working under Ubuntu"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by nez on 2006-06-04
I installed Dapper on my pc but I can't get acces the internet. 

My pc is directly connected to the modem (no router between it), and I'm the only one on the network.

In Windows I would set my network config to dhcp and change my computername to a name provided by my ISP. 
If I do the same thing in Dapper it won't work.

What am I doing wrong?

---

### Post by rbalfour on 2006-06-04
Are you getting an IP address?

command ref:
> ifconfig

---

### Post by nez on 2006-06-04
No eth0 doesn't receive an ip address.

---

### Post by RRS on 2006-06-04
What type of connection, dsl, dial-up or cable? Also what type modem if dsl, or cable; ethernet or USB?

If DSL try System>Administration>Networking
Under connections select eth0 and properties. DHCP from the dropdown menu, check "enable this connection", "OK" "OK"

If this doesn't work or if you have another type of connection please post back with any error messages and connection details.

---

### Post by rbalfour on 2006-06-04
I have seen this problem with comcast internet cable.
The only way I got it to work, 
1) connect computer
2) boot up
3) cycle power on cable modem
4) wait 2 mins.

---

### Post by nez on 2006-06-04
I have Cable. The cablemodem is ethernet. I already went to system -> administration -> networking before (that's how I configured it) but it didn't work. I tried again and did everything you said but unfortunately it didn't work.

edit:
For some strange reason the 'Default gateway device'-dropdown menu won't stick to eth0. I always select eth0 and press ok and close Network settings. But when I return it's empty again.

---

### Post by rbalfour on 2006-06-04
can you post the ifconfig

command ref:

# ifconfig > net.txt

---

### Post by nez on 2006-06-04
I have an Arris modem, and I tried the thing you did with your comcast modem but it didn't work.


**net.txt file:**
eth0      Link encap:Ethernet  HWaddr 00:10:A4:E4:1D:A9  
          inet6 addr: fe80::210:a4ff:fee4:1da9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168218 (164.2 KiB)  TX bytes:3204 (3.1 KiB)
          Interrupt:11 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18004 (17.5 KiB)  TX bytes:18004 (17.5 KiB)

---

### Post by deadgobby on 2006-06-05
It seems people are haven problems with connecting to the internet with a cable modem running Dapper. Here is a simple thing to do.
1. Power down your pc.
2. Unplug your cable modem and wait at least 1 minute and plug the modem back in.
3. Turn on the modem and wait for the modem do it self test.
4. Boot up your PC with the cable modem on.
 I have a cable modem and if I have the cable modem off after I boot up my pc. I will not have no internet connection. If I reboot my pc with the cable modem on. I can connect to the internet. So if you are use to turning on you modem after you boot up. Try this little simple trick.
Gobby

---

