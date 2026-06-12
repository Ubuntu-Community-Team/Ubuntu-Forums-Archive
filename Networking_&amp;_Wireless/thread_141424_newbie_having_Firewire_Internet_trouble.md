---
title: "newbie having Firewire Internet trouble"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by chessieman on 2006-03-08
Hello all, I am Brand Spanking new to Ubuntu and Linux I hope someone will assist me and thank you in advance.

My Setup
I have a "main" PC that is running window xp MCE 2005. It is connected to my cable modem.
My secondary computer which I have just installed Ubuntu on is connected to his computer via firewire. I have a Firewire (8) pci card in both computers (ipod).

Situation:
I had been having difficulty choosing which version of linux to install on my Secondary computer, I ran several "live" Cd's and when I ran Ubuntu Live much to my amazement, it detected my firewire internet and I was off and running right away. I was very excited and decided to do a full install. Now it is not detecting or connecting to my firewire internet connection.

Can anyone help?
I know I need a NIC and a router and plan on purchasing one soon but in the mean time can i get this to work?

Thanks for your time

---

### Post by Lambert on 2006-03-08
Not that familiar with eth1394 but 

1. Check if driver is loaded. Run from a terminal this command:

```
lsmod | grep eth1394
``` 
You will get either this

```
eth1394                20616  0
ieee1394              299832  1 eth1394

``` 
or just another prompt.

2. If you get just another prompt run this command to load the module

```
sudo modprobe eth1394
``` 
3. Now look to see if you have your device listed in the network window
System->Administration->Network

If so try to configure the device and activate it.

---

