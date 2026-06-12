---
title: "Edimax EW-7722IN"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by wadio87 on 2011-07-18
Hello everyone, I am finally decided to try Linux

Today I received a new PC and has the following hardware configuration:

- Core i7 2600K
- 8 GB DDR3
- Nvidia GT210
- 1 TB WD RE
- Wireless PCI Adapter Edimax EW-7722IN

As a system, I installed **Ubuntu 10.04 LTS 64bit**, because I saw that will be supported for a long period.
The installation was lightning, all hardware is recognized fine except the wireless card and I think the LAN card

As a motherboard i have the following motherboard: Asus P8P67 PRO (B3), B3 Intel P67, LGA1155, CFX / SLI

The paradox of the Wireless card is that there  are drivers for Linux.

I have done that: I downloaded the zip file, then copied the folder on the desktop of ubuntu, I have entered with the terminal the folder than i have written "sudo make" after "sudo make install"

I rebooted the PC but nothing seems to work :confused:

You have any suggestions?!


Many thanks to all!

---

### Post by chili555 on 2011-07-18
What file did you install? rt3562sta? Please open a terminal and run and post:```
lspci -nn | grep 0280
lsmod | grep -e rt2 -e rt3
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by wadio87 on 2011-07-18
Hello Chilli! Thanks for your reply.

I list here the output of the commands.

first command output:

> 
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1503] (rev 05)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 5 [8086:1c18] (rev b5)
00:1c.6 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b5)
00:1c.7 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 8 [8086:1c1e] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c46] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 210] [10de:0a65] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
03:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)
05:00.0 SATA controller [0106]: JMicron Technology Corp. Device [197b:2362] (rev 10)
06:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)
07:00.0 PCI bridge [0604]: Device [1b21:1080] (rev 01)
08:01.0 Network controller [0280]: RaLink Device [1814:3062]
08:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)
09:00.0 SATA controller [0106]: Device [1b4b:9172] (rev 11)



second command output:

> 
rt3562sta             956792  0 



the wireless driver folder is the following one:

2010_07_16_RT3062_Linux_STA_v2.4.0.0

---

### Post by chili555 on 2011-07-18
When you compiled it, did you do this step:> 3> In os/linux/config.mk 

** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.Please check the file. If not, please change it and re-compile:```
cd Desktop/2010_07_16_RT3062_Linux_STA_v2.4.0.0 
sudo su
make clean
make
make install
exit
```Reboot and give us your report.

---

### Post by wadio87 on 2011-07-18
Ok, now i will do it.

I have been able to install Intel LAN drivers, now works perfectly the LAN :popcorn:

Just need the Wireless now and my Ubuntu will be 100% ok :D

I write asap ;)

---

### Post by wadio87 on 2011-07-18
awesome, it works, beer and pop corns for all :popcorn::popcorn::popcorn:

---

### Post by chili555 on 2011-07-18
I love :popcorn: !! Please use thread tools at the top and Mark Solved.

---

### Post by wadio87 on 2011-07-18
ehehehe cool, me tooo love :popcorn:

but there is a strange problem, after i restarted, the lan has gone away, maybe i have to enable it automatically but dont know how :confused:

---

### Post by chili555 on 2011-07-18
Does it come to life if you do:```
sudo modprobe rt3562sta
```If so, please do:```
sudo su
echo rt3562sta >> /etc/modules
exit
```It ought to start on boot now.

---

### Post by wadio87 on 2011-07-18
Hi, sorry. Not the Wireless LAN, but the Local LAN (ETHERNET)

The wireless starts automatically without problems :)

---

### Post by wadio87 on 2011-07-18
This is the link for my LAN drivers

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3299&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3299&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A)

Model :   Intel 82579 Gigabit LAN

Thanks for the big help :)

---

### Post by chili555 on 2011-07-18
Try this:```
sudo su
echo e1000e >> /etc/modules
exit
```If it doesn't work as expected, we'll need to dig deeper.

---

### Post by wadio87 on 2011-07-18
Hmmm strange... does not work.

Is there a way to uninstall and reinstall ?

---

### Post by chili555 on 2011-07-18
Let's have a look at:```
dmesg | grep -e e100 -e eth
```

---

### Post by wadio87 on 2011-07-19
Hi, thanks very much, as soon as i will find some time i will do it ;)
The most important is that now the wireless works perfectly since i needed it a lot :D

---

### Post by nennec on 2011-07-21
Hey guys,

Just wanna say thanks to all the contributors in this thread. I had the exact same problem and the suggested solution worked like a charm.

I'm very grateful & please keep up the good work.

Thanks again to all,
Nennec

---

### Post by Ciambello on 2011-07-27
Hi everybody,
i just bought this wlan card today, but I can't figure out how to make it work with Ubuntu 11.04. I've followed chilli55 suggestions but it still doesn't work. When I'm doing 
```

make clean
make
make install

```warnings keep coming up in the terminal:
```
make: warning: File 'Makefile' has modification time 2.6e108 s in the future
```
```
make: warning: Clock skew detected. Your build may be incomplete.
```I hope you can give me some support!

---

### Post by chili555 on 2011-07-27
Please open a new terminal, cd to the correct directory and repeat all the commands as I outlined. Then run:```
date
```Copy and paste the result into your reply.

That's a new one on me.

---

### Post by Ciambello on 2011-07-28
Thanks for your quick answer. I've tried what you suggested: 
```
cd /home/max/Scriviania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/
suso su
make clean
make
make install
```and then the date command gave me this output:
```
ven 5 apr 2002, 05.11.59, CEST
```I don't think this can be useful, personally I think the problem here is that I can't compile the source correctly since I haven't got any LAN connection to install build-essentials packages. What do you think?

---

### Post by chili555 on 2011-07-28
> I can't compile the source correctly since I haven't got any LAN connection to install build-essentials packages. What do you think?I think you are correct. Can you get an ethernet connection and do:```
sudo apt-get install linux-headers-generic build-essential
```I'd also adjust the date and time on your computer.

---

### Post by Ciambello on 2011-07-29
OK so I've found a way to get a LAN connection, installed the packages and went run the commands again, but it still seems not to work. Here is the overall output from terminal:
```

max@BIGPAVI:~$ cd /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/
max@BIGPAVI:~/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0$ sudo su
root@BIGPAVI:/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0# make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: ingresso nella directory "/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux"
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: uscita dalla directory "/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux"
rm -rf os/linux/Makefile
root@BIGPAVI:/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0# make
make -C tools
make[1]: ingresso nella directory "/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/tools"
gcc -g bin2h.c -o bin2h
make[1]: uscita dalla directory "/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/tools"
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux modules
make[1]: ingresso nella directory "/usr/src/linux-headers-2.6.38-8-generic"
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/mlme.o
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/mlme.c:5692:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/action.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_aes.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/spectrum.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/rt_channel.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_profile.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../sta/sync.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../sta/connect.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.o
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:1586:3: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:695:1: warning: the frame size of 1288 bytes is larger than 1024 bytes
In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess.h:571:0,
                 from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:211,
                 from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/include/os/rt_linux.h:38,
                 from /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/include/rtmp_os.h:31,
                 from /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/include/rt_config.h:63,
                 from /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:31:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:3671:28:
/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:4157:28:
/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:7069:1: warning: the frame size of 1336 bytes is larger than 1024 bytes
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:7268:1: warning: the frame size of 1344 bytes is larger than 1024 bytes
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.o
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c:1717:38: warning: initialization discards qualifiers from pointer target type
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c:1754:38: warning: initialization discards qualifiers from pointer target type
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_main_dev.o
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_main_dev.c:111:13: warning: unused variable ‘Cancelled’
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/ba_action.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa_adhoc.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.o
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPResetTxRxRingMemory’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:25:13: warning: unused variable ‘num’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:108:16: warning: unused variable ‘IrqFlags’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:107:16: warning: unused variable ‘pPacket’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:106:15: warning: unused variable ‘pTxD’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:105:16: warning: unused variable ‘pTxRing’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:104:19: warning: unused variable ‘j’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:104:6: warning: unused variable ‘index’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:436:11: warning: unused variable ‘BufBaseVa’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:435:11: warning: unused variable ‘BufBasePaLow’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:434:11: warning: unused variable ‘BufBasePaHigh’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:421:15: warning: unused variable ‘pPacket’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:420:15: warning: unused variable ‘pDmaBuf’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:419:16: warning: unused variable ‘pTxRing’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:417:14: warning: unused variable ‘pRxD’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:416:14: warning: unused variable ‘pTxD’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:414:10: warning: unused variable ‘RingBaseVa’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:413:10: warning: unused variable ‘RingBasePaLow’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:412:10: warning: unused variable ‘RingBasePaHigh’
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:478:4: warning: ‘index’ may be used uninitialized in this function
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/ee_prom.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/ee_efuse.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/rt_rf.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../chips/rt30xx.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../chips/rt35xx.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/pci_main_dev.o
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../os/linux/pci_main_dev.c:321:13: warning: assignment discards qualifiers from pointer target type
  LD [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/rt3562sta.o
see include/linux/module.h for more information
  CC      /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/rt3562sta.mod.o
  LD [M]  /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/rt3562sta.ko
make[1]: uscita dalla directory "/usr/src/linux-headers-2.6.38-8-generic"
root@BIGPAVI:/home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0#

```

---

### Post by chili555 on 2011-07-29
What about it doesn't work? Did you:```
sudo make install
sudo modprobe rt3562sta
iwconfig
```

---

### Post by Ciambello on 2011-07-29
In the folder I've downloaded from the producer website there's a file called README_STA and there's some Build Informations. In the second step it says:
> define the linux kernel source include file path LINUX_SRCwhat does it mean. Also after this is says  to:
> define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -dI've just started using Ubuntu and Linux so I can't understand everything, do you know what it means?
I've restored the system, so I didn't perform the commands you said before. I'll try a new clean installation, if you can help me.

Thank you very much

---

### Post by chili555 on 2011-07-29
> define the linux kernel source include file path LINUX_SRC
what does it mean. Also after this is says to:
Quote:
define the GCC and LD of the target machine
define the compiler flags CFLAGSYou may safely ignore this. The package is written to work as is for most ordinary Linux installs.> Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.You definitely need to do this. In the folder that appeared when you extracted the tar.bz2, there is a folder called *os*; inside it is one called *linux*; inside it is a file called *config.mk*. Open it with a text editor and make the changes. Proofread, save and close the text editor.> => #>cd wpa_supplicant-x.x
=> #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
** Build for being controlled by WpaSupplicant with Ralink Driver
Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
=> #>cd wpa_supplicant-0.5.7
=> #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d You can safely ignore that; since you told it that Network Manager will do the hard work, you thankfully don't need to do all that.

Please proceed and ask more questions if you have them.

I applaud your work so far. A lot of people never consult the file conspicuously marked README and then come complain that it didn't work.

---

### Post by Ciambello on 2011-07-31
Ok so I've redone everything from scratch, reinstalled a fresh Ubuntu distro, made the changes to the config.mk file and run the commands you have outlined in your first posts. Now if I do iwconfig in terminal I see this
```

max@BIGPAVI:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated  
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```Is the driver installed and I have to configure the wireless card or something else, what do I have to do?

By the way it's really nice to find people as you on forums, usually if you are kind of a noob you're not really welcome :P

---

### Post by chili555 on 2011-07-31
I remember 120 years ago when I was a Linux noob and, frankly, I was treated badly. I determined that if I ever was able to help someone, it would be with kindness and empathy. If I couldn't answer with kindness and empathy, I wouldn't answer at all. Most of the frequent repliers here are the same. I'd like to humbly think I've led by example.

Let's have a look at:```
lsmod | grep -e rt2 -rt3
sudo modprobe rt3562sta
dmesg | grep -e rt2 -e rt3
```Some of these commands may return nothing; that's OK, sometimes a command that is accepted without warning or error tells us volumes. If there is an error, the wording of the error is informative, also.

---

### Post by Ciambello on 2011-07-31
Good ethics there. That's nice to see and that's what open source is about, I guess. Back to problems: here's what the commands gave as output:
```

max@BIGPAVI:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             819169  0 
rt2800pci              18119  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
max@BIGPAVI:~$ sudo modprobe rt3562sta
[sudo] password for max: 
max@BIGPAVI:~$ dmesg | grep -e rt2 -e rt3
[   15.107371] rt2800pci 0000:02:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.159106] Registered led device: rt2800pci-phy0::radio
[   15.159288] Registered led device: rt2800pci-phy0::assoc
[   15.159489] Registered led device: rt2800pci-phy0::quality
[   15.392764] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  681.625210] rt3562sta: module license 'unspecified' taints kernel.
[ 1984.974255] rt2800pci 0000:02:09.0: PCI INT A disabled
[ 1985.468735] rt2800pci 0000:02:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 1992.520845] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware

```As you can see the second one returned nothing and I've supposed the first command you wrote was actually ```
lsmod | grep -e rt2 -e rt3
``` I hope you can sort all this info out.

---

### Post by chili555 on 2011-07-31
> I hope you can sort all this info out.Quick as a wink, my friend. Please do:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

---

### Post by Ciambello on 2011-07-31
Looks like we are getting somewhere. Now iwconfig's output looks like this:
```

max@BIGPAVI:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
But it still doesn't find my wireless home network.

---

### Post by chili555 on 2011-07-31
> But it still doesn't find my wireless home network.Please go back to the os > linux > config.mk file and verify...double verify that you did this step:> [QUOTE]Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
You definitely need to do this. In the folder that appeared when you extracted the tar.bz2, there is a folder called os; inside it is one called linux; inside it is a file called config.mk. Open it with a text editor and make the changes. Proofread, save and close the text editor.[/QUOTE]If not, you'll need to recompile:```
sudo su
ifconfig ra0 down
rmmod -f rt3562sta
cd /home/max/Scrivania/2010_07_16_RT3062_Linux_STA_v2.4.0.0/
make clean
make
make install
modprobe rt3562sta
exit
```If it still doesn't work, please post:```
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by Ciambello on 2011-07-31
I've verified it twice, the y are there in the right place, I've also recompiled and everything. Here's what I get when i run dmesg command:
```
max@BIGPAVI:~$ dmesg | grep -e rt2 -e rt3
[   14.088071] rt3562sta: module license 'unspecified' taints kernel.
[   14.572977] rt2860 0000:02:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.240943] <==== rt28xx_init, Status=0
[   15.318484] <==== rt28xx_init, Status=0
[  164.372057] <==== rt28xx_init, Status=0
max@BIGPAVI:~
```

---

### Post by chili555 on 2011-07-31
I wonder if you have the right .dat file in the right place. Please post:```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```I wonder if we should really work on the GPL warning.

---

### Post by Ciambello on 2011-07-31
```
max@BIGPAVI:~$ cat /etc/Wireless/RT2860STA/RT2860STA.dat 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
PSP_XLINK_MODE=0
WscManufacturer=
WscModelName=
WscDeviceName=
WscModelNumber=
WscSerialNumber=
RadioOn=1
max@BIGPAVI:~$ 

```

---

### Post by chili555 on 2011-07-31
I suggest you build the later version here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592)

Change the config.mk file:> # Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

All the remainder of the file is unchanged. Then change os > linux > pci_main_dev.c to add a line about line 91:```
MODULE_DEVICE_TABLE(pci, rt2860_pci_tbl);
#ifdef CONFIG_STA_SUPPORT
#ifdef MODULE_VERSION
MODULE_VERSION(STA_DRIVER_VERSION);
[COLOR="Red"]MODULE_LICENSE("GPL");[/COLOR]
#endif
#endif // CONFIG_STA_SUPPORT //
```You are only adding the line I've highlighted. All before and after is unchanged. Proofread very carefully; spacing, spelling, punctuation, etc. are critical and must be exact. Save and close the text editor. Now do:```
sudo su
ifconfig ra0 down
rmmod -f rt3562sta
cd /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
make clean
make
make install
modprobe rt3562sta
exit
```Now is it working?

---

### Post by Ciambello on 2011-08-01
That's really sad, it's still not working. Here's the complete output from terminal, looks like the are some warnings:
```

max@BIGPAVI:~$ sudo su
[sudo] password for max: 
root@BIGPAVI:/home/max# ifconfig ra0 down
root@BIGPAVI:/home/max# rmmod -f rt3562sta
root@BIGPAVI:/home/max# cd /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
root@BIGPAVI:/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: ingresso nella directory "/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux"
rm -f ../../common/*.o
rm -f ../../common/.*.{o,cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: uscita dalla directory "/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux"
rm -rf os/linux/Makefile
root@BIGPAVI:/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make
make -C tools
make[1]: ingresso nella directory "/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools"
gcc -g bin2h.c -o bin2h
make[1]: uscita dalla directory "/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools"
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/2.6.38-10-generic/build SUBDIRS=/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: ingresso nella directory "/usr/src/linux-headers-2.6.38-10-generic"
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_md5.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.o
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1096 bytes is larger than 1024 bytes
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.o
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.c:5657:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wep.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/action.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.o
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c:1391:4: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_aes.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sync.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/eeprom.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_info.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/dfs.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/spectrum.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_channel.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_profile.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/assoc.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sync.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sanity.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/connect.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/wpa.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/ags.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.o
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:596:1: warning: the frame size of 1288 bytes is larger than 1024 bytes
In file included from /usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/uaccess.h:571:0,
                 from /usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:211,
                 from /usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/include/os/rt_linux.h:40,
                 from /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/include/rtmp_os.h:32,
                 from /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/include/rt_config.h:60,
                 from /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:28:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:3056:28:
/usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:3533:28:
/usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:5844:1: warning: the frame size of 1336 bytes is larger than 1024 bytes
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:6043:1: warning: the frame size of 1344 bytes is larger than 1024 bytes
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.o
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:1699:38: warning: initialization discards qualifiers from pointer target type
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:1736:38: warning: initialization discards qualifiers from pointer target type
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.o
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c:118:13: warning: unused variable ‘Cancelled’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c: In function ‘WriteDatThread’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c:1250:3: warning: ‘return’ with no value, in function returning non-void
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ba_action.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.o
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPResetTxRxRingMemory’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:36:13: warning: unused variable ‘num’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:119:16: warning: unused variable ‘IrqFlags’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:118:16: warning: unused variable ‘pPacket’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:117:15: warning: unused variable ‘pTxD’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:116:16: warning: unused variable ‘pTxRing’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115:19: warning: unused variable ‘j’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115:6: warning: unused variable ‘index’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:447:11: warning: unused variable ‘BufBaseVa’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:446:11: warning: unused variable ‘BufBasePaLow’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:445:11: warning: unused variable ‘BufBasePaHigh’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:432:15: warning: unused variable ‘pPacket’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:431:15: warning: unused variable ‘pDmaBuf’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:430:16: warning: unused variable ‘pTxRing’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:428:14: warning: unused variable ‘pRxD’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:427:14: warning: unused variable ‘pTxD’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:425:10: warning: unused variable ‘RingBaseVa’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:424:10: warning: unused variable ‘RingBasePaLow’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:423:10: warning: unused variable ‘RingBasePaHigh’
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:489:4: warning: ‘index’ may be used uninitialized in this function
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_prom.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_efuse.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_rf.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt30xx.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt35xx.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/pci_main_dev.o
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/pci_main_dev.c:321:13: warning: assignment discards qualifiers from pointer target type
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.o
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c: In function ‘RTMPHwCoexSwitch’:
/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c:963:2: warning: format ‘%x’ expects type ‘unsigned int’, but argument 6 has type ‘ULONG’
  CC [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt3592cb.o
  LD [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.mod.o
  LD [M]  /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
make[1]: uscita dalla directory "/usr/src/linux-headers-2.6.38-10-generic"
cp -f /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko /tftpboot
root@BIGPAVI:/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make install
make -C /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: impossibile creare la directory "/etc/Wireless": File già esistente
make[1]: ingresso nella directory "/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux"
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-10-generic
make[1]: uscita dalla directory "/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux"
root@BIGPAVI:/home/max/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# modprobe rt3562sta

```I've also tried to follow what's written in [this]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") guide but still nothing. Also  if I open /etc/network/interfaces the device isn't there, but if I got it correctly it should show up there or not?

---

### Post by chili555 on 2011-08-01
> I've also tried to follow what's written in this guide but still nothing. Also if I open /etc/network/interfaces the device isn't there, but if I got it correctly it should show up there or not?That guide is more than a little old. Changes to /etc/network/interfaces tell Network Manager that the interface, ra0, I assume, will be managed manually, not by NM. In my experience, it does so not terribly successfully. Therefor, most users should rely on NM or manual methods, but not mixed. If there are any listings for ra0 in your interfaces file, they should be removed. Of course, do not touch the loopback stanza.

The compile looks messy, but it got all the way to make install without error. I compiled the same thing last evening and my results were the same. I don't have the device, so I have no way to verify its success.

NM will disallow a wireless connection as long as you have a wired ethernet connection. With the ethernet cable detached, does NM see networks? Does it scan?```
sudo iwlist ra0 scan
```If there are no scan results, what is the error message?

Let's do a full diagnostic. We will create a text document with many tests included, zip it and attach it to your reply. Please reboot so that we have a clean slate and do:```
lspci -nn | grep 0280 > ciam.txt
lsmod | grep -e rt2 -e rt3 >> ciam.txt
sudo modprobe rt3562sta >> ciam.txt
dmesg >> ciam.txt
modinfo rt3562sta >> ciam.txt
sudo cat /var/log/syslog | grep etwork | tail -n50 >> ciam.txt
zip ciam.zip ciam.txt
```In your user directory, you will find the file ciam.zip. Please attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by Ciambello on 2011-08-01
Sorry for being a bit late, but it's national day here in Switzerland so I was a bit busy partying a little. Here's the scan result:
```

ra0       No scan results

```Nothing. Hopefully you can find something interesting in the other test results. Thanks for your precious work man!

---

### Post by chili555 on 2011-08-02
I am sorry for the delay in replying. Your case is perplexing because I have worked with this driver and chipset many times previously and never had so much trouble connecting. Perhaps the gap between the creation of the driver file and our newest kernel version has now become too great. I don't know for sure.

Your logs are filled to the brim with signs of the driver's activity, but it just never connects. One thing is quite suspicious:> <info> (ra0): driver does not support SSID scans (scan_capa 0x00).It then tries to connect from the information in the .dat file. The first thing I suggest you try is putting your details in the file /etc/Wireless/RT2860STA/RT2860STA.dat. ```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=[COLOR="Red"]CH[/COLOR]
ChannelGeography=1
SSID=[COLOR="Red"]<your_router>[/COLOR]
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=[COLOR="Red"]WPA2PSK[/COLOR]
EncrypType=[COLOR="Red"]TKIP??[/COLOR]
WPAPSK=[COLOR="Red"]<your_key>[/COLOR]
DefaultKeyID=1
<snip>
```Reboot and run another log. I have two other thoughts and rt3562sta is not included!

---

### Post by Ciambello on 2011-08-03
I've tried to put the details in /etc/Wireless/RT2860STA/RT2860STA.dat as superuser, but things reset themselves as I  reboot. The SSID keeps resetting its self to Dennis2860AP and AuthMode stays OPEN. Do I have to restore the system completely another time? By the way what did you mean previously by "run another log"?

---

### Post by chili555 on 2011-08-03
> I've tried to put the details in /etc/Wireless/RT2860STA/RT2860STA.dat as superuser, but things reset themselves as I reboot. The SSID keeps resetting its self to Dennis2860AP and AuthMode stays OPEN.Please try:```
sudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```Make your changes, proofread carefully, save and close gedit. Reboot and run:```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```Did your changes stick?> By the way what did you mean previously by "run another log"? I meant the same process as here:> Let's do a full diagnostic. We will create a text document with many tests included, zip it and attach it to your reply. Please reboot so that we have a clean slate and do:
```
lspci -nn | grep 0280 > ciam.txt
lsmod | grep -e rt2 -e rt3 >> ciam.txt
sudo modprobe rt3562sta >> ciam.txt
dmesg >> ciam.txt
modinfo rt3562sta >> ciam.txt
sudo cat /var/log/syslog | grep etwork | tail -n50 >> ciam.txt
zip ciam.zip ciam.txt

```
In your user directory, you will find the file ciam.zip. Please attach it to your reply using the paperclip tool at the top of the reply box. 

---

### Post by Ciambello on 2011-08-03
I made the changes again, but they just stick until I reboot. Attached is the new log file. This thing is really messed up!

---

### Post by chili555 on 2011-08-03
Please open Synaptic Package Manager. You have Network Manager installed. If Wicd or connman are also installed, please remove them and reboot. The other two will conflict.

I am continuing to study your logs but will be away from my computer for 2 1/2 hours or so.

---

### Post by Ciambello on 2011-08-03
I've checked the Package Manager: Network Manager is installed, while the other two aren't. Once again thanks for your support! 

:)

---

### Post by chili555 on 2011-08-03
I am having difficulty understanding how the RT2860STA.dat file gets rewritten. Please confirm that you have edited the file as sudo, saved and closed gedit; then run:```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```Are your changes still there? Then when you reboot and do nothing further except:```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```Are you saying that the file has somehow reverted to Dennis2860AP?

If so, I am stunned. If that is indeed the case, let's try another approach. Please go into the file from which you compiled the driver and change that file.```
cd Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
gedit RT2860STA.dat
```Now make the needed changes in the file. Be sure to save and close gedit. Now recompile:```
sudo su
rmmod -f rt3562sta
make clean
make
sudo make install
```Now reboot and do:```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```Are your details present?

Does your wireless connect?

---

### Post by Ciambello on 2011-08-04
> Are you saying that the file has somehow reverted to Dennis2860AP?Yes, that's what was happening. Now I've recompiled as you said and the changes stick this time, but it still doesn't connect to my network, maybe I have to change a few other things in that file?

In [this]("https://wiki.archlinux.org/index.php/Wireless_Setup#rt2860_and_rt2870") guide that I've found online it says:
> In order to get it to work, disabling the following modules in [COLOR=#005500][FONT=monospace]/etc/modprobe.d/modprobe.conf[/FONT][/COLOR] has proven to be successful: 
```

blacklist rt2800pci    
blacklist rt61pci    
blacklist rt2x00pci    
blacklist rt2800usb    
blacklist rt2800lib    
blacklist rt2x00usb    
blacklist rt2x00lib
```Do you think it can be useful in our case?

---

### Post by chili555 on 2011-08-04
> maybe I have to change a few other things in that file?You certainly should. At the least, insert the details I outlined in post #38. Unfortunately, as we have learned, you must recompile after you edit the file.> n this guide that I've found online it says:
Quote:
In order to get it to work, disabling the following modules in /etc/modprobe.d/modprobe.conf has proven to be successful:
Code:

blacklist rt2800pci    
blacklist rt61pci    
blacklist rt2x00pci    
blacklist rt2800usb    
blacklist rt2800lib    
blacklist rt2x00usb    
blacklist rt2x00lib

Do you think it can be useful in our case? No, I do not. In every case, in your logs, when you've run lsmod | grep -e rt2 -e rt3, the only module that's loaded is rt3562sta. You could certainly look at your loaded modules:```
lsmod
```Are any of the above loading?

It does no good to blacklist modules that are not loading.

---

### Post by Ciambello on 2011-08-04
```
blacklist rt2800pci    
blacklist rt61pci    
blacklist rt2x00pci    
blacklist rt2800usb    
blacklist rt2800lib    
blacklist rt2x00usb    
blacklist rt2x00lib
```There's no such module fortunately.

> You certainly should. At the least, insert the details I outlined in post #38.What options are there for parameters like EncrypType and AuthMode. How do I set the correct channel and frequency?

---

### Post by chili555 on 2011-08-04
Here is a zip of the README. The parameters are explained at the end. I notice that CH is not listed as a valid Country Code. You might try this:> "" => using default setting: 2.4 G - ch 1~11; 5G - ch 52~64, 100~140, 149~165

---

### Post by Ciambello on 2011-08-05
Good news: now when i reboot my machine, the WLan card seems trying to connect to the network, but it still doesn't work. It keeps prompting me a window asking for the network password.  Here's the output from iwconfig:
```

lo        no wireless extensions.

eth1      no wireless extensions.

ra0     Ralink STA  ESSID:"" Nickname:"RT3562STA" 
          Mode:Auto  Frequency:2.427 GHz  Access Point: 00:24:C9:66:39:50   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-68 dBm  Noise level:-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Also now in the .dat file I've set:
```

CountryCode=""
Channel=11

```is this right so?

---

### Post by chili555 on 2011-08-05
If you know your network is set to channel 11, then I believe it is. Do you have the encryption details set correctly in the .dat file? Can you please show us the config.mk file?

---

### Post by Ciambello on 2011-08-05
I've scanned the wireless card of the PC that I'm using right now to write this and its channel is set to 4, so I've changed that on the other one and recompiled. As for the encryption data it looks all correct. Attached is the config.mk file that I've compiled.

I've just found out that the device is unable to do a scan. In fact if I run ```
sudo iwlist ra0 scan
``` I get no results.

I've just run dmesg command and found out that the device is trying to scan repeatedly but with no success. I post you the output from the terminal.

---

### Post by chili555 on 2011-08-07
I have given considerable thought and a few nightmares to your situation. I am quite concerned because I have handled quite a few cases over the years involving rt3562sta and even your same pci.id 1814:3062. I am mystified as to why it doesn't spring to life. I don't understand why it doesn't scan and see your network. We see in your logs that Network Manager is looking for an access point with the same name as specified in the .dat file and can't see it. It can't see it because it can't see anything!

I don't know of anything you might have done differently in the compile process. We have both compiled this file several times; we have both re-read the README innumerable times. I have several thoughts and let's pursue them one at a time, in order. I will list them, but let's just change one thing at a time so we don't lose track of where we are:

1. Change config.mk to HAS_RFKILL_HW_SUPPORT=n and recompile.

2. Remove Network Manager and try Wicd.

3. Email Ralink and ask why it won't scan and connect. Point out the large number of warnings in compile.

4. Try ndiswrapper.

5. Dr. Chili flies to Switzerland with a new PCI wireless card in his luggage.

So, let's try #1. Please change config.mk to set HAS_RFKILL_HW_SUPPORT=**n** and recompile:```
sudo su
rmmod -f rt3562sta
make clean
make
make install
modprobe rt3562sta
exit
```Is there any improvement? What does this tell us?```
sudo cat /var/log/syslog | grep etwork | tail -n25
```

---

### Post by Ciambello on 2011-08-07
Hi Chilli,
I'm sorry for this causing you nightmares, at least you are not alone. Yesterday I stood up all night long and I've figured out a couple of things:

[LIST=1]
[*]I've set up an Ad-hoc network from another pc with functiong wireless connection and guess what the desktop pc with the Edimax pci card was able to connect to that network and ```
iwlist ra0 scan
``` returns a result, isn't that strange?
[*]If I run ```
sudo lspci -v
``` in the output it says ```
Kernel modules: rt3562sta, rt2800pci
``` Now rt3562sta is loaded in kernel but the other one not, is this correct?
[/LIST]
> So, let's try #1. Please change config.mk to set HAS_RFKILL_HW_SUPPORT=**n** and recompile:     Code:
     sudo su rmmod -f rt3562sta make clean make make install modprobe rt3562sta exit 
I've tried this, but there's still no improvement. Attached is the log file you have asked me.

> 5. Dr. Chili flies to Switzerland with a new PCI wireless card in his luggage.If you're planning a trip to Switzerland you're welcome! :)

---

### Post by chili555 on 2011-08-07
> I've set up an Ad-hoc network from another pc with functiong wireless connection and guess what the desktop pc with the Edimax pci card was able to connect to that network and
Code:

iwlist ra0 scan

returns a result, isn't that strange?It's very strange, although I feel it suggests that the driver is fundamentally capable of connecting normally. > Kernel modules: rt3562sta, rt2800pciThat suggests that both are loaded, let's check:```
lsmod | grep rt2
lsmod | grep rt3
```I thought when we checked before that only rt3562sta was loaded. Maybe not.

---

### Post by Ciambello on 2011-08-07
```
lsmod | grep rt2
lsmod | grep rt3

```only the second prompted a result, which is ```
rt3562sta 874110 1
```Is the problem more clear to you now or is the situation still as unclear as before?

---

### Post by chili555 on 2011-08-09
It's as unclear as ever. I suggest step number 2, > 2. Remove Network Manager and try Wicd.Be sure to get Wicd first, because when you remove NM, you will lose all connectivity, aside from manual methods. If you need further guidance, please post back.

---

### Post by Ciambello on 2011-08-09
How do I remove Network Manager? Also can I install Wicd from USB or do I have to get an Internet connection to install it?

---

### Post by chili555 on 2011-08-09
You can get Wicd here: [http://packages.ubuntu.com/natty/wicd](http://packages.ubuntu.com/natty/wicd)

Be sure to also get its dependencies wicd-daemon and wicd-gtk. Notice that wicd-daemon has a few dependencies itself: [http://packages.ubuntu.com/natty/wicd-daemon](http://packages.ubuntu.com/natty/wicd-daemon)

You probably have all those except python-wicd. Get them on a USB key. Drag and drop them to your desktop. Install them with:```
cd Desktop
sudo dpkg -i *.deb
```The wildcard * will install every .deb on your desktop. If any dependencies are missing, go back and get them, too.

Once Wicd is successfully installed, open Synaptic Package Manager and search for network-manager. Mark all the installed packages for removal.

As always, post back if you get stuck.

---

### Post by Ciambello on 2011-08-12
I've removed the packages from terminal, after looking at them in  Synaptic Manager, because removal kept failing from there. But is it  normal to get this message :> ldconfig deferred processing now  taking placeafter removal?

Wicd seems to work: I've rebooted and it started to scan for available networks. It found nothing so I've search for a hidden ESSID network and it found my home network. I've entered the password, but after a while Wicd prompted me a message saying the password was incorrect: the exact seam problem as with network-manager.

---

### Post by chili555 on 2011-08-12
> But is it normal to get this message :
Quote:
ldconfig deferred processing now taking place
after removal?Yes, it is.> It found nothing so I've search for a hidden ESSID network and it found my home network. I've entered the password, but after a while Wicd prompted me a message saying the password was incorrect: the exact seam problem as with network-manager. Hidden ESSIDs are always very difficult and, in many cases, impossible. I don't know whether it's the wireless driver or wpa_supplicant. Clearly it's not Network Manager. I'm not sure I know a better answer.

---

### Post by Ubunru_rookie on 2011-11-04
Hi all,
 
I am here really newcomer, so sorry for my more than limited Linux knowledge. I hope I improve soon :D
 
I have one a bit old piece of HW and I needed to connect it to WiFi network. I have purchased Edimax EW-7722IN card to do so. I have decided to have two OS side by side, Ubuntu and Win XP using the Grub multiboot. For the installation of OS I have plugged the network to on-board NIC while WiFi HW has been already put in the PC chasis. The installation of Ubuntu and Win XP passed successfully, latest patches loaded, including all drivers.
 
Then I moved the PC to a new place and trying to connect via WiFi. I realized a problem. In Win XP it works perfectly, without any problem or dropdown. But in Ubuntu, I am not able to connect at all. Moreover, I cannot see any list of available WiFi networks, even I tried to configure manually, it doesn't work.
 
I tried to follow the process described here, downloaded the drivers for Linux on Edimax, compiled, installed... and nothing changed. Even if I can see the WiFi card listed. When I reboot to Windows, it works again.
 
Any idea? :confused:
 
Thanks

---

### Post by chili555 on 2011-11-05
> **Ubunru_rookie said:**
> Hi all,
 
I am here really newcomer, so sorry for my more than limited Linux knowledge. I hope I improve soon :D
 
I have one a bit old piece of HW and I needed to connect it to WiFi network. I have purchased Edimax EW-7722IN card to do so. I have decided to have two OS side by side, Ubuntu and Win XP using the Grub multiboot. For the installation of OS I have plugged the network to on-board NIC while WiFi HW has been already put in the PC chasis. The installation of Ubuntu and Win XP passed successfully, latest patches loaded, including all drivers.
 
Then I moved the PC to a new place and trying to connect via WiFi. I realized a problem. In Win XP it works perfectly, without any problem or dropdown. But in Ubuntu, I am not able to connect at all. Moreover, I cannot see any list of available WiFi networks, even I tried to configure manually, it doesn't work.
 
I tried to follow the process described here, downloaded the drivers for Linux on Edimax, compiled, installed... and nothing changed. Even if I can see the WiFi card listed. When I reboot to Windows, it works again.
 
Any idea? :confused:
 
ThanksPlease open the terminal and run and post:```
lspci -nn | grep 0280
lsmod | grep -e rt2 -e rt3
uname -r
```Thanks.

The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Ubunru_rookie on 2011-11-06
Thank you for a quick response ;-)
 
Here is the listing:
 
[EMAIL="ubuntu@ubuntu-desktop:~$"]ubuntu@ubuntu-desktop:~$[/EMAIL] lspci -nn | grep 0280
03:06.0 Network controller [0280]: Ralink corp. Device [1814:3062]
[EMAIL="ubuntu@ubuntu-desktop:~$"]ubuntu@ubuntu-desktop:~$[/EMAIL] 

[EMAIL="ubuntu@ubuntu-desktop:~$"]ubuntu@ubuntu-desktop:~$[/EMAIL] lsmod | grep -e rt2 -e rt3
rt3562sta             819288  0 
rt2800pci              18340  0 
rt2800lib              48717  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
[EMAIL="ubuntu@ubuntu-desktop:~$"]ubuntu@ubuntu-desktop:~$[/EMAIL] 

[EMAIL="ubuntu@ubuntu-desktop:~$"]ubuntu@ubuntu-desktop:~$[/EMAIL] uname -r
3.0.0-12-generic
[EMAIL="ubuntu@ubuntu-desktop:~$"]ubuntu@ubuntu-desktop:~$[/EMAIL]

---

### Post by chili555 on 2011-11-06
Let's try a simple change:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

---

### Post by Ubunru_rookie on 2011-11-07
Well, goog news! I started to work perfectly! I can see now all the networks and I was able to connect to my network.
 
Where was the problem? It was some kind of HW blacklist? I did not understand.
 
Thank you very much for a small explanation ;-)

---

### Post by Sedum on 2011-11-07
Thank you, Thank you, Thank you!!
I am so glad I found this thread. I too have been faffing about for some time with this same problem & your 'Blacklist' code sorted it out for me as well.
Thank you again.

---

### Post by RWB36 on 2011-11-12
I have been reading through the posts on this thread as I have this WIFI card.
I have installed the card into a free pci slot, the LED's on the back do not light up, when I insert the CD, that came with the card, and get to the Linux driver folder I try to open it. When I do this I get the following response from Archive Manager
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
Where do I go from here? :confused:

---

### Post by chili555 on 2011-11-12
> **RWB36 said:**
> I have been reading through the posts on this thread as I have this WIFI card.
I have installed the card into a free pci slot, the LED's on the back do not light up, when I insert the CD, that came with the card, and get to the Linux driver folder I try to open it. When I do this I get the following response from Archive Manager
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
Where do I go from here? :confused:Our approach depends on some additional details. Please open a terminal and run and post:```
uname -r
lspci -nn | grep 0280
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by sparticus2311 on 2011-11-12
I too have to thank everyone who contributed to this thread. It solved my problem and I can finally use the wireless on my Ubuntu. I am a late adopter of Ubuntu, I have used it for about 6 hours (5 hours were spent trying to figure out how to install my wireless card) and I frankly love it!

---

### Post by RWB36 on 2011-11-13
Hi
This is the reply from the terminal
Thanks

susan@Study:~$ uname -r
2.6.32-35-generic
susan@Study:~$ lspci -nn | grep 0280
00:0a.0 Network controller [0280]: RaLink Device [1814:3062]
susan@Study:~$ lsmod | grep rt2

---

### Post by chili555 on 2011-11-13
It looks like we are going to have fun building the driver from the CD. Do you have a temporary ethernet connection so we can install some prerequisites? If so, please open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
```Now drag and drop the file from the CD to your desktop. Right-click it and select Extract Here. Now post back the name of the file you extracted. I'd like to know how old it is.

---

### Post by RWB36 on 2011-11-14
I have an ethernet connection available, and I have done the prerequisites in the terminal
This is the name of file that I have dragged and dropped onto the desktop from the included installation cd
2010_07_16_RT3062_Linux_STA_v2[1].4.0.0.tar.bz2
I selected the file, right clicked it, selected extract here, and a stop message box appeared saying

An error occurred while loading the archive.
- Command line output
bzip2: (stdin) is not a bzip2 file.
tar: child returned status 2
tar: exiting with failure status due to previous errors

No file has been extracted

---

### Post by chili555 on 2011-11-14
Please try:```
cd Desktop
```Verify that is the correct location of your file:```
ls
```If so, let's extract it:```
tar -zxvf 2010
```Press Tab and the remainder will fill in automagically. Press Enter. Did it extract? If so:```
cd DPO
```Press Tab and the remainder will fill in automagically. Press Enter. Open the file os/linux/config.mk with a text editor. Change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread, save and close the text editor. Now back to the terminal.```
sudo su
make
make install
modprobe rt3562sta
exit
```Post back if you get stuck.

---

### Post by RWB36 on 2011-11-15
The file extracted

Doing the cd DPO part did nothing

root@Study:/home/susan/Desktop# cd DPO
bash: cd: DPO: No such file or directory
root@Study:/home/susan/Desktop#

---

### Post by chili555 on 2011-11-15
You need to press Tab to let the remainder of the file name fill in before you press Enter:> ```
cd DPO
```
Press Tab and the remainder will fill in automagically. Press Enter. 

---

### Post by RWB36 on 2011-11-15
I have been pressing the tab button, no details are filled in, it does nothing

---

### Post by chili555 on 2011-11-15
Please show us:```
cd Desktop
ls
```It's got to be there!

---

### Post by praseodym on 2011-11-15
Hi,

you can try this driver, Version 2.4.1.1 (all modifications are done):

```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz)
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Just copy/paste these lines one by one. Reboot and check:
```
iwconfig
ifconfig -a
lsmod
sudo iwlist scan
rfkill list
iwlist chan
```

[COLOR="Red"]Edit[/COLOR]: Dont delete the folder, if a kernel upgrade occurs you need to compile again:
```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean 
sudo make
sudo make install 
```

---

### Post by RWB36 on 2011-11-16
Result from terminal

susan@Study:~$ cd Desktop
susan@Study:~/Desktop$ ls
2010_07_16_RT3062_Linux_STA_v2[1].4.0.0.tar.bz2  Desktop clean up  Scan info
2010_07_16_RT3062_Linux_STA_v2.4.0.0             diss 11 2 11      stuff
317                                              Gallery           Wedding
Budget.xls                                       Powerpoints
susan@Study:~/Desktop$

---

### Post by chili555 on 2011-11-16
> **RWB36 said:**
> Result from terminal

susan@Study:~$ cd Desktop
susan@Study:~/Desktop$ ls
2010_07_16_RT3062_Linux_STA_v2[1].4.0.0.tar.bz2  Desktop clean up  Scan info
2010_07_16_RT3062_Linux_STA_v2.4.0.0             diss 11 2 11      stuff
317                                              Gallery           Wedding
Budget.xls                                       Powerpoints
susan@Study:~/Desktop$Please do:```
cd Desktop
cd 2010
```Press Tab. It will automagically fill in to 2010_07_16_RT3062_Linux_STA_v2 and stop. Type a period . and press Tab and the remainder will fill in. Press Enter and continue as previously discussed.

---

### Post by RWB36 on 2011-11-16
I have done all you have said chili555, and the result is that the wifi card is now ..... working!

:KS:popcorn::KS:popcorn::KS:guitar:

Thank you!!!!!!!

---

### Post by chili555 on 2011-11-16
Awesome! I'm glad it's working. Sorry it took a couple of extra steps.

---

### Post by RustyRedbeard on 2011-12-22
Hello, I have read through this thread and have made a mistake somewhere as i have a connection briefly, but then I'm repeatedly asked to authenticate the connection and it fails to connect. I've lost track of where I am now and will have to move the pc downstairs and into everyone's way for a cable connection. which I will do if needed.
How do we find out where I got to before i nurffed it all up?
Ihave just noticed that Chili555 is offline (probably due to the fact he is from the US and the time difference n all that)
Anyone out there online?
Thanks in advance

---

### Post by chili555 on 2011-12-22
> Ihave just noticed that Chili555 is offline (probably due to the fact he is from the US and the time difference n all that)Indeed. Sometimes I sleep!

Let's do some diagnostics. Please run and post:```
lsmod | grep -e rt2 -e rt3
sudo cat /var/log/syslog | grep -e etwork -e rt3
```Thanks.

---

### Post by RustyRedbeard on 2011-12-23
Morning! thanks for replying, sorry for the delay. I've updated the os to 11.10, so clean slate! I'm gonna try again in the morning to install the driver, having given it more thought and another read through the thread. your help so far, albeit to others, has been invaluable.

---

### Post by chili555 on 2011-12-23
> **RustyRedbeard said:**
> Morning! thanks for replying, sorry for the delay. I've updated the os to 11.10, so clean slate! I'm gonna try again in the morning to install the driver, having given it more thought and another read through the thread. your help so far, albeit to others, has been invaluable.No problem. I look forward to your report.

---

### Post by alexandru.bujor on 2011-12-26
Hello,

Great topic, as I have recently bought one Edimax EW-7722 adapter and this thread was very useful for configuring it. 
Few remarks:
- note that the driver does not implement all iwconfig's options
- use iwpriv and take a look at iwpriv_usage file from the driver's folder
- the card works well with a 10.04 system, x86, 2.6.32-33-generic-pae kernel

However, simply configuring the device to connect to an AP is not enough for me. I want to use the Edimax card as an Access Point for my other devices. Has anyone tried this? I am afraid that the driver does not support the Master mode of the iwconfig options, but maybe there is a workaround. 

Any ideas for transforming this device into an A.P.?

Thanks,
Alex

---

### Post by chipbuster on 2011-12-29
Chili. I love you. Took me two whole days to get this sucker working, but I finally found the right combination of tricks. I had to download the 3062pci driver from RaLink's site at 

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

and do the thing with inserting the GPL license in to file in os/linux/(something)

I'm running the 3.0.0-14-generic kernel right now, and it didn't power up until I blacklisted the rt2800pci module. Does anyone know why modprobe -r rt2800pci doesn't accomplish the same thing?

EDIT: hmmmmm...looks like I suck at using forum features. Edited for link

---

### Post by praseodym on 2011-12-30
Because the module rt2800pci also contains the device ID like the compiled driver. "On-the-fly" you need to "modprobe -r" both modules and reload the new one. But blacklisting is the way

---

### Post by Indigo340 on 2012-01-05
[SIZE=2]Thank you for this thread, it really helped me understand my problem and to get it fixed. The questions and answers were clearly worded, the responses were patient and understanding and although  I am not very experienced it gave me the confidence to work through my problems and finally correctly diagnose and fix the problem. It was exactly the same as others reported which was a need to blacklist a certain driver.
Thanks again
and again 
and again

Ian [/SIZE] :D :KS :D :KS :D :KS :D :popcorn:

---

### Post by alexandru.bujor on 2012-01-06
Hi,

I have transformed the card into an AP using the latest drivers from this [ 1 ] webpage (the bleeding-edge version). The driver released by Ralink was included and improved in the newer versions of this project and now the device works fine for me. 
The card is named 'wlan0' and can enter Master mode also when configured by hostapd.

[ 1 ] - [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

---

### Post by aquila06 on 2012-02-11
Hi,

I also have problems with the EW-7722IN on a Lucid 10.04LTS (kernel 2.6.32-38-generic) 64-bits. Network manager does find my wifi connection, connects to the  box, but the signal strength varies a lot, and today I got disconnected ten times (at least). I tested a 6-year old laptop at the same position and the signal strength remains constant (my office room is 10 meters from the box, so it shouldn't be a problem). I have noticed this problem since the update of the kernel a few days ago, and I was wondering if my configuration was fine. So here is the result of iwconfig  ```
  
lo          no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"glaucidium"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 38:60:77:0C:17:71   
          Bit Rate=130 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=44/100  Signal level:-66 dBm  Noise level:-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```And the result of lspci -nn | grep 0280  ```
07:01.0 Network controller [0280]: RaLink Device [1814:3062]

```

Any other checks that I could make to be sure that I have correctly installed the driver (I took the one posted by [praseodym]("http://ubuntuforums.org/member.php?u=1411497"))

I am still wondering if it's just that the bow stands at the upper floor or if it is a driver problem...

Thank you in advance for any hint

Alex

---

### Post by praseodym on 2012-02-11
Please show

```
lsmod
sudo iwlist scan
dmesg | egrep 'rt3|rt2'
```
Did you compile again after the kernel upgrade? Which encryption mode do you use (WPA/WPA2)?

---

### Post by mogators on 2012-02-11
> **chili555 said:**
> When you compiled it, did you do this step:
3> In os/linux/config.mk

** Build for being controlled by NetworkManager or wpa_supplicant wext functions
Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. 

Please check the file. If not, please change it and re-compile:```
cd Desktop/2010_07_16_RT3062_Linux_STA_v2.4.0.0 
sudo su
make clean
make
make install
exit
```Reboot and give us your report.

chili555, just came across this post and this was the key to getting my EW-7722In working! 

Here is the rundown of what I did with the EW-7722.
11.10 - Downloaded the drivers from Ralink (DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.t gz) and unzipped. In the unzipped files, edited os/linux/config.mk: set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. This was key as before I did this, I could not connect to my wireless. The readme file that came with the download had other stuff to edit, but these two lines are the only ones I changed.
sudo su
make clean
make
make install
echo rt3562sta >> /etc/modules
exit

edit /etc/modprobe.d/blacklist.conf and added:
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

rebooted and had wireless!

For 10.4LTS:
Same as above but did not need to edit blacklist.conf. I guess the rt2x00 module is not already in the 2.6 kernel.

Hopefully this will help someone else down the line.

---

### Post by elnene68 on 2012-03-10
hola, mis intententos en instalar esta tarjeta han sido en vano.Mí equipo es un dell optiplex 330,placa base dell inc modelo 0kp561,procesador intel pentiun dual cpu E2180.2GHZ.Tarjeta de red controladora de red gigabit broadcom netxtreme 57xx(802.3).Edimax 802.11n.Utilizo ubuntu 11.10
Realice los cambios en el archivo config.mk y make install pero no obtuve resultados, necesitaria ayuda, soy nuevo en linux.gracias

---

### Post by chili555 on 2012-03-10
> **elnene68 said:**
> hola, mis intententos en instalar esta tarjeta han sido en vano.Mí equipo es un dell optiplex 330,placa base dell inc modelo 0kp561,procesador intel pentiun dual cpu E2180.2GHZ.Tarjeta de red controladora de red gigabit broadcom netxtreme 57xx(802.3).Edimax 802.11n.Utilizo ubuntu 11.10
Realice los cambios en el archivo config.mk y make install pero no obtuve resultados, necesitaria ayuda, soy nuevo en linux.graciasYou might have better luck here: [http://www.ubuntu-es.org/forum](http://www.ubuntu-es.org/forum)

---

### Post by elnene68 on 2012-03-10
> **chili555 said:**
> You might have better luck here: [http://www.ubuntu-es.org/forum](http://www.ubuntu-es.org/forum)
gracias por tu sugerencia, pero ya lo intente en ese foro y no obtuve contestación.Un saludo

---

### Post by chili555 on 2012-03-10
> **elnene68 said:**
> gracias por tu sugerencia, pero ya lo intente en ese foro y no obtuve contestación.Un saludoIf you can read my English, I will be glad to try. If you'd like to proceed, please open a terminal and run and post:```
lsusb
sudo modprobe rt3562sta
iwconfig
```Thanks...or is it gracias?

---

### Post by elnene68 on 2012-03-10
> **chili555 said:**
> If you can read my English, I will be glad to try. If you'd like to proceed, please open a terminal and run and post:```
lsusb
sudo modprobe rt3562sta
iwconfig
```Thanks...or is it gracias?
lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0566:3004 Monterey International Corp. Genius KB-29E
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
sudo modprobe rt3562sta:
FATAL: Module rt3562sta not found.
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2012-03-10
Since rt3562sta is not found, the compile didn't go well. > Realice los cambios en el archivo config.mk y make install Can you please try again:```
cd Desktop/rt3562files  <--or wherever you extracted the files
sudo su
make
make install
exit
```Post the errors here.

I am sorry, I meant to ask for this and not *lsusb*:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by elnene68 on 2012-03-10
salida lspci -nn | grep 0280

03:02.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]

---

### Post by chili555 on 2012-03-10
> Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]rt3562sta is correct for this device. Please show us what went wrong with make and make install.

---

### Post by elnene68 on 2012-03-10
No se si lo conseguiremos, pero agradezco tu esfuerzo.
Según la traducción me pides que te mande los errores de make y make install.
root@david-pc:/home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0# make
make -C tools
make[1]: se ingresa al directorio «/home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/tools»
gcc -g bin2h.c -o bin2h
make[1]: se sale del directorio «/home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/tools»
/home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/3.0.0-16-generic/build SUBDIRS=/home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.0.0-16-generic»
  CC [M]  /home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux/rt3562sta.ko
make[1]: se sale del directorio «/usr/src/linux-headers-3.0.0-16-generic»
root@david-pc:/home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0# make install
make -C /home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux -f Makefile.6 install
mkdir: no se puede crear el directorio «/etc/Wireless»: El archivo ya existe
make[1]: se ingresa al directorio «/home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux»
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.0.0-16-generic
make[1]: se sale del directorio «/home/david/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0/os/linux»

---

### Post by chili555 on 2012-03-10
It doesn't look like there are *any* errors. Now does this look better?```
sudo modprobe rt3562sta
iwconfig
```

---

### Post by elnene68 on 2012-03-10
david@david-pc:~/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0$ sudo modprobe rt3562sta
david@david-pc:~/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2012-03-10
> ra0 Ralink STA ESSID:"" Nickname:"RT3562STA"
Mode:Auto Frequency=2.412 GHz Access Point: Not-Associated
Bit Rate:1 Mb/s
RTS thrff Fragment thrff
Link Quality=10/100 Signal level:0 dBm Noise level:0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0Now that you have a wireless interface, when you click the Network Manager icon, do you see your network? Does it scan?```
sudo iwlist ra0 scan
```

---

### Post by elnene68 on 2012-03-10
efectivamente veo mi red, pero puede ser que tenga mal configurada lo datos en ella.
la salida del comando:
david@david-pc:~/Escritorio/2010_07_16_RT3062_Linux_STA_v2.4.0.0$ sudo iwlist scan RA0
iwlist: unknown command `RA0' (check 'iwlist --help').

---

### Post by elnene68 on 2012-03-10
perdon habia escrito mal el comando.
la salida del escaneo es un exito. 
Necesitas que te ponga la salida del comando?

---

### Post by elnene68 on 2012-03-10
ya tengo conexion inalambrica. 
Te doy muchas gracias por tu paciencia.
por favor dime si hace falta hacer algo más?

---

### Post by chili555 on 2012-03-10
> la salida del escaneo es un exito. Excellent! If it scans and sees networks, then Network Manager ought to see your network and connect. Does it?> Necesitas que te ponga la salida del comando? No. Just knowing it scans is enough; thanks.

---

### Post by elnene68 on 2012-03-10
perdona que te moleste otra vez, pero es que he reiniciado la pc y ya no me aparecen las redes en manager. 
 
pongo el comando sudo iwlist ra0 scan y la salida es:


ra0       Interface doesn't support scanning.

---

### Post by chili555 on 2012-03-10
> **elnene68 said:**
> perdona que te moleste otra vez, pero es que he reiniciado la pc y ya no me aparecen las redes en manager. 
 
pongo el comando sudo iwlist ra0 scan y la salida es:


ra0       Interface doesn't support scanning.After you rebooted, did the driver rt3562sta load as expected?```
lsmod | grep rt3
```If it is not loaded, load it manually:```
sudo modprobe rt3562sta
```Does that bring your wireless to life? If so, let's load it automatically:```
sudo su
echo rt3562sta >> /etc/modules
exit
```

---

### Post by elnene68 on 2012-03-10
Realizados los pasos me vuelven a salir las redes inalambricas.
reinicio la pc? o primero tenemos que hacer algo màs.

---

### Post by chili555 on 2012-03-10
> **elnene68 said:**
> Realizados los pasos me vuelven a salir las redes inalambricas.
reinicio la pc? o primero tenemos que hacer algo màs.You certainly could test it by rebooting but I'm confident it's fixed. Now that you see wireless networks, does it connect as expected?

---

### Post by elnene68 on 2012-03-10
He reiniciado la pc y funciona perfectamente.
Te vuelvo a dar las GRACIAS y un saludo, sois formidables.

---

### Post by chili555 on 2012-03-10
> **elnene68 said:**
> He reiniciado la pc y funciona perfectamente.
Te vuelvo a dar las GRACIAS y un saludo, sois formidables.I was very glad to help and I'm glad it's working.

Whenever a newer kernel version, also known as linux image, is installed by Update Manager, you will need to rebuild the driver for the newer kernel. It's the same as before with one additional step:```
cd Desktop/rt3562directory  <--or wherever you extracted the files
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe -rv rt3562sta
modprobe rt3562sta
exit
```You might save these instructions for that day.

Have fun!

---

### Post by Graham C Williams on 2012-07-04
Hi Chili.

Working through your suggestions here and now my wireless system is working.
Very Big Thanks.

Graham.

---

### Post by superkeest on 2012-07-12
Hello Chilli, thanks to this thread i was able to get up and running with this card on kubuntu 12.04 

My problem was that the card was scanning and recognizing networks, but it could not obtain an IP.  I followed the directions and downloaded the driver, made the modifications to the config, and compiled and installed. Still wasnt working, then i noticed that it was using module:rt2800pci

So i created /etc/modprobe.d/modprobe.conf  and added the following lines:

```
blacklist rt2800pci    
blacklist rt61pci    
blacklist rt2x00pci    
blacklist rt2800usb    
blacklist rt2800lib    
blacklist rt2x00usb    
blacklist rt2x00lib
```

Im not sure if all of that was vital, but the first line for sure, once i did that and rebooted, it worked right away.

THANKS ALOT.

---

