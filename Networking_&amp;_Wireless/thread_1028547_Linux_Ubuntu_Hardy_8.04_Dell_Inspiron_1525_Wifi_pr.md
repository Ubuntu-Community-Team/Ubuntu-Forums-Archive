---
title: "Linux Ubuntu Hardy 8.04 Dell Inspiron 1525 Wifi problems"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by niled on 2009-01-02
Wifi problems with Dell Inspiron 1525 Linux Ubuntu 8.04 Hardy
Hi!

I got a Dell inspiron 1525 Laptop with Linux Ubuntu 8.04 Hardy

The Wifi modem I got is a: 0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I have problems with my Wireless connection. I recently tried to insert a sim-card into the modem to get wireless internet. But I didn't get a wireless icon anywhere and it didn't work, I tried just to find some wireless networks in my neighbourhood(I know that least one got it cuz I found it with my brothers computer) but I still can't find the icon or anything. I've been looking around on the different forums to find a solution, tried some of them i.e. this one:

[http://www.debianadmin.com/enable-wp...ntu-linux.html](http://www.debianadmin.com/enable-wp...ntu-linux.html)

Which didn't work for me. I don't have this icon which is shown here: [http://www.debianadmin.com/images/wpa/1.png](http://www.debianadmin.com/images/wpa/1.png)

And in the System-->Administration-->Hardware drivers |Nothing is shown, it's empty, which makes me wonder if the computer even knows that there's a Wifi-modem.

Anyone know what to do? Or what is the problem? Appreciate any help!

//Johan****

---

### Post by ieee488 on 2009-01-02
do a search on this forum for your card model #; there are others who have it contrary to the notion that yours is unique

---

### Post by niled on 2009-01-07
done a search, none has a solution to the others problems. No one has solved the problem.

---

### Post by superprash2003 on 2009-01-07
post output of 
1)lshw -C network 

 from the terminal

---

### Post by niled on 2009-01-08
This is what I get:

  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:02:5e:77
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.2.100 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945

If you need anything else just let me know

---

### Post by superprash2003 on 2009-01-08
it looks like it has been recognized..post output of
1)iwlist scanning
2)iwconfig

---

### Post by superprash2003 on 2009-01-08
sorry..double post..

---

### Post by niled on 2009-04-02
My wireless does now work. Because of a failure in my computer, the button on the side was broken, that's why it didn't start the wireless. But it now works fine!

---

