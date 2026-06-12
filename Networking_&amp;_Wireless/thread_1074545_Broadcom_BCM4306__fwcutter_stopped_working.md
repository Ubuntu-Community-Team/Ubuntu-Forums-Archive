---
title: "Broadcom BCM4306 / fwcutter stopped working"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by philosophia on 2009-02-19
Running Intrepid Ibex on a dell Latitude D600.  Wireless was working previously - my wireless card is a Broadcom BCM4306, I had to install install fwcutter to get it working.  Since my wired nic was also Broadcom and non functional on this machine, I had to burn b43-fwcutter_011-4ubuntu1_i386,deb to a cd along with the broadcom windows drivers and install from disk.  Anyway it worked, and wireless was working for a couple of months on this laptop.

Yesterday, the wireless connection on this machine just stopped working.  I'm not sure if this had to do with a system update I applied yesterday, but it stopped in the middle of a download.  I try to reconnect, but it asks me to reenter my wireless password, then attempts to connect for a long time but ultimately fails without any sort of error.

I tried reinstalling fwcutter, but that didn't seem to work.  Anyone know what's going on?

---

### Post by superprash2003 on 2009-02-19
ensure that you have chosen the right authentication type WEP 64bit or 128 bit etc.. try all combinations if you are unsure

---

### Post by philosophia on 2009-02-19
I'm sure I'm using the same authentication type and passphrase - these settings have not changed on my wireless router.  And I've tried reentering them.

---

### Post by philosophia on 2009-02-19
bump - anyone?

---

### Post by philosophia on 2009-02-19
The reason I think this is related to a recent system update is that the card was working fine previously.  

I've tried reinstalling the b43-fwcutter package but that doesn't solve the problem fyi.  When I enable the card under Hardware Drivers and try to reconnect to my wireless network, it just fails silently without any error.

---

### Post by cbch on 2009-02-19
Same problem here - any suggestions?

---

### Post by acimmarusti on 2009-02-19
Hi there,

Normally Ubuntu's b43-fwcutter version should work, but since you are saying that is broken I'm going to give you expanded instructions. I have a broadcom chip in my wireless and I made it work by doing this:

```

wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o

```

Now restart, connect and test it.

You can download the packages you need without wget by simply going to the urls.

It works fine on Ubuntu 8.10, Fedora 10 and OpenSuSe 11.1 for my broadcom 4318 which is supported by the same firmware I'm telling you to install.

Let me know if it works

---

### Post by philosophia on 2009-02-20
> **acimmarusti said:**
> Hi there,

Normally Ubuntu's b43-fwcutter version should work, but since you are saying that is broken I'm going to give you expanded instructions. I have a broadcom chip in my wireless and I made it work by doing this:

```

wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o

```

Now restart, connect and test it.

You can download the packages you need without wget by simply going to the urls.

It works fine on Ubuntu 8.10, Fedora 10 and OpenSuSe 11.1 for my broadcom 4318 which is supported by the same firmware I'm telling you to install.

Let me know if it works


I've already done this - but it just stopped working after upgrading to the 2.6.27-11 kernel.  What version of the kernel are you running?  I just looked up several posts on this forum that confirmed it's broken for the 2.6.27-11 kernel but works if you upgrade or downgrade your kernel.  I also went to the #bcm-users IRC channel, and they claim b43-fwcutter is broken for ubuntu.

---

### Post by acimmarusti on 2009-02-20
I was using 2.6.27-9 kernel with Ubuntu 8.10. But to tell you the truth, I'm now using only OpenSuSe 11.1 which uses Kernel 2.6.27.7-9-pae.

Mmm, you could try using an older firmware? have you tried that? (it's a temporary solution, of course) The easiest way is for you to go to this website: [http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/) and install the b43-firmware binary (I know, I know they are for hardy, but they worked flawlessly when I had Intrepid).

It's worth a shot. Hope it works for ya

---

### Post by philosophia on 2009-02-20
> **acimmarusti said:**
> I was using 2.6.27-9 kernel with Ubuntu 8.10. But to tell you the truth, I'm now using only OpenSuSe 11.1 which uses Kernel 2.6.27.7-9-pae.

Mmm, you could try using an older firmware? have you tried that? (it's a temporary solution, of course) The easiest way is for you to go to this website: [http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/) and install the b43-firmware binary (I know, I know they are for hardy, but they worked flawlessly when I had Intrepid).

It's worth a shot. Hope it works for ya

Some people have tried the older firmware in some of the threads I looked up, but were unsuccessful, so I haven't tried it.

---

### Post by cbch on 2009-03-01
After hours of trying I'm still unsucessful. Will do a clean install and see how long it works for then.

To be cleaar, what is it that has suddenly happend to stop wireless functioning? Hardware conflict? Incompatible software update? Noobism?!

Cheers for the suggestions anyway

---

### Post by acimmarusti on 2009-03-19
Hey,

I'm running Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

and I have no problem with my bcm4318 wireless card. However, I am using the older firmware version 4.80.53.0. I encourage you to try it. Or you could try using a simple package installation of the older firmware, go here:

[http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)

and get the b43-firmware_1.0-0cafuego0_all.deb package. It's meant for hardy, but it works well on intrepid. Try it, because the package installation I'm describing doesn't require you to download b43-fwcutter

---

