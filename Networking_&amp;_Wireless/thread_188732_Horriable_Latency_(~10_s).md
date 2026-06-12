---
title: "Horriable Latency (~10 s)"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by schroder on 2006-06-04
After having installed a clean copy of Dapper Draker I realized that latency is horriable (~10 s) whenever connecting to the Internet (firefox, evolution, Synaptic).

I've tried all the suggested actions regarding disabling IPv6. However this haven't solved my problem. On the same machine I have Breezy Badger running with no problems (even with IPv6 enabled).

What can I do to debug this?

---

### Post by bigpook on 2006-06-04
[QUOTE=schroder]After having installed a clean copy of Dapper Draker I realized that latency is horriable (~10 s) whenever connecting to the Internet (firefox, evolution, Synaptic).

I've tried all the suggested actions regarding disabling IPv6. However this haven't solved my problem. On the same machine I have Breezy Badger running with no problems (even with IPv6 enabled).

What can I do to debug this?[/QUOTE]

Are there any other machines on your network? if so, are they having the same latency issues?

If so, then it may be your firewall/switch/internet....

Otherwise, check your patch cable and nic. Everything should be well seated in your computer.

I have dapper running on a spare box myself. While I have issues with network printing and autofs, latency is not a problem....

bp

forgot to mention. are you running a DHCP server or static IP. If static, you may want to check your address and subnet mask, verify the default gateway address is correct. also verify your DNS servers are correct.

---

### Post by schroder on 2006-06-04
Have a couple of other machines (Linux + WIn) on the same network. None of those have any problems.

My Breezy is sitting on another disk in the same machine as the troubled Dapper, which excludes HW problems.

Running static IP with the exact same setup as the Breezy machine (copied the files over to exclude typ-o's).

Any ideas?

---

### Post by jvl on 2006-06-21
are all your dns servers accessible? (I.e. isn't the primary timing out? )

check your /etc/resolv.conf settings.

---

