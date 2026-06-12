---
title: "Problem in getting my NIC's Mac address ..."
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by Luk8 on 2006-06-10
I attached some files with what command if used to try to debug the problem I have. 
I should get my IP and settings from my ISP's DHCP servers , but I coudn't do that even with   sudo dhclient -s 213.157.xxx.xxx eth0 .

First problem I had was that the kernel was loading 2 modules for my Realtek Card : 8139cp , 8139too , and after checking both separtely I renamed 8139cp to 8139cp.bak to avoid loading it.
Also I disabled IPv6 from the /etc/modprobe.d/aliases file .

Still ... ifconfig return a invalid MAC for my NIC , it's always :  00:00:00:00:00:00 . I had the same problem in breezy and I don't have a clue how I fixed it then ( more then half a year ago ). I am on a dual boot station and the Internet works fine on WinXp .

What can I do to fix this ? I am struggling to fix this for a couple of days , searched the forums intensivly for answers .

I tried to make a static config for eth0 ( from the GUI first then from the /etc/network/interfaces file , but nothing solved , so I reverted to DHCP ).

Any advices ? ](*,) ](*,) ](*,)

---

### Post by dvarsam on 2006-06-13
[QUOTE=Luk8]Still ... ifconfig return a invalid MAC for my NIC , it's always:  00:00:00:00:00:00.
I had the same problem in breezy and I don't have a clue how I fixed it then ( more then half a year ago ). I am on a dual boot station and the Internet works fine on WinXp .

What can I do to fix this?
I am struggling to fix this for a couple of days, searched the forums intensivly for answers.

I tried to make a static config for eth0 ( from the GUI first then from the /etc/network/interfaces file , but nothing solved , so I reverted to DHCP ).

Any advices ?[/QUOTE]

I am NO expert at this, but I have an idea:

IF you connect your NIC to a Router (if you can find one...), then the Router can finally be able to "show" you your MAC address.

If all you care is to see what is your MAC address, maybe that is a way to do it...

Hope I helped...

P.S.> I just saw that through my Router I can see the MAC addresses...
(hope you find this idea valuable...)

---

