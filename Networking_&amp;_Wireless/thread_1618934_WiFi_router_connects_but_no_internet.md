---
title: "WiFi router connects but no internet"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by DenisP on 2010-11-11
I am trying to run 10.04 netbook live from a memory stick with a view to installing it on my laptop. However although I can see my wireless router and connect to it I cannot access the internet. I have tried this on my laptop and desktop with the same result. I was however able to download Seamonkey browser using the software manager....this also cannot access the internet.

Both of my PC's have no problem when using XP or Linux Mint.

I have also discovered that if I piggyback, using Ubuntu 10.04, on a neighbours open wifi link I can gain access to the internet. My wifi is using WEP protection but as I said I can set the link up to the router, entering the appropriate key code, and have a good signal strength, I just cannot access a google search page.

Any help would be much appreciated

Denis

---

### Post by P4man on 2010-11-11
Once connected, run these commands in a terminal and post the output
```

ifconfig
iwconfig
```

To narrow down the problem, maybe you can also try turning WEP temporarily  OFF on the router and see if that works

---

### Post by uncaspi on 2010-11-11
To ensure the nameserver is ok. Can you ping google.com

---

### Post by DenisP on 2010-11-11
> **P4man said:**
> Once connected, run these commands in a terminal and post the output
```

ifconfig
iwconfig
```To narrow down the problem, maybe you can also try turning WEP temporarily  OFF on the router and see if that works

**Here are the results on running ifconfig and iwconfig.**


 ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:15:e7:a2  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:15:00:46:dd:04  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe46:dd04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1623 (1.6 KB)  TX bytes:4219 (4.2 KB)
          Interrupt:22 Base address:0x2000 Memory:fe9ff000-fe9fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8016 (8.0 KB)  TX bytes:8016 (8.0 KB)

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"GWART2-54125"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:30:54:41:65:92   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/100  Signal level=-58 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

pan0      no wireless extensions.


Regards

Denis

---

### Post by DenisP on 2010-11-11
> **uncaspi said:**
> To ensure the nameserver is ok. Can you ping google.com


Sorry for being so thick but how do I do that?

Regards

Denis

---

### Post by Zhukov on 2010-11-11
give us the output of this:

route -n

cat /etc/resolv.conf

You can optionally try this, might just work:

echo "nameserver 8.8.8.8" > /etc/resolv.conf

To ping just do:

ping [www.google.com](www.google.com)

---

### Post by DenisP on 2010-11-12
> **DenisP said:**
> I am trying to run 10.04 netbook live from a memory stick with a view to installing it on my laptop. However although I can see my wireless router and connect to it I cannot access the internet. I have tried this on my laptop and desktop with the same result. I was however able to download Seamonkey browser using the software manager....this also cannot access the internet.

Both of my PC's have no problem when using XP or Linux Mint.

I have also discovered that if I piggyback, using Ubuntu 10.04, on a neighbours open wifi link I can gain access to the internet. My wifi is using WEP protection but as I said I can set the link up to the router, entering the appropriate key code, and have a good signal strength, I just cannot access a google search page.

Any help would be much appreciated

Denis

**SOLUTION**

The problem was as follows:-

You can see the wifi router and even enter the WEP code to make connection but the browsers will not load pages OR do so intermittantly OR take ages to do so. Mine was nearly none existant.

The problem is in the DNS settings..........ie how the browser looks up addresses.

I did the following

Disconnect from the wifi router, right click on the wifi icon, the one just used to disconnect, and select **Edit Connection**.

In the new window select the **wireless** tab, highlight your wireless link and select edit.

In the new window select **IPV4 Settings** tab, from the Method drop menu choose **Automatic DHCP addresses only**.

In the DNS Servers box enter the following two addresses    **8.8.8.8       8.8.4.4   **   with just one space between the two four bit numbers and full stops as shown.

Click apply, reconnect to your wifi router and all should be well.

Thanks to all who posted in allowing me to figure this out.

Best of luck

Denis

---

### Post by grahammechanical on 2010-11-12
Hi DenisP

Is it not great when something mysterious become a little less mysterious? This is how we leard to help others.

Regards

---

### Post by Zhukov on 2010-11-13
More than you think actually :D

I don't know why I memorized Google's DNS as 8.8.8.8 and 4.4.4.4, instead of 8.8.8.8 and 8.8.4.4.

Glad this thread sorted it out for me :D

---

