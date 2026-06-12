---
title: "unable to turn wifi on after windows hibernate"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by soin on 2011-08-14
Hi ubuntu comunity.

I have searched all the forums and solutions i could find but still can't solve my problem. 

I own an Acer Aspire 5552g. I have installed 2 systems on it: Windows 7 and ubuntu 10.10. Everything works fine except wifi.

There is a lot of threads connected to this topic, but none has solved my problem yet.

The problem occurs when I hibernate Windows and then load ubuntu - I get unable to turn wifi on. As rfkill says - it is hard blocked. It wouldn't be a problem if i had a hard switch for wifi. but I only have fn+F3 for that, which somehow fails to work in my situation.

```

igor@igor-Aspire-5552G:~$ rfkill list
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

If I reboot Windows and then start ubuntu - everything's fine and working. fn+F3 turns wifi on and off as expected.

I will provide some more info:

when wifi's working:
```

igor@igor-Aspire-5552G:/sys/class/rfkill/rfkill1$ cat state
1

```
when it doesn't:
```

igor@igor-Aspire-5552G:/sys/class/rfkill/rfkill1$ cat state
2

```

some additional info:
```

igor@igor-Aspire-5552G:/$ lspci -nn
//left only network-connected info
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
08:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01) 

```

Waiting for some help, that thing has nearly made me desperate..

---

### Post by soin on 2011-08-18
bump

---

### Post by soin on 2011-08-23
Bump,
please, somebody?

---

### Post by praseodym on 2011-08-23
What happens if you do the following:

```
sudo su
echo 1 | tee /sys/class/rfkill/rfkill/state
exit
```
Maybe Windows shuts down the radio kill switch when hibernating. Can you change these settings somewhere?

---

### Post by soin on 2011-08-23
> **praseodym said:**
> What happens if you do the following:

```
sudo su
echo 1 | tee /sys/class/rfkill/rfkill/state
exit
```
Maybe Windows shuts down the radio kill switch when hibernating. Can you change these settings somewhere?

Thanks for the reply. I have already tried it myself. It doesn't raise any errors, but state still remains "2" (((

I will try to dig into Windows to search for ways for editing its wi-fi management while hibernating, thanks for the thought.

By the way, I have upgraded to 11.04 and the problem is still there.

---

### Post by praseodym on 2011-08-23
echo 1 | tee /sys/class/rfkill/rfkill/state

Check this when booting into the revovery mode.

---

