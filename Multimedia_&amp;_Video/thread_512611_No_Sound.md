---
title: "No Sound"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by raaj72 on 2007-07-29
Hi All,

I lost my sound in Fujitsu Laptop. I try install based on thread given below. Am getting  error. Can you advise. Pls check the attachments.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Thanks

---

### Post by moore.bryan on 2007-07-29
[I]the only way i was able to make it work was being specific about kernel location when compiling the most recent alsa-driver.  for example, when the guide tells you to > cd alsa-driver-1.0.14rc4
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
i had to specifically state my kernel this way:
```
cd alsa-driver-1.0.14rc4
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-2.6.20-16-server
sudo make --with-kernel=/usr/src/2.6.20-16-server
sudo make install --with-kernel=/usr/src/2.6.20-16-server
```
the apparent reason is the alsa install drivers are always looking for a /usr/src/linux directory and not necessarily the headers for the kernel you have.
you can try that and see how it works out for you...
[/I]

---

