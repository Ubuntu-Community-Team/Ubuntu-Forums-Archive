---
title: "Broadcom STA wireless driver Activation failed- Dell Studio1558"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by naveenbabue on 2012-04-28
I just upgraded to 12.04 from 11.10. For the previous upgrades untill 11.10, I used to connect ethernet cable and activate broadcom sta wireless drivers. It worked well.
Now, it failed with the error message.
Sorry, Installation of the driver failed. Please have a look at the log files for details: var/log/jockey.log

Appreciate any help.

Thanks,
Naveen

---

### Post by chili555 on 2012-04-28
We need more information. A known issue is that jockey; also known as Additional Drivers, suggests the wrong driver for a few Broadcom cards. Let's find out what you have and solve it. Please open a terminal and run and post:
```
lspci -nn | grep 0280
```

The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by naveenbabue on 2012-04-28
The output:
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

Your suggestion on the post titled: [B]Broadcom STA Wireless drivers not working on Acer aspire 5750G, Ubuntu 12.04. Worked well for me.

Appreciate your help. Thank you!
[/B]

---

### Post by Morate on 2012-04-28
I have the same problem. When I enter that command, here's what it looks like:

g******@m******:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

Any suggestions help! Thanks!

---

### Post by chili555 on 2012-04-28
> **Morate said:**
> I have the same problem. When I enter that command, here's what it looks like:

g******@m******:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

Any suggestions help! Thanks!This should work for you too: [http://ubuntuforums.org/showpost.php?p=11882998&postcount=4](http://ubuntuforums.org/showpost.php?p=11882998&postcount=4)

**Note to searchers**: The exact fix depends on your pci.id. If yours is not the same, the fix may not be the same. Ask in a new thread.

---

### Post by hmms on 2012-04-29
Had the same problem with the wireless on my studio 1558. chili555 your solution worked! Thanks a lot! :)

---

### Post by mojitoking on 2012-04-30
This worked perfectly for me, what was the cause for the error? The log read 'blacklisted' or something of that sort. Here's the output.


```
mojitoking@XXX:~$ tail /var/log/jockey.log
2012-04-30 20:58:40,289 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-30 20:58:40,335 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-30 20:59:22,789 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-30 20:59:23,585 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-30 20:59:23,585 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-04-30 20:59:23,657 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-30 20:59:25,450 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-30 20:59:25,479 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-30 20:59:25,525 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

---

