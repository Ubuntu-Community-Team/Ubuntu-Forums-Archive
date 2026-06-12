---
title: "Firewall settings for Firefly Media Server (mt-daapd)"
date: 2009-02-25
forum: Multimedia Software
---

### Post by LakesideLoafer on 2009-02-25
I want to be able to stream my music collection to my Pinnacle Soundbridge M1001 (Roku Soundbridge outside the UK). I have the Firefly music server installed and running OK. I use Guarddog as my firewall. If I disable the firewall the music server works fine. However, if I turn it on, there is no connection.

I have tried allowing all of the various preset protocols in Guarddog to no effect. I presume I need to set up a new protocol to allow access, but I have no what the settings are. 

Anyone any ideas?

---

### Post by LakesideLoafer on 2009-03-01
Bump! Anyone?

---

### Post by slockton on 2009-04-10
Have the same issue. ufw firewall is off - works fine. But when enabled, and 3689 and 5353 open, no luck.

Which ports are supposed to be open for mt-daapd?

---

### Post by Zillion on 2009-04-13
Same here... plz someone guide me how to get Firefly working with firewall

---

### Post by Zillion on 2009-04-14
OK found here [http://www.openfsg.com/forum/viewtopic.php?f=18&t=3147](http://www.openfsg.com/forum/viewtopic.php?f=18&t=3147) some answers.

But I found out that my Mabook only sees in Itunes the Firefly server if its connected wired. That is because in my router multicast needs to be set on as stated here [http://wiki.fireflymediaserver.org/Troubleshooting](http://wiki.fireflymediaserver.org/Troubleshooting), which is not possible on my dutch Tele2 modem router it seems :(

---

### Post by shantzg001 on 2009-07-06
Hi

I made some fixes to the latest trunk version of FireFly and compiled it. This version fixes many of the crashes and security issues and also adds some missing database functionalities. Would you like to try it out? I've posted up the binaries as well as instructions on how to compile it (along with my modified sources) at:
[http://tech.shantanugoel.com/2009/07/03/compiling-latest-firefly-mt-daapd-asus-wl-500w.html](http://tech.shantanugoel.com/2009/07/03/compiling-latest-firefly-mt-daapd-asus-wl-500w.html)
Please let me know if you have any comments/queries. I hope we can keep this great little media server going :)

---

