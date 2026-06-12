---
title: "Realtek 8111C Issues: No link, but works in windows"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by BobSutan on 2009-01-08
I just built a new system with the below mobo and integrated NIC and I'm dual-booting with Windows XP.

GIGABYTE GA-EP45-UD3R and the LAN chipset is a Realtek 8111C.

In windows the NIC functions perfectly fine. However, in 8.10 Intrepid the NIC shows up, but is not showing link on the adapter. I reboot into Windows and it works just fine, so I know it's getting link from the switch. I tried to toggle the interface with the below commands to see if maybe it's getting stuck when the OS was coming up, but that didn't work either. What gives?

```
sudo ifdown eth0
sudo ifup eth0
```


**Edit**
I've been doing some more searching and the particular problem I have seems to be related to a Wake on LAN setting in Windows. I took care of that, but it's still not coming up with link. Next up is to pull the power plug, wait 15 seconds, then reboot and see if that fixes it.

---

### Post by x22 on 2009-01-08
found this in a forum search:--

Re: Problems with Realtek RTL8168C/8111C
Solved it thanks to this:
[http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

---

### Post by BobSutan on 2009-01-09
> **x22 said:**
> found this in a forum search:--

Re: Problems with Realtek RTL8168C/8111C
Solved it thanks to this:
[http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

Saw that when I was doing my searches. I got it working with the hard reboot by the way, so I think it is something to do with the WoL after all.

---

### Post by BobSutan on 2009-01-09
Just a heads-up that cold reboot by pulling the plug and booting straight into Ubuntu got it to work. Time to find a permanent solution so I don't have to pull the plug every time I reboot.

---

### Post by BobSutan on 2009-01-10
Turned off Wake on LAN in the bios and it works fine now. Thanks guys!

---

### Post by jcpshd on 2009-02-20
Hi guys!!! This worked for me:

[http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

Hope it helps!

---

