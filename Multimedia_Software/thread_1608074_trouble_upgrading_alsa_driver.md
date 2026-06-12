---
title: "trouble upgrading alsa driver"
date: 2010-10-28
forum: Multimedia Software
---

### Post by killermonkey on 2010-10-28
Hi everyone!

I just found out that my microphone doesn't work. I use Maverick and I read [this ]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")troublesh0oting guide, the fact is that it says that Ubuntu 10.10 comes with alsa drivers 1.0.23 by default and mine is 1.0.21. I read another post where they said upgrading this might work (in fact it did in 10.04).

 I tried to upgrade it by instaling alsa-driver-1.0.23 from the alsa website, but when I run ./configure it says "Please install the package with full kernel sources for your distribution" I have the Kernel Linux 2.6.32-25-generic installed on my computer. Does anyone know how to upgrade alsa-driver?

Thanks!

---

### Post by lidex on 2010-10-28
> **killermonkey said:**
> Hi everyone!

I just found out that my microphone doesn't work. I use Maverick and I read [this ]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")troublesh0oting guide, the fact is that it says that Ubuntu 10.10 comes with alsa drivers 1.0.23 by default and mine is 1.0.21. I read another post where they said upgrading this might work (in fact it did in 10.04).

 I tried to upgrade it by instaling alsa-driver-1.0.23 from the alsa website, but when I run ./configure it says "Please install the package with full kernel sources for your distribution" I have the Kernel Linux 2.6.32-25-generic installed on my computer. Does anyone know how to upgrade alsa-driver?

Thanks!

You're loading the wrong kernel. Try this:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now reboot. At the grub screen make sure the latest kernel is selected - should be 2.6.35*

---

### Post by killermonkey on 2010-10-28
Yes that worked perfectly! How do I know when its time to 
sudo update-grub
You guys at this forum are amazing!

---

### Post by lidex on 2010-10-28
> **killermonkey said:**
> Yes that worked perfectly! How do I know when its time to 
sudo update-grub
You guys at this forum are amazing!

Should be done automatically - I haven't had a problem for a long time. Just be aware of the kernel series for a given release.
```
karmic 2.6.31*
lucid  2.6.32*
maverick  2.6.35*
```
At some point you'll want to uninstall the outdated kernel and header packages.

---

### Post by angliski on 2010-10-30
I have a similar problem with the same kernel heading in grub. When I tried to run the above command in terminal all I got was. "the update command takes no arguments. Please help. I am desperate to talk to my girl friend in Sweden
Steve

---

### Post by lidex on 2010-10-30
> **angliski said:**
> I have a similar problem with the same kernel heading in grub. When I tried to run the above command in terminal all I got was. "the update command takes no arguments. Please help. I am desperate to talk to my girl friend in Sweden
Steve

OK, you lost me.
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
One line at a time. Nothing comes after 'update-grub'

---

### Post by Eddie-GNOME on 2011-03-07
> **killermonkey said:**
> Hi everyone!

I just found out that my microphone doesn't work. I use Maverick and I read [this ]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")troublesh0oting guide, the fact is that it says that Ubuntu 10.10 comes with alsa drivers 1.0.23 by default and mine is 1.0.21. I read another post where they said upgrading this might work (in fact it did in 10.04).

 I tried to upgrade it by instaling alsa-driver-1.0.23 from the alsa website, but when I run ./configure it says "Please install the package with full kernel sources for your distribution" I have the Kernel Linux 2.6.32-25-generic installed on my computer. Does anyone know how to upgrade alsa-driver?

Thanks!

ok...i got the same problem and ive solved it,,,,,

open your terminal and type

sudo aptitude install build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r`

(for the installation of alsa tools...drivers and other stuffs)

than download the latest alsa driver from here  [PHP]http://www.alsa-project.org/main/index.php/Main_Page[/PHP]download these things:
-

[LIST]
[*] [alsa-driver-1.0.24]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.24.tar.bz2")
[*] [alsa-lib-1.0.24.1]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.24.1.tar.bz2")
[*] [alsa-utils-1.0.24.2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.24.2.tar.bz2")
[/LIST]
they are on the right top of page,,,,

than place it on desktop..
when you do that open your terminal and type

sudo mkdir -p /usr/src/alsa 
cd /usr/src/alsa 
sudo cp ~/Desktop/alsa* .
sudo tar xjf alsa-driver*.bz2 
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2 

the next steps are compiling and installing ALSA driver.

type in terminal 

cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install

next steps are compiling and installing ALSA-lib

cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

then after that is compiling and installing ALSA-utils

sudo apt-get install libncurses5-dev
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

THATS IT,,,,IF YOU DIDNT HAVE ANY MISTAKES THAN JUST RESTART YOUR COMPUTER AND ENJOY IN YOUR SOUND!!! :D

---

### Post by James MG on 2012-11-02
<deleted>

---

