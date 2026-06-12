---
title: "Need help creating home network ubuntu xp with ics"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by aviramof on 2010-03-09
i have two computer one has windows seven and ubuntu and another computer with xp 
the connection between the two is crossed(reversed)RG45 cable between seven and xp 
everything is fine the seven is 192.168.137.2 xp 192.168.13.1 the work group is home my
problem is with ubuntu i don't know how to set workgroup home here i can't connect via rdp 
can't get ping nothing what can i do to fix the problem?

and one more thing i have gnome-user-share installed but it said the feature cannot be enabled because the required pacages are not 
installed why is that and what are the requierd pacages because i think it was installed with ubuntu(lucid)so how it possible that it have 
a dependecies problem?

thanks in advance.

---

### Post by aviramof on 2010-03-09
no one knows?

---

### Post by Iowan on 2010-03-09
> **aviramof said:**
> ...the seven is 192.168.137.2 xp 192.168.13.1 Typo? Those aren't in the same subnet... unless it's a big subnet (which you didn't mention). Workgroup shouldn't affect **ping** - firewall(s) might, though...

---

### Post by aviramof on 2010-03-10
seven 192.168.137.1 xp 192.168.137.2 and i don't have any firewall not in xp not anything but still no ping no rdp or vnc or anything eles when i seven and xp everything is working fine.

---

### Post by Iowan on 2010-03-10
Did you say this is a Lucid machine? 
Check (from a terminal) **ifconfig -a** to verify the machines's address.
Static IP configured from Network Manager or */etc/network/interfaces*?

---

### Post by aviramof on 2010-03-11
i have two networks cards and network manager don't work so well when i try to configure something there i did managed i think to set static ip from a command i'v found but i would try to check *etc/network/interfaces once i install ubuntu again today beta1freeze version once it's releasd.*

---

### Post by aviramof on 2010-03-12
Finally managed to do it and incerdibly it was much simpler then i thought all i had to do is to add wire connection 1 with the ip 192.168.137.1 and dns server and workgroup that create the network and the work group and then i enable internet sharing using firestarter and that it.

thanks for all the help.

---

