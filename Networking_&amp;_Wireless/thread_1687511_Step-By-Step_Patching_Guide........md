---
title: "Step-By-Step Patching Guide......."
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by Muzafsh on 2011-02-14
Hi,

Its a fact that Ubuntu is becoming one of the most user friendly linux distros,
primarily for its ability to work out of the box without much to do.

I am one such user (of the 'noob' category), who has no intention of becoming an
expert at linux OS. I want to remain a plane **'Ubuntu USER'** 
I believe that is the
case with quite a lot of Ubuntu users. And that is going to be the case in future, as
it grows in its No. of Users.

Being from this category of **just a 'Ubuntu User'**.

We noobs have our own problems because of our inability to turn pros, cos we are
often from non-tech backgrounds...We know Ubuntu OS is a self-service OS.
In spite of that we don't mind treading its path.
We also know that we need to be ready to dig in for solutions all by ourselves.
One frequent dead end that we often encounter because of our very nature,
Is when we have to apply a certain patch to fix a certain problem.

I would like to start this thread exclusively for us Noobs.

I hope o see this thread develop into a one point stop which provides
a Step-By-Step Patching Guide.......

Eg:

Step : 1 ...
Step : 2 ...
Step : 3 ...
;
;
Step : last ...

(with "command lines" included within the listed steps.)

I hope and request the experts of this community to [B]help us noobs with detailed
steps which should not be more than 'simple copy paste operations' to
have a fix patch applied.[/B]

One good example on how these guides need to be, would be a patch applying procedure
i came across, posted by viktors petrovs...here...
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/comments/14](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/comments/14)

----------------
Sometimes i need to compile just one kernel module for current kernel without compiling full kernel tree.
This is how i get it done:

1) get attached patch
2) install and extract kernel source

sudo apt-get install linux-source
tar xjf /usr/src/linux-source-2.6.32.tar.bz2

3) patching and compilation (only drivers/usb/serial subdirectory)

mkdir temp

cd ./linux-source-2.6.32
patch -p1 < ../usb-wwan-2.6.32.diff

cp /lib/modules/`uname -r`/build/.config ../temp
cp /lib/modules/`uname -r`/build/Module.symvers ../temp
cp /lib/modules/`uname -r`/build/Makefile .

make O=../temp outputmakefile
make O=../temp archprepare
make O=../temp prepare
make O=../temp modules SUBDIRS=scripts
make O=../temp modules SUBDIRS=drivers/usb/serial/

4) copy resulting modules to kernel modules directory

sudo cp ../temp/drivers/usb/serial/usb_wwan.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/
sudo cp ../temp/drivers/usb/serial/qcserial.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/
sudo cp ../temp/drivers/usb/serial/option.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/
sudo /sbin/depmod -a
----------------


I really hope experts of this community would spare some time and provide us newbie's
with similar or even better...copy/paste instructions for applying patch fixes.

thanks.

---

### Post by Muzafsh on 2011-02-14
1st request :)

_**Request for a patching Guide**_

**OS : **Ubuntu 10.10
**Machine : **Acer Netbook

**Patch to Fix : **To enable GPS and Diagnostic features of a Gobi 2000 device.

**Resources :**
Patch description : [https://patchwork.kernel.org/patch/204812/](https://patchwork.kernel.org/patch/204812/)

Please check attachments too.

Other Description : After a great deal of patience and research i had my Gobi 2000 device up and running the WWAN connection works perfectly. But the GPS and Diagnostic features are not enabled. Hence this request

thanks,

---

### Post by Muzafsh on 2011-03-15
:( no patrons !!!

---

### Post by nukleuzN on 2011-05-29
> **Muzafsh said:**
>  After a great deal of patience and research i had my Gobi 2000 device up and running the WWAN connection works perfectly.

Could you post the solution? And I also wanna know what ID your card has.0000x0000 something :-)

---

### Post by Muzafsh on 2011-05-29
Can you post the following details...

1. Which Laptop are you using ?
2. What version of Ubuntu ?
3. Which brand of Gobi card(HP, Lenovo, etc) ?
hope it is Gobi 2000 card...

---

