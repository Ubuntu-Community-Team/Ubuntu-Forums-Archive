---
title: "Lost ethernet in Ubuntu, only"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by ratcheer on 2012-02-05
I have a weird situation. Last night, I was using Ubuntu with no problems and I shut down my system, normally.

This morning, I first booted to Arch Linux and everything was fine there, too. I rebooted, normally, and started Ubuntu. There was no network connection. I rebooted to Recovery mode. I couldn't ping anything, even the router by IP address.

So, I rebooted to Arch and the network is fine. So, it is pretty obviously not a LAN or hardware problem.

Ethernet seems to have disappeared in Ubuntu. Where should I start looking to fix this?

Thanks,
Tim

---

### Post by praseodym on 2012-02-05
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```
Install the package ethtool from [http://packages.ubuntu.com](http://packages.ubuntu.com) and show additionally
```
sudo ethtool eth0
```

---

### Post by ratcheer on 2012-02-05
Sorry, I went to church. When I got back, I was trying to troubleshoot the network problem when I discovered that /home was not mounted. I ran fsck on it's partition and it fixed a few orphan inodes. That doesn't seem to be a big deal. Then, I rebooted and everything is now back to normal.

This all seems very strange, to me. Why wasn't the filesystem fixed and mounted, automatically? Why did /home being unmounted kill the ethernet connection?

Should I still be concerned?

Through all of this, I rebooted to both Ubuntu and Arch, several times. The network was always fine in Arch, so I have to assume that the Ubuntu filesystem problem was indeed the problem. But I feel uncomfortable.

Thanks,
Tim

---

### Post by praseodym on 2012-02-05
Check the disk with

```
sudo smartctl -t long /dev/sda
```
My 500GB disk took 90 minutes for that! I deactivated X for that because of the temperature rising.

```
sudo smartctl -a /dev/sda
```

shows the results after that. In my case the "dead" sectors were shown in this line:

```
  5 Reallocated_Sector_Ct   0x0033   098   098   036    Pre-fail  Always       -       [COLOR="Red"]107[/COLOR]
```
as "107"

---

### Post by ratcheer on 2012-02-05
Ok, it happened again. I will run the test.

This PC (and disk drive) is less than a year old. :(

Thanks,
Tim

---

### Post by ratcheer on 2012-02-05
My installation does not have smartctl, but I am running palimpsest. It passed the quick test with flying colors. I am now running the long test.

As a humorous aside, I was looking at the palimpsest manual. The entire contents of the manual seem to be, "Palimpsest Disk Utility is a complex program, with many advanced       features." :D

[http://library.gnome.org/users/palimpsest/stable/advanced.html.en](http://library.gnome.org/users/palimpsest/stable/advanced.html.en)

---

### Post by ratcheer on 2012-02-05
Long Smart scan says the drive is healthy and everything has a Good rating.

???

Tim

---

