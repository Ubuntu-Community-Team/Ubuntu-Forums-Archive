---
title: "ndiswrapper doesn't work"
date: 2005-02-19
forum: Networking &amp; Wireless
---

### Post by gotcha80 on 2005-02-19
I tried the ndiswrapper howto to use my rtl8180 wifi card on my laptop (acer aspire 1350), I'm using Hoary with kernel 2.6.8

ndiswrapper -i net8180.inf  works and if I do ndiswrapper -l it reports 

root@mifune ~ # ndiswrapper -l
Installed ndis drivers:
net8180 driver present, hardware present

but if I do 

modprobe ndiswrapper root@mifune ~ # modprobe ndiswrapper
FATAL: Module ndiswrapper not found.


Why does this happen? Did I miss something? I also tried with a different kernel version... 2.6.7 but with same results

please help!

---

### Post by telmo on 2005-02-19
The only way i got ndiswrapper working in hoary was updating the kernel to 2.6.10 and downloading the ndiswrapper rc1 and installing it manually. Before that... modprobe hell!

My wireless card is different from yours, but i think there's no problem in that.

By the way... don't forget to install the kernel headers and restricted modules and making a shortcut to kernel headers, like this: 

ln -s /usr/src/linux-headers-2.6.10-2 /lib/modules/2.6.10-2-686/build 
(for kernel 2.6.10-2.686 in this case).

Make install and modprobe it.

Good luck!

---

### Post by ekko on 2005-02-20
ndiswrapper consists on two things: ndiswrapper - the program - which loads NDIS drivers to the kernel module and ndiswrapper - the kernel module. ndiswrapper-utils only contains the first, and that's why you can't find the module.

---

