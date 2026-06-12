---
title: "Intel 82566DC-2 unable to install in 8.10"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by kalpesh on 2008-12-11
Hi 

This is my 5th unsuccessful day of trying To install this drivers (e1000)
So i decided now Post in forum now

I tried to search in ubuntu forum, Google, Linuxquiestion, 
Found many solution  one is here 

[http://ubuntuforums.org/showpost.php?p=3389934&postcount=8](http://ubuntuforums.org/showpost.php?p=3389934&postcount=8)

But non of them tell that how to solve this thing

**cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode**


I am quite new to linux world I have just complete 40 days in this world

I was using ubuntu 8.04 in vmware after i upgraded to 8.10 after some practice I decided to install 8.10 in my PC 

I have installed 8.10 successfully 
(Installed using Wubi)

But I notice that my network drivers is not working

My Motherboard is Intel DG33FBC

[B]__________________
He also got this error 
But how he fixed that thing I cant understand 

which permissions and which folder did he use?

[SIZE="4"][http://ubuntuforums.org/showpost.php?p=3389934&postcount=8](http://ubuntuforums.org/showpost.php?p=3389934&postcount=8)[/SIZE]



The last line of that install gave me " can not write to var/cache........in catman mode e1000.
I logged in as root and changed the permissions of the folder listed above and ran another time, this time without any errors.
I then went back into the terminal and ran: rmmod e1000 & then sudo modprobe e1000...
__________________________________________[/B]

[SIZE="5"]**Log of shell installation**[/SIZE]

user@ubuntu:~/Desktop/e1000-8.0.6/src$ sudo make install
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/user/Desktop/e1000-8.0.6/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_main.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_82540.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_82542.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_82541.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_82543.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_mac.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_nvm.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_phy.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_manage.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_param.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_ethtool.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/kcompat.o
  CC [M]  /home/user/Desktop/e1000-8.0.6/src/e1000_api.o
  LD [M]  /home/user/Desktop/e1000-8.0.6/src/e1000.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/user/Desktop/e1000-8.0.6/src/e1000.mod.o
  LD [M]  /home/user/Desktop/e1000-8.0.6/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
gzip -c ../e1000.7 > e1000.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.27-7-generic -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.27-7-generic -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.27-7-generic/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man: 
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.
user@ubuntu:~/Desktop/e1000-8.0.6/src$ sudo make install
[SIZE="5"]
**Log of lspci -v**[/SIZE]
See last part

user@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: Intel Corporation Device 5044
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0000000-d1ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp


00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
	Subsystem: Intel Corporation Device 5044
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2225900 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: heci
	Kernel modules: heci

00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
	Subsystem: Intel Corporation Device 0000
	Flags: fast devsel, IRQ 20
	Memory at d2200000 (32-bit, non-prefetchable) [size=128K]
	Memory at d2224000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30e0 [size=32]
	Capabilities: <access denied>
	Kernel modules: e1000e


[B]Which drivers and version of divers i should use e1000 or e1000e?
Which version of Ubuntu should I use?
How can fix this error?

(cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.)

Is i need to Change Network Card?
If yes Then which one should i Buy?[/B]

---

### Post by kalpesh on 2008-12-11
Can I degraded My kernel of 8.10 to 2.6.20.15

---

