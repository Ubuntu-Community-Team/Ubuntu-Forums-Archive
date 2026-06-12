---
title: "Data drom Wireshark"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by Bakakun on 2011-03-23
Hello,
I'm on windows, and I've installed Ubuntu 10.10 on a virtual machine with VMware player.
I'm trying to use Wireshark, and I've suceeded to find interfaces. So I choose eth0 or any.

The problem is that I only see datas from my own traffic, and only on my virtual machine. I mean that if me, or anybody else on the network is doing something, I can't see it.
Is that normal ? I know that on Windows, the "microsoft" interface just allows to see what's going on on your own computer.

Does someone know how to receive datas from windows computers on my network ? Is the problem from the fact that it is a virtual machine ?

Thanks you very much

Bakakun

PS : If I made any language mistake, I'm sorry, I'm French ^^"
PS 2 : I meant "from" and not "drom", of course ...

---

### Post by Fire_Chief on 2011-03-23
I'd guess your VMware Player networking setup has the interface using NAT by default for conneting to the network. If you have the option, change it from NAT to bridging. This will allow the VM to talk directly on the network and appear like any other PC on the subnet.

Cheers!

---

### Post by Bakakun on 2011-03-23
Thank you

Ok, I did it, but now the problem is that I don't have any connection from Ubuntu.

When I'm in networking configs, I don't really know what to do ... I mean the wireless network I've in my boarding school is open, no WEP or WPA key ... Ubuntu is asking me for SSID, MAC adress, etc. How can I find it ?

Bakakun

---

### Post by conneco on 2011-03-23
Ive never used VMPlayer but try Virtual Box its open source and in VBOX you can bridge your adaptor so if your windows connects via wireless you tell virtual box to bridge your wifi adaptor, and then your Ubuntu will pick it up as its eth0

However wireshark will only pick up connections that are directly from or to your machine and it will only pick up broadcast packets from the entire LAN, 

If your looking to pick up everything and sniff all network traffic then you'd need to look at ettercap and ARP poisoning get the permision of your school and people on the LAN 1st though as it could be seen as hacking and get you kicked out and or put in Jail

---

