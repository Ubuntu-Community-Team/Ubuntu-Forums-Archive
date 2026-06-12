---
title: "Intel Pro 2200 b/g shows connected but I can't browse"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by champion77 on 2009-06-23
I have used Ubuntu since 8.04. I installed it on my Dell Inspiron B130 (Centrino). I am now running 9.04 Jaunty. It has an Intel Pro 2200 B/G wireless card. This card worked great everywhere (Panera, DSL at work, at home wpa/wpa2). Somewhere along the line after an update to Ubuntu somewhere (don't even ask me, I don't know), I began having problems.

Here is what is interesting: **It still works using open connections** like at Panera, or at a hotel, and at home with no security. 

**But it no longer connects using WPA**. I haven't tried WEP, nor am I interested in using it, as it is a less secure, outdated method.

I have used every combination in my Belkin wireless network router related to WPA. Each time, it keeps asking for my password again, and tries to connect. It eventually says, "not connected." 

Even more interesting, When the security is set at WPA-PSK+WPA2-PSK with TKIP+AES, Network manager shows it is connected and shows a strong signal. But I cannot browse the web or check e-mail. I tried using the network tools, and it will not ping to Google or even the router. I tried reinstalling Jaunty, and even tried installing Fedora 11! Same problem in Fedora.

Is it a hardware problem, a driver problem, or a Linux problem? Does anyone have a similar problem? Someone please help. Many thanks.:confused:

---

### Post by marcusdwight on 2009-06-23
i am having the same issues on my latitude D630 since i upgraded from Intrepid (8.10) to Jaunty (9.04). and i also have the Belkin router at home, running WPA security... my laptop is constantly dropping the signal, and when it does work it runs at around 70% instead of the normal 85 - 90% that it was getting before the upgrade. half the time i turn my computer on it asks for my password over and over, but does not connect.

does anyone else have this problem: when i open the network manager to re-enter my info, the password had been replaced with a long string of random characters, and i mean a *loooonnnggg* string, rather than my normal 10 character password.

i am at a complete loss, and i am normally good at figuring these things out... i do hope that someone out there has an answer.


marc

---

### Post by champion77 on 2009-06-23
Well, it is my understanding that the long string of random characters is supposed to be a security measure, and something you shouldn't be worried about. I could be wrong about that, but I have seen others reply that elsewhere.

---

### Post by champion77 on 2009-06-23
Hey Marc,

Did you try to use different security settings in your Router like AES, then try TKIP? Did you try WEP? I am curious, because if it says you are connected with the same settings as mine above, but you can't surf or ping, then you may have the exact problem I have. 

I am curious if the driver got fouled up by Ubuntu developers?

---

### Post by MaindotC on 2009-06-23
champion - when you are connected to a protected network, post the output of:
```

lspci | grep Network
lsusb
lshw -C network
iwlist | scan
ifconfig
cat /etc/resolv.conf

```

---

### Post by marcusdwight on 2009-06-23
ok,

thanks champion! i try to teach myself as much as i can about Linux, but there is always more to learn.

**BTW**, i had been using **Wicd** as my network manager up until i upgraded to Intrepid Ibex, at which point i found the default app to be sufficient. i have just reinstalled **Wicd** on my Jaunty system, and it started up with no issues whatsoever, and upon reboot it ran flawlessly... i  am also experiencing the strong signal strength that i used to. i think that i just found my "fix" (there seems to be a reason that Linux Mint and other distros are now making **Wicd** their default network manager).

marc

---

### Post by marcusdwight on 2009-06-23
Champ,

i have not tried changing my security settings, i have kept WPA2. i haven't logged into my router to check or change settings in over a year.

in my last post i mentioned switching my wifi manager to Wicd, and i am now cruising the net like i used to, no dropped or weak signals, it's all good now.

marc

---

### Post by champion77 on 2009-06-23
lspci | grep Network:
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lshw -c network:
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:15:c5:6d:3b:a9 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.3 latency=64 module=ssb multicast=yes 
  *-network:1 
       description: Wireless interface 
       product: PRO/Wireless 2200BG [Calexico2] Network Connection 
       vendor: Intel Corporation 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       logical name: eth1 
       version: 05 
       serial: 00:16:6f:b4:5c:cf 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.2.4 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 6a:95:94:b4:19:ad 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
iwlist | scan:
Usage: iwlist [interface] scanning [essid NNN] [last] 
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
The program 'scan' can be found in the following packages: 
 * dvb-apps 
 * mailutils-mh 
 * nmh 
Try: sudo apt-get install <selected package> 
bash: scan: command not found 

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6d:3b:a9  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::215:c5ff:fe6d:3ba9/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:56055 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:24974 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:68717931 (68.7 MB)  TX bytes:2008077 (2.0 MB) 
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:b4:5c:cf  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:6fff:feb4:5ccf/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:5 errors:48 dropped:48 overruns:0 frame:0 
          TX packets:3 errors:0 dropped:5 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:3480816 (3.4 MB)  TX bytes:22801 (22.8 KB) 
          Interrupt:17 Base address:0x4000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

cat /etc/resolv.conf:
# Generated by NetworkManager 
domain Champ 
search Champ Champ 
nameserver 192.168.2.1

---

### Post by champion77 on 2009-06-23
I would check all combos of settings on your router.

Interesting on the Wicd. I tried it and wpa_supplicant fails with it. So i uninstalled it. I'm also working in a fresh install of Jaunty today.

---

### Post by champion77 on 2009-06-23
Okay. I got wicd manager working. It installed fine this time and this is what happens:

It cannot connect in any setting except WPA+WPA2  with TKIP+AES. When it does connect, though signal strength shows 79%, it says at the bottom, connected to  me at 0% or 5%. Then it disconnects and reconnects at 0% or 5%, then a new cycle starts.
:confused:

---

### Post by MaindotC on 2009-06-23
Sorry it's not iwlist | scan it's
```

iwlist eth1 scan

```

---

### Post by marcusdwight on 2009-06-24
Champ,

it's a day later, and while changing my network manager to Wicd has been an improvement, my wifi is still under-performing as compared to when i was running Intrepid Ibex. i'm gonna do some more research and tweaking, there has to be a way to fix this...

marc

---

### Post by MaindotC on 2009-06-24
I really don't like the fact you are using these graphical interface applications.  Use the iwlist command and you should get some output stating which interface can scan for wireless networks and what (if any) associations it has and of what type.

---

### Post by champion77 on 2009-06-24
eth1      Scan completed :
          Cell 01 - Address: 00:22:3F:78:A7:2C
                    ESSID:"Clark2.4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    Extra: Last beacon: 7928ms ago
          Cell 02 - Address: 00:13:10:BC:B3:B0
                    ESSID:"linksys1"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    Extra: Last beacon: 7928ms ago
          Cell 03 - Address: 00:1C:DF:20:55:6B
                    ESSID:"champ"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-29 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1468ms ago
          Cell 04 - Address: 00:1A:C4:44:D5:B9
                    ESSID:"2WIRE840"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-59 dBm  
                    Extra: Last beacon: 7700ms ago

---

### Post by champion77 on 2009-06-24
Cell 05 - Address: 00:24:56:D4:D3:99
                    ESSID:"2WIRE427"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 8272ms ago


Sorry, it's interpreting some of the code as smilies. Here's the rest.

---

### Post by champion77 on 2009-06-24
On my computer, wicd and Network manager work the same. They both serve the same purpose. 

But getting the code by typing these commands in the terminal will tell us everything. If nothing is wrong with any of the code, I will have narrowed it down to a hardware problem, either the Belkin router or my Intel Pro wifi card. Or even the antenna.

---

### Post by MaindotC on 2009-06-24
Well looks like you're connected and using protected access.  Good job.

---

### Post by champion77 on 2009-06-25
Now if only I can surf and check my mail. 

When I go wireless, it shows I am connected, but I can't do those things or update/run synaptic.

---

### Post by MaindotC on 2009-06-25
Ok, post:
```

ifconfig
cat /etc/resolv.conf

```
See if you can ping your access point and then see if you can ping google.com.

---

### Post by champion77 on 2009-06-25
I cannot ping. No successful packets from my router or google. 

....even though "active: champ (94%)"

---

### Post by MaindotC on 2009-06-25
Post ifconfig and resolv.conf plz

---

### Post by champion77 on 2009-06-26
laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6d:3b:a9   
          inet6 addr: fe80::215:c5ff:fe6d:3ba9/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:686711 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1157963 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:64109434 (64.1 MB)  TX bytes:1694814273 (1.6 GB) 
          Interrupt:18  
 
eth1      Link encap:Ethernet  HWaddr 00:16:6f:b4:5c:cf   
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:6fff:feb4:5ccf/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:710 errors:205 dropped:205 overruns:0 frame:0 
          TX packets:48 errors:0 dropped:5 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:2381925 (2.3 MB)  TX bytes:37454 (37.4 KB) 
          Interrupt:17 Base address:0x6000 Memory:dfbfd000-dfbfdfff  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:10568 (10.5 KB)  TX bytes:10568 (10.5 KB)

laptop:~$ cat /etc/resolv.conf 
# Generated by NetworkManager 
domain Champ 
search Champ 
nameserver 192.168.2.1

---

### Post by MaindotC on 2009-06-26
You have your own DSN server and domain?  The reason I ask is because I'm connected to an AP and usually the AP forwards any settings it gets from the ISP. Here's mine:
```

search twcny.rr.com
nameserver 24.92.226.40
nameserver 24.92.226.41

```
You should be telling your AP to accept an address via DHCP from your ISP if it isn't already.

---

### Post by champion77 on 2009-06-26
No. I am going through an isp. I do not have any domain service. My only "dhcp server" is my Belkin router.

---

### Post by champion77 on 2009-06-26
I mean I don't have any domain _server_...

Another bit of info. I just switched my router to wpa with aes, and plugged my Airlink 101 USB adapter (uses atheros driver) and it does work.It doesn't work with wpa+wpa2. I hate having it sticking out the side. :(

I don't know what that tells us, except it's not the operating system. 

So what do I need to do given that my settings are not getting forwarded?

---

### Post by MaindotC on 2009-06-27
If you don't have your own DNS server then your resolv.conf is getting the wrong settings.  The addresses in your resolv.conf are for machines on your network, and if none of them are a DNS server then your machine doesn't know what address to send DNS queries.

Check your access point settings (which you call a router) and see if it has any settings enabling it to issue its own DNS settings or get those settings from the ISP's DHCP server.  The access point should be requesting that information from your ISP and then forwarding that information to any machine that connects to the network.  Your access point MAY be holding onto the DNS settings and telling any clients that connect to it "if you have any DNS queries just send them to me and I'll contact the DNS server for you" so look for a setting that coincides with that.  

Check your network settings to see if you have any information set statically.  Even if you do, ask for a new address & dns information by typiing:
```

sudo dhclient eth1

```

Worst case scenario - find out the DNS servers for your ISP and put them in /etc/resolv.conf - then restart networking with: 
```

/etc/init.d/networking restart

```

---

### Post by champion77 on 2009-07-27
I finally figured out the problem. It was not the driver, the Intel card, or Ubuntu. It was my Belkin Router. I had upgraded it, and had not accessed the Internet with my laptop for a while. So the fix was this:

I went to the Belkin website and reinstalled the firmware. Now it works better than Windows. :)

---

