---
title: "Can't install wireless Compaq CQ58-253"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by tasclew on 2013-01-09
I have just bought a Compaq CQ58-253 and I've made an Ubuntu 12.04 partition, but I can't figure out how to installa the appropiate wireless driver. I think the wireless devices comes with the blutooth device, but the blutooth device is active.

My wireless adapter is Qualcomm Atheros QCA9565 802.11b/g/n WiFi Adapter

By running either "lspci -nn | grep 0280" or "lspci -nn | grep Atheros" I get:
> 04:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)


I don't get any output by typing:
> $ ifconfig
$ iwconfig
$ lsmod
iwlist scan

I'm using Ubuntu 12.04 LTS

Edit:

I've tried it again after installing
> sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
but I still don't get anything from
> sudo modprobe ath9k


SOLVED:
This is what made it work:
> **chili555 said:**
> 
...we install the prerequitites needed to compile:```
sudo apt-get install linux-headers-generic build-essential
```Now we download the package, extract it and install it:```
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2
tar xvf compat*
cd compat-wireless-3.6.6-1-snpc
sudo su
./scripts/driver-select ath9k
make
make install
modprobe ath9k
exit
```Voila!Your wireless should now be working.

---

### Post by chili555 on 2013-01-09
> I don't get any output of "lspci -nn | grep 'Wireless Brand'"I think, by 'Wireless Brand' the original author hoped you'd run:```
lspci -nn | grep Atheros
```I'd prefer you run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by tasclew on 2013-01-12
Thank you **chili555**, I have edited my post with the new information.

---

### Post by chili555 on 2013-01-12
Please try:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```After it's done, do:```
sudo modprobe ath9k
```If that doesn't help, we'll plunge into the more complex: [http://askubuntu.com/questions/215498/upcoming-support-for-qualcomm-atheros-ar9565-wireless](http://askubuntu.com/questions/215498/upcoming-support-for-qualcomm-atheros-ar9565-wireless)

As in many things in life, try the easy way first.

---

### Post by tasclew on 2013-01-12
I've tried the easy way, but it still doesn't work. Should I try the other way? I really don't get how to use the other one, do I have to compile my own driver or something like that?

---

### Post by chili555 on 2013-01-12
Please reboot and then let's see:```
modinfo ath9k | grep -e file -e 0036
```

---

### Post by tasclew on 2013-01-12
This is what I get.

> filename:       /lib/modules/3.2.0-35-generic/updates/cw-3.6/ath9k.ko


By the way, thank you for your help :D .

---

### Post by praseodym on 2013-01-12
Did you also install the compiling tools?

```
sudo apt-get install linux-headers-generic build-essential dkms
```

Reboot and check:
```

uname -a
modinfo ath9k | grep -e file -e 0036
```

---

### Post by chili555 on 2013-01-12
The absence of an entry for 0036 indicates your device is not covered by the backports package. Let's undertake the process in my link. First, remove the possibly conflicting backports:```
sudo apt-get remove --purge linux-backports-modules-cw-3.6-precise-generic
```There is a companion package for your current kernel version and we'll purge it, too:```
sudo apt-get remove --purge linux-backports-modules-cw-3.6-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.

Now we install the prerequitites needed to compile:```
sudo apt-get install linux-headers-generic build-essential
```Now we download the package, extract it and install it:```
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2
tar xvf compat*
cd compat-wireless-3.6.6-1-snpc
sudo su
./scripts/driver-select ath9k
make
make install
modprobe ath9k
exit
```Voila!> $ modinfo drivers/net/wireless/ath/ath9k/ath9k.ko | grep 0036
alias:          pci:v0000[COLOR="Red"]168C[/COLOR]d0000[COLOR="Red"]0036[/COLOR]sv*sd*bc*sc*i*
Your wireless should now be working.

---

### Post by tasclew on 2013-01-12
**praseodym**, thanks for your help, but I still get the same message.

**chili555**, thank you very much, I will try right now, lets see if it works :D .

---

### Post by tasclew on 2013-01-12
Thank you very much, **chili555**, it worked, I'm posting this wireless. :D

Now I don't need to enter Windows anymore >.<. This thread can be closed

---

### Post by chili555 on 2013-01-12
Not so fast! You will need to re-compile whenever there is a newer kernel version installed by Update Manager:```
cd compat-wireless-3.6.6.1-snpc
sudo su
make clean
make
make install
modprobe ath9k
exit
```Please use thread tools at the top to mark Solved.

Have fun!

---

### Post by tasclew on 2013-01-12
But when there is a new kernel and I have to recompile it again, do I need to download a new version of compat-wireless? 

Thank's chilli.

---

### Post by chili555 on 2013-01-12
The version you have now should be just fine throughout 12.04. If not, post back and we'll assist.

---

### Post by qlimax on 2013-01-23
Thank you!
I just bought a Laptop "HP Envy dv5-7275ez" and I was having the same problem.

The wireless adapter is the same (Qualcomm Atheros QCA9565)

This solution has worked for me too!:KS

Note:
I downloaded a most recent package (29Nov 2013):
[http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2)

same steps worked!
Thank you again!

---

### Post by imnotjack on 2013-04-08
Worked like a charm. my friend. Your the best!

---

### Post by ronwit on 2013-06-24
**$ sudo apt-get install linux-headers-generic build-essential**

$ **wget [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2)**
--2013-06-24 19:11:23--  [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2)
Resolving [www.orbit-lab.org](www.orbit-lab.org) ([www.orbit-lab.org](www.orbit-lab.org))... 128.6.192.131
Connecting to [www.orbit-lab.org](www.orbit-lab.org) ([www.orbit-lab.org)|128.6.192.131|:80](www.orbit-lab.org)|128.6.192.131|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-06-24 19:11:23 ERROR 404: Not Found.

$ **sudo apt-get install linux-backports-modules-cw-3.6-precise-generic**

q@Q:~$ **sudo modprobe ath9k**
FATAL: Could not load /lib/modules/3.5.0-34-generic/modules.dep: No such file or directory

---

### Post by praseodym on 2013-06-24
Install it via:
```

sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic linux-backports-modules-cw-3.6-$(uname -r) linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```
Reboot.

---

### Post by 9k lai on 2013-06-28
I tried that  - and it just says:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-3.6-quantal-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.6-quantal-generic'

```
Any suggestions?

---

### Post by chili555 on 2013-06-28
> **9k lai said:**
> I tried that  - and it just says:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-3.6-quantal-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.6-[COLOR="#FF0000"]quantal[/COLOR]-generic'

```
Any suggestions?Are you running Quantal? You haven't given us any details. Please let us see:```
lspci -nn | grep 0280
lsb_release -d
```

---

### Post by 9k lai on 2013-06-28
1.:
```
04:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)
```

2.:
```
Ubuntu 12.04.2 LTS
```

Computer is a HP Compaq CQ58

---

### Post by chili555 on 2013-06-28
Ubuntu 12.04.2 LTS is code-named 'precise.' Please try:```
sudo apt-get install linux-backports-modules-cw-3.6-*precise*-generic linux-backports-modules-cw-3.6-$(uname -r) linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```Then load the module:```
sudo modprobe ath9k
```

---

### Post by 9k lai on 2013-06-29
I'm trying that and don't get any errors. But the wireless is still not working... :/

---

### Post by chili555 on 2013-06-29
Let's see:```
modinfo ath9k | grep -e lib -e 0036
iwconfig
rfkill list all
```Thanks.

---

### Post by 9k lai on 2013-06-29
then it says:
```
~$ modinfo ath9k | grep -e lib -e 0036
filename:       /lib/modules/3.2.0-48-generic/updates/cw-3.6/ath9k.ko

~$ iwconfig
lo        no wireless extensions.
usb0      no wireless extensions.
eth0      no wireless extensions.

~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
 
```

---

### Post by chili555 on 2013-06-29
Please get a temporary wired ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```If either or both is already installed, please proceed. Download this file to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.7.9/compat-drivers-3.7.9-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.7.9/compat-drivers-3.7.9-1.tar.bz2)  Right-click it and select 'Extract Here.' Now back to the terminal:```
cd Desktop/compat-drivers-3.7.9-1
./scripts/driver-select ath
make
sudo make install
sudo modprobe -r ath9k && sudo modprobe ath9k
```Now is it working?

---

### Post by 9k lai on 2013-06-29
**UUUUH YES!**
The last command gave some errors, but I just rebooted anyways - and now it works just fine. :)
Thank you so much, chili555. This was my very first posting and I was about losing hope to solve this.
Have a nice day and thanks again.

---

### Post by chili555 on 2013-06-29
I'm glad it's working! The module you compiled is for your currently running kernel only. When a new kernel, also known as linux-image, is installed by Update Manager, you'll need to re-compile after the reboot:```
cd Desktop/compat-drivers-3.7.9-1
./scripts/driver-select ath
make clean
make
sudo make install
sudo modprobe -r ath9k && sudo modprobe ath9k
```Please retain the files and these instructions for that day.

Have fun!

---

### Post by 9k lai on 2013-06-29
OK. Good to know.

Thanks a lot.

---

### Post by spinaotey on 2013-10-27
Hi, I'm Tasclew but with the new loggin I had to create this new account. I hope you can help me again. After every new kernel update I had to recompile my driver and it went smoothly. But after the latest kernelupdate I tried to recompile and I get the following error by executing the "make" command:

```
$ make./scripts/gen-compat-autoconf.sh /home/tasclew/Escritorio/compat-drivers-3.7.9-1/.config /home/tasclew/Escritorio/compat-drivers-3.7.9-1/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-55-generic/build M=/home/tasclew/Escritorio/compat-drivers-3.7.9-1 modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-55-generic»
  CC [M]  /home/tasclew/Escritorio/compat-drivers-3.7.9-1/compat/main.o
In file included from /home/tasclew/Escritorio/compat-drivers-3.7.9-1
/include/linux/compat-2.6.h:67:0,
                 from <línea-de-orden>:0:
/home/tasclew/Escritorio/compat-drivers-3.7.9-1/include/linux/compat-3.4.h:43:21: error: redefinición de ‘kmalloc_array’
include/linux/slab.h:243:21: nota: la definición previa de ‘kmalloc_array’ estaba aquí
make[3]: *** [/home/tasclew/Escritorio/compat-drivers-3.7.9-1/compat/main.o] Error 1
make[2]: *** [/home/tasclew/Escritorio/compat-drivers-3.7.9-1/compat] Error 2
make[1]: *** [_module_/home/tasclew/Escritorio/compat-drivers-3.7.9-1] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-55-generic»
make: *** [modules] Error 2

```

I know it is in spanish but the error comes from here I think
```
/home/tasclew/Escritorio/compat-drivers-3.7.9-1/include/linux/compat-3.4.h:43:21: error: redefinición de ‘kmalloc_array’
```
which is saying like "error: redefining of 'kmalloc_array'. Then it says
```
include/linux/slab.h:243:21: nota: la definición previa de ‘kmalloc_array’ estaba aquí
```
which says "Note: the previous definition of 'kmalloc_array' was here".

Thank's for you help people :) .

---

### Post by chili555 on 2013-10-27
I am guessing a bit here as I have neither the device nor kernel version 3.2.0-xx. I found this: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc3/ChangeLog-3.9-rc3-1](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc3/ChangeLog-3.9-rc3-1)> compat: declare kmalloc_array() through LINUX_BACKPORT()I suggest you try this package instead of compat-drivers-3.7.9-1.  

[https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/compat-drivers-3.9-rc4-2.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/compat-drivers-3.9-rc4-2.tar.bz2)

---

### Post by spinaotey on 2013-10-27
Chili, I get again an error of redefining something:

```
/home/tasclew/Escritorio/compat-drivers-3.9-rc4-2# makemake -C /lib/modules/3.2.0-55-generic/build M=/home/tasclew/Escritorio/compat-drivers-3.9-rc4-2 modulesmake[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-55-generic»
  CC [M]  /home/tasclew/Escritorio/compat-drivers-3.9-rc4-2/compat/main.o
In file included from /home/tasclew/Escritorio/compat-drivers-3.9-rc4-2/include/linux/compat-2.6.h:71:0,
                 from <línea-de-orden>:0:
/home/tasclew/Escritorio/compat-drivers-3.9-rc4-2/include/linux/compat-3.8.h:49:32: error: redefinición de ‘kref_get_unless_zero’
include/linux/kref.h:47:32: nota: la definición previa de ‘kref_get_unless_zero’ estaba aquí
make[3]: *** [/home/tasclew/Escritorio/compat-drivers-3.9-rc4-2/compat/main.o] Error 1
make[2]: *** [/home/tasclew/Escritorio/compat-drivers-3.9-rc4-2/compat] Error 2
make[1]: *** [_module_/home/tasclew/Escritorio/compat-drivers-3.9-rc4-2] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-55-generic»
make: *** [modules] Error 2
```

This time it's  ‘kref_get_unless_zero’.

Thanks for your help

---

### Post by chili555 on 2013-10-27
Please check here: [http://ubuntuforums.org/showthread.php?t=2149438](http://ubuntuforums.org/showthread.php?t=2149438)  After you've made the change, then try again with:```
[COLOR="#FF0000"]make clean[/COLOR]
make
sudo make install
```

---

### Post by spinaotey on 2013-10-28
Thank you **chili555, **that worked fine, now I can compile my driver again. Perfect :D .

---

### Post by chili555 on 2013-10-28
Whew! Glad we finally got it.

---

### Post by Oz_DiGennaro on 2014-02-25
This worked for me on a Dell 15R.  MANY other suggestions failed.  It was essential to install this driver.  It moved by wireless hardware device  (command "lshw -C network")

**from**

*-network UNCLAIMED
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter" 
(sounds pretty bad doesn't it? -- and it is bad!)  

**to **

*-network
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter"

---

### Post by coju-20 on 2014-05-28
> **chili555 said:**
> 

Now we install the prerequitites needed to compile:```
sudo apt-get install linux-headers-generic build-essential
```Now we download the package, extract it and install it:```
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2
tar xvf compat*
cd compat-wireless-3.6.6-1-snpc
sudo su
./scripts/driver-select ath9k
make
make install
modprobe ath9k
exit
```Voila!Your wireless should now be working.
Finally it works on my DELL Inspiron 3537 thanks to you chili555.

---

### Post by chili555 on 2014-05-28
For the benefit of the searchers, there are better ways to do this in 2014; just ask me.

---

### Post by luccka92 on 2014-07-24
Hello, I am new at the forum and with ubuntu too. I bought a Dell  inspiron 3537 with ubuntu 12.04 on it, this was my first meeting with  this OS and i definitely liked it. 
However after the first update my  laptop couldn't see any of the wireless networks around me. I got upset  and installed windows instead. I realized I liked ubuntu more, so i  installed 12.04 again, and hope that somehow i can fix the wifi problem.
So I came here to ask for help. I tried the commands written above in this thread but nothing happened with my network manager.  :(
Please, help, i like this OS very much!

---

### Post by praseodym on 2014-07-24
Hi,

please run these commands and show the outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
route -n
rfkill list
ifconfig -a
```
Does LAN work?

---

### Post by luccka92 on 2014-07-24
LAN is working, yes, I am using that right now.

> bella@bella:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05ea]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A] [1002:6660]
bella@bella:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 003: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:58c2 Realtek Semiconductor Corp. 
bella@bella:~$ lsmod
Module                  Size  Used by
vesafb                 13844  1 
snd_hda_codec_realtek   224215  1 
joydev                 17693  0 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_intel          33719  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
psmouse                98051  0 
uvcvideo               72627  0 
snd_seq_midi           13324  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
rts5139               351188  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13211  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
ath3k                  12961  0 
btusb                  18332  0 
bluetooth             180113  12 rfcomm,bnep,ath3k,btusb
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 dell_wmi
video                  19651  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62190  0 
bella@bella:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

bella@bella:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
bella@bella:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
bella@bella:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
bella@bella:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr ec:f4:bb:9b:97:f7  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe9b:97f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60448200 (60.4 MB)  TX bytes:5671669 (5.6 MB)
          Interrupt:61 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:323994 (323.9 KB)  TX bytes:323994 (323.9 KB)


(sorry, I don't know how to make the message to the right form but i hope this is good as well)

---

### Post by praseodym on 2014-07-24
Can you load the driver by hand?
```

sudo modprobe -v ath9k
```

---

### Post by luccka92 on 2014-07-24
This was the response to the command:

> bella@bella:~$ sudo modprobe -v ath9k
[sudo] password for bella: 
insmod /lib/modules/3.2.0-67-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-67-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-67-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.2.0-67-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.2.0-67-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-67-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 


And thank you for helping!

---

### Post by praseodym on 2014-07-24
Lets check now:
```

iwconfig
iwlist chan
sudo iwlist scan
dmesg | egrep 'wlan0|ath'
```

---

### Post by luccka92 on 2014-07-24
> bella@bella:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

bella@bella:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

bella@bella:~$ sudo iwlist scan
[sudo] password for bella: 
Sorry, try again.
[sudo] password for bella: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
bella@bella:~$ dmesg | egrep 'wlan0|ath'
[   10.937476] ath3k: probe of 1-1.5:1.0 failed with error -2
[   10.937512] usbcore: registered new interface driver ath3k
[   11.391656] type=1400 audit(1406204464.343:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=879 comm="apparmor_parser"
[   11.392130] type=1400 audit(1406204464.343:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=879 comm="apparmor_parser"
[   40.873108] type=1400 audit(1406204493.831:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1984 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0



I suppose this is not very good :/

---

### Post by praseodym on 2014-07-24
Obviously, I doesnt work with this driver. Update it via

```
sudo apt-get install linux-backports-modules-cw-3.6-$(grep CODE /etc/lsb-release | cut -c18-28)-$(uname -r | cut -c10-23) 
```
Reboot.

---

### Post by luccka92 on 2014-07-24
I did what you said, there was no problem, and did a reboot, but the network manager is still not showing any wireless connections

---

### Post by praseodym on 2014-07-25
Ok, install the hardware enablement stack (new kernel and X-server):

```
sudo apt-get -s install --install-recommends linux-generic-lts-trusty linux-image-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty linux-headers-generic-lts-trusty 
```

This is a test! If it shows no errors, then run:

```
sudo apt-get install linux-generic-lts-trusty linux-headers-generic-lts-trusty linux-image-generic-lts-trusty
sudo apt-get install xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty
```
Reboot.

---

### Post by luccka92 on 2014-07-25
The test went okay, no error. But the for the other part it said "aborted". I don't know if it matters, but I see this is for trusty tahr, but i have precise. Does it matter?

> bella@bella:~$ sudo apt-get install linux-generic-lts-trusty linux-headers-generic-lts-trusty linux-image-generic-lts-trusty
Csomaglisták olvasása&#8230; Kész0%
Függ&#337;ségi fa építése       
Állapotinformációk olvasása&#8230; Kész
Az alábbi extra csomagok kerülnek telepítésre:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic
Javasolt csomagok:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0
  linux-lts-trusty-tools
Az alábbi ÚJ csomagok lesznek telepítve:
  linux-generic-lts-trusty linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-headers-generic-lts-trusty
  linux-image-3.13.0-32-generic linux-image-generic-lts-trusty
0 frissített, 6 újonnan telepített, 0 eltávolítandó és 658 nem frissített.
Letöltend&#337; adatmennyiség: 66,4 MB.
A m&#369;velet után 274 MB lemezterület kerül felhasználásra.
Folytatni akarja [I/n]? i
Megszakítva.



---

### Post by praseodym on 2014-07-25
Then run
```

sudo apt-get install --install-recommends linux-generic-lts-trusty linux-image-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty linux-headers-generic-lts-trusty
```

---

### Post by luccka92 on 2014-07-26
It was working for quite long time, and then finished, and the update manager popped up and says there's a lot of things i should update. Should I?

In the lines it said close to the end, that:

> W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-2.fw for module r8169


I don't know what this means, but it seems suspicious. But i think everything went great, because it didn't show any errors.

---

### Post by praseodym on 2014-07-26
Install the package "linux-firmware" from 14.04, it contains these files, see the package list:

[http://packages.ubuntu.com/trusty/all/linux-firmware/filelist](http://packages.ubuntu.com/trusty/all/linux-firmware/filelist)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb)

---

### Post by luccka92 on 2014-07-26
Sorry for my ignorance, but how can I do that? I downloaded the .deb file

---

### Post by praseodym on 2014-07-27
Double-click and installation with the software-centre

---

### Post by Lakshmi_Narayan_V on 2014-09-14
Thank you very much, Chili555

You saved my day!!!

DELL Latitude 3540, Wifi not working after update, Qualcomm Atheros QCA9565/ AR9565 - SOLVED

---

