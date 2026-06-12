---
title: "Problem with Ralink 3060 after upgrade from Ubuntu 10.10 to 11.04"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by gina5 on 2012-05-28
I have a D-Link DWA-525 wireless network that worked fine in Ubuntu 10.10.  I followed the instructions on the following link to compile the driver and load it as a kernel module and everything worked fine.
 
[http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/](http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/)

However, a few days back I upgraded to 11.04 and after that I was unable to repeat the same procedure successfully.  After downloading the system headers as suggested on some sites, I could compile the driver. "make && make install" succeed.  But when I try to load the driver using "modprobe rt3562sta", I get the error 

FATAL: Error inserting rt3562sta (/lib/modules/2.6.38-15-generic/kernel/drivers/net/wireless/rt3562sta.ko): Invalid module format

From reading online I gather I may not be using the same headers that are used to compile the kernel.  But how do I check this?  'uname -r' says 2.6.38-15-generic, and the make process seems to be using headers from /usr/src/linux-headers-2.6.38-15-generic, so this seems to be correct.  

Pls note that the headers did not come with the kernel upgrade, and I had to install them later using apt-get.  Could I still be using the wrong headers?  Pls help!

Thanks a lot.

ps: my upgrade did not exactly go very smooothly so I seem to have several versions (including -pae variants) of the kernel compiled. But the one running fine is, as per uname, 2.6.38-15-generic.

---

### Post by chili555 on 2012-05-28
First of all, I think I'd do some housekeeping. Do you want and need pae kernels? [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

If so, I suggest you reboot into a pae kernel and go into Synaptic and remove the non-pae kernels and headers. If, for some reason, you can't boot into or use pae, I'd remove those.

Next, let's address headers. There is a package linux-headers-generic or linux-headers-generic-pae that will make sure the correct headers matching your running kernel are installed. Please install whichever is appropriate.

Now, once you're sure the correct headers are installed, let's try to troubleshoot your compile:```
cd Desktop/RT3572  [COLOR="Red"]<--or wherever you extracted the driver[/COLOR]
sudo su
make clean
make
make install
modprobe rt3572sta
exit
```Did the module load correctly? Were there any alarming warnings? Post them here and we'll take a look.

---

### Post by gina5 on 2012-05-29
Thanks for the help.  Here is an update when I followed (I hope!) your instructions. Unfortunately I still get the "[COLOR="red"]Invalid module format[/COLOR]" error :(

----


First I uninstalled all linux-headers-* packages in synaptic, as well all the kernel builds that I am not using.  This includes a couple of -pae builds---reading the above site tell me I do not need pae.  I have 8GB RAM visible on an i7 processor, so I assume I am running a true 64 bit OS.  uname -arsv says:

[COLOR="Red"]Linux linux-server 2.6.38-15-generic #59-Ubuntu SMP Fri Apr 27 16:03:32 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]

The I tried to install in synaptic linux-headers-generic, which seems to depend on linux-headers-2.6.38-15-generic, which in turn depens on linux-headers-2.6.38-15, so I installed all three.

Then I did sudo su followed by make clean etc.  But still got the same error on trying to load the compiled module.  Here is the log:

-----------------------------------------------------------------

root@linux-server:/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
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

make[1]: Leaving directory `/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf os/linux/Makefile
root@linux-server:/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make
make -C tools
make[1]: Entering directory `/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/2.6.38-15-generic/build SUBDIRS=/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-15-generic'
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_md5.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.o
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1096 bytes is larger than 1024 bytes
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_arc4.o

CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.o
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.c:5657:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wep.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/action.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.o
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c:1391:4: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_aes.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sync.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/eeprom.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_info.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/dfs.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/spectrum.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_channel.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_profile.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/assoc.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sync.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sanity.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/connect.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/wpa.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/ags.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ba_action.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.o
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPResetTxRxRingMemory’:
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:36:13: warning: unused variable ‘num’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:119:16: warning: unused variable ‘IrqFlags’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:118:16: warning: unused variable ‘pPacket’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:117:15: warning: unused variable ‘pTxD’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:116:16: warning: unused variable ‘pTxRing’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115:19: warning: unused variable ‘j’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115:6: warning: unused variable ‘index’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:447:11: warning: unused variable ‘BufBaseVa’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:446:11: warning: unused variable ‘BufBasePaLow’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:445:11: warning: unused variable ‘BufBasePaHigh’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:432:15: warning: unused variable ‘pPacket’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:431:15: warning: unused variable ‘pDmaBuf’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:430:16: warning: unused variable ‘pTxRing’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:428:14: warning: unused variable ‘pRxD’

/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:427:14: warning: unused variable ‘pTxD’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:425:10: warning: unused variable ‘RingBaseVa’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:424:10: warning: unused variable ‘RingBasePaLow’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:423:10: warning: unused variable ‘RingBasePaHigh’
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:489:4: warning: ‘index’ may be used uninitialized in this function
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_prom.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_efuse.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_rf.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt30xx.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt35xx.o
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.o
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c: In function ‘RTMPHwCoexSwitch’:
/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c:963:2: warning: format ‘%x’ expects type ‘unsigned int’, but argument 6 has type ‘ULONG’
  CC [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt3592cb.o
  LD [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
see include/linux/module.h for more information

  LD [M]  /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-15-generic'
cp -f /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko /tftpboot
root@linux-server:/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make install
make -C /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38-15-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/2.6.38-15-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-15-generic
make[1]: Leaving directory `/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
root@linux-server:/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# modprobe rt3562sta
FATAL: Error inserting rt3562sta (/lib/modules/2.6.38-15-generic/kernel/drivers/net/wireless/rt3562sta.ko): Invalid module format
root@linux-server:/home/gina/wireless/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217#

---

### Post by chili555 on 2012-05-29
Ah ha!! I think the 'invalid format' may be that the module isn't suitable for 64-bit. I have a copy of the driver in the exact same version. I built it just now, with as many or more alarming warnings and it at least loads without error on my 32-bit pae system. Maybe there is another way to get it going. So we have some additional details about the card, please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by gina5 on 2012-05-30
> **chili555 said:**
> Ah ha!! I think the 'invalid format' may be that the module isn't suitable for 64-bit. I have a copy of the driver in the exact same version. I built it just now, with as many or more alarming warnings and it at least loads without error on my 32-bit pae system. Maybe there is another way to get it going. So we have some additional details about the card, please run and post:```
lspci -nn | grep 0280
```Thanks.


chili555, 

You are right!  It was a 32-bit vs 64-bit issue, just not sure exactly how to fix the headers right.  I realized my usb_storage driver also would not install for the same reason.  I finally backed up my data and did a clean install, and both wireless and usb are working now.

Thanks!

---

