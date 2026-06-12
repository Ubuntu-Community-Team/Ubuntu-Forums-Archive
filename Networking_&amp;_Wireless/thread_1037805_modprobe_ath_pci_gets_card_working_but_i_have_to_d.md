---
title: "modprobe ath_pci gets card working but i have to do that every time i reboot"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by spermw0rm on 2009-01-12
installed madwifi drivers and lost my wifi conection tried numerous bits of info and the only way i can get my atheros card working is th use the command modprobe ath_pci logged in as root
once used i can see card in ifconfig and iwconfig and also icon for networks at top of screen

there must be a way to make this auto load on bootup
as you may have guessed im new to ubuntu and to the whole linux field so any help would be greatly appreciated

useing eeepc untubu 8.10

---

### Post by dmizer on 2009-01-12
> **spermw0rm said:**
> installed madwifi drivers and lost my wifi conection tried numerous bits of info and the only way i can get my atheros card working is th use the command modprobe ath_pci logged in as root
once used i can see card in ifconfig and iwconfig and also icon for networks at top of screen

there must be a way to make this auto load on bootup
as you may have guessed im new to ubuntu and to the whole linux field so any help would be greatly appreciated

useing eeepc untubu 8.10

Why do you have to log in as root to run that command? Just use sudo:
```
sudo modprobe ath_pci
```

That's a different issue though. Can you post the output of:
```
cat /etc/modprobe.d/blacklist | grep ath
```

If there is no output from that command, are you sure you have the Atheros driver enabled in System > Administration > Hardware Drivers?

If so, can you please post the output of this command (before you modprobe):
```
lshw -C network
```

---

### Post by spermw0rm on 2009-01-12
cat /etc/modprobe.d/blacklist | grep ath

responds cat: /etc/modprobe.d/blacklist: no such file directory

lshw -C network responds

*-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:3e:f3:0b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E
driverversion=1.0.0.7-NAPI firmware=L1e latency=0 module=atl1e
multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:2a:c0:0e:6b:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3
firmware=N/A multicast=yes

---

### Post by spermw0rm on 2009-01-12
admin hardware drives says support for atheros 802.11 wireless lan cards the driver is active but not currently in use

---

### Post by dmizer on 2009-01-12
> **spermw0rm said:**
> cat /etc/modprobe.d/blacklist | grep ath

responds cat: /etc/modprobe.d/blacklist: no such file directory
This could be a problem.

What is the output of:
```
ls /etc/modprobe.d
```

---

### Post by spermw0rm on 2009-01-12
> **dmizer said:**
> This could be a problem.

What is the output of:
```
ls /etc/modprobe.d
```

ls: cannot access /etc/modprobe.d: no such file or directory

---

### Post by dmizer on 2009-01-12
It appears as though you've messed up your system somehow. The account you're currently signed in under ... is it an account you created or is it the one that was created during install? Or ... is this pre-installed from the factory?

---

### Post by spermw0rm on 2009-01-12
account created on install

---

### Post by dmizer on 2009-01-12
What is the output of this command:
```
groups
```

---

### Post by spermw0rm on 2009-01-12
groups
skeav adm dialout cdrom plugdev lpadmin admin sambashare

---

### Post by dmizer on 2009-01-12
Well, that makes no sense.

Can you use sudo at all? For example, can you get a root prompt by typing the following:
```
sudo -i
```

---

### Post by spermw0rm on 2009-01-12
sudo -i
[sudo] password for skeav
entered password
root@ubuntu:-#

---

### Post by dmizer on 2009-01-12
Well, I'm stumped at this point. Your problem seems to be that your primary user account doesn't have privileges to important parts of the system and this is why you can't start your network.

Obviously you can sudo, but something is very wrong and it's going to be beyond my ability to help you determine what it is. I will make some inquiries to see if I can find someone with an answer. In the mean time, I highly suggest that you try talking to the folks at the ubuntu IRC channel: [http://www.ubuntu.com/support/community/chatirc](http://www.ubuntu.com/support/community/chatirc)

Sorry :(

---

