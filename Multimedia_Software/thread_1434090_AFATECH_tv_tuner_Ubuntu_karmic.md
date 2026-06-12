---
title: "AFATECH tv tuner Ubuntu karmic"
date: 2010-03-19
forum: Multimedia Software
---

### Post by chrisj26 on 2010-03-19
I've got an Afatech chipset based tv-tuner which worked previously well under 8.04, 8.10 and 9.04. My problem is now the TV viewing software don't detect any tuner. However lsmod lists the following which appear to show the modules are loaded.
```

dvb_usb_af9015         25308  0 
dvb_usb                16200  1 dvb_usb_af9015
dvb_core               87364  1 dvb_usb

```
However my /etc/dev/ shows no dvb path. Is this strange, or has someone experienced it and got around it?

---

