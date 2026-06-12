---
title: "Updating ACX driver for Netgear 311v2"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by GQed76 on 2006-01-13
The ACX driver that comes with Breezy does not work out of box with this card.  There has been alot of development over at [http://acx100.sourceforge.net](http://acx100.sourceforge.net).

I did get my card to work with NDIS wrapper, but I'd prefer to have a linux built driver work from kernel. ( The windows driver hardlocks the system occasionally)

So I follwed the instructions for oustside of tree, and got "cannot find" message when I did insmod ./acx.ko

So I thought I'd try compiling inside the  kernel...I'm such a  risk taker ;)

Anyway everything worked until I got to compling the kernel.  Here the directions get a bit unclear to a linux newbie and I couldnt get the commansds to work

```
cd ..
echo 'obj-m += acx/' >> Makefile[CODE]
```[/CODE]

Since the ACX driver already had a line in breezy...i commented it out and placed in the above code. however..was the >> Makefile meant to be part of that code? Or was it writer shorthand?

Then comes > Anyway, all thats life to do is configure and compile your kernel. 

```
cd ../../..
make menuconfig # You won't find an acx option - don't worry about it, it will get built anyway
make && make modules_install
```
and i get

```
root@gqubuntu:/usr/src/linux-headers-2.6.12-10-k7-smp# make menuconfig
  HOSTLD  scripts/kconfig/mconf
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

>> Unable to find the Ncurses libraries.
>>
>> You must install ncurses-devel in order
>> to use 'make menuconfig'

```

Im currently looking for this package but dont see it in the repos.

---

### Post by GQed76 on 2006-01-13
any help?

---

