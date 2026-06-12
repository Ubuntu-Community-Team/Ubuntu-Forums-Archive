---
title: "Network Manager error messages possible?"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by vasa1 on 2012-02-12
If I access my internet via MS Windows and if there's a problem, I get various error messages, mostly 651 (*Your modem (or other connecting device) has reported an error*) or 678 (*There is no answer*).

However, when I do the same via Network Manager on Ubuntu 11.10 for the same ISP on the same PC and if there's a problem, I don't get an error code, just a pop-up informing me that I'm disconnected and, of course, the up/down arrows are replaced with an "empty wedge".

The reason I'm asking is because the guys at the ISP ask me for the error code ... which I can provide only if I reboot into Windows which I don't want to do just to answer their question when it's nearly always been a problem at their end.

For now, I just lie and say I'm seeing error 651.

Does anyone know how to get these (or equivalent) error messages to show up when using Ubuntu so I don't have to lie?

---

### Post by praseodym on 2012-02-12
Hi,

just check the system error messages:

```
dmesg >> dmesg.txt
```
Upload this text file. More info about your particular system:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
cat /etc/network/interfaces
sudo iwlist scan
```
How do you connect? Modem, Router/Modem combination?

The debug-mode of the NM starts with:

```
sudo service network-manager stop
sudo NetworkManager --no-daemon
```
cancelling with CTRL+C. Show this output, too. Restart with:

```
sudo service network-manager start
```

---

