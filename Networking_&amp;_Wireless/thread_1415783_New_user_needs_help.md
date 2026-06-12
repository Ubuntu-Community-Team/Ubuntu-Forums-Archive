---
title: "New user needs help"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by RedDog1 on 2010-02-25
I just installed Ubuntu onto my netbook, and I cannot log onto the internet through my wireless network.  I am wondering if there is a program I can download & install, or if there is a way to connect in Ubuntu.  Any and all help is greatly appreciated.

---

### Post by amsterdamharu on 2010-02-25
Can you copy the output of the following command and post it here?

```
ifconfig
```

You an run the command in the terminal which is under applications -> accessories 

Assuming you don't have kubuntu but Ubuntu with gnome.
There should be a network icon left of the time (top right of your screen). Click that and see if there is wireless network.

Check if your laptop has a button combination that can switch wireless on or off (usually a light will turn on or off).

---

### Post by RedDog1 on 2010-02-25
> **amsterdamharu said:**
> Can you copy the output of the following command and post it here?
 
```
ifconfig
```
 
You an run the command in the terminal which is under applications -> accessories 
 
Assuming you don't have kubuntu but Ubuntu with gnome.
There should be a network icon left of the time (top right of your screen). Click that and see if there is wireless network.
 
Check if your laptop has a button combination that can switch wireless on or off (usually a light will turn on or off).
 
I will have to do it tonight, as my problem is with my home wireless network.
 
Yes, I loaded Ubuntu 9.10 from a cd a friend gave me.  A drop menu pops up when I hit that button, and no, there is not a way to turn off the wireless adapter on the outside of the netbook.  thanks though, for your assistance.  I will post later tonight to see if you, or anyone, can help diagnose my problem.

---

### Post by gordintoronto on 2010-02-25
Also, tell us exactly what netbook you have.  Then Google:
 "netbook brand and model" Linux

Right-click the network icon and select "edit connections," then click the wireless tab and the "add" button, then you will have to enter your router's ID, encryption typoe and password.

---

### Post by RedDog1 on 2010-02-25
> **gordintoronto said:**
> Also, tell us exactly what netbook you have. Then Google:
"netbook brand and model" Linux
 
Right-click the network icon and select "edit connections," then click the wireless tab and the "add" button, then you will have to enter your router's ID, encryption typoe and password.
 
 
Router's ID?  Where would I find that?

---

### Post by gordintoronto on 2010-02-25
> **RedDog1 said:**
> Router's ID?  Where would I find that?

Also known as the SSID.  It's your router, you have set it up.

---

### Post by RedDog1 on 2010-02-25
> **amsterdamharu said:**
> Can you copy the output of the following command and post it here?

```
ifconfig
```

You an run the command in the terminal which is under applications -> accessories 

Assuming you don't have kubuntu but Ubuntu with gnome.
There should be a network icon left of the time (top right of your screen). Click that and see if there is wireless network.

Check if your laptop has a button combination that can switch wireless on or off (usually a light will turn on or off).

what am I looking for when I run ifconfig?  I am on that machine, but it would take a while to type all that.

---

### Post by r-senior on 2010-02-25
Could you copy and paste it into a file, pop it onto a USB stick, transfer that to the machine where you are posting from and post?

---

### Post by RedDog1 on 2010-02-25
> **r-senior said:**
> Could you copy and paste it into a file, pop it onto a USB stick, transfer that to the machine where you are posting from and post?

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:26:18:91:34:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:5e:90:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-25-D3-5E-90-B5-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by RedDog1 on 2010-02-25
Is that what you were asking for?

---

### Post by RedDog1 on 2010-02-25
bump

---

### Post by RedDog1 on 2010-02-25
Never Mind, I got it working.

---

### Post by r-senior on 2010-02-26
Before you get impatient with people replying you need to remember that:

a. This is a community, not a helpdesk
b. Not everyone is in the same timezone as you are

Are you going to tell us how you got it working?

---

### Post by RedDog1 on 2010-02-26
> **r-senior said:**
> Before you get impatient with people replying you need to remember that:
 
a. This is a community, not a helpdesk
b. Not everyone is in the same timezone as you are
 
Are you going to tell us how you got it working?
 
I wasn't getting impatient. I am sorry if it came across that way.
 
a. I understand that.
b. I understand that.
 
I got it working by reading another thread where you attempt to connect to hidden wireless networks. After I typed in my password, it connected to my wireless network.

---

### Post by marbertone on 2010-02-26
Try wicd, it solved me all my wireless troubles! :KS
Ciao,
Mario Alberto:popcorn:

---

