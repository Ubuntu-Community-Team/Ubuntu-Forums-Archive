---
title: "Intel wireless 5100agn"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by AmerNewbieInDE on 2009-08-09
ok, i got my wireless working, as with the instruction given in                           [Known Jaunty Wireless/Ethernet workarounds ]("http://ubuntuforums.org/showthread.php?t=1176117")

but, when i restart my pc, i have no wireess and must reinter 
sudo modprobe -r iwlagn
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

 where do i put this so it automatically starts

---

### Post by AmerNewbieInDE on 2009-08-09
can anyone help me here?

---

### Post by AmerNewbieInDE on 2009-08-09
anyone???

---

### Post by unhot on 2009-08-26
Have you seen this thread? It seems to be related. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378189](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378189)

Unfortunately, I am having an issue where if I use a bittorrent client or move a 'lot' (not by modern standards) of data around the network, I get a disconnect. Same card on a Sony Vaio AW. 

Try updating the firmware:
[http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads)

---

