---
title: "network connection problem in 11.04"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by piyush| on 2011-09-14
since 11.04 introducing unity interface, so I thought to give it a try but not as a dual boot OS
I installed 11.04 via WUBI and i was able to set up network connections without any problems
the internet connection was working fine

Now after liking Unity interface, I thought to make it as a dual boot OS
installed it but the network problem arose
I used the same settings but the problem persist

Need help
thanks

---

### Post by HugoSerrano on 2011-09-14
Some info about your system will help us to help you :-)

---

### Post by piyush| on 2011-09-14
if you are asking for hardware config..then

AMD Athlon II x4 635
MSI 880gma e45
4gb ddr3 1333mhz kingston
500gb seagate HDD

---

### Post by praseodym on 2011-09-14
Hi,

please show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by piyush| on 2011-09-14
> **praseodym said:**
> Hi,

please show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

```

piyush@piyush-MS-7623:/home$ lspci -nnk | grep -iA2

Usage: grep [OPTION]... PATTERN [FILE]...

Try `grep --help' for more information.


piyush@piyush-MS-7623:/home$ lsusb

Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 

1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 

1.1 root hub
Bus 005 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 

005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 

Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root 

hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 

1d6b:0002 Linux Foundation 2.0 root hub


piyush@piyush-MS-7623:/home$ lsmod

Module                  Size  Used by
binfmt_misc            17565  1 
snd_hda_codec_hdmi     

28103  1 
snd_hda_codec_realtek   336693  1 
radeon                982197  3 
snd_hda_intel    

      33211  2 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 

snd_seq_midi
ppdev                  17113  0 
snd_hda_codec         103804  3 

snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 

snd_hda_codec
snd_pcm                96625  3 

snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ttm                    76664  1 radeon
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                73535  0 
drm_kms_helper  

       42136  1 radeon
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
drm    

               227495  5 radeon,ttm,drm_kms_helper
parport_pc             36959  1 
snd_timer 

             29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 

snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13400  1 radeon
sp5100_tco            

 13744  0 
serio_raw              13166  0 
snd                    67382  14 

snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,

snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13303  0 
edac_core           

   53845  0 
k10temp                13119  0 
xhci_hcd               77643  0 
edac_mce_amd    

       23464  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 

snd_hda_intel,snd_pcm
shpchp                 37297  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid      

              91020  1 usbhid
ahci                   25951  4 
libahci                26642  

1 ahci
pata_atiixp            13165  0 
r8169                  48022  0 
pata_jmicron          

 12747  0 


piyush@piyush-MS-7623:/home$ iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.



piyush@piyush-MS-7623:/home$ rfkill list


piyush@piyush-MS-7623:/home$ sudo iwlist scan
[sudo] password for piyush:
 
lo        Interface doesn't support scanning.

eth0   
   Interface doesn't support scanning.

```

---

### Post by praseodym on 2011-09-14
The first line again, input per copy/paste

---

### Post by piyush| on 2011-09-14
didnt get you

---

### Post by praseodym on 2011-09-14
```
lspci -nnk | grep -iA2 net
```
is one line. There was sth. missing.

---

### Post by piyush| on 2011-09-21
here is the result

```

piyush@piyush-MS-7623:~$ lspci -nnk|grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7623]
	Kernel driver in use: r8169
--------------------------
piyush@piyush-MS-7623:~$ lsusb
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

piyush@piyush-MS-7623:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1
snd_hda_codec_hdmi     28103  1
snd_hda_codec_realtek   336693  1
snd_hda_intel          33211  2
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ppdev                  17113  0
snd_seq_midi           13324  0
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
radeon                982197  3
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
sp5100_tco             13744  0
psmouse                73535  0
i2c_piix4              13303  0
serio_raw              13166  0
ttm                    76664  1 radeon
k10temp                13119  0
parport_pc             36959  1
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53845  0
edac_mce_amd           23464  0
drm_kms_helper         42136  1 radeon
drm                   227495  5 radeon,ttm,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 radeon
xhci_hcd               77643  0
shpchp                 37297  0
lp                     17825  0
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0
hid                    91020  1 usbhid
ahci                   25951  4
pata_jmicron           12747  0
pata_atiixp            13165  0
libahci                26642  1 ahci
r8169                  48022  0

piyush@piyush-MS-7623:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


piyush@piyush-MS-7623:~$ rfkill list
piyush@piyush-MS-7623:~$ sudo iwlist scan
[sudo] password for piyush:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by praseodym on 2011-09-21
Install the "real" driver for device 8168, most of the time the r8169 driver makes problems.

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

Just copy/paste the lines.

---

### Post by piyush| on 2011-09-21
> **praseodym said:**
> Install the "real" driver for device 8168, most of the time the r8169 driver makes problems.

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

Just copy/paste the lines.

but to install these drivers, wont i need an active internet connection on the first hand?
and many thanks for your quick replies :)

---

### Post by praseodym on 2011-09-21
Well,  yes. Please show

```
uname -a
```
The package build-essential can be installed from CD, just insert it and add it to the software packages. I will give you the links for the other packages. The source code of the driver can be directly downloaded from here:

[http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2)

---

### Post by piyush| on 2011-09-21
> **praseodym said:**
> Well,  yes. Please show

```
uname -a
```
The package build-essential can be installed from CD, just insert it and add it to the software packages. I will give you the links for the other packages. The source code of the driver can be directly downloaded from here:

[http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2)

i installed it via usb
so what should i do?

---

### Post by praseodym on 2011-09-21
Type in the terminal

```
sudo apt-get install build-essential
```
and write down the packages named to be installed (cancel the installation). These packages can be installed from the stick, too, just open the file manager.

If "uname -a" shows the "2.6.38-generic" kernel, install additionally these packages:

32 bit:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8-generic_2.6.38-8.42_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8-generic_2.6.38-8.42_i386.deb)

64 bit:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8-generic_2.6.38-8.42_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8-generic_2.6.38-8.42_amd64.deb)

Both:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8_2.6.38-8.42_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8_2.6.38-8.42_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-5ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-5ubuntu1_all.deb)

Save the needed three packages in "Downloads" and install via:

```
sudo dpkg -i ~/Downloads/*.deb
```
Then compile the driver. If the network works now, update your system:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
```
and reboot.

---

### Post by MarkX on 2011-09-22
Maybe not relevant but I had a problem getting online and changed the ipv6 setting from "Automatic" too "ignore" which cured the problem.

---

### Post by piyush| on 2011-09-22
here is the uname -a result
```

piyush@piyush-MS-7623:~$ uname -a
Linux piyush-MS-7623 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

ok i tried your way of installing the packages i.e. through terminal commands while USB plugged in but I couldn't
so i just manually installed them

but the thing is Ubuntu Software Centre informed me that I have already these packages installed in this build EXCEPT ALL .deb
so i installed it

Now what should i do next?

---

### Post by praseodym on 2011-09-22
Now compile the driver as described and update the system if it works.

---

### Post by piyush| on 2011-09-22
how to comile things
i'm noob to commands

---

### Post by praseodym on 2011-09-22
Save the driver (.tar.bz2-file) on your Desktop and install it via:

```
cd Desktop/
tar xvf r8168-8.024.00.tar.bz2
cd r8168-8.024.00
sudo ./autorun.sh
echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by piyush| on 2011-09-23
```

piyush@piyush-MS-7623:~/Desktop$ tar xvf r8168-8.024.00.tar.bz2
r8168-8.024.00/
r8168-8.024.00/Makefile
r8168-8.024.00/src/
r8168-8.024.00/src/Makefile
r8168-8.024.00/src/r8168_asf.h
r8168-8.024.00/src/rtl_eeprom.c
r8168-8.024.00/src/r8168.h
r8168-8.024.00/src/r8168_n.c
r8168-8.024.00/src/r8168_asf.c
r8168-8.024.00/src/rtl_eeprom.h
r8168-8.024.00/src/rtltool.h
r8168-8.024.00/src/rtltool.c
r8168-8.024.00/src/Makefile_linux24x
r8168-8.024.00/README
r8168-8.024.00/autorun.sh
piyush@piyush-MS-7623:~/Desktop$ cd r8168-8.024.00
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ sudo ./autorun.sh
[sudo] password for piyush: 

Check old driver and unload it.
rmmod r8169
Build the module and install
echo[: 48: r8168: unexpected operator
Backup r8169.ko
rename r8169.ko to r8169.bak
Depending module. Please wait.
 'blacklist rload module r8168
Completed.
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist r8169
[B]piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ sudo modprobe -rf r8169
FATAL: Module r8169 not found.[/B]
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ 


```

what should i do now?
it failed in between

---

### Post by praseodym on 2011-09-23
Just continue. The module was renamed, therefore it cannot be found

---

### Post by piyush| on 2011-09-23
here is the total result

```

piyush@piyush-MS-7623:~$ cd Desktop/
piyush@piyush-MS-7623:~/Desktop$ tar xvf r8168-8.024.00.tar.bz2
r8168-8.024.00/
r8168-8.024.00/Makefile
r8168-8.024.00/src/
r8168-8.024.00/src/Makefile
r8168-8.024.00/src/r8168_asf.h
r8168-8.024.00/src/rtl_eeprom.c
r8168-8.024.00/src/r8168.h
r8168-8.024.00/src/r8168_n.c
r8168-8.024.00/src/r8168_asf.c
r8168-8.024.00/src/rtl_eeprom.h
r8168-8.024.00/src/rtltool.h
r8168-8.024.00/src/rtltool.c
r8168-8.024.00/src/Makefile_linux24x
r8168-8.024.00/README
r8168-8.024.00/autorun.sh
piyush@piyush-MS-7623:~/Desktop$ cd r8168-8.024.00
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ sudo ./autorun.sh
[sudo] password for piyush: 

Check old driver and unload it.
rmmod r8169
Build the module and install
[: 48: r8168: unexpected operator
Depending module. Please wait.
load module r8168
Completed.
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist r8169
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ sudo modprobe -rf r8169
FATAL: Module r8169 not found.
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ sudo modprobe -v r8168
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ sudo depmod -a
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
piyush@piyush-MS-7623:~/Desktop/r8168-8.024.00$  

```

btw i checked one thing
i tried to ping to my server in ubuntu but the error was "Address not found"(or is it normal in this situation?)
though in win7 its working fine as you can see

---

### Post by praseodym on 2011-09-23
Reboot and check:

```
lspci -nnk | grep -iA2 net
ifconfig -a
lsmod
dmesg | grep r8
route -n
```

---

### Post by piyush| on 2011-09-23
here it is:
```

piyush@piyush-MS-7623:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7623]
	Kernel driver in use: r8168
piyush@piyush-MS-7623:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:4e:86:c9  
          inet addr:172.22.1.1  Bcast:172.22.255.255  Mask:255.255.0.0
          inet6 addr: fe80::6e62:6dff:fe4e:86c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7295 errors:0 dropped:24 overruns:0 frame:0
          TX packets:498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1061933 (1.0 MB)  TX bytes:49348 (49.3 KB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29902 (29.9 KB)  TX bytes:29902 (29.9 KB)

piyush@piyush-MS-7623:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
radeon                982197  3 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ttm                    76664  1 radeon
ppdev                  17113  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42136  1 radeon
psmouse                73535  0 
drm                   227495  5 radeon,ttm,drm_kms_helper
edac_core              53845  0 
serio_raw              13166  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_mce_amd           23464  0 
k10temp                13119  0 
i2c_algo_bit           13400  1 radeon
parport_pc             36959  1 
sp5100_tco             13744  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13303  0 
shpchp                 37297  0 
xhci_hcd               77643  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  4 
pata_atiixp            13165  0 
libahci                26642  1 ahci
r8168                 194904  0 
pata_jmicron           12747  0 
piyush@piyush-MS-7623:~$ dmesg | grep r8
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800cfc00000 s84416 r8192 d22080 u262144
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u262144 alloc=1*2097152
[    2.764724] r8168 Gigabit Ethernet driver 8.024.00-NAPI loaded
[    2.764752] r8168 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.764770] r8168 0000:02:00.0: setting latency timer to 64
[    2.764825] r8168 0000:02:00.0: irq 43 for MSI/MSI-X
[    2.838401] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    2.838406] r8168  Copyright (C) 2011  Realtek NIC software team <nicfae@realtek.com> 
[   11.669244] r8168: eth0: link down
[   13.221287] r8168: eth0: link up
[   13.660067] r8168: eth0: link up
piyush@piyush-MS-7623:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.22.0.0      0.0.0.0         255.255.0.0     U     1      0        0 eth0
0.0.0.0         172.22.1.1      0.0.0.0         UG    0      0        0 eth0
piyush@piyush-MS-7623:~$  


```

---

### Post by praseodym on 2011-09-23
Check the mtu-value of your ISP (most 1500 or 1492) and add it as a number instead of "Automatic" in the network-manager applet.

---

### Post by piyush| on 2011-09-23
> **praseodym said:**
> Check the mtu-value of your ISP (most 1500 or 1492) and add it as a number instead of "Automatic" in the network-manager applet.

how to check it?
plz elaborate as i'm still new to ubuntu
thanks anyways

---

### Post by piyush| on 2011-09-23
and how to add that value?

---

### Post by praseodym on 2011-09-23
Google for it, ask your ISP or try those 2. In the NM-applet->Edit connection-> cable connection

Replace "Automatic" at MTU with 1500 or 1492.

---

### Post by PayPaul on 2011-09-23
> **praseodym said:**
> ```
lspci -nnk | grep -iA2 net
```is one line. There was sth. missing.


I used the same command thinking this might diagnose my network and sharing issues and got the following. I'm not sure what it means other than telling me what drivers or ethernet cards I have on my system.

XXXXw@ubuntu:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7309]
    Kernel driver in use: forcedeth

What is "forcedeth"? Sounds ominous

I'm trying to do filesharing and get access to my wired and wireless home network. I'm told in the Networks and Sharing dialog that certain "packages are not installed on my system". Where do I get these packages?

---

### Post by praseodym on 2011-09-23
Try a module parameter for your device:

```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```
and reboot. "forcedeth" is the name of the module.

---

### Post by varunendra on 2011-09-29
Hello Piyush,

Didn't read all the posts thoroughly as soon as I saw this:
> **piyush| said:**
> 
```

piyush@piyush-MS-7623:~$ lspci -nnk|grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  **RTL8111/[COLOR=Red]8168B PCI[/COLOR]** Express Gigabit Ethernet controller [10ec:8168] (rev  03)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7623]
    **Kernel driver in use: [COLOR=Red]r8169[/COLOR]**

```
..so please excuse me if I missed something more important.

With this hardware-driver combination, this post has helped a few people: [http://ubuntuforums.org/showthread.php?p=11053381](http://ubuntuforums.org/showthread.php?p=11053381)

So if you are still having problems, you may try above, although it suggests doing almost exactly same what you have already done with *praseodym's* help.

Since the very first step involves downloading the relevant package, either get connected via a cable connection while doing this, or download it in advance from here: [http://www.foxhop.net/attachment/r8168-8.023.00.tar.bz2](http://www.foxhop.net/attachment/r8168-8.023.00.tar.bz2) and just copy it to your home directory > then proceed with the next steps.

Also, you won't need the blacklisting step as it is already done. Plus, you will have to **rmmod r8168** instead of **r8169** as it is **r8168** which is currently loaded. You will then end up compiling and loading the same driver again, just a different (older) version.

However, as much as I could notice, the module suggested by *praseodym* is newer and seems to have been correctly loaded. So can't say if my post is going to make it any better. But since it went smooth with a few people who responded there, let's hope it does the magic for you too.

---

### Post by piyush| on 2011-10-02
heck...things are messed up
I'll do a fresh install of 11.04 and will inform if the problem persists 
thanks all of you

---

### Post by piyush| on 2011-10-15
OK the problem got solved
I installed 11.10 and everything went fine

but now opera .deb package is not getting installed'
Internal Error is being shown

and when i try to open with Ubuntu Sofware Center, the USC crashes

PS:I havent installed the drivers and other distributors updates

---

### Post by varunendra on 2011-10-15
> **piyush| said:**
> but now opera .deb package is not getting installed'
Internal Error is being shown

and when i try to open with Ubuntu Sofware Center, the USC crashes
That is not related with the original topic of the thread, so you should start a new one with this question (you may put a link to it here then).

As for this topic, we'd appreciate if you can share with us whether it worked by default with 11.04, or you had to do some tweaks as told in this thread or somewhere else.

**PS:** I think you should mark this one as [Solved] now.

---

