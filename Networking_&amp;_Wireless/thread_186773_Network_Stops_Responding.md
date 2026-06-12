---
title: "Network Stops Responding"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by rustinh on 2006-06-02
I have a Dell Dimension 4400 with a CNET Pro200WL Ethernet Adapter and SMC 2602W wireless PCMCIA to PCI adapter card.  When running Ubuntu 6.06 from the Live CD I have no trouble at all connecting to the router/internet.  Once I install Ubuntu to my hard drive I can ping the router for about thirty seconds then I get the "Destination Host Unreachable" message.  It's like the connection is terminated and I cannot ping anything again until I restart Ubuntu.

I have tried disabling one card and using the other with the same results.  I have tried using static IPs and this doesn't work either.  I have reinstalled Ubuntu several times and I'm still having the same problem.

Does anyone have any suggestions for me at all?  Is this a problem with Ubuntu and I just need to wait for them to come out with a fix?

---

### Post by s31523 on 2006-06-02
You should search through bugzilla... This sounds similar:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/41634](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/41634)

---

### Post by TimJ on 2006-06-02
Try this one: [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by rustinh on 2006-06-02
This thread worked for me.  Problem now resolved.  Thanks for the help.


[QUOTE=TimJ]Try this one: [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)[/QUOTE]

---

### Post by bt224 on 2006-06-02
Did you have a Devicom adapter? Will this work for any adapter?

---

### Post by h3h_timo on 2006-06-02
bt224, i dunno, it could, worth a shot, just make sure you back up your config files before you change them! good luck

---

### Post by bt224 on 2006-06-02
It worked perfect!

---

