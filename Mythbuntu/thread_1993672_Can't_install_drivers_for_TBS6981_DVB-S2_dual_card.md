---
title: "Can't install drivers for TBS6981 DVB-S2 dual card"
date: 2012-06-02
forum: Mythbuntu
---

### Post by roundhay on 2012-06-02
I recently took the plunge and decided to buy a TBS6981 card to upgrade my HTPC however I cannot get the card to work.

I have tried to follow the step-by-step guide that is on various web pages:

[http://blog.mohammadzadeh.info/index.php/step-by-step-guide-to]("http://blog.mohammadzadeh.info/index.php/step-by-step-guide-to")

and I have followed the instructions in the TBS6981 README file but so far I have not managed get the card working.

I am not an expert but I'm competent enough to work through these types of things. 

I'm not even sure what the problem is?

I have done a clean install of mythbuntu 12.04 64 bit

I have attached a zip file with the output of dmesg, lspci, uname -r & the make make install when I tried to build the driver. I have also attached the installation instructions from the README file

I don't see any errors during the make and make install but there are warnings and certain drivers cannot be found?

Any assistance would be greatly appreciated

---

### Post by Kr0nZ on 2012-06-02
Is there anything in your 'dmesg' log about the card?

---

### Post by roundhay on 2012-06-02
I'm not exactly sure which parts if the log may refer to the card. The only bit I'm certain does refer to the card is

> [   16.386986] cx23885 driver version 0.0.3 loaded
[   16.387219] cx23885 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.387224] cx23885[0]: Your board isn't known (yet) to the driver.
[   16.387226] cx23885[0]: Try to pick one of the existing card configs via
[   16.387227] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   16.387228] cx23885[0]: version might help as well.
[   16.387230] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   16.387232] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   16.387234] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   16.387236] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   16.387238] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   16.387240] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   16.387242] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   16.387244] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   16.387246] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[   16.387248] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[   16.387250] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[   16.387252] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[   16.387254] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[   16.387256] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[   16.387258] cx23885[0]:    card=13 -> Compro VideoMate E650F
[   16.387260] cx23885[0]:    card=14 -> TurboSight TBS 6920
[   16.387262] cx23885[0]:    card=15 -> TeVii S470
[   16.387264] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[   16.387266] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[   16.387268] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[   16.387270] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[   16.387272] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[   16.387274] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[   16.387276] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[   16.387278] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[   16.387280] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[   16.387282] cx23885[0]:    card=25 -> Compro VideoMate E800
[   16.387284] cx23885[0]:    card=26 -> Hauppauge WinTV-HVR1290
[   16.387286] cx23885[0]:    card=27 -> Mygica X8558 PRO DMB-TH
[   16.387288] cx23885[0]:    card=28 -> LEADTEK WinFast PxTV1200
[   16.387290] cx23885[0]:    card=29 -> GoTView X5 3D Hybrid
[   16.387292] cx23885[0]:    card=30 -> NetUP Dual DVB-T/C-CI RF
[   16.387294] cx23885[0]:    card=31 -> Leadtek Winfast PxDVR3200 H XC4000
[   16.387296] cx23885[0]:    card=32 -> MPX-885
[   16.387648] CORE cx23885[0]: subsystem: 6981:8888, board: UNKNOWN/GENERIC [card=0,autodetected]
[   16.514501] cx23885_dev_checkrevision() Hardware revision = 0xa5
[   16.514509] cx23885[0]/0: found at 0000:01:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xe1000000
[   16.514518] cx23885 0000:01:00.0: setting latency timer to 64

---

### Post by Kr0nZ on 2012-06-02
Im not 100% sure but I think you need to select your card from that list.

Looking at the list '14' seems to be the closest match, but no exact match.

Try doing it using:
```
sudo rmmod cx23885
```
```
sudo modprobe cx23885 card=14
```

I havnt seen this mentioned yet by other people setting up this card, so not sure if its the right solution.
Is this the most up to date driver for this card?

*EDIT*
Make sure the firmware is loading
```
dmesg | grep firmware
```

---

### Post by anonymousdog on 2012-06-02
There is also **specific mention** in that thread that the procedure didn't work on 11.04; so, I don't really expect that driver to compile and work correctly on even newer kernels.

There is **also** a **specific link** to another writeup on getting the 6980 driver to compile in 11.04.  **Look at the commentary** after the writeup for the 6980 driver, [http://blog.mohammadzadeh.info/index.php/howto-install-the-tbs-6980](http://blog.mohammadzadeh.info/index.php/howto-install-the-tbs-6980).

---

### Post by nickrout on 2012-06-03
I'd have to say "buy a card that is supported in the kernel next time"

I can't see anything in dmesg about loading firmware into the card, this is likely the problem.

Did you install using the generic README or the the Ubuntu README?

Lastly which driver zip file did you actually download?

---

### Post by roundhay on 2012-06-03
I'm not sure what the problem was but I did a clean install of mythbuntu 12.04 64 bit (default recommended distribution) and managed to get the card working.

I based my work on the following threads:

[http://knap-home.no-ip.org/forum/viewthread.php?thread_id=57&pid=189#post_189]("http://knap-home.no-ip.org/forum/viewthread.php?thread_id=57&pid=189#post_189")

[http://www.tbsdtv.com/forum/viewtopic.php?f=22&t=7706]("http://www.tbsdtv.com/forum/viewtopic.php?f=22&t=7706")

[http://www.tbsdtv.com/forum/viewtopic.php?f=22&t=1632&sid=cbd64370b4e5d0614d0eb831e12b0e20]("http://www.tbsdtv.com/forum/viewtopic.php?f=22&t=1632&sid=cbd64370b4e5d0614d0eb831e12b0e20")

This is a step by step of what I did, some of the steps maybe unnecessary but this is what I did and it worked.

```
$ sudo aptitude install linux-headers-`uname -r` build-essential cvs libncurses5-dev gcc rar tar gzip
```

```
$ sudo mkdir /tbs6981
```

If you have not already done so now download the Linux driver file form the TBS web site:

[http://www.tbsdtv.com/download/]("http://www.tbsdtv.com/download/")

When I did this the driver version was TBS6981 Linux Driver v120521

Now go to the download folder in your home directory and unzip the folder.

Now move the following files/folders to /tbs6981

linux-tbs-drivers.tar.bz2
szap-s2.tar.bz2
scan-s2.tar.bz2
astra_szap-s2.conf
astra_scan-s2.conf
v4l-cx23885-avcore-01.fw

I used the Thunar file manager as the root user to move the files. To open Thunar as root do the following:

```
$sudo thunar
```

Once you have moved the files close Thunar

Now move to /tbs6981

```
cd /tbs6981
```

From this point forward I carried out all commands and root:
```
$ sudo su
```

Now extract the driver folder linux-tbs-drivers
```
# tar xjvf linux-tbs-drivers.tar.bz2
```

Some posts mention issues with file permissions, I don't really understand this but decided to include the following to commands which I found in one of the treads at the start of this post

```
# find linux-tbs-drivers -type d -exec chmod u+wx '{}' \;
```

```
# find linux-tbs-drivers -name "*.sh" -o -name "*.pl" -exec chmod u+x '{}' \;
```

Now move to the driver folder
```
cd linux-tbs-drivers
```

```
# ./v4l/tbs-x86_64.sh
```
This configures v4l for 64bit installations, if you are not using a 64bit installation then you will have to run one of the following:

[HTML]- for x86 kernel 3.x (x86 32 bit installations of kernel 3.x):

# ./v4l/tbs-x86_r3.sh

- for x86 kernel 2.6.x (x86 32 bit installations of kernel 2.6.x):

# ./v4l/tbs-x86.sh[/HTML]

```
# make
```
Now take a break as it can take a while for this to finish

```
# make install
```
This is the final step, next reboot and hopefully the DVB adapters will load.....

```
# shutdown -r now
```

Once rebooted open the terminal and type:

```
# dmesg | grep frontend
```

if everything is OK, the output from the above command lists the registered
frontends for your card model and their number is equal to the number of 
tuners on the card, for example:

DVB: registering adapter 0 frontend 0 (TurboSight TBS 6981 DVBS/S2 frontend)...
DVB: registering adapter 1 frontend 0 (TurboSight TBS 6981 DVBS/S2 frontend)...

This card is working now and I have managed to scan channels into mythtv

---

### Post by gammelobst on 2012-07-24
hi,

thanks [roundhay]("http://ubuntuforums.org/member.php?u=318562"). this is the correct way to get it working under yavdr 0.5alpha1 (Ubuntu 12.04LTS).

I made a script out of it and here it is:

```

#!/bin/sh

cd ~
wget http://www.tbsdtv.com/download/document/common/tbs-linux-drivers_v120709.zip
apt-get install -y gcc rar tar gzip
aptitude install -y linux-headers-`uname -r` build-essential cvs libncurses5-dev gcc rar tar gzip unzip
cd /usr/local/src/
rm tbs* -r
mkdir tbs6981
cd tbs6981
unzip ~/tbs-linux-drivers_v120709.zip
tar xjvf linux-tbs-drivers.tar.bz2
find linux-tbs-drivers -type d -exec chmod u+wx '{}' \;
find linux-tbs-drivers -name "*.sh" -o -name "*.pl" -exec chmod u+x '{}' \
cd linux-tbs-drivers
./v4l/tbs-x86_64.sh
make
make install
cd ..
cp v4l-cx23885-avcore-01.fw /lib/firmware/
echo ""
echo "please reboot..."
echo ""


```i hope this will help

cya

gammelobst

---

### Post by miyop on 2012-12-18
I installed the driver with these commands. But my job is to open this card with vlc in command line. Can anyone help me with this?

---

### Post by brettser on 2013-01-02
thanks roundhay, have been trying for months to try and get various DVB-T and DVB-S cards working on Ubuntu, your guide worked like a charm.

---

### Post by ralf_b2 on 2013-08-12
hello,

i try to install the latest TBS driver, but it dont work

download ok
make driver (seems) ok
install ok

but i have an error message here:

> ralf@ubuntu:~$ dmesg | grep frontend
[   11.846350] videobuf_dvb: disagrees about version of symbol dvb_frontend_deta
ch
[   11.846352] videobuf_dvb: Unknown symbol dvb_frontend_detach (err -22)
[   11.846370] videobuf_dvb: disagrees about version of symbol dvb_unregister_fr
ontend
[   11.846372] videobuf_dvb: Unknown symbol dvb_unregister_frontend (err -22)
[   11.846380] videobuf_dvb: disagrees about version of symbol dvb_register_fron
tend
[   11.846382] videobuf_dvb: Unknown symbol dvb_register_frontend (err -22)

---

### Post by oleg-radkov on 2013-10-03
Just in case if someone cares: [https://github.com/ljalves/linux_media/wiki/Installating,-Upgrading-and-Tvheadend](https://github.com/ljalves/linux_media/wiki/Installating,-Upgrading-and-Tvheadend)
read more here: [http://tvheadend.wordpress.com/2013/07/11/tbs-6981-debacle/](http://tvheadend.wordpress.com/2013/07/11/tbs-6981-debacle/)

---

### Post by pauldmallett on 2014-05-24
The instructions here are so close to what I have been doing that I can not tell what is different but your instructions have worked for me; after a day or so of trying. I'll just go back and reverse all the file permissions I have changed to try and get these drivers to load. Thank you.

---

