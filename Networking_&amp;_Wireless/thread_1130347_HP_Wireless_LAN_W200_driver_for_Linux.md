---
title: "HP Wireless LAN W200 driver for Linux"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by kyle7119 on 2009-04-19
I am trying to use my HP W200 multiport card with Ubuntu 8.10.  I have followed [[COLOR="Blue"]these[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200") intructions and I have been successful until the part where you have to compile the driver:

> # cd usb
# make
# sudo make install

I get this error message while running the "make" command:

> ubuntu@ubuntu:~$ cd usb
ubuntu@ubuntu:~/usb$ make
make -C /usr/src/linux-headers-2.6.27-7-generic M=/home/ubuntu/usb KERNELRELEASE=2.6.27-7-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
CC [M] /home/ubuntu/usb/orinoco.o
In file included from /home/ubuntu/usb/orinoco.c:90:
/home/ubuntu/usb/orinoco.h: In function ‘orinoco_spin_unlock’:
/home/ubuntu/usb/orinoco.h:188: warning: ‘__raw_spin_unlock’ is static but used in inline function ‘orinoco_spin_unlock’ which is not static
/home/ubuntu/usb/orinoco.h:188: warning: ‘raw_local_irq_enable’ is static but used in inline function ‘orinoco_spin_unlock’ which is not static
/home/ubuntu/usb/orinoco.c: In function ‘orinoco_translate_scan’:
/home/ubuntu/usb/orinoco.c:3975: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:3975: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:3975: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/ubuntu/usb/orinoco.c:3975: error: too few arguments to function ‘iwe_stream_add_event’
/home/ubuntu/usb/orinoco.c:3985: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:3985: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:3985: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:3985: error: too few arguments to function ‘iwe_stream_add_point’
/home/ubuntu/usb/orinoco.c:3995: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:3995: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:3995: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/ubuntu/usb/orinoco.c:3995: error: too few arguments to function ‘iwe_stream_add_event’
/home/ubuntu/usb/orinoco.c:4005: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:4005: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:4005: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/ubuntu/usb/orinoco.c:4005: error: too few arguments to function ‘iwe_stream_add_event’
/home/ubuntu/usb/orinoco.c:4019: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:4019: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:4019: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/ubuntu/usb/orinoco.c:4019: error: too few arguments to function ‘iwe_stream_add_event’
/home/ubuntu/usb/orinoco.c:4028: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:4028: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:4028: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:4028: error: too few arguments to function ‘iwe_stream_add_point’
/home/ubuntu/usb/orinoco.c:4053: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:4053: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/ubuntu/usb/orinoco.c:4053: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/ubuntu/usb/orinoco.c:4053: error: too few arguments to function ‘iwe_stream_add_value’
make[2]: *** [/home/ubuntu/usb/orinoco.o] Error 1
make[1]: *** [_module_/home/ubuntu/usb] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2 

Any help would be appreciated.  Thanks!

---

### Post by ajgreeny on 2009-04-19
Have you got **build-essentials** installed?  If not, get it and you may find all is well.

---

### Post by kyle7119 on 2009-04-19
> **ajgreeny said:**
> Have you got **build-essentials** installed?  If not, get it and you may find all is well.
Yes, I have build-essentials installed, and the process still doesn't work.

---

### Post by JK3mp on 2009-04-19
try config before make, make install. And have you installed all updates? If not do that first.

---

### Post by kyle7119 on 2009-04-19
> **JK3mp said:**
> try config before make, make install. And have you installed all updates? If not do that first.
How do I configure?

And yes, I have installed the updates.

---

### Post by JK3mp on 2009-04-19
run ./configure before make make install.

---

### Post by kyle7119 on 2009-04-19
I will try JK3mp's advice, but also take a look at this.

> Try following the instructions in *markds*'s post here ([http://www.slax.org/forum.php?action=view&parentID=31051](http://www.slax.org/forum.php?action=view&parentID=31051)). 

---

