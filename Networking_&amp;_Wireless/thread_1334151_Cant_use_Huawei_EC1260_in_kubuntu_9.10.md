---
title: "Cant use Huawei EC1260 in kubuntu 9.10"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by Vasan on 2009-11-22
I am not able to use my reliance net in kubuntu 9.10. I was using it in ubuntu 9.04. But cant use in kubuntu 9.10. Help me solve this...

Thank u..

---

### Post by CbrPad on 2009-11-22
Is this a 3g usb modem ?   I could never get them working under Kubuntu, it would detect alright but there seems to be a bug where it fails to connect.   Try switching to the gnome-network-manager (nmapplet) and see what happens. 

Oh, and it may not work even then either, see possible solutions here...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

---

### Post by Vasan on 2009-11-23
I executed these commands.
sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x14b0
sudo pppd ttyUSB0 

Then my reinserted the modem. Now the modem was not detected. First it was detected as Storage device. Now its not even detecting so.

Help me.

Is there no other way to connect my reliance broadband + in kubuntu 9.10 ?????

---

### Post by pdc on 2009-11-24
maybe go back to 9.04 as you know it worked?

9.10 has had problems with 3G modems

---

### Post by anaconda on 2009-11-24
> **pdc said:**
> maybe go back to 9.04 as you know it worked?

9.10 has had problems with 3G modems

I thought that those problems were solved by installing a new kernel. That is newer kernel than the one that ships with 9.10....

---

