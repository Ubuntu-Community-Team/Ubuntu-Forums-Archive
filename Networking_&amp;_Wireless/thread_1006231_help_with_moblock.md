---
title: "help with moblock"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by dbzkid on 2008-12-09
Ive installed moblock and i whitelisted my lan, but here is tyhe deal im useing cablevision as my isp and moblock keeps blocking that ip and also blocks microsoft (for msn in pidgin) and i was wondering if it was ok to whitelist the ip for my isp and the msn ip? because if i leave it it wont let me go on the internet but if i whitelist it it will let me go on the internet like websurfing ect. thanks

---

### Post by jre on 2008-12-09
No need to doublepost: [http://ubuntuforums.org/showpost.php?p=6335835&postcount=154](http://ubuntuforums.org/showpost.php?p=6335835&postcount=154)
lovinglinux's answer given in the other thread is correct of course. Just whitelist them.

Your ISP knows everything about you, if you block him or not ...

For MSN you can either whitelist the microsoft IP or the MSN port.
Or if you are paranoid the combination of both (via /etc/moblock/iptables-custom-insert.sh, there's an example given in the file).

---

### Post by dbzkid on 2008-12-09
thank you very much :p

---

