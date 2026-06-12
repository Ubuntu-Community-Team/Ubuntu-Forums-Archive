---
title: "b43 terminal Help"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by den160593 on 2009-01-07
Hi,

I'm having trouble with my driver. I have found this site on how to make it work, however being a linux newbie I need a little help in making it work.

I am working from this:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Now that guide assumes you have some backup internet, but I sadly do not (driver works on Windows XP so I'm working off that now).

So i have downloaded these:
[http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

How would I install them? It says the following:

> Follow these instructions if you are using the b43 driver from linux-2.6.25 and newer or compat-wireless-2.6, or from any current GIT tree.

Use version 011 of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

```
Use version 4.150.10.5 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. 

That wget I'm guessing downloads it, so how would I make this work if I save the two things that need to be downloaded somewhere (and where should I save them too?).

If I'm being confusing I can clear this up, but I'm a newbie and I pretty confused myself, so I'll try :)

Oh, and also about my card. The card is a Belkin F5D7000au (which is supported (F5d7000), the au I'm guessing is because I bought the card in Australia) and the driver has the following files:

bcm43xx.cat, bcmwlf5.inf, bcmwl5.sys

If that helps :confused:

Thanks
-Den

---

### Post by Unparallelogram on 2009-01-08
Is there a particular reason why you're using b43 and fwcutter? If so, is there a particular reason why you're building it from source?

It would be a lot easier, and potentially a lot better, if you enabled the wl driver (called Broadcom STA under the System -> Administration -> Hardware Drivers dialogue), and if necessary blacklisted the b43 and ssb drivers in /etc/modprobe.d/blacklist file.

(copy pasting because I just finished giving someone else the same instructions, after following them myself around a week ago)

1. Update your system through wired internet.

2. Install wl from restricted driver dialogue. Go to System -> Hardware Drivers and activate Broadcom STA.

3. Go edit the modprobe blacklist (You may or may not need this step, but it won't hurt since you're using wl.)
> sudo gedit /etc/modprobe.d/blacklist
and add the lines to the end
> blacklist b43
blacklist ssb

Edit: 4. Reboot

---

### Post by den160593 on 2009-01-08
Hi, I can't even do the first step (enabled the wl driver (called Broadcom STA under the System -> Administration -> Hardware Drivers dialogue) because it's not there :(

I think this is the way for me to do, but I'm not sure :(

---

### Post by melojo on 2009-01-08
Have a look here, this should allow you to install from the cdrom if you have intrepid 8.10.

[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by den160593 on 2009-01-08
It works! Omg, 3 days of trawling through support and lauchpad bugs, with people just telling me to give up and then you fixed it. Thank you sooo much!

---

### Post by melojo on 2009-01-08
You fixed it, I just pointed you to Ayuthia tutorial.  Glad its working for you!!

---

