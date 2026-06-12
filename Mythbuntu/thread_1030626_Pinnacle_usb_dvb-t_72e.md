---
title: "Pinnacle usb dvb-t 72e"
date: 2009-01-04
forum: Mythbuntu
---

### Post by stuntmasterzs on 2009-01-04
Is there any way to use [this]("http://www.pinnaclesys.com/PublicSite/uk/Products/Consumer+Products/PCTV+Tuners/PCTV+Digital+PVR+(DVB-S_DVB-T)/PCTV+DVB-T+Stick+Documents/Technical+Specifications/Technical+Specifications+72e+solo+UK.htm") in mythbuntu?

---

### Post by ian dobson on 2009-01-04
Hi,

Have a look here :- [http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_72e](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_72e)

Regards
Ian Dobson

---

### Post by stuntmasterzs on 2009-01-04
Thanks for the response Ian,

Is there any instructions on how to do this anywhere?

Kind Regards

Dave Jenkins.

---

### Post by ian dobson on 2009-01-04
Hi,

You should be able to just plug the tuner in and it should just work.

Regards
Ian Dobson

---

### Post by stuntmasterzs on 2009-01-05
I wish it would but when i go to add new capture device all of the options say failed to open.

---

### Post by ian dobson on 2009-01-05
Hi,

What capture device type are you selecting? A tip it should be dvb.

Also check what rights do you have for your /dev/dvb device?
for me:-

```

ls /dev/dvb/adapter0 -o -a
total 0
drwxr-xr-x 2 root    140 2009-01-01 19:19 .
drwxr-xr-x 4 root     80 2009-01-01 19:19 ..
crw-rw---- 1 root 212, 4 2009-01-01 19:19 ca0
crw-rw---- 1 root 212, 0 2009-01-01 19:19 demux0
crw-rw---- 1 root 212, 1 2009-01-01 19:19 dvr0
crw-rw---- 1 root 212, 3 2009-01-01 19:19 frontend0
crw-rw---- 1 root 212, 2 2009-01-01 19:19 net0

```

Regards
Ian Dobson

---

### Post by WitchCraft on 2009-01-07
See this: [http://ubuntuforums.org/showthread.php?p=6503305](http://ubuntuforums.org/showthread.php?p=6503305)

---

### Post by jens-mct on 2009-07-12
in U9 it works plug and play in kaffeine
i'm from Flanders (Belgium), so it works good, so lang as i get good reception, if the reception goos bad, the OS crashes
very weird, but i've mounted my antenna in a good place, so no problems :)

---

