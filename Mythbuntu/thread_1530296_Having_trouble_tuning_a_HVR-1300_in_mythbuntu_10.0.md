---
title: "Having trouble tuning a HVR-1300 in mythbuntu 10.04"
date: 2010-07-13
forum: Mythbuntu
---

### Post by davidsig on 2010-07-13
Hello.
I am kinda new to mythbuntu (been using it for about a year). had ubuntu 9.04 setup that worked pretty well.

But I wanted tu upgrade to 10.04 so i installed a fresh mythbuntu 10.04 and I can't get signal lock on any antena.

As I said I have Hauppauge HVR-1300. tried to install the v4l-dvb driver wich did not help.
Googled around and tried a bunch of things that did not work.

Installed a fresh copy of mythbuntu 10.04 (again) and decided to ask for help soving my issue(s).

Can someone help me toubleshoot this ?

Regard.
Davíð

---

### Post by davidsig on 2010-07-13
BTW. running this command does work and it finds 86 services so the driver seems to be working but I don't get channel lock in mythtv.

$ scan /usr/share/dvb/dvb-t/is-Reykjavik

Anyone ?

Regards.
Davíð

---

### Post by LowSky on 2010-07-13
try this

1.Open a terminal and type: ```
sudo apt-get install build-essential mercurial linux-headers-generic libncurses5-dev
```
2. ```
hg clone http://hg.kewl.org/pub/v4l-dvb-20100517/
```
3. ```
cd v4l-dvb-fixes
```
4. ```
make menuconfig

# -> Multimedia Support -> DVB/ATSC adapters -> disable FireDTV and FloppyDTV
```
5. ```
make
```
6. ```
sudo make install
```
7. ```
sudo reboot
```

---

### Post by davidsig on 2010-07-13
Thanks for the reply but i get an error:

root@HTPC:~# hg clone [http://hg.kewl.org/v4l-dvb-fixes/](http://hg.kewl.org/v4l-dvb-fixes/)
abort: HTTP Error 404: Not Found

Found the working url is: [http://hg.kewl.org/pub/v4l-dvb-20100517/](http://hg.kewl.org/pub/v4l-dvb-20100517/)

And this seems to be working now, Thanks for your help.

Regards.
Davíð

---

### Post by LowSky on 2010-07-13
your welcome

---

