---
title: "Got wireless working but..."
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by malignor on 2008-12-24
Every time I restart my system I have to again run 

[INDENT]sudo modprobe ndiswrapper[/INDENT]

Where should I add "modprobe ndiswrapper" as a script?
Currently running 7.10 (Gibbon)

---

### Post by S_e_P_p on 2008-12-24
```
sudo gedit /etc/modules
```

add the word ndiswrapper to the end of this file.


Here are some more information:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de)

Greets,
SePp

---

### Post by iponeverything on 2008-12-24
a shorter version of the above.. this will just add it to the file without you having to edit anything

```
sudo echo ndiswrapper >> /etc/modules
```

---

