---
title: "iwlagn driver gets sluggish with time"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by bluesmanu on 2009-11-10
Hi all,

I am running karmic (kernel 2.6.31-14-generic-pae) on a dell e6400 that has an Intel 5100 wifi controller. The wifi card was well detected and worked out-of-the-box with the iwlagn. However I noticed that the wireless connection gets slower with time and eventually gets disconnected sometimes. All i need to do to make it work fast again is to rmod and modprobe again the iwlagn module. Unfortunately I was only able to test that on one wifi network but it seems i am the only one who has this issue on this network (doz and mac users are fine), so it's definitely an issue with my machine.

Thank you for your help,

ET

---

### Post by hal10000 on 2009-11-10
Look into your /var/log/messages file for messages related to iwlagn

---

### Post by bluesmanu on 2009-11-10
I get a lot of these :

Nov  9 16:41:54 gaugino kernel: [ 8906.418778] iwlagn 0000:0c:00.0: iwl_tx_agg_start on ra = 00:26:0b:29:c1:c0 tid = 0

I suppose that's a problem.

ET

---

### Post by hal10000 on 2009-11-10
I'm sorry but i don't know what this message means.

But i jus remember that some months ago i had also problems with my intel PRO/wireless 4965 wireless card (uses the same driver, (iwlagn) randomly disconnecting and the problem was solved by uninstaling at crappy **network-manager** package and installing **wicd** instead, which is much better.

Maybe this could jelp you too.

---

