---
title: "fglrx w/2.6.18 kernel?"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by dave_abrahams on 2006-09-25
Hi,

I'm running a 2.6.18 kernel (self-built, with suspend2, ipw3945, and a few other patches) and I've been unable to figure out how to get the latest ati proprietary driver to work with it.  It seems as though the kernel modules don't even get loaded at startup.  Can anyone provide pointers?

Thanks,
Dave

---

### Post by tworkemon on 2006-09-25
I had to backport module-assistant from edgy because there is a bug in the current version where it does not find 2.6.18 header files. Other then that I dont think I had any other problems.

---

### Post by dave_abrahams on 2006-09-25
Interesting...

The module assistant instructions shown at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver")
are 

```

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

```

To get module-assistant not to complain I changed the procedure as follows:



```

# sudo module-assistant prepare # no ubuntu package for 2.6.18
sudo module-assistant update
sudo module-assistant build -k *path-to-my-kernel-sources* fglrx
sudo module-assistant install -k *path-to-my-kernel-sources* fglrx
sudo depmod -a

```

and it finished without complaint.  But that doesn't mean it worked, and I was really guessing at the right thing to do.  In fact, I suspected I was doing something wrong; the only mention of fglrx in /lib/modules/2.6.18-xxx is in kernel/drivers/char/drm/fglrx.ko.

So, does it look to you like there's something wrong with my procedure?  And how can I get the sources to your backported module-assistant?

Thanks,
Dave

---

### Post by dave_abrahams on 2006-09-25
Oh, there was one other odd thing...

After ```
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb
``` I had to ```
tar  xjf /usr/src/fglrx.tar.bz2
chmod +x modules/fglrx/make.sh
sudo tar cjf /usr/src/fglrx.tar.bz2 modules
``` or I would get permission errors during the steps that followed.

---

### Post by dave_abrahams on 2006-09-25
False alarm.  I had a residual Device section in my xorg.conf that was still specifying the "vesa" driver.  Maybe the installation instructions from ATI should tell you to *rename* your xorg.conf before doing the ```
aticonfig --initial
```.  Anyway, thanks for responding.

---

### Post by tworkemon on 2006-09-25
This is probably not the best way to do it but this is what I did. Remember this is what I did you might have to modify this abit to get it working.

```
sudo mv /usr/bin/module-assistant /usr/bin/module-assistant-old
wget gttp://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.10.2.tar.gz
tar -zxvf module-assistant_0.10.2.tar.gz
cd module-assistant-0.10.2/
sudo cp module-assistant /usr/bin/module-assistant
```

I would then remove any packages you might have installed previously.

```
sudo dpkg -r fglrx-kernel-source
sudo dpkg -r fglrx-kernel-`uname -r`
sudo dpkg -r fglrx-control
sudo dpkg -r xorg-driver-fglrx
```

Then try to install the ati drivers again. Bellow is what I did. You should always make a backup of your xorg.conf file. I had some wierd problems where it would only work if I replaced my old working xorg.conf file.```
wget -c http://home.comcast.net/~ubuntu64user/linux-restricted-modules-common
#The above grabs a linux-restricted-modules-common file that already has fglrx entered.

sudo rm -f /etc/default/linux-restricted-modules-common
#This removes your current file. Dont do this if you already edited this file.

sudo cp -f ~/Desktop/APPS/ATI/linux-restricted-modules-common /etc/default/linux-restricted-modules-common
#Same with this.

wget -c https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.29.6.run
#This grabs the current drivers from the site.

chmod +x ati-driver-installer-8.29.6.run
#This makes it executable

sudo mv /bin/sh /bin/SH
sudo ln -s /bin/bash /bin/sh
# The above was a fix for some other problem I had. Not sure if you will need that or not. It wont hurt anything.

./ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
#This should create the packages for you.

sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb
#This should start installing them.

sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare     
sudo module-assistant update
sudo module-assistant  build fglrx
sudo module-assistant install fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

sudo mv /bin/SH /bin/sh
#This remove the link you made earlier.
#Reboot
```

---

### Post by zasf on 2006-09-25
why use module-assistant when you have make-kpkg?

[Here]("http://www.ubuntuforums.org/showthread.php?t=240892") is how I do it, with ATI driver 8.29.6 you don't need the patch I attached in the other post

---

### Post by tworkemon on 2006-09-25
Ive always done it that way. Its hard to teach old dogs new tricks ;)

---

