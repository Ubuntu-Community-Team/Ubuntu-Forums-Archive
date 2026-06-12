---
title: "Networking failing on both wired and wireless connections"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by Shay Guy on 2012-01-26
Running 11.10 on a Lenovo B570, maybe a month old. When I try to connect to a network, wired or wireless, nm-applet does its normal "connecting" animation, but sort of "spasming" at the end of the loop. I think what appears in that icon's place for a frame or so *might* be a "loading applet" icon. After maybe a minute, the applet gives up trying to connect. This behavior started in the past few hours and has persisted after a reboot.

---

### Post by Shay Guy on 2012-01-26
Did some Googling. Tried some tips. Here was the output of netstat -nr:

```
$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

```

This seems likely to be relevant.

---

### Post by varunendra on 2012-01-27
Please post outputs of:
```
uname -mr
sudo lshw -C network
lsmod
ifconfig -a
iwconfig
rfkill list all
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

Do you have DHCP enabled on your router? Have you checked its 'pool' to see it is not full and it has IPs available to be leased?

---

### Post by Shay Guy on 2012-01-27
Never mind. It's working now, possibly because I booted Windows 7, then restarted and went back to Ubuntu. (Can I resurrect this thread if it happens to me again?)

---

### Post by varunendra on 2012-01-27
> **Shay Guy said:**
> (Can I resurrect this thread if it happens to me again?)
Sure you can.

And it is not uncommon with a dual boot system. As far as I know, it happens (on a few systems) due to the residues of firmware of one OS, in the flash memory of the NIC, while the other one is trying to use it. One solution is to give it a couple of minutes after shutting down, to let the firmware completely unloaded, before booting into the other OS. I'm not aware if there is a permanent and better solution.

Also, it is just one of the many possibilities. As such, your problem might be a different one. So if the problem re-occurs, post back with the outputs I asked in my previous post.

---

