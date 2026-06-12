---
title: "Ubuntu 10 and RealTek 8190 issues"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by Nichellek on 2011-01-22
Hi, So brand new to Ubuntu and linux for that matter. Can't seem to get my network card up and running I have tried the various fixes through the forums, as you can see in the screenshots. Just hoping an expert could help me out so I can finally close the box and get sleep. I have a ASUS M4A78T-E with phenom II. I downloaded ndiswrapper (1.9) and have wicd. The card is trendnet 643PI but it shows up as RealTek 8190.

---

### Post by chaosdx on 2011-01-30
I have the same wifi card, and my own investigation brought this:

0. Using 32-bit Linux, it's possible to use ndiswrapper to load WinXP drivers (there are multiple success stories to that effect).

This is not an option for me, since I use x86_64.

1. For a 64-bit Linux, it's probably not possible so far, and, frankly, ill-advised, to use ndiswrapper with WinXP-64 drivers for this card; this is why:

I tried both Trendnet-supplied and Realtek-supplied RTL819xP drivers with ndiswrapper and both caused my system to freeze/crash in interesting ways [COLOR="Silver"]forcing to use SysRq-sequences to reboot and fallback to root console through safe-mode to remove ndiswrapper[/COLOR]. So, really, not advised.

2. Native r8192e_pci driver *feels* to me like it should work with 8190 chip, since Realtek's Windows driver is the same for both models (819xP), and there is some code for 8190 support in the Linux driver. However, it might be a wrong assumption, and I don't know if it is possible to get it to recognize a 8190 device, which has [10ec:8190] code, not 10ec:8192.


So, I haven't found a solution, but maybe a summary will be useful to someone... :) I have yet to try asking for native x86_64 linux drivers from realtek.

---

### Post by chaosdx on 2011-01-31
So, I emailed Realtek support for a driver, listing my kernel version and architecture, and got it quite promptly. Thank you, Realtek! (Although they could've done better having it on their site directly)

For anyone deciding to do the same: the one you need is RTL8190P driver.

Included in the tar.gz archive was a quite clear *readme.txt* describing the compilation and install process. Just a couple of amends to it, if a newbie should find my post and try the same:

a) "make install" won't work, unless you type "sudo -s make install" instead.

b) respectively, if you choose to manually copy the firmware to /lib/firmware with "cp", you will need to sudo it.

c) will need to do
```
make clean
make
make install
```
anew every time the kernel is updated. It is an obvious thing, but not mentioned explicitly, so I thought I'd better ;)


After the installation, modprobe worked, lsmod shows my new driver **r8190_pci**. But "iwconfig" lists wlan1 unconnected and "lshw -C network" shows "*-network DISABLED" for it (but driver is present). WiCD doesn't seem to notice it exists, either. There are no obvious errors in dmesg after the driver loading.

**REQUEST FOR HELP:** Anyone has any idea where to go from here? What can I try that doesn't involve manually configuring /etc/network/interfaces?

---

### Post by chaosdx on 2011-02-02
Continuing the cautionary tale of what I did and what happened. Warning: This part is not for a faint newbie heart :twisted:

(NB: My kernel is 2.6.35, x86_64)

Since my previous post, I've noticed that Realtek-supplied driver sends errors into /var/log/debug when attepmting to scan for networks, to the effect of this:

```
Download Firmware: Put code fail!
ERR in CPUcheck_maincodeok_turnonCPU()
CPUcheck_maincodeok_turnonCPU fail!
ERR!!! _rtl8192_up(): initialization is failed!

```

I followed the messages into the source of /HAL/rtl_core.c, and found out that the CPU returned status code that wasn't expected. After some pondering, I changed the timeout of waiting for that code from 20 to 200 ms in a couple of places.

Recompile, reinstall, wow! It worked. I could see wireless networks and connect to them. For all of 2 minutes; after this my system froze hard and required a hard-reset (not even SysRq helped).

Logs later showed a heap of errors like this:
```
DMA: Out of IOMMU space for 9000 bytes
...
...
```

I found a [thread on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all") addressing a very similar issue for 8192se.

In the comments, there was a proposed patch to a file that rtl8190 source also has (in /rtllib). Examining it, I found out that only some function names were different from the 8192se, so it is possible to carefully apply the patch code exactly into the same places. The line numbers were the same.

Recompile, reinstall... No more DMA error.
Still, it freeses my box pretty soon, but there aren't any obvious signs in logs.

Being bored, I might proceed to experiment around, but I generally dislike hard-crashing my main system :( Kids, don't do this at home.

---

### Post by Nilakka on 2011-02-25
Hi,

Please let me know if you /anyone else ever succeeds in getting RTL8190 chip working in Ubuntu 64bit. I'd really appreciate that. :)

BR Ilkka

---

### Post by klive77 on 2011-05-17
I also have a similar problem.  
lspci | grep 8190 gives
05:05.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190

I emailed realtek for a driver but no response :(
I think I can hack my way into getting it to work, but without a driver I can't see how to proceed.  

Does anyone know a link to the driver for this thing?  Instructions also appreciated but I think there is enough in the forums already... its the lack of a driver thats the trouble.

p.s. I am running debian squeeze on one machine and natty ubuntu on another and couldn't get it to work on either

---

### Post by st0kes on 2011-05-19
hello peeps,

I had big problems with this wifi driver. It would keep asking me for the password, even though it was typed in correctly. Other times it would work fine, for no reason at all. Ubuntu natty is using the r8192e_pci driver out of the kernel staging tree. I used an alternate one I found on the interwebs which seems to work great. Perhaps the one in the kernel is faulty. 

My laptop is a samsung nc210 by the way. This is what I did:

1. Plug in a network cable. 
2. Open a terminal window. 
3. First, get kernel headers:, and make a directory where we will build the driver.

```
sudo apt-get install linux-headers-$(uname -r)
cd ~
mkdir realtek
cd realtek
```

4.Make certain that you have working Internet. We're removing the current 'broken' driver.

```
sudo rmmod r8192e_pci
```

5. Get the driver and extract it

```
wget http://people.debian.org/~benh/rtl-wlan/rtl8192e_linux_2.6.0014.0401.2010.tar.gz
tar zxf rtl8192e_linux_2.6.0014.0401.2010.tar.gz 
cd rtl8192e_linux_2.6.0014.0401.2010/
```

6. Now compile the driver. If this fails, you might need to install the gcc package. I think it's installed by default usually.

```
make
```

7. Install the driver. This has to be done as root. sudo doesn't work. Substitute **yourname** with your username. 
```

sudo su -
cd ~yourname/realtek/rtl8192e_linux_2.6.0014.0401.2010
make install

```

8. This step probably isn't necessary, but it gave me extra warm and fuzzies. I'm removing the old driver from the system and symlinking the new driver to the old location. The locate command is helping me find the old driver on disk.

```
locate r8192e_pci.ko
rm /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8192e/r8192e_pci.ko
ln -s /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless//r8192e_pci.ko /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8192e/r8192e_pci.ko

```

After a reboot it was working fine. Good luck!

---

### Post by berserkpi on 2011-05-20
I'm also stuck on rtl8190 chip using natty 64bits.

```
*-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:d000(size=256) memory:fe500000-fe500fff
```

I've tried rtl8190xp.inf (using ndiswrapper) and rtl8192e (compiling it). No luck. I'll buy a TP-LINK :P. Just kidding, still trying.

---

### Post by berserkpi on 2011-05-20
Ok, at this point I started to think this is not in our hands... at least not solving it in a elegant way...

---

### Post by ptkirby on 2011-06-07
Hello all,

I am having the same problem as [berserkpi]("http://ubuntuforums.org/member.php?u=614777") and many of the rest of you. I have spent the past few days problem solving, and have come to an absolute dead end. 

Has any progress been made?


Thank you,


Peter

---

