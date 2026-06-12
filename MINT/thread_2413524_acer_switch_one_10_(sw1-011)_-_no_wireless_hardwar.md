---
title: "acer switch one 10 (sw1-011) - no wireless hardware detected"
date: 2019-02-26
forum: MINT
---

### Post by t1m3 on 2019-02-26
hello,

i have what is essentially a tablet, with built in wifi capability.
it came with windows, but it runs at a snails pace.
acer support said they would not help.
Installed linux successfully, but unfortunately, wifi is undetectable by Linux this far.
windows wifi driver already installed.

how do I detect and install wifi on this device?

---

### Post by jeremy31 on 2019-02-26
See the wireless script link in my signature and post results

---

### Post by t1m3 on 2019-02-26
[https://pastebin.com/7rWtzyZF](https://pastebin.com/7rWtzyZF)

note: I currently have a USB wireless adapter attached.

---

### Post by jeremy31 on 2019-02-26
Post results for ```
ls /sys/bus/sdio/devices/
```

---

### Post by t1m3 on 2019-02-26
entered: ls /sys/bus/sdio/devices/

result: mmc1:0001:1

---

### Post by jeremy31 on 2019-02-26
```
ls -R /sys/bus/sdio/devices/
```

---

### Post by t1m3 on 2019-02-27
entered: ls -R /sys/bus/sdio/devices/

result: 
/sys/bus/sdio/devices/:
mmc1:0001:1

---

### Post by howefield on 2019-02-27
Moved to the "*MINT*" forum.

---

### Post by t1m3 on 2019-02-27
I suspect that this Acer wifi hardware is not yet supported, by any Ubuntu flavour.  I've found:

brand: tp-link
model: 150mpbs high gain wireless USB adapter
year: 2017

works as a solution, until there is one.
note: Also had success with other older USB wifi adapters.

Can you confirm this is the case?

---

### Post by jeremy31 on 2019-02-27
```
cat /sys/bus/sdio/devices/mmc1:0001:1/data
```

USB wifi devices that are supported by the kernel will work

---

### Post by t1m3 on 2019-02-28
entered:  ls -R /sys/bus/sdio/devices/
returned: /sys/bus/sdio/devices/: mmc1:0001:1

entered: cat /sys/bus/sdio/devices/mmc1:0001:1/data
returned: cat: '/sys/bus/sdio/devices/mmc1:0001:1/data': No such file or directory
------

I'm trying to avoid a pile of USB devices beside my computer - or I might as well have got a bigger computer, right?  In time there has to be better 2-1 tablet PC support, because It's compact, faster, and (nearly) easier to do programming, and essay type work; with all the 2-1 benefits.

---

