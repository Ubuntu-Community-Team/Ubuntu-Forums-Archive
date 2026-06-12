---
title: "Xubuntu 16.04.3 plays some DVD's but not all"
date: 2017-12-26
forum: Multimedia Software
---

### Post by mörgæs on 2017-12-26
The problematic DVD's are new and hence in fine physical condition but they are not even visible in Thunar. 

The DVD drive makes many attempts at reading the disc but to no avail. The command ```
lsdvd
``` can't verify that a disc is present. 

```
apt-cache policy libdvd-pkg
``` shows version 1.4.0-1-1. Libdvdnav4 and libdvdread4 are version 5.0.3-1.

Other DVD's play as expected and show ud correctly using ```
lsdvd
```

Has anybody seen a similar problem?

---

### Post by Autodave on 2017-12-26
I have run into a defective DVD ROM that will do that: play some but not others. Had 2 different machines brought to me like that. Found it by plugging in my external USB unit and they worked in there.

Just a thought.

---

### Post by User-007 on 2017-12-26
> **Autodave said:**
> I have run into a defective DVD ROM that will do that: play some but not others. Had 2 different machines brought to me like that. Found it by plugging in my external USB unit and they worked in there.

Just a thought.

I confirm this is really possible. I had this problem, too. But I fixed it, by instructions from [http://binflash.cdfreaks.com/](http://binflash.cdfreaks.com/) . So if you have a drive listed there, your problem may be fixable.

Although i think, it wont burn your house, do the firmware update at your own risk. I still think the worst which can happen is to destroy your dvd drive completely but maybe it is not the armageddon in case of already defetive device.

---

### Post by mörgæs on 2017-12-27
I didn't know that DVD drives had firmware embedded. 

The drive is not supported:

```
./necflash -scan -v
Binflash - NEC version - (C) by Liggy and Herrie

List of supported devices:
Trying to query device /dev/sg1
device TSSTcorp CDRWDVD TS-H493A D200 unsupported
No supported devices found
```

I'll search for similar software which supports the drive. Thanks for the idea.

---

### Post by User-007 on 2017-12-27
Based on very quick googling, seems that firmware updates are available, but are only installable on Windows. You dont have dual-boot?

---

### Post by mörgæs on 2017-12-27
Correct, no Windows here, but I can boot from Freedos and see if it works.

Do you have a link, please?

---

### Post by User-007 on 2017-12-27
I found firmware updates to run only on Windows, sorry. Maybe there still are some for Dos?

---

