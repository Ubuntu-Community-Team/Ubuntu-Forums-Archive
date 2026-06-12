---
title: "I can connect to the internet, but not to any websites"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by rogerdpenguin on 2010-08-10
I recently installed Ubuntu 10.4 on my laptop, realtek 8712 wireless chipset. I can connect to the internet, but websites don't load. Any ideas on what I should do?

---

### Post by Peter09 on 2010-08-10
Can you tell us how you know you are connected to the internet?
 
Also if you open a terminal and run the command
 
```
ping google.com
```
 
what messages do you get.

---

### Post by BlueGene1402 on 2010-08-10
This sounds very similar to my own problem, so I'm sticking around.
 
Got a new Compaq 610 Notebook yesterday with only FREEDos on it. I installed Lucid Lynx & it started fine but refused to connect on wireless. Eventually it somehow worked & it now tells me that yes it's connected but the 'signal strength' as I will call it is at 0%
 
It tells me I'm connected, but there's nothing really there.
 
 
 
I know very little Linux & not too familiar with my hardware :-S

---

### Post by Autonomous_user on 2010-08-10
I had that yesterday but today its fine, after I connected with a different distro via live disk then logged back into Ubuntu....weird. 

I hope your problem is that easy.

---

### Post by Peter09 on 2010-08-10
BlueGene1402 can you provide the output if the command
 
```
ifconfig
```
 
Do this with your wireless connected.

---

### Post by BlueGene1402 on 2010-08-10
[SIZE=2]Here is my output:[/SIZE]
 
[FONT=Times New Roman][SIZE=3]bluegene@Sirius:~$ ifconfig[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]eth0      Link encap:Ethernet  HWaddr d8:d3:85:22:59:ea  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          Interrupt:17 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:136 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:10512 (10.5 KB)  TX bytes:10512 (10.5 KB)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:30:32:a8  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          Interrupt:17 Memory:f8408000-f8408100 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[SIZE=2]Is there hope lol[/SIZE]

---

### Post by Peter09 on 2010-08-10
BlueGene
 
You are connected with the following parameters
 
wlan0 Link encap:Ethernet HWaddr 70:f1:a1:30:32:a8 

[SIZE=3][FONT=Times New Roman]inet addr:10.42.43.1 Bcast:10.42.43.255 Mask:255.255.255.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]your internet ip address is given as 10.42.43.1 - does this conform to your router setup?[/SIZE][/FONT]

---

### Post by VH-BIL on 2010-08-10
> **rogerdpenguin said:**
> I recently installed Ubuntu 10.4 on my laptop, realtek 8712 wireless chipset. I can connect to the internet, but websites don't load. Any ideas on what I should do?

Sounds like a DNS issue.

---

### Post by BlueGene1402 on 2010-08-10
[SIZE=2]@ Peter09 .. I wouldn't know o.O How do I find out?[/SIZE]

---

### Post by Peter09 on 2010-08-10
BlueGene - can you provide the output of command
 
```
route
```

---

### Post by BlueGene1402 on 2010-08-10
[SIZE=2]I really do NOT know what I'm doing :-S[/SIZE]
 
[EMAIL="bluegene@Sirius:~$"]bluegene@Sirius:~$[/EMAIL] route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      *                     255.255.255.0   U     2      0        0 wlan0
link-local          *                   255.255.0.0     U     1000   0        0 wlan0
 
[SIZE=2]All I know is that the main computer has DSL & all us moochers are hooked up via wireless.. I was given the network "name" & password "key" which got me this far.[/SIZE]

---

### Post by Peter09 on 2010-08-10
BlueGene
 
it appears that your main maichine (desktop) which you suggest is the way to get to the internet is not being detected by your machine as a gateway. 
 
What O/S is the desktop machine running - you need to get its IP address.

---

### Post by BlueGene1402 on 2010-08-10
Windows XP
 
IP Address 192.168.1.4
Default Gateway 192.168.1.1

---

### Post by Peter09 on 2010-08-10
OK, well if this is the case then the IP address in your machine is screwed up. Right click on the network icon and select the wifi tab, check that you have DHCP selected (or if not DHCP then an address similar to the desktop).
 
Are you sure you have connected to the right network? Did you need to enter a password?

---

### Post by BlueGene1402 on 2010-08-12
There was no wifi tab by the way & could not find this DHCP thing anywhere..
 
I had to get my hard drive formatted for other reasons & now starting over. This time around I can't get a connection in the first place lol.
 
Thank you for your time & I will probably be back for more help after I'm done experimenting with other systems & deciding which one I'll be sticking with - Xubuntu seems to have automatically resolved other issues I was struggling with e.g. camera & microphone etc.
 
Thanks again!

---

### Post by BlueGene1402 on 2010-08-12
Kubuntu!! First time to set eyes on it but connection management easier for me because everything mentioned so far is right there & I don't have to go looking for it e.g. typing in IP address or finding this DHCP thing.
 
My laptop's own wireless whatever didn't connect at all but when plugging a usb wifi thingie it managed to connect at 23% so once again it SAYS I'm connected fine but nothing happening.
 
Does this mean my laptop has wireless driver issues? Where do I go from here?
 
Kubuntu thankfully has a dialup option so if I need to download any files to fix the wireless problem then I can at least give that a try.

---

### Post by Peter09 on 2010-08-12
I would start a new thread saying that you have wireless connection issues. It looks like you wireless card needs drivers downloaded. Start a new thread and include the output of
 
```
lshw -C network
```
 
Do this with no hardwired connection attached.

---

### Post by Iowan on 2010-08-12
> **BlueGene1402 said:**
> My laptop's own wireless whatever didn't connect at all but when plugging a usb wifi thingie it managed to connect at 23% so once again it SAYS I'm connected fine but nothing happening. From a terminal (on Ubuntu it's Applications>Accessories>Terminal - not sure about Kubuntu), check **ifconfig -a**
to see if your interface has an IP address. The "connected" message *might* mean you reached the router/DHCP server, but something else is amiss. 
(The link-local *might* be an issue...)

---

