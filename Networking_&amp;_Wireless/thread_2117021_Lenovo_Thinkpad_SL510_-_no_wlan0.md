---
title: "Lenovo Thinkpad SL510 - no wlan0"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by blommethomas on 2013-02-17
Hi all,

In the past I had issues with wireless on my Lenovo laptop running Ubuntu.  However I found a solution by installing the appropriate driver from apt-get:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
ifconfig wlan0 up
```


recently however, I upgraded a few packages using Synaptic and suddenly wireless stopped working completely.  I tried solving it by running the commands above but I get the following error:
```
thomas@OrsoBruno:~$ sudo ifconfig wlan0 up
wlan: ERROR while getting interface flags: No such device

```

Can someone help me?

---

### Post by praseodym on 2013-02-17
```
sudo ifconfig wlan[COLOR="Red"]0[/COLOR] up
```
?!

---

### Post by blommethomas on 2013-02-17
nope, same issue. i made a typo in the above code snippet

---

### Post by blommethomas on 2013-02-20
can someone help me with this?

---

### Post by praseodym on 2013-02-20
Did you install the tools needed to compile:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
```

Reboot.

---

### Post by blommethomas on 2013-02-24
I ran this command but it didn't change anything.
I still have no wlan0 available.

Perhaps there are some commands I can run to give some extra details on my situation?

---

### Post by praseodym on 2013-02-24
Yes, please show:
```

lspci -nnk
lsusb
lsmod
iwconfig
dmesg | egrep 'rtl8|wlan0|81'
```

---

