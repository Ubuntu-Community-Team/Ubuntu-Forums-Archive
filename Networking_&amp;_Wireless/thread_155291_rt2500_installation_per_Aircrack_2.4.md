---
title: "rt2500 installation per Aircrack 2.4"
date: 2006-04-04
forum: Networking &amp; Wireless
---

### Post by boltorg on 2006-04-04
Sorry for my uncomprehension to this new and exciting world (for myself that is), but I'm having an issue trying to get rt2500.ko to build.

I've followed these steps given by akseli:

[COLOR="Red"]STEP 1: Perform a complete reinstall of Ubuntu without the rt2500 card inserted at any moment
STEP 2: Boot up into Ubuntu without your card inserted
STEP 3: Delete the pre-installed drivers for the rt2500 chipset:
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2500/
STEP 4: Download the current CVS-daily for the rt2500 drivers from [http://rtx00.serialmonkey.com](http://rtx00.serialmonkey.com)
STEP 5: Untar the downloaded file:
tar -xzf rt2500-cvs-daily.tar.gz
STEP 6: Build the driver module:
cd rt2500-cvs-*/Module
make
STEP 7: Copy the newly built module into your drivers folder:
sudo cp rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2500.ko
STEP 8: Now we make sure that everything is as it should be:
sudo ifdown ra0
If the output of this is "ra0 is not configured" or something of the sorts you are on your way to getting this working!
STEP 9: Actually configure the driver:
echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500
sudo depmod

Now you have the correct drivers installed allowing you to use aireplay correctly, but to get everything to work you still need to complete phase two:

STEP 1: sudo modprobe rt2500
STEP 2: sudo iwconfig ra0 mode monitor
STEP 3: sudo iwpriv ra0 rfmontx 1
STEP 4: sudo iwconfig ra0 channel x
STEP 5: sudo ifconfig ra0 up

Now everything is setup and ready for using aircrack.
This is the easy part :)

STEP 1: download aircrack-2.4.tgz
STEP 2: untar
tar -xzf aircrack-2.4.tgz
STEP 3: build the programs
cd aircrack-2.4
make
STEP 4: install everything so you can run directly from a bash prompt
sudo make install"[/COLOR]

I get to step 6 and it fails giving me this error:

make
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
rt2500.ko failed to build!
make: *** [module] Error 1

Thanks in advance.

---

### Post by ranf on 2006-04-06
You will need to install `linux-headers-*' where * matches your kernel version.
This tells you what it is:
```
uname -r
```

Next you need gcc-3.4 installed.

Before typing make do this:
```
export CC=/usr/bin/gcc-3.4
```

Then it _should_ work. (I can't say for sure because I don't have this card.)

---

### Post by boltorg on 2006-04-11
thanks for at least replying =).

I will give this a go and reply my findings.

---

