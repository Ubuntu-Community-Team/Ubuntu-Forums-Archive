---
title: "Linksys dual band wireless NUSB adapter not working on 10.04"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by Ons308 on 2010-07-30
Hello,

I'm not a new user to ubuntu but I'm stuck with a driver issue on a wireless adapter upgrade for ubuntu 10.04 lucid lynx. I'm running an acer aspire am1201-e1622a with amd athlon x2 64 bit processor, however i'm only running the 32 bit version of lucid lynx.  The following are a few outputs of some commands that might assist in finding the proper driver. Before though i will tell you what i have done.

I have installed a few different drivers from windows wireless driver installer such as the xp and vista 32 and 64 bit versions with no success in the computer actually recognizing that i have a wireless adapter installed. The windows wireless driver installer said that hardware was present but i was unable to scan for networks or even see that i had a choice to do that. This meaning that it didn't show i had wireless capabilities in my network manager.  i tested this with gnome network manager which is the default manager for 10.04 and also with wicd with no success.

Following these tests i attempted to install a driver from source following the instructions on another forum. This allowed me to manually turn on the wireless adapter but i was still unable to find any networks. This meaning that wicd was able to see that i had a wireless adapter installed but it for some reason was unable to see any wireless networks around. I'm 100% sure my router is in range and that it is configured correctly. I have 5 other computers connect to this router along with some of them being ubuntu.


lsusb

    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 003: ID 1737:0079 Linksys 
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


iwconfig

    lo        no wireless extensions.

    eth0      no wireless extensions.




- Just to make sure everything is clear I'm running 10.04 lucid lynx 32 bit on my acer aspire am1201-e1622a with amd athlon x2 64 bit processor 3gb ram.

- I'm using a Linksys Dual-band Wireless-N USB Adapter WUSB600N V2



Many Thanks

---

### Post by attractedtofire on 2010-08-04
Hi Ons308,

follow the instructions here to get your WUSB600N working properly (without the need of using ndiswrapper): [http://ubuntuforums.org/showpost.php?p=9534492&postcount=34](http://ubuntuforums.org/showpost.php?p=9534492&postcount=34)

Cheers,
a.

---

### Post by Ons308 on 2010-08-12
I followed the below steps but still nothing. There is an error when running the "sudo sh ~/Documents/rt2870_install.sh" command in the terminal

The following is the error i get when installing the source code from the script.

make -C tools
make[1]: Entering directory `/usr/src/RT2870/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/usr/src/RT2870/tools'
/usr/src/RT2870/tools/bin2h
cp -f os/linux/Makefile.6 /usr/src/RT2870/os/linux/Makefile
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/usr/src/RT2870/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /usr/src/RT2870/os/linux/../../common/rtmp_mcu.o
  LD [M]  /usr/src/RT2870/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /usr/src/RT2870/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make -C /usr/src/RT2870/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/usr/src/RT2870/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /usr/src/RT2870/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-24-generic
make[1]: Leaving directory `/usr/src/RT2870/os/linux'
wlan0: ERROR while getting interface flags: No such device


That is the entire output of the command when run. This output is the second time running the script. I originally did all the steps and then ran the script and it got errors similar to the one above but it also listed a directory not found. Following rebooting the computer, and wireless still not working i ran the script again and the above is the entire output.

Please help as to what i'm doing wrong, or how to fix this flag error.

---

