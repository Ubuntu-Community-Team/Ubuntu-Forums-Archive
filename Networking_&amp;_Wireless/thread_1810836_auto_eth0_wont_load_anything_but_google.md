---
title: "auto eth0 wont load anything but google"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by moorhead98 on 2011-07-23
Hello, I have an Acer Aspire M1610 desktop with Vista (SP2) and Ubuntu 10.04 LTS dual boot. When i first tried to download Ubuntu, i tried the 10.10 install Cd, and it froze up every time. When i tried the LTS, it downloaded, but the internet connection doesn’t work. It uses auto eth0. I can not get it to use the wireless network (the modem is connected to the desktop), and the auto eth0 can only get to Google, Google images, and anything else Google. It cannot go anywhere else. It just shows the loading bar/circle thing, but it doesn’t load. I left it overnight once and it still didn’t work. this is for both Firefox, chrome, and anything else that uses the internet. It wont download updates either. 
Is this a compatibility error with the computer itself? or are there drivers missing? Any ideas?

---

### Post by papibe on 2011-07-23
Could you post the result of these commands?
```
$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Regards.

---

### Post by wildmanne39 on 2011-07-23
Hi, run these commands in a terminal and it will help us help you.
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
rfkill list All
```
Are you not able to connect with a wire and wireless both?

---

### Post by moorhead98 on 2011-07-23
> **papibe said:**
> Could you post the result of these commands?
```
$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```Regards.

sorry these arent exact. i copied the output to a document to a flash drive, then took the drive to my laptop and pasted the contents here

for $ ifconfig I got:

```
eth0                Link encap:Ethernet   HWaddr 00:1c:25:3e:bc:b0
                       inet addr:192.168.1.31   Bcast:192:.168.1.255   Mask:255.255.255.0
                       inet6 addr: fe80::21c:25ff:fe3e:bcb0/64 Scope:link
                       UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
                       RX packets:25 errors:0 dropped:0 overruns:0 frame:0
                       TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
                       collisions:0 txqueuelen:1000
                       RX bytes:2748 (2.7 KB)   TX bytes:5042 (5.0 KB)
                       Interrupt:19 Base address:0xdead

lo                   Link encap:Local Loopback
                      inet addr:127.0.0.1   Mask:255.0.0.0
                      inet6 addr: ::1/128  Scope:Host
                      UP LOOPBACK RUNNING MTU:16436   Metric:1
                      RX packets:98 errors:0 dropped:0 overruns:0 frame:0
                      TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
                      collisions::0 txqueuelen:0
                      RX bytes:11083 (11.0 KB)   TX bytes:11083 (11.0 KB)
```for  $ route -n :

```
Kernel IP routing table
Destination        Gateway            Genmask            Flags    Metric    Ref       Use   Iface
192.168.1.0        0.0.0.0            255.255.255.0      U        1         0           0   eth0
169.254.0.0        0.0.0.0            255.255.0.0        U        1000      0           0   eth0
0.0.0.0          192.168.1.1        0.0.0.0            UG       0         0           0   eth0
```for nslookup ubuntu.com :

```

Server:        208.67.222.222
Address:    208.67.222.222#53

Non-authoritative answer:
Name:    ubuntu.com
Address: 91.189.94.156


```for dig ubuntu.com :

```

; <<>> DiG 9.7.0-P1 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30278
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1280
;; QUESTION SECTION:
;ubuntu.com.            IN    A

;; ANSWER SECTION:
ubuntu.com.        542    IN    A    91.189.94.156

;; Query time: 47 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Jul 23 20:36:51 2011
;; MSG SIZE  rcvd: 55

```Does that help?

---

### Post by moorhead98 on 2011-07-23
> **wildmanne39 said:**
> Hi, run these commands in a terminal and it will help us help you.
```
sudo lshw -C network
``````
lspci -nn | grep 0280
``````
rfkill list All
```Are you not able to connect with a wire and wireless both?

ok for sudo lshw -C network :

```
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1c:25:3e:bc:b0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=full ip=192.168.1.31 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:19 memory:fdffc000-fdffc07f ioport:fe00(size=128)


```when i ran ```
lspci -nn | grep 0280
``` it did absolutely nothing.
Was that supposed to happen?



for rfkill list All :

```
Bogus list argument 'All'.
```was that helpful?

---

### Post by wildmanne39 on 2011-07-23
Hi, run this command please 
```
lsusb
```
I am checking for your wireless connection.
Thank you.

---

### Post by papibe on 2011-07-24
> **moorhead98 said:**
> 
$ ifconfig
```
...
UP BROADCAST RUNNING MULTICAST   [COLOR="Red"]**MTU:1500**[/COLOR]   Metric:1
...
**[COLOR="Red"]Interrupt:19 Base address:0xdead[/COLOR]**
```


> **moorhead98 said:**
> 
$ sudo lshw -C network :
```

  *-network 
...
       [COLOR="Red"]**vendor: Silicon Integrated Systems [SiS]**[/COLOR]
```
...


I think I got something!  This is my [reference]("http://www.linuxquestions.org/questions/linux-networking-3/sis191-ethernet-controller-failing-to-function-with-current-kernel-drivers-724910/"). Try this:

```
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 mtu 1024
$ sudo ifconfig eth0 up
```
Now try to access other sites than Google.
Let us know how it goes.

---

### Post by moorhead98 on 2011-07-24
> **papibe said:**
> I think I got something!  This is my [reference]("http://www.linuxquestions.org/questions/linux-networking-3/sis191-ethernet-controller-failing-to-function-with-current-kernel-drivers-724910/"). Try this:

```
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 mtu 1024
$ sudo ifconfig eth0 up
```Now try to access other sites than Google.
Let us know how it goes.

Before I do that, would it at all affect the vista partition or any other devices wirelessly  connected to the network?

---

### Post by jmoorse on 2011-07-24
No, it will only affect that interface (eth0) on ubuntu.

I cannot believe that a driver would max out at an MTU of 1024...sigh.

For all those interested in MTU: [http://staff.psc.edu/mathis/MTU/](http://staff.psc.edu/mathis/MTU/)

---

### Post by moorhead98 on 2011-07-24
> **papibe said:**
> I think I got something!  This is my [reference]("http://www.linuxquestions.org/questions/linux-networking-3/sis191-ethernet-controller-failing-to-function-with-current-kernel-drivers-724910/"). Try this:

```
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 mtu 1024
$ sudo ifconfig eth0 up
```Now try to access other sites than Google.
Let us know how it goes.

Yay! Lowering the mtu to 1024 works perfectly! And @jmoorse, it is sad that it topped out at 1024, but I'm just glad it works now! I can now make Ubuntu my main desktop environment (except when I have to use that pesky iTunes... Darn you Apple!).

Thanks to everyone for helping out and responding so quickly.

---

### Post by moorhead98 on 2011-07-24
> **moorhead98 said:**
> Yay! Lowering the mtu to 1024 works perfectly! And @jmoorse, it is sad that it topped out at 1024, but I'm just glad it works now! I can now make Ubuntu my main desktop environment (except when I have to use that pesky iTunes... Darn you Apple!).

Thanks to everyone for helping out and responding so quickly.

Well, it seems that whenever I (or somebody else for that matter) logs into windows, the mtu value is reset to the one windows uses, and not the one that works with Ubuntu. Is there any way i can create a launcher/program that turns it to what I need, or do I have to reset it every time?

---

### Post by nm_geo on 2011-07-24
> **moorhead98 said:**
> Well, it seems that whenever I (or somebody else for that matter) logs into windows, the mtu value is reset to the one windows uses, and not the one that works with Ubuntu. Is there any way i can create a launcher/program that turns it to what I need, or do I have to reset it every time?

```
gksudo gedit /etc/rc.local
``````
ifconfig eth0 mtu 1024
```add the line above the exit0 line
Save the file then exit close terminal
Reboot and run
```
ifconfig
```Let us know...By the way i just did it since I rarely run etho .. Hmm.. better fix mine back:P

---

### Post by papibe on 2011-07-24
Since your are running the desktop version, you can also easily set the MTU value using the GUI. Go to Network Connections, select eth0, edit, and then set the MTU value as in the attached picture.

Regards.

---

### Post by nm_geo on 2011-07-24
> **papibe said:**
> Since your are running the desktop version, you can also easily set the MTU value using the GUI. Go to Network Connections, select eth0, edit, and then set the MTU value as in the attached picture.

Regards.
+1 to papibe's method I always seem to do it the hard way.. q:o)

---

### Post by moorhead98 on 2011-07-24
thanks for the help everyone... now marking this thread as solved. If you guys are interested I have another thread with another problem that needs fixing. [http://ubuntuforums.org/showthread.php?t=1811361](http://ubuntuforums.org/showthread.php?t=1811361)
Thanks to everyone!

---

