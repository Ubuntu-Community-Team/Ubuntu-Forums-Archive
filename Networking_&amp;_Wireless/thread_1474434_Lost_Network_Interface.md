---
title: "Lost Network Interface"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by tommoose on 2010-05-06
Hi,
I've just spent the entire day trying to work this thing through, to no avail. Can anyone give me a hand?

I recently updated to 9.10 and got a login bug, which has been fixed but in the process, I may have caused this problem:

The initial problem was that the wired network was showing "not connected" in network manager, and no gui configuration seemed to change that.

Now, 
lshw doesn't list the wired interface,
ifconfig doesn't list the wired interface
networking won't start the interface if it's configured in /etc/network/interfaces


i tried clearing /etc/udev/rules.d/70-persistent-net.rules and it didn't add the interface after shutdown.

I feel like I've tried every solution to similar-looking problems, but getting squat.

Can anyone please help?

---

### Post by yeeeev on 2010-05-06
Don't know if I can help, but I currently experience the same problem. Wired network is not recognized. I upgraded the kernel yesterday to 2.6.31-21 (I'm on 64 bit karmic ubuntu) so maybe it's related.

```

$ lspci
:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
$ lshw -short
/0/100/1e/0    eth0      network     BCM4401-B0 100Base-TX

```

What's your ethernet card model?

---

### Post by yeeeev on 2010-05-06
Got it working using info from this thread:
[http://ubuntuforums.org/showthread.php?t=1109585](http://ubuntuforums.org/showthread.php?t=1109585)

followed by a
```

sudo service network-manager restart

```

But my card was recognized, so I'm not sure your case is identical.

---

