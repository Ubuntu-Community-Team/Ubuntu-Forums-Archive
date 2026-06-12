---
title: "mythtv locking up"
date: 2012-05-28
forum: Multimedia Software
---

### Post by someitalian123 on 2012-05-28
Mythtv keeps locking up on me while I'm watching tv on my wintv pvr 150 mce. I'm not sure why it does it, is it possibly because I'm setting the bitrate too high? All I know is that it keeps locking up and I am unable to kill it.

---

### Post by uRock on 2012-05-28
Moved to *Multimedia & Video*.

---

### Post by someitalian123 on 2012-05-28
Found this in my kern.log

```
May 28 20:56:26 upstairs kernel: [   31.543620] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
```

According to this page 

[http://www.mythtv.org/wiki/PCI_Latency#Hauppauge_PVR_Cards](http://www.mythtv.org/wiki/PCI_Latency#Hauppauge_PVR_Cards)

I can fix it with this command for my stat controller 

setpci -v -s xx:yy.z latency_timer=[n]

but that only works on pci buses and my sata controller is on a pcie bus, how can I increase the latency?

---

### Post by someitalian123 on 2012-05-29
I can post any logs or anything anybody wants, I just really need help here.

---

