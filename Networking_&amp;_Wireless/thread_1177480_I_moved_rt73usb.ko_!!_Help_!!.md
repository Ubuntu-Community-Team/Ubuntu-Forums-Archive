---
title: "I moved rt73usb.ko !! Help !!"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by NoOne121 on 2009-06-03
I wanted to try out driver rt73 for use on aircrack and used this guide
[http://www.aircrack-ng.org/doku.php?id=rt73](http://www.aircrack-ng.org/doku.php?id=rt73)
and also to 'blacklist' the rt73usb which comes with ubuntu 9.04 I ran the script on that page.

now basically the script just moves the unwanted rt73usb.ko module from its folder. 
being a windows user i thought i could just move the file rt73usb.ko back into its folder if i wanted to use it again. oh how wrong i was.

this happens when i run modprobe rt73usb

FATAL: Error inserting rt73usb (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

how can i get back my rt73usb driver? I am interested in using it with aircrack. maybe i should not have messed around in the first place but its too late now.:D

thanks

---

### Post by Ayuthia on 2009-06-03
It looks like the kernel module was moved to /root/rt73module.  You can check and see if the file is there:
```
ls /root/rt73module/rt73usb.ko
```
If it is there, you can copy it back to /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2x00:
```
sudo cp /root/rt73module/rt73usb.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2x00/
sudo depmod -a
```
And that module should be available again.

---

### Post by NoOne121 on 2009-06-04
thanks for the help....
i already did as you suggested and when i  run modprobe rt73usb i get this....

FATAL: Error inserting rt73usb (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

after moving the file the script runs command
depmod -ae
is there a command i must run once i place the rt73usb.ko file back into its correct folder?

---

### Post by Ayuthia on 2009-06-05
> **NoOne121 said:**
> thanks for the help....
i already did as you suggested and when i  run modprobe rt73usb i get this....

FATAL: Error inserting rt73usb (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

after moving the file the script runs command
depmod -ae
is there a command i must run once i place the rt73usb.ko file back into its correct folder?
If you haven't already, you should check dmesg to see what it says.  Most likely there is another file that is missing.  If dmesg does not provide too much information, you might try:
```
sudo modprobe --show-depends rt73usb
```
and it will list all the modules it needs.  If it does have other modules, you should check /root/rt73module to see if they are there and move them back.

---

### Post by NoOne121 on 2009-06-07
thats great...thanks for the help

---

