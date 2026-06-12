---
title: "Bad Password! Bad Password! Bad Password!"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by Krovas on 2010-06-02
Okay, even after getting my wifi nub to function correctly a couple weeks ago (with help; thank you again **chili555**), I am still completely unable to log into my home wlan.

1. I tried updating the kernel to 2.6.33.02063303, because I read this problem might be kernel related. No joy.

2. I tried dumping network-manager and installing wicd in it's place, because I read it might be an NM issue. I like wicd better, but it hasn't helped. Wicd exhibits precisely the same behavior as NM did: my ISP-assigned key evokes "Bad Password" no matter what login variation I attempt.

So here I am at square one, again. I don't what direction to head. Any assistance would be greatly appreciated. Thank you.

---

### Post by SaintDanBert on 2010-06-14
I have this exact issue with Ubuntu Lucid and my ThinkPad laptop.
The dual-boot, win-dose half does perfectly well ... for win-dose.
However, wicd sees the access points whirls and dies saying "Bad Password" time and again.  Using the debug-mode of wicd, I see that it is using the correct passphrase string.

Does this suggest a problem with the wpa_supplicant software or its configuration?

My wireless-router-gateway is a DLink DIR-655 running WPA-personal encryption. All of my win-dose hosts use this AP without much trouble.
Even the failing linux box works under win-dose boot.

[highlight]Someone[/highlight] please tell us how to diagnose whatever is happening here.

~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-06-14
see [http://ubuntuforums.org/showthread.php?t=1509759](http://ubuntuforums.org/showthread.php?t=1509759)

~~~ 0;-Dan

---

### Post by ryokea on 2010-06-16
Some digging through my system after a re-install today showed me that the WICD install process no longer completely removes Network-Manager anymore. Purged all instances of NM and stopped the network-manager script then it worked like a charm. Confirmed that it still works after a reboot.

---

### Post by SaintDanBert on 2010-06-17
> **ryokea said:**
> 
Some digging through my system after a re-install today showed me that the WICD install process no longer completely removes Network-Manager anymore. Purged all instances of NM and stopped the network-manager script then it worked like a charm. Confirmed that it still works after a reboot.

Did you notice what was left behind?  Might be useful for the wicd package bug report.

How did you purge?  Was Synaptic "completely remove" required or was
"remove" good enough?  Did you do other things?

If you "remove" or "completely remove" network-manager, does it step on any parts of wicd?

Does the fool proof work-around become:
1. plug in a wire eth
2. "completely remove" network-manager
3. install wicd
4. run and configure wicd
5. unplug the wire eth

---

