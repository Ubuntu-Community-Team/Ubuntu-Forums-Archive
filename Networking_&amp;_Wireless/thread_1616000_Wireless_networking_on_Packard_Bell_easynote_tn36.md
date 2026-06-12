---
title: "Wireless networking on Packard Bell easynote tn36"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by SAJA4 on 2010-11-07
[B]Hi 

I'm using a Packard Bell Easynote Tn36 laptop, and I'm having trouble with  Ubuntu 10.10 and the wireless network card, (probably because of lack of  driver). I.e. it is disabled. [/B] [B]

How can I enable it?[/B] 

[B]
I input this code [/B]

sudo lshw -C network

**and here is the output**

saja@saja-EASYNOTE-TN36:~$ sudo lshw -C network
[sudo] password for saja: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:11:ec:24
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.67 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:2000(size=256) memory:f2010000-f2010fff memory:f2000000-f200ffff memory:f2020000-f203ffff
  *-network UNCLAIMED
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:f2200000-f220ffff
saja@saja-EASYNOTE-TN36:~$ 

[B]
Thanks.[/B]

---

### Post by uncaspi on 2010-11-07
I think the driver of this card is ath9k

sudo /sbin/modprobe ath9k

---

### Post by SAJA4 on 2010-11-08
> **uncaspi said:**
> I think the driver of this card is ath9k

sudo /sbin/modprobe ath9k
[B][COLOR=Black]
I did this but still the wireless is disabled. 

what can I do ??[/COLOR][/B]

---

### Post by SAJA4 on 2010-11-08
**help please!!**

---

### Post by uncaspi on 2010-11-08
See if the ath9k driver is loaded. Type lsmod
If it`s there listed restart network. sudo service network-manager restart

Also look in sudo /sbin/lshw -C network

at the bottom card if it`s asigned to the wifi card.

Please post the content of /etc/network/interfaces

---

### Post by SAJA4 on 2010-11-09
[B]Thank you for helping

I found now how to [/B]**make it work****. first I have to write this **```
sudo /sbin/modprobe ath9k
```** then go to network icon on the top then right click  and click on Enable wireless. **[B]The problem is I have to do this each restart so I put it in startup application but it doesn't work. 
[/B]

---

### Post by uncaspi on 2010-11-11
Type su and give root passwd.

then pico /etc/modules  or gedit /etc/modules

Append ath9k.ko in the file. Next time you boot the driver is loaded. Notify me if you get problems. Glad I could help you.

---

### Post by cucu007 on 2010-11-11
> **uncaspi said:**
> Type su and give root passwd.

then pico /etc/modules  or gedit /etc/modules

Append ath9k.ko in the file. Next time you boot the driver is loaded. Notify me if you get problems. Glad I could help you.


That was awesome uncaspi, thank you for this great contribution to the community.

---

### Post by uncaspi on 2010-11-11
Thank you.

---

### Post by alphaamanitin on 2010-11-11
Don't forget to mark the thread as solved, so others with the same problem know this fixes it. 

AlphaA

---

### Post by uncaspi on 2010-11-11
How do you do that? Sorry I never figured it out. Perhaps only SAJA4 could do it:)

---

### Post by SAJA4 on 2010-11-11
> **uncaspi said:**
> Type su and give root passwd.

then pico /etc/modules  or gedit /etc/modules

Append ath9k.ko in the file. Next time you boot the driver is loaded. Notify me if you get problems. Glad I could help you.

[B]I did what you say but I type sodo instead of su cause I didn't know the root password 
and I type in the file just ath9k because ath9k.ko doesn't work with me after restart.

now [/B][B]each restart I do only Enable wireless ,is there any way to make it always Enabled?.

Thanks a lot.
[/B]

---

### Post by uncaspi on 2010-11-11
I`m not sure what you mean. Putting ath9k in /etc/modules should load the driver module at boot. You did save the file after editing it? Use Ctrl o in the pico editor.

---

### Post by SAJA4 on 2010-11-11
> **uncaspi said:**
> I`m not sure what you mean. Putting ath9k in /etc/modules should load the driver module at boot. You did save the file after editing it? Use Ctrl o in the pico editor.

**yes I saved it and the driver is loaded. but I still have to ****go to network icon on the top then right click  and click on Enable wireless.**

---

### Post by uncaspi on 2010-11-11
It don`t connect automaticly. I had to think about it:)

---

### Post by uncaspi on 2010-11-12
Try this found in a thread.
Found the solution.
Right click wireless icon, select edit connections, select wireless tab, edit connection, check "connect automatically".

---

### Post by SAJA4 on 2010-11-13
> **uncaspi said:**
> Try this found in a thread.
Found the solution.
Right click wireless icon, select edit connections, select wireless tab, edit connection, check "connect automatically".
[B][COLOR=Black]
I try this but doesn't work.[/COLOR][/B]

---

### Post by uncaspi on 2010-11-13
Ok. Then I don't know. Sorry

---

