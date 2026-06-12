---
title: "Realtek 8139D Install"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by hellmet on 2006-05-05
I have been trying and trying to 
install this stupid ethernet card since 3 days.
All in vain.
Please tell me guys if this card DOES work in Ubuntu.
Else I'm gonna throw this shit into the bin.

If it DOES work...PLEASE   PLEASE...
give me the installation instructions..
I shall be very very grateful to u guys.

Thanks in Advance..
-Sanjay

P.S::I have decided firmly not to get frustrated.
I shall setup Ubuntu Internet..somehow..and I need
ur help guys for that.

---

### Post by hellmet on 2006-05-05
One more thing.
when i did

**lspci | grep Eth**

i got a 
"No hardware Found ...."

I really can't give u the original lines..
as i type from Wndows...
and I don't remember the lines properly.

---

### Post by hellmet on 2006-05-06
Help Anyone??

---

### Post by hellmet on 2006-05-06
HERE ARE THE  lspci AND THE dmesg OUTPUTS

If u get anything out of it..please let me know.
Thanks

---

### Post by hellmet on 2006-05-06
this is wat i got ...when i loaded both the drivers..and did
lsmod | grep 8139

8139cp 18432 0
8139too 23552 0
mii 5248 2 8139cp,8139too


wat the heck does tat mean??

---

### Post by mips on 2006-05-07
What in your /etc/iftab file ?

---

### Post by hellmet on 2006-05-07
Nothing!! 

[B]
# This file assigns persistent names to network interfaces.  See iftab(5)[/B]

---

### Post by mips on 2006-05-07
Try adding a line with your cards MAC address:

eth0 mac [COLOR="Red"]00:0f:ea:74:27:e6[/COLOR] arp 1

MAC address is sometimes written on the card or can be optained from windows. I'm busy grasping at straws here.

---

