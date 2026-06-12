---
title: "Trouble compiling IMQ into Ubuntu 9.10 server kernel"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by dhbernard on 2010-02-11
We are trying to setup a rate limiting server using Ubuntu Server 9.10 with a transparent Bridge, iptables, IMQ and Master Shaper.
The issue we are having is getting IMQ compiled into the 2.6.31 kernel and iptables 1.4.4.

We have found a couple of How-To sites but most are only as current as the Edgy distro.

Can anyone give us a heads up on getting this working with the 9.10 distro.

Thanks in advance.

---

### Post by roskiy on 2010-02-12
here i just installed it and will try to describe what i have done

install dependancy packages

# sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile 

kernel-package
# sudo apt-get build-dep linux
# sudo apt-get install libncurses5 libncurses5-dev

create some directory to download Kernel source
as example:
# mkdir /home/sysop/k_src
and enter that directory
#cd /home/sysop/k_src

Get the kernel source * (or use your own method)
# sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
# sudo apt-get source linux-image-$(uname -r)

find out your Kernel version
# uname -r

Download IMQ patch from [http://www.linuximq.net/](http://www.linuximq.net/)
As example : # wget [http://www.linuximq.net/patchs/linux-#.#.##.#-imq.diff](http://www.linuximq.net/patchs/linux-#.#.##.#-imq.diff)
where linux-#.#.##.#-imq.diff is a version of IMQ that patch your kernel

Create link named "linux' in your /usr/src directory
# sudo ln -s /home/sysop/k_src/linux-2.6.31/ /usr/src/linux
where /home/sysop/k_src - is the directory where you downloaded linux source 

and linux-2.6.31 is unpacked linux source directory which can have other 

numbers in your system (match Kernel version)

copy current Kernel configuration into source directory
# sudo cp /boot/config-2.6.31-14-server /usr/src/linux/.config
enter into /usr/src/linux directory
# cd /usr/src/linux

try IMQ patch to kernel
# sudo patch -p1 -i /home/simax/linux-2.6.31.6-imq.diff  --dry-run
if any error found start looking for versions inconsistencies in files you 

have downloaded do not proceed any further
apply IMQ patch to kernel
# sudo patch -p1 -i /home/simax/linux-2.6.31.6-imq.diff

open kernel configuration menu
# sudo make menuconfig
navigate menu into Device Drivers -> Network Device Support ->
and mark <M> IMQ (intermediate queueing device) support
then Exit -> Exit -> Exit -> save

Set number of processors cores for compiler
# sudo export CONCURRENCY_LEVEL=5
where 5 is 1+number of processor cores (quad core in this case)

compile Kernel and headers into deb files
# fakeroot make-kpkg --initrd --append-to-version=-imq kernel-image kernel-

headers

take a nap while kernel is compiling 

...zzzzzz..zzz..zzzzzz..zzzzz.zzz...coffee...coffee...tetris...

install kernel new kernel
sudo dpkg -i linux-image-2.6.20-16-2be-k7_2.6.20-16_i386.deb
sudo dpkg -i linux-headers-2.6.20-16-2be-k7_2.6.20-16_i386.deb

finnaly reboot into new kernel

hope it work

---

### Post by dhbernard on 2010-02-12
Thanks for the quick reply.

I will give your instructions a try
and post back the results.

---

### Post by monico on 2010-03-18
Hi, all. I appreciate this useful information to patch Ubuntu kernel with IMQ. I followed each section, however, when I did 

open kernel configuration menu
# sudo make menuconfig
navigate menu into Device Drivers -> Network Device Support ->
and mark <M> IMQ (intermediate queueing device) support
then Exit -> Exit -> Exit -> save

I didn't find IMQ option inside of Network Device Support Menu

I ran this instructions on Ubuntu 9.10 server.

Any ideas?

TIA

Monico

---

