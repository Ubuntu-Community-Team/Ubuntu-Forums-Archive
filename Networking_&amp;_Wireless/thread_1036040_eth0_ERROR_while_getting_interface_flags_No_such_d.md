---
title: "eth0: ERROR while getting interface flags: No such device"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by bappythegreat on 2009-01-10
Hi Guys

Im having some trouble with ubuntu server edition 8.04.1 x32

basically I have picked up a load of thin clients going spare from work.

they are neoware capio 800s. I have customized them by adding 5GB+ old laptop hdds. one of them is to be an http/php server, one a database server and the other a web proxy server.

Im trying to configure the database server.

The only way to install linux on this machine was to put the laptop harddrive in an actual laptop (one with a cd drive lol) and install server edition.

from there I had to apt-get install linux-386 as the 686 build does not boot on the thin client's cpu (AMD Geode 300Mhz)

now my laptop has a 8139cp compatable lan card, the thin client does not.

when the thin client boots it says "this (some ids) is not an 8139C+ compatable card" and then below that is says to try 8139too driver instead.

I know for a fact that 8139too works fine because the same machine booting delilinux can access the card and the network fine using 8139too

lsmod showed both 8139too and 8139cp as having been loaded so I blacklisted 8139cp thus preventing the error at bootup.

I also added 8139too to the initramfs/modules file and did the update-initramfs thing.

now it boots without any error message (expect the usual acpi one that caused me to add pci=noacpi to /boot/grub/menu.lst file)

when i get into the system and type ifconfig it lists only the loopback device.

if i run sudo /etc/init.d/networking start it brings up several errors like the one in the topic title.

even plugging in a usbnet device won't work. (modprobe automatically starts usbnet) 

can someone please help me? I have spent from 1:30pm to 7pm on this problem using google (a lot) and with lots of help from the people at #ubuntu but we still cannot get the system to start my lan device. 

Im sure there is nothing wrong with the hardware, as, like i said delilinux works fine with it - its just delilinux is not glibc so wont run mysql.

thanks in advance,
Ben

---

