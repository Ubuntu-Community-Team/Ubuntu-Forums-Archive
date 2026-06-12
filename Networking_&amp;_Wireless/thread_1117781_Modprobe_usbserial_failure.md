---
title: "Modprobe usbserial failure"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by tilugulilwa on 2009-04-06
Hello,
I am trying to connect my usb huawei ets 2288 modem on Ubuntu 9.4 without success...

I can not do modprobe usbserial...as it fails saying that module usbserial not found.

root@frank-laptop:/etc/init.d# modprobe -r usbserial vendor=0X0451 product=0X3410
FATAL: Module usbserial not found.


the wvdial ttcl command fails as well giving this error

root@frank-laptop:/etc/init.d# sudo wvdial ttcl
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: Input/output error

Any assistance will be highly appreciated

---

### Post by GeorgeVita on 2009-04-06
Hi **tilugulilwa**,

> **tilugulilwa said:**
> ...
I can not do modprobe usbserial...as it fails saying that module usbserial not found.

root@frank-laptop:/etc/init.d# modprobe -r usbserial vendor=0X0451 product=0X3410
FATAL: Module usbserial not found.
...

with **modprobe -r usbserial** you are trying to remove the module usbserial which does not exists (not found).

As I understand you want to **add** the module usbserial so:
**modprobe usbserial vendor=0X0451 product=0X3410**

The above will try to add serial communication port(s) to **0451:3410** usb peripheral. These can be found as /dev/ttyUSB* or /dev/ttyS* or /dev/ttyACM*


From terminal try **man modprobe**

Regards,
George

---

### Post by ramnarayan on 2009-06-14
Hi

Ok the problem is not really only the -r 

I have the same device and get the same error
 ram@ram-laptop:~$ sudo modprobe usbserial vendor=0X0451 product=0X3410
FATAL: Module usbserial not found.

There are other issues with this said device which i am posting on - [http://ubuntuforums.org/showthread.php?p=7455061#post7455061](http://ubuntuforums.org/showthread.php?p=7455061#post7455061)

because this device does not really need a modprobe as it has already been recognized by the system.


While trying to figure out a solution to my problem with being able to
use a USb serial device on Ubuntu 9.04 came across a problem someone
else had
[http://ubuntuforums.org/showthread.php?t=1163615&highlight=Huawei+ets+2280](http://ubuntuforums.org/showthread.php?t=1163615&highlight=Huawei+ets+2280)

seems like the kernal itself might need to be updated

So any ideas on how to proceed


thanks
ram

---

### Post by GeorgeVita on 2009-06-14
Hi **ramnarayan**,

I am happy that you are trying to solve this Very Difficult and Rare situation with the ETS 2288 modem/phone.

> Ok the problem is not really only the -r
In 1st post on this thread dated **April 6th, 2009** (before release of Jaunty) usbserial was an external module. With 9.04 this is encapsulated to the kernel ... and the problems began! (also wvdial is missing!)
[COLOR="Navy"][B]>>> UPDATE: From kernel 2.6.28-13-generic you can use it as in the past:
sudo modprobe usbserial vendor=0x1c9e product=0x6061[/B][/COLOR]
Please read: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002)

and try:
> **Pete Graner**:
"As a short term workaround until we can get it added pls try and report back with:
Built in modules can have module params passed on the kernel command line: can you try booting with:

usbserial.vendor=**0x0451** usbserial.product=**0x3410**

You will need to press ESC during to grub pause upon restart/power on.
Arrow down to the kernel you wish to boot.
press "e" (for edit)
Arrow down to the 2nd line (the command line)
Press Enter to begin editing
Arrow to the end of the line and add:
usbserial.vendor=**0x0451** usbserial.product=**0x3410**
When done press enter. Then press "b" to boot"

I just edit the VendorID, productID fro the launchpad post.

The "other way" (you should have a connection) is some posts below on this bug-report:
> **Pete Graner**:
"The module is no longer complied in the kernel. You can get it now by enabling the -proposed repo and updating the kernel, or you can wait until it hits the -updates repo."

Regards,
George

---

### Post by ramnarayan on 2009-06-14
> **GeorgeVita said:**
> Hi **ramnarayan**,

I am happy that you are trying to solve this Very Difficult and Rare situation with the ETS 2288 modem/phone.

Thanks if it works it would be really great
 (also wvdial is missing!)

which i managed to set up after reading your very helpful help page. Thanks

and try:


I just edit the VendorID, productID fro the launchpad post.



Ok is there a way of adding it to the menu.lst so that every time i boot i don't need to add it as a boot up line. 

Am guessing it will be ok if i add it as a line under my normal boot options

like
**
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dd3799a7-81db-49a7-8c03-e972859199f8
kernel		/vmlinuz-2.6.28-11-generic root=UUID=febd703e-8639-47f6-bafd-81602f266bfb ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
usbserial       usbserial.vendor=0x0451 usbserial.product=0x3410
quiet
**

you think this will work 
will try and get back

thanks a lot
ram

---

### Post by ramnarayan on 2009-06-14
adding the line to menu.lst did not seem to work

so tried the suggested method of adding it to the second line

after that tried sudo wvdial xx and got this error message
laptop:~$ sudo wvdial 93
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

**
so its still back to square 1 for the time being 

ram

---

### Post by GeorgeVita on 2009-06-14
Hi again,

**ramnarayan** try this:

**sudo /boot/grub/menu.lst**

convert line:
```
kernel /vmlinuz-2.6.28-11-generic root=UUID=febd703e-8639-47f6-bafd-81602f266bfb ro quiet splash
```

adding at the end: **usbserial.vendor=0x0451 usbserial.product=0x3410**

the result is:
```
kernel /vmlinuz-2.6.28-11-generic root=UUID=febd703e-8639-47f6-bafd-81602f266bfb ro quiet splash usbserial.vendor=0x0451 usbserial.product=0x3410
```
[COLOR="Blue"]WARNING: add "usbserial.ve..." to your existing line (extension).
I don't know if UUID is the same to your system![/COLOR]

NOTE: above work with a ZTE modem but we are NOT sure it will work with yours. Nevertheless it is good to try it. Also is there any parameter on the modem/phone menu for Timeout or DataOnly or Handshaking that you have to adjust? 

Regards,
George

---

### Post by mbogo.kariuki on 2011-03-30
I have tried editing menu.lst and adding the following

usbserial.vendor=0x19d2 usbserial.product=0xfff1

but still can solve the problem!:confused:

---

### Post by GeorgeVita on 2011-03-30
> **mbogo.kariuki said:**
> I have tried editing menu.lst and adding the following
usbserial.vendor=0x19d2 usbserial.product=0xfff1
but still **can solve** the problem!:confused:
Suppose you mean "cannot solve the problem".
As this thread is very old, you must check it again with the latest version of Ubuntu. If still you have "connecting problems", open a new thread **including your modem type-model into "thread title"** to get specific ideas. Post here the link of your new thread also.
Regards,
George

---

