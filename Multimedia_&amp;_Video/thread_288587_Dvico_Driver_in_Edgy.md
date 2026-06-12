---
title: "Dvico Driver in Edgy"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by noisymime on 2006-10-30
I just upgraded from Dapper to Edgy on my mythtv box and have experienced a few problems.

One of the most annoying is that I can't get the Dvico Dual DVB tuner card driver to 'stick'. Due to having a new card I need to use the drivers from linuxtv which compile and work fine. I do the following:

```
make
sudo make install
sudo make reload
```

I then get 2 devices within /dev/dvb which work perfectly. When I reboot however the devices are gone. Going through dmesg shows that when rebooting Ubuntu is still loading the old driver version.

How do I install the new driver permanently? The above work perfectly in Dapper.

---

### Post by noisymime on 2006-10-30
Looks like I got it.

Needed to do:
```
make distclean
make
sudo make rminstall
sudo make install
sudo make reload
```

Strange that this wasn't needed in Dapper.

---

