---
title: "MCE Remote stopped working"
date: 2012-08-01
forum: Mythbuntu
---

### Post by frego on 2012-08-01
I had this remote working ok:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16880101007](http://www.newegg.com/Product/Product.aspx?Item=N82E16880101007)

My son dropped it and then it stopped working.  I ordered another one and it too doesn't work.  So I used a different machine, performed a fresh install of Mythbuntu 12.04 64 bit and went into MMC choosing to add LIRC for 'Windows Media Center Transceivers/Remotes (all)'.  When I press a key on the remote the USB receiver lights up as if it sees it.  irw shows no activity.  And when I stop or start lirc I get:
```
 * Loading LIRC modules                                                                                                                                                                 [ OK ] 
find: `/sys/class/rc/*/': No such file or directory
 * Starting remote control daemon(s) : LIRC
```     

I see in dmesg that it sees the interface drive for mceusb.  

syslog shows it's having trouble with some file (presumably the above):
```
Aug  1 17:16:05 htpc lircd-0.9.0[9937]: accepted new client on /var/run/lirc/lircd
Aug  1 17:16:05 htpc lircd-0.9.0[9937]: could not get file information for /dev/lirc0
Aug  1 17:16:05 htpc lircd-0.9.0[9937]: default_init(): No such file or directory
Aug  1 17:16:05 htpc lircd-0.9.0[9937]: Failed to initialize hardware

```

So I think I was blaming my son for breaking it and perhaps it was an update I took about two weeks back instead.  Anyone have any ideas on where to start troubleshooting this?

---

### Post by Lester_Burnham on 2012-08-02
What does lsusb give you?

Lester

---

### Post by frego on 2012-08-02
lsusb gives me:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 147a:e042 Formosa Industrial Computing, Inc. 
Bus 002 Device 003: ID 0bda:0103 Realtek Semiconductor Corp. USB 2.0 Card Reader
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 006 Device 002: ID 0403:fc60 Future Technology Devices International, Ltd 
```

---

### Post by anonymousdog on 2012-08-02
[http://www.hack-job.org/uncategorized/recompile-a-kernel-module-example-mceusb-c/](http://www.hack-job.org/uncategorized/recompile-a-kernel-module-example-mceusb-c/)

---

### Post by frego on 2012-08-04
Yikes!  please tell me there is a better way than compiling the kernel!  I might as well roll with Gentoo if that's the way to install the remote.  Anyone know of a different method to gain support for that remote?

---

### Post by topcat5 on 2012-08-04
Stop lirc.  Then what is the output of

"ls -al /dev/input/by-id"

with the IR receiver plugged in?

---

### Post by anonymousdog on 2012-08-05
> **frego said:**
> Yikes!  please tell me there is a better way than compiling the kernel!  I might as well roll with Gentoo if that's the way to install the remote.  Anyone know of a different method to gain support for that remote?

I'm not suggesting you recompile the whole kernel; there's no point in that.  You **can**, however, very easily patch the kernel module and compile **just** the driver as a module.  The whole procedure is in that very well written how to.

---

### Post by anonymousdog on 2012-08-05
> **frego said:**
> Yikes!  please tell me there is a better way than compiling the kernel!  I might as well roll with Gentoo if that's the way to install the remote.  Anyone know of a different method to gain support for that remote?

I'm not suggesting you recompile the whole kernel; there's no point in that.  You **can**, however, very easily patch the kernel module and compile **just** the driver as a module.  The whole procedure is in that very well written how to.  I've had to do this many times for various input devices; it is not cause for distress.

---

### Post by frego on 2012-08-06
> **topcat5 said:**
> Stop lirc.  Then what is the output of

"ls -al /dev/input/by-id"

with the IR receiver plugged in?

"ls -al /dev/input/by-id" gives me:

lrwxrwxrwx 1 root root   9 Jul 31 16:49 usb-Logitech_USB_Receiver-event-kbd -> ../event1
lrwxrwxrwx 1 root root   9 Jul 31 16:49 usb-Logitech_USB_Receiver-event-mouse -> ../event0
lrwxrwxrwx 1 root root   9 Jul 31 16:49 usb-Logitech_USB_Receiver-if02-event-kbd -> ../event1
lrwxrwxrwx 1 root root   9 Jul 31 16:49 usb-Logitech_USB_Receiver-if02-event-mouse -> ../event0
lrwxrwxrwx 1 root root   9 Jul 31 16:49 usb-Logitech_USB_Receiver-if02-mouse -> ../mouse0
lrwxrwxrwx 1 root root   9 Jul 31 16:49 usb-Logitech_USB_Receiver-mouse -> ../mouse0

---

### Post by frego on 2012-08-06
> **anonymousdog said:**
> I'm not suggesting you recompile the whole kernel; there's no point in that.  You **can**, however, very easily patch the kernel module and compile **just** the driver as a module.  The whole procedure is in that very well written how to.  I've had to do this many times for various input devices; it is not cause for distress.

Thanks for the input anonymousdog... That is a very well written how to.  I was following the instructions step by step and ran into a problem at the make:

```
make: *** No targets specified and no makefile found.  Stop.
```
 which got me to reading about compiling the kernel, which scared me off.  But if it's just one specific module, then I feel more comfortable with it.  I did follow the how to step by step with no problem.  The make command didn't work though.  Anyone know where I should go from here?

---

### Post by anonymousdog on 2012-08-06
From terminal in current dir as home (i.e., '~/'):
```

#Get the kernel source
sudo apt-get install linux-source
#Unpack JUST the mceusb driver
tar jxvf /usr/src/linux-source-3.2.0.tar.bz2 linux-source-3.2.0/drivers/media/rc/mceusb.c
cd linux-source-3.2.0/drivers/media/rc/

```
Now modify the mceusb.c file as per the how to (i.e., patching by hand)
Proceed with the following (still in terminal with current dir = ~/linux-source-3.2.0/drivers/media/rc/):
```

#no Makefile needed
make -C /usr/src/linux-headers-$(uname -r) M=$(pwd) modules
#Backup the old module
cd /lib/modules/$(uname -r)/kernel/drivers/media/rc/
sudo mv mceusb.ko mceusb.ko.old
#Install the new one
cd ~/linux-source-3.2.0/drivers/media/rc/
sudo cp -v mceusb.ko /lib/modules/$(uname -r)/kernel/drivers/media/rc
#Activate the module:
sudo rmmod mceusb
sudo modprobe mceusb
```
and add it to your /etc/modules file as per the how to.

You will HAVE to repeat this process (except the /etc/modules edit) on EVERY kernel update.

---

### Post by dangerous_d on 2012-08-08
I had the same problem.  My solution was to order a new remote control.  I suggest buying from Amazon due to their generous return policy.  The key is finding a USB receiver with a manufacturer ID that the kernel supports.  You can find the supported IDs in the kernel source mceusb.c (or maybe they're in a header .h file, I can't remember).  To find the ID of your device plug it into the computer and do `lsusb'.

This is the one that worked for me.  Noah Company MediaGate GP-IR02BK

---

