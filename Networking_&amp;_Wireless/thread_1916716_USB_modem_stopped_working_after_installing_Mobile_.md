---
title: "USB modem stopped working after installing Mobile Partner"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by Jerph on 2012-01-28
Hi,
I have 3G USB modem huawei e173 and I'm using xubuntu 11.10 kernel 3.0.0-15.
The modem worked automatically on fresh xubuntu installation. I could connect to the internet using network manager.
Problem started after I installed this [http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html]("http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html") version of Mobile Partner.

Modem huawei e173 has two modes:
a) It behaves like a CD - it's for windows to install the Mobile Partner program
b) Modem mode

After installation of Mobile Partner it started to behave like a CD after plug in. But after short time Mobile Partner started up and changed the mode to modem.
I can also see it using lsusb command.
```
Bus 001 Device 003: ID 12d1:1c0b Huawei Technologies Co., Ltd. 

```
changes to
```
Bus 001 Device 003: ID 12d1:1c08 Huawei Technologies Co., Ltd.

```

I didn't like the program ( it is really annoing ) so I uninstalled it. And now the modem works in CD mode after plug in :( and I can't see it in network manager.
I tried the modem using xubuntu live USB and it worked perfectly so the problem must be in computer.

Here is the output from installation of Mobile Partner:
```

usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u
            user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] file ...
There is no sudo command in your system,you'd better run the software by root
Press any key to continue...

old path =/usr/local/Movistar_3.5G/driver
INSTALL_PATH is set 
path=/usr/local/Movistar_3.5G
cp: cannot copy a directory, `/usr/local/Movistar_3.5G', into itself, `/usr/local/Movistar_3.5G/Movistar_3.5G'
INSTALL_PATH=/usr/local/Movistar_3.5G
/usr/local/Movistar_3.5G/driver/ndis_driver
Usage: modinfo [-0][-F field][-k kernelversion][-b basedir]  module...
 Prints out the information about one or more module(s).
 If a fieldname is given, just print out that field (or nothing if not found).
 Otherwise, print all information out in a readable form
 If -0 is given, separate with nul, not newline.
 If -b is given, use an image of the module tree.
ERROR: Removing 'cdc_ether': No such file or directory
ERROR: Removing 'usbnet': No such file or directory
ERROR: Removing 'hw_cdc_driver': No such file or directory
make -C src/ clean
make[1]: Entering directory `/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/add_header.sh  "clean" "/lib/modules/3.0.0-15-generic/build/include/linux/usb"
rmmod -f hw_cdc_driver
ERROR: Removing 'hw_cdc_driver': No such file or directory
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src'
make: *** [clean] Error 2
make -C src/ modules
make[1]: Entering directory `/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src'
#/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/add_header.sh  "modules" "/lib/modules/3.0.0-15-generic/build/include/linux/usb"
make -C /lib/modules/3.0.0-15-generic/build SUBDIRS=/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-15-generic'
  CC [M]  /usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: In function ‘rx_tlp_parse’:
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:1084:7: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: In function ‘cdc_ncm_config’:
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:2035:24: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:2036:3: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:2036:3: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:2040:21: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: In function ‘hw_cdc_probe’:
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:3021:26: warning: ‘ctx’ may be used uninitialized in this function [-Wuninitialized]
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:2794:21: note: ‘ctx’ was declared here
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.mod.o
  LD [M]  /usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/hw_cdc_driver.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-15-generic'
strip --strip-debug hw_cdc_driver.o
make[1]: Leaving directory `/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src'
make -C src/ install
make[1]: Entering directory `/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src'
#install -m 744 -c hw_cdc_driver.o /lib/modules/3.0.0-15-generic/kernel/drivers/usb/net
#depmod -a
#modprobe hw_cdc_driver
/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src/add_header.sh  "install"
modprobe hw_cdc_driver
make[1]: Leaving directory `/usr/local/Movistar_3.5G/driver/ndis_driver/ndis_src/src'

The Linux NDIS driver is installed successfully.
have usb_modeswitch rules to HUAWEI DataCard: COUNT=0
AUTORUNPATH=/home/jergus/.config/autostart
AUTORUNPATH=/root/.config/autostart
ADDRUNLEVEL=/etc/rc2.d
`/etc/rc2.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc2.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc5.d
`/etc/rc5.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc5.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc4.d
`/etc/rc4.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc4.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc3.d
`/etc/rc3.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc3.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
./install: line 516: ./hw_pppd/sbin/install_pppd: No such file or directory
                                                                                                          [ done ] 

Finished, press any key to exit

```

I tried to reinstall kernel using synaptic but it didn't help. I  also tried to change mode using usb_modeswitch but I it did't work.
Please help. Thanks

---

### Post by manish671 on 2012-01-29
[SIZE=2]I have huawei UMG1831. I also didn't liked that version of mobile partner U mentioned and I was having tough time to connect using Network Manager. However latter I found better stable version 21.003.28.711. It can be downloaded from [http://support.videotron.com/_media/document/UTPS21.003.28.05.711_MAC21.003.28.05.711_LNX21.003.28.00.711.exe](http://support.videotron.com/_media/document/UTPS21.003.28.05.711_MAC21.003.28.05.711_LNX21.003.28.00.711.exe).

This file includes Mobile Partner for all Linux-Windows-MAC.  Remember that if U run this exe file from Windows it will replace the dashboard of modem.

However here is one issue with this in Ubuntu. During installation it will give message that no sudo command in system and should be run as root. more detail U can see here [http://ubuntuforums.org/showthread.php?t=1916533](http://ubuntuforums.org/showthread.php?t=1916533) 
[/SIZE]

---

### Post by dwilkie on 2012-07-19
I just had the exact same problem. Somewhere in the installation it must change the following line in /lib/udev/rules.d/40-usb_modeswitch.rules:

ATTRS{idVendor}=="Huawei", ATTRS{idProduct}=="1446", RUN+="usb_modeswitch '%b/%k'"

This line **should** read:

ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="usb_modeswitch '%b/%k'"

Once I changed that back and plugged in the modem again it was recognized in the network manager. Just to make sure it didn't the installation didn't screw anything else up, I ran:

sudo apt-get purge usb-modeswitch-data
sudo apt-get install usb-modeswitch-data

---

