---
title: "Scanner works, but isn't detected"
date: 2009-06-02
forum: Multimedia Software
---

### Post by ocwo92 on 2009-06-02
I've connected a HP LaserJet CM1312 scanner to my computer using the scanner's LAN port. After configuring the scanner with hp-setup and making a symbolic link from /usr/lib/libhpmud.so.0 to /usr/lib/libhpmud.so (the latter is a known bug), I can scan using:

```
xsane hpaio:/net/HP_Color_LaserJet_CM1312nfi_MFP?ip=192.168.1.150
```

Also,

```
scanimage -T -d hpaio:/net/HP_Color_LaserJet_CM1312nfi_MFP?ip=192.168.1.150
```

works as expected.

However, when I enter xsane by itself, or enter scanimage -L (that is, without the explicit device name), the scanner isn't detected.

I could enter the device name for those applications, of course, but some applications (e.g., gscan2pdf) don't seem to allow me to enter the device name. So, I'm thinking about sharing the scanner instead so that the clients don't need to know the device name.

I've configured saned.conf on the server to allow the client's IP, and net.conf on the client instructs the clients to connect to the server. This part appears to work: saned -d128 shows that access is granted to the scanner clients.

However, the clients don't detect the scanner. I'm assuming the reason is that the server doesn't detect the scanner with scanimage -L.

How can I force the scanner sharing server to share a specific scanner device, even if scanimage -L doesn't detect the scanner automatically?

---

### Post by xc3RnbFO8P on 2009-06-02
Read this:
[http://foxlx.acmesystems.it/?id=158]("http://foxlx.acmesystems.it/?id=158")

---

### Post by ocwo92 on 2009-06-02
> **Ringi said:**
> Read this:

Thanks, but that doesn't seem to be the issue here. I'm able to connect the scanner to the server as an USB device, and network shared scanning works fine as long as the scanner is connect to a USB port. (That is, after I had added "saned" to the "lp" group...)

The problem occurs when I connect the scanner to the LAN rather than using a USB connection.

---

### Post by ronacc on 2009-06-28
I have the same problem with my brother MFC7440n , it will print when connected with either usb or lan but will only scan through the usb connection, xsane dosen't find it when its connected by the lan port .

---

### Post by ronacc on 2009-07-01
Update , I had sent a query to brother tech support . they replied with a suggestion that worked for me ( see below ) , mabye something similar will work for other makes .
```
Would you please try to run the following command?
 
brsaneconfig3 -a name=scanner model=MFC-7440N ip=xx.xx.xx.xx
(Type your MFC's ip address for xx.xx.xx.xx part)
 
We have to tell brscan3 the network scanner's model and ip with that
command.
 
Please see the step 5 in the following website as a reference.
http://solutions.brother.com/linux/en_us/instruction_scn1b.html
 
```

---

