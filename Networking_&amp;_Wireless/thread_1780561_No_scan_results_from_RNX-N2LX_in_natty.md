---
title: "No scan results from RNX-N2LX in natty"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by pyrate on 2011-06-12
I just bought a RNX-N2LX under the supposition that it work out of the box in natty.

Another thread on here ([http://ubuntuforums.org/showpost.php?p=10812701&postcount=6](http://ubuntuforums.org/showpost.php?p=10812701&postcount=6)) suggested this as well. 

When I insert the device it loads the r8712u module and the device turns on, but I don't see any networks in range.

I really need help with this. I've had problems with realtek cards in the past, I'm currently using one right now, but I'm on shifting sand constantly having to recompile the buggy driver from their site, every time a kernel update comes out.

Any ideas? I'd love some suggestions on where to go forward with this device.

---

### Post by Janiporo on 2012-02-09
Can't really help, similar problem.

I have Ubuntu 11.10 + Realtek RTL8191SU-chip based wlan-stick, which uses same module (r8712u)

I think I have the same issue. But I think it is a range problem. Mine works top speed at 1 meter distance, over that speed drops dramatically. Try yours, move it closer, and youll see. And even then the speed does not always be the same.

No f**ing idea WHY it does this.

Many people have the same problem, and need help. Some have help with "iwlagn 11n_disable=1" command, some with "ath9k nohwcrypt=1" and some with disabling ipv6 (all instructions here --> [http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/) )

Only when link (signal) quality is 100/100 I get full speed.

I definetly know that with my unit, it is motherboard hardware issue, two machines have the same issue. My mothers laptop (new acer) however does not have this issue. plug in, set password and go --> full speed.

I think this module is buggy. Same problem with 12.04 alpha (live).

---

### Post by Janiporo on 2012-02-11
Actually seems to be hardware conflict of some kind. (on MY computer, don't know about yours)

Tested on windows xp (on Asus A8V-VM motherboard / newest drivers) and same problem, so not really a driver issue, but a hardware conflict (with some old computers).

---

