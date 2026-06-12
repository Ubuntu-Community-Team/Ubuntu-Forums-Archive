---
title: "linux headache"
date: 2009-08-01
forum: Multimedia Software
---

### Post by whatever_omg on 2009-08-01
I have a creative zen v plus mp3 player. I've been trying to get it to work with gnomad 2 & amarok. and not having any luck. any sugestions?

---

### Post by ad_267 on 2009-08-01
Look likes it's an MTP device. I haven't had any problems with Banshee and Rhythmbox with a Samsung MTP player. Just check that the MTP plugin is enabled. I haven't tried using Amarok or Gnomad so can't really help there.

According to the libmtp website your device should work perfectly: [http://libmtp.sourceforge.net/compatibility.php](http://libmtp.sourceforge.net/compatibility.php)

---

### Post by whatever_omg on 2009-08-01
thankyou. I'll try those

---

### Post by ad_267 on 2009-08-01
The libmtp page doesn't indicate which version of the library supports that player, so if it's a relatively new device and you can't get it to work you could try downloading and compiling the most recent version of libmtp. Hopefully that won't be necessary though. Ubuntu 9.04 has version 0.3.0, the most recent is 0.3.6.

---

### Post by vinutux on 2009-08-01
Try banshee or exaile..```
sudo apt-get install banshee
```

---

