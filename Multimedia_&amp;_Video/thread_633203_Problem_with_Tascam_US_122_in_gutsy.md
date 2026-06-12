---
title: "Problem with Tascam US 122 in gutsy"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by [censored] on 2007-12-06
Hi. I'm trying to get a Tascam US122 usb soundcard up and running in ubuntustudio 7.10

Following this Howto:

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

The problem is when I get to this stage: 

>  sudo fxload -s /home/user/downloads/TascamPrep/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/003/004

I get the error:

```
/proc/bus/usb/004/003: No such file or directory 
```

 I never had this problem in Feisty. What's changed in gutsy, and how can I get around it?

---

### Post by [censored] on 2007-12-13
Solved.

Use /dev/bus/usb instead of /proc/bus/usb

---

### Post by scrondle on 2007-12-26
Did you get it working decently with Gutsy? I ended up downgrading to Feisty to get it to work, and I am not very happy with it. Please let me know,

Thanks,

Kjel

---

### Post by shawn_mcmurdo on 2008-01-03
I am also trying to get a Tascam US-122 working on Gutsy without much success.
After reading various howtos and postings I did the following.

Installed alsa-tools, alsa-utils, and fxload using the Synaptic Package Manager.

I downloaded alsa-firmware-1.0.15.tar.bz2 from ftp.alsa-project.org and extracted it.

I installed libc6-dev using the package manager.

Then I built and installed the alsa-firmware package by doing:
./configure
make
sudo make install

Then I created the file /etc/udev/rules.d/55-tascam.rules
with the following 2 lines:

BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/local/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/local/share/alsa/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

So now when I plug in the us-122 or boot up it is found but there are still problems.

lsusb shows it is on the usb bus and the product id has been changed to 8007 so I know at least the first stage fxload was successful.

lsusb shows:
Bus 001 Device 006: ID 1604:8007 Tascam US-122 Audio/Midi Interface

cat /proc/asound/cards shows:
 1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 001/006

I set the default sound card by doing:
asoundconf set-default-card USX2Y

amixer info shows:
Card default 'USX2Y'/'TASCAM US-X2Y (1604:8007 if 0 at 001/006)'
  Mixer name    : ''
  Components    : ''
  Controls      : 0
  Simple ctrls  : 0

aplay startup.wav gives the following error:
aplay: main:545: audio open error: No such file or directory

Anyone have any suggestions on how to proceed from here or what the problem might be?
Thanks!
Shawn

---

### Post by cingo on 2008-02-03
I have been trying and trying and trying (with a us-428). My last success is getting as far as this:
> sudo fxload -D /dev/bus/usb/001/006 -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us428fw.ih
/lib/firmware/usx2yloader/us428fw.ih: unable to open for input.
Any idea how to fix this?
Thanks.

---

### Post by shawn_mcmurdo on 2008-02-03
Did you make a typo and leave the x off of .ihx?

FYI, I was able to get the Tascam US-122 USB soundcard to work on Ununtu 7.10 Gutsy by downloading the version 1.0.15 sources for alsa-lib, alsa-tools, alsa-utils, and alsa-firmware from [ftp://ftp.alsa-project.org/pub/](ftp://ftp.alsa-project.org/pub/) and building them on my system.
I am still using the Ubuntu supplied 1.0.14 alsa-driver.

Shawn

---

### Post by cingo on 2008-02-03
Thanks for your answer Shawn :)
It was just a typo here, I eventually got the green light somehow. Not sure how to configure and use now, since I still cannot see the us-428 in alsa mixer.
I'll do a couple more searches in the forums and see if I find anything.
Cheers :)

---

### Post by LeavingEvil on 2008-02-13
Hi, I am working with the us428 as well. I am using Gutsy

root@power:/# fxload -s /usr/src/alsa/alsa-firmware-1.0.16/usx2yloader/tascam_loader.ihx -I /usr/src/alsa/alsa-firmware-1.0.16/usx2yloader/us428.ihx -D /dev/bus/usb/002/003 /usr/src/alsa/alsa-firmware-1.0.16/usx2yloader/us428.ihx: unable to open for input.

Any ideas?
Thanks in advance.

---

### Post by sodasound on 2008-02-15
As a Ubuntu newbie, watching you folks talk about this, and remembering similar problems with re-installs in Windows, I have come to the conclusion that we should all just send our Ta-Scam products back to Ta-Scam in various states of dismemberment. Musicians are not generally code-freaks by nature, and Ta-Scam should know this after thirty-odd years in the business. I don't understand why they're still kissing Microsoft's tush. Windows doesn't like them either. I'm not about to go back to Windows to rescue this piece of trash.:guitar:

---

