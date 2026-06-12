---
title: "No Internet afer 9.04 Install"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by draugel on 2009-08-15
Hi,

I´m completely new to Linux. I´ve been having a malfunction on my internet connection.

I have an P4 2.66 Ghz with an Intel 945G Mother, 2 Gb RAM, Nvidia 8400GTS, SATA2 500GB and IDE 80 GB hard drives.

I´ve intalled Win XP in my SATA disk (making 2 partitions) an then Ubuntu in my IDE drive(Dual Boot - GRUB is working great!). The first time I´ve installed both OS they work perfectly. After last night. I´ve installed the Log Me In soft for accessing my pc from my place of work (under windows), then I´ve restarted and "oops", no internet in Linux. The funny thing about that is that my Auto eth0 says it´s connected, but i cannot access to nothing on the web. So, like an completely noob that I am, i´ve restarted windows, uninstalled the log me in, search for all the entries in the regedit and getting rid of them and then i´ve retarted again. NO INTERNET ON LINUX (freaking windows is working good). 
After that i´ve starting to read the formuns and trying a bunch of things. 

ifconfig (gives me the ip address)
changing the values on interfaces
and a lot of other stuff i´ve been reading.

None worked
I´ve reinstalled both Windows and Ubuntu (Formatting the particions for each one of them). 

Now the Jack Pot, Internet still does not work in Linux.  
I connect directly to a Modem and the very bizarre thing is that internet work before perfectly. In windows it still does.
I have an Intel 82801G Lan Card (lspci gives me that).

If anyone can help me i´ll be very grateful

Thanls!

---

### Post by nixscripter on 2009-08-15
One thing you might want to try is see if Linux has the routing information set up correctly or not. Run the **route** command in the Terminal and see what it gives back.

---

### Post by draugel on 2009-08-16
Thanks for answering nixscripter.

Here the results of the **route** command:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
186.18.52.0     *               255.255.252.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0

---

### Post by nixscripter on 2009-08-16
Assuming that you were connected when you ran that, it means your routes are off.

Try this next time you connect:
```
sudo route add default gw **p2p-end-point**
```

Where the end point is the IP address used as a gateway. If you don't know what that is, see what DNS server they gave you in the DNS file **/etc/resolv.conf**; it might be the same.

---

### Post by draugel on 2009-08-17
Ok, i've started Ubuntu today and internet is working, don't ask me how but it works.

I'm testing all right now (currently upgrading) and it seems to work just fine. After the upgrade i'll try to run the Hardware drivers and see if I can get the propietary drivers for my NVIDIA card.

Thanks for your help, eitherway I would like to understand WTF happenned.

---

