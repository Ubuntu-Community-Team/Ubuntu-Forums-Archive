---
title: "can not connect reliance LG LXU Modem800"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by sai_nath on 2011-07-10
hey hi all,

i am beginner to this field of ubuntu(linux)...:grin:last week i have installed ubuntu 11.04...alongside windows xp...

but i couldnt configure my net connection...

i am using reliance LG LXU800 modem(cdma)
intially  it was working after using this command
sudo modprobe usbserial version=0xeab product=0x9357

that time my linux version is 2.6.38.7

but now it gives fatal error and it is

**FATAL: Error inserting usbserial  (/lib/modules/2.6.38-8-generic/kernel/drivers/usb/serial/usbserial.ko):  Unknown symbol in module, or unknown parameter (see dmesg)**

how do i get out of this problem....:confused:

---

### Post by dineshs on 2011-07-11
> sudo modprobe usbserial [COLOR="Red"]version[/COLOR]=0xeab product=0x9357I think this is not correct.It should be something like [COLOR="Red"]sudo modprobe usbserial vendor=0x4348 product=0x5523[/COLOR]. Note:Replace the vendor and product ids .Command```
lsusb
```can help you findout the ids

---

### Post by sai_nath on 2011-07-11
Thanks dineshs for reply:D
but still it doesnt work....:(
for your reference attaches is snapshot of terminal.....

---

### Post by dineshs on 2011-07-12
Should be ```
sudo modprobe usbserial vendor=0x[COLOR="Red"]0[/COLOR]eab product=0x9357
```You forgot the zero marked in red.

---

### Post by sai_nath on 2011-07-12
hey...
its work.....
thank you so much.....
actually each time i have  done some silly mistake i think its because of i am beginner in linux,,,

but ya  slowly i will surely grasp all things...

:)

---

### Post by dineshs on 2011-07-12
Glad you got it working.It is always better to copy and paste commands to avoid errors.
Please mark the thread as solved via thread tools

---

