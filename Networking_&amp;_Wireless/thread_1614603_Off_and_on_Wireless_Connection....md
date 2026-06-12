---
title: "Off and on Wireless Connection..."
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by Coda_ on 2010-11-05
I recently upgraded to 10.04, and after a day, had connection problems. So I got rid of the Network Manager, and set up Wicd. Only now, It connects, and then disconnects shortly after. The connection (while it is connected) jumps from strong to signal, to next to nothing. What could the problem be?

---

### Post by cipherboy_loc on 2010-11-05
Post the output of dmesg right after this connection issue. I am having a similar issue where with NetworkManager it disconnects and then reconnects. Right after the disconnect I did a dmesg and found a SEGV fault with the wifi module. 

Edit: It turns out there was a SEGV, but it just happened again and there was no SEGV. Just a note. 

Cipherboy

---

### Post by Coda_ on 2010-11-05
> **cipherboy_loc said:**
> Post the output of dmesg right after this connection issue. I am having a similar issue where with NetworkManager it disconnects and then reconnects. Right after the disconnect I did a dmesg and found a SEGV fault with the wifi module. 



Cipherboy


How do I do that? I'm still learning the basics of Ubuntu.


Edit- I can connect fine after a restart, but it goes down hill from there. Starts strong, then cuts out more and more frequently, then it gives me a message that it cant find the IP Address.I dunno if that helps at all.

---

### Post by cipherboy_loc on 2010-11-06
Nvmind about that one. It turns out it is something with the libipw on my system. Open up a terminal using alt+f2 and in the box type in gnome-terminal. (Assuming you run Ubuntu, not KUbuntu, XUbuntu, etc).

In the box that pops up, enter:
```
lspci  | grep -i 'wireless'
```

and post the output. Also enter:
```
lsmod  | grep -i 'ipw'
```
and post the output of that.



Cipherboy

---

### Post by LouisaLou on 2010-11-06
Hi, 

I'm having a similar issue. I'm a total newcomer to Ubuntu but am enjoying learning the ropes. I apologize in advance for the naivete of my questions...

I arrived in the Central African Republic only to find that my wireless (on an HP Mini 5102) wasn't working -- it didn't detect any wireless networks. I had had problems once or twice before, but nothing this bad. So I wiped off Windows and installed Ubuntu 10.10, hoping that would help. Luckily, it did! (Partly.) 

At first, I still didn't get any wireless networks. I messed around with all the various things you have to do to get Broadcom wireless drivers working. Finally, following a forum suggestion, I installed Wicd -- and this did the trick. Not knowing any better, I kept Network Manager alongside Wicd, but Wicd is what works much better. (Is it OK to keep Network Manager alongside Wicd?)

However, when I try to connect wirelessly to the network at this country's one cafe with wifi (which usually works really well, by CAR standards), their wireless network doesn't appear. At the office, when I open Wicd, it includes a box with the message "<connection name>: obtaining IP address", and bit by bit it connects. But when I open Wicd at the cafe, this doesn't happen -- it just gives me a list of random signals from nearby offices (all secured and low-signal), none of which I can connect to. Any ideas how I could get the cafe network to show up, and how I can get it to refresh the IP address, if necessary?

I'm at the office now, and so it's working. However, in order to get it working I had to restart three times -- Wicd only seems to work about half or 33% of the time. Sometimes I get the message: "Connection failed: unable to get IP address" and sometimes I get the message "No wireless networks detected." Then I try again and eventually it works. So far. 

Any suggestions/advice would be so much appreciated! I'm headed out to a small provincial town many hours from the capital, and there will be only one wifi connection there, so I'm eager to work the bugs out beforehand. I'm happy to post more technical info, I just need a little guidance!

Thanks so much!!

---

### Post by Coda_ on 2010-11-06
> **cipherboy_loc said:**
> ```
lspci  | grep -i 'wireless'
```

```
05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico1] Network Connection (rev 05)
```

> ```
lsmod  | grep -i 'ipw'
```

```
ipv2200                            135216  0
lipipw                              39896  1 ipw2200
lib80211                             5046  2 ipw2200,libipw
```

---

