---
title: "Can't setup network in AD-hoc mode for ubuntu server 10.04"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by rahulht on 2013-05-10
HI Guys, 

I m struggling in setting up my network to start up in Ad-hoc mode. Actually, I had successfully done it before; but I m really not sure what went wrong and now it doesn't work.
I have installed ubuntu server on my mother board and attached Atheros ath5k wireless card. I have modified the interface file /etc/network/interface to work in Ad-hoc mode as follows:

auto wlan0
iface wlan0 inet static
address 10.11.12.5
netmask 255.255.255.0
wireless-essid myid
wireless-mode ad-hoc
wireless-channel 1
wireless-key off

When i run the command ifconfig, i do not find the entry for wlan0, instead find entries for 'lo' and 'virbr0'.

Moreover, when i run the following command:  sudo lshw -class network, i get the following results :

*-network DISABLED
description: wireless interface
.
.
logical name: wlan 1 --- > which I find strange, since I have an entry only for wlan0 in interface file.

Any help is highly appreciated .. Thanks !

---

### Post by chili555 on 2013-05-11
It's funny how a user sometimes asks a simple question that raises even more questions for which there are no easy answers.> logical name: **wlan 1** --- > which I find strange, since I have an entry only for wlan0 in interface file.

First, you, the humble user, do not set the interface name wlan0, wlan1, wlan168, etc. Normally the driver sets the name to wlan(next_available) or eth(next_available) or wifi(next_available), etc. A mechanism called udev finds out if you have or ever in history had a wlan0 with some different MAC address. If so, it sets the next wireless instance as wlan1.

However, do you really care? If it connects and works as expected, could you be happy even if it were named spaghetti12? The first step I suggest you try is to change your /etc/network/interfaces to wlan1. Reboot and tell us if everything works as expected. If so, case closed and another Solved for old Chili. If not, we'll troubleshoot further.

Why do you need your server as ad hoc? That's a very unusual setup.

---

### Post by prodigy_ on 2013-05-11
> **rahulht said:**
> *-network **DISABLED**
description: wireless interface
Here's the root of your problem. The output of ```
rfkill list all
``` could help identify the issue.

---

### Post by rahulht on 2013-05-13
Hi  @chilli555 and @prodigy_,  thanks for your response..

I apologize for the delay in responding..

Well, yaa the name really doesn't matter whether wlan0 or 1 .. but it used to work previously.. so i had some doubt.. (before posting this question i had tried wlan2)
Actually, I  m working on a project to implement a group of systems connected in Ad-hoc to get practical statistics about network performance in real environment.

Anyways, I changed to wlan 1 and now, the output of ifconfig shows wlan1 set to my set IP address. 

The output of lshw -class network now is:
*-network         ---> looks to be solved
    description: Wireless interface

  and the output of 'rfkill list all' in both cases for wlan0 and 1: 0: phy0: Wireless LAN
                                                                                     Soft bloked: no
                                                                                     Hard blocked: no

Well, but this still doesn't solve my problem, I cant ping to the other system which I have configured exactly in the same way of course with a different IP.. (Destination host unreachable) I really don't know where i went wrong..  

Thanks.. awaiting for your reply..

---

