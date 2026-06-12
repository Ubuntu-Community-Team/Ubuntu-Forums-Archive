---
title: "Host AP with D-Link DWL-650 rev. P2 Gives Procfs Error"
date: 2006-04-29
forum: Networking &amp; Wireless
---

### Post by distortedstar on 2006-04-29
I've been trying get my D-Link DWL-650 rev. P2 to work with HostAP for quite some time...I've it to work in other distributions before (Puppy Linux) but Ubuntu is giving me a bit of a problem. 

Compiling and installing HostAP and hostap-utils went without a hitch. When I tried to load the firmware with hostap_fw_load, however, I got the following output:
```

nathan@70-133-129-4:~$ sudo hostap_fw_load wlan0
Host AP driver data for device wlan0 not found in procfs.
```

Is this is a problem with pcmcia drivers? 

Also, I noticed that when I issued
```

modprobe hostap_pci
```

that interface wlan0 wasn't created.

same with 

```
modprobe hostap_cs
```

I would really appreciate any help.

---

### Post by distortedstar on 2006-05-02
anybody?

---

