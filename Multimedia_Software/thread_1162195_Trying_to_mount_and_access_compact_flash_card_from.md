---
title: "Trying to mount and access compact flash card from digital camera"
date: 2009-05-17
forum: Multimedia Software
---

### Post by DnDer on 2009-05-17
I have an old USB card reader that I plugged in, and inserted my first CF card. It mounted to the desktop just fine. Then I right-clicked and unmounted the drive, so I could use my second CF card. It did not show up on the desktop.

Google told me to try this "sudo lsusb" and I got the following results:
```
Bus 001 Device 003: ID 0b30:0005 PNY Technologies, Inc. 
Bus 001 Device 002: ID 04b4:0001 Cypress Semiconductor Corp. Mouse
Bus 001 Device 001: ID 0000:0000 
```

The next step it to make a directory to mount the card to. But I can't get "mkdir" to work. Can anyone give me a hand?

"sudo mkdir /<user name>/<new directory - cfcard>" right? But I've done something wrong.

```
mkdir: cannot create directory `/<user name>/cfcard': No such file or directory
```

What did I goof on?

---

### Post by xc3RnbFO8P on 2009-05-17
Read this:
[http://www.qbik.ch/usb/devices/showdev.php?id=890]("http://www.qbik.ch/usb/devices/showdev.php?id=890")

---

### Post by DnDer on 2009-05-17
I'm sorry... What I'm reading doesn't make a lot of sense. TBQH, I'm not 100% sure on how to properly mount a drive in the first place, let alone a CF Card.

Can you walk me through it again, but a little slower this time?

---

### Post by xc3RnbFO8P on 2009-05-17
Sorry, what you need is:
> sudo su
> sudo mkdir -p cfcard

---

### Post by DnDer on 2009-05-17
Awesome!! Thank you!!

Now, how do I mount it? I can't quite figure out how to do it right. =\

"mkdir -p /username/cfcard" made the folder, and the mount point, right? So, when I mount something, that's where I should be able to find all the files, right? [FAQ I found](http://www.cyberciti.biz/tips/linux-how-to-use-usb-penflash-stick.html) told me to "mount /dev/sda1 /username/cfcard" would do just that. But there's nothing in the folder when I go open it.

I'm missing a step.

---

### Post by xc3RnbFO8P on 2009-05-18
Read this:
[http://vic.gedris.org/linux-UsbMassStorage/]("http://vic.gedris.org/linux-UsbMassStorage/")

---

