---
title: "Can't Mount Lumia 530 on Ubuntu 14.10"
date: 2015-01-31
forum: Multimedia Software
---

### Post by Alex Eagle on 2015-01-31
Simple as that. The title says it all. I get a warning about not being able to claim the device and error code (-53).

Any ideas what's wrong? Thanks :-)

---

### Post by ajgreeny on 2015-01-31
Is that running the MS phone OS or android?

I think the Lumia uses MS software, in which case I assume it is possible to connect as a mass-storage device, but I am not sure how you would do that.

Plug it in and straight away run **dmesg | tail** in terminal to see if the system has even seen it, and as what sort of device it detects it.

---

### Post by Alex Eagle on 2015-02-10
Windows Phone 8.1 (Denim).

```
:~$ dmesg | tail
[ 1242.584907] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1244.872603] wlan1: authenticate with c0:3f:0e:24:e7:58
[ 1244.900854] wlan1: send auth to c0:3f:0e:24:e7:58 (try 1/3)
[ 1244.921741] wlan1: authenticated
[ 1244.924084] wlan1: associate with c0:3f:0e:24:e7:58 (try 1/3)
[ 1244.926485] wlan1: RX AssocResp from c0:3f:0e:24:e7:58 (capab=0x411 status=0 aid=5)
[ 1244.934205] wlan1: associated
[ 1244.934265] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1664.669770] usb 1-4.2: USB disconnect, device number 14
[ 1693.724107] usb 1-4.2: new high-speed USB device number 17 using ehci-pci
```

---

### Post by Alex Eagle on 2015-04-10
I've now got Windows 10 Technical Preview on my desktop. That mounts it fine (obviously). It even has a dedicated "Windows Phone" app.

Thanks anyways ;-)

---

### Post by trufanovan on 2015-06-02
The author of this project: [Android File Transfer For Linux]("https://github.com/whoozle/android-file-transfer-linux") luckily for me agreed to add WP8 support and now this is the only solution that reliable works, afaik.   
Now it's able to connect my Lumia 1020 WP8.1 Denim and Kubuntu 15.04 via usb.   
Of course, device shall be unlocked with correct PIN beforehand.  
The project is a library and has simple GUI which is mostly for library demonstration and testing purposes, so don't blame it for UX.

---

