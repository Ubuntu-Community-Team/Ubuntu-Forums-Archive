---
title: "Realtech rtl8192_8188CU install problem"
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by kobudo on 2012-09-12
I'm trying to compile a driver for a new Asus USB-N13 network adapter. The driver/version provided with the hardware is rtl8192_8188CU_linux_v3.0.2164.20110715.tar.gz, I tried installing with the shell script provided by Asus, but got an error message. Then I tried doing it in terminal, and came across this error at the end (seemingly important bits in red):

```
mike@mike-computer:~/Desktop/Wifi/driver/rtl8192_8188CU_linux_v3.0.2164.20110715$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-30-generic-pae/build M=/home/mike/Desktop/Wifi/driver/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-30-generic-pae'
  CC [M]  /home/mike/Desktop/Wifi/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o
In file included from /home/mike/Desktop/Wifi/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:24:0:
/home/mike/Desktop/Wifi/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h:49:29: [COLOR="Red"]fatal error: linux/smp_lock.h: No such file or directory[/COLOR]
compilation terminated.
make[2]: *** [/home/mike/Desktop/Wifi/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/mike/Desktop/Wifi/driver/rtl8192_8188CU_linux_v3.0.2164.20110715] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-30-generic-pae'
make: *** [modules] Error 2
mike@mike-computer:~/Desktop/Wifi/driver/rtl8192_8188CU_linux_v3.0.2164.20110715$ 

```

I really don't know how to fix this... I am incredibly new to Linux, and learning as I go. I assume this is a file or directory that should have been installed during the "make" process, but I don't know how to fix it. I have been able to figure out that it refers to an outdated something or other, but that's about it.

**[COLOR="Blue"]EDIT 1[/COLOR]**

I found an updated Realtek driver and was able to install it by running the included shell script. Unfortunately, the card will still do what it's done since I plugged it in -- continuously attempt to connect and fail, asking for a new wpa/wpa2 password every few minutes. I have double-checked the password, with no positive results.

**[COLOR="Blue"]EDIT 2[/COLOR]**

I am still unable to connect with the card. looking at ```
lsmod |grep rt
```, I get this result:
```
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48805  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  6 rtl8192cu,rtl8192c_common,rtlwifi,rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178679  3 rtlwifi,rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
parport_pc             32114  1 
parport                40930  3 ppdev,parport_pc,lp
```

my lsusb looks like this:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 001 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90

```

I have followed the code below using the instructions found in [this thread]("http://ubuntuforums.org/showthread.php?t=1964197"):

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.3.23192
sudo dkms build -m rtl8192cu -v 3.3.23192
sudo dkms install -m rtl8192cu -v 3.3.23192
```

When I entered the last line above, here was the resulting output in terminal:

```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all.............
cleaning build area....

DKMS: build completed.
mike@mike-computer:~$ sudo dkms install -m rtl8192cu -v 3.3.23192

8192cu:
Running module version sanity check.
Error! Module version v3.3.2_3192.20120103 for 8192cu.ko
is not newer than what is already found in kernel 3.2.0-30-generic-pae (v3.4.4_xxxx.20120730).
You may override by specifying --force.

depmod.......

DKMS: install completed.

```

Would I be correct in my guess that the error above is not really a problem? It just kept the newer version of the module in the kernel. Also, I realize I still need to blacklist the driver for my Ralink RT2760 chipset driver. Would I be correct in assuming it's rt2800pci from the lsmod output listed above?

**[COLOR="Blue"]EDIT 3[/COLOR]**

I just noticed this in sudo lshw -C network:

```
 *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan1
       serial: 54:04:a6:df:16:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-30-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

```

Should I not have firmware, or is this because it won't display the firmware for a USB device?

---

### Post by kobudo on 2012-09-13
Arrrgh... I finally found the driver for my old not-really-working pci card (it was the RT2800pci driver I thought it was), and blacklisted it. No luck. Another strange thing, the Network Manager was listing my router as hidden before the last restart, now it's showing up in the lists for both cards. Other than that, I'm still at square one with this USB adapter. :(

---

### Post by mikewhatever on 2012-09-13
That module you are trying to load is older then the built it one. Try the [latest version]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true") from realtek instead.

---

### Post by kobudo on 2012-09-13
Thanks you very much! I downloaded the newest driver, and ran their shell script. At the end of the install process, I got the following error messages:

```
Compile make driver ok!!
##################################################
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.2.0-30-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-30-generic-pae

```

What would be the best way of correcting those errors? Delete the driver, and try installing again? If so, I don't really know how to go about that in terminal yet...

---

### Post by mikewhatever on 2012-09-13
You have to blacklist the built in rtl8192cu module. The Linux kernel has a built in driver wich doesn't work (it's actually shown in your lsmod output), but it is loaded, so the installation script can't insert the compiled module. Blacklisting will prevent the built in, non-working module from autoloading. To do that, either run
```
echo "blacklist rtl8192cu | sudo tee -a /etc/modprobe.d/blacklist.conf"
```

or gksudo gedit /etc/modprobe.d/blacklist.conf

and add 'blacklist rtl8192cu' at the end.

Reboot when done, and re-run the installation script.

I've filed a [bug report]("https://bugs.launchpad.net/linux/+bug/852190"), vote it up if you can.

---

### Post by kobudo on 2012-09-13
GEdited the modprobe.d/blacklist file, re-started, ran the script again, and all is well. Thank you very much for your help! I kinda feel a bit bone-headed messing with a year-old "update" for a few hours, but I learned something. I will go try to vote up that bug report. Solved!

---

### Post by kobudo on 2012-09-24
Annnd I installed the updates today, and it's like the USB stick isn't even plugged in. It still shows up as connected in terminal when I do a lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 001 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90

```

but the drivers aren't listed when I enter lsmod |grep rt:

```
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48805  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
parport_pc             32114  1 
parport                40930  3 ppdev,lp,parport_pc

```

The native drivers are still blacklisted. I guess it's time to re-download and re-install the driver...

EDIT: re-installing the driver worked. I wonder why the update would kill off a perfectly good driver?

---

### Post by mikewhatever on 2012-09-28
That must have been a kernel update. Any locally built module must be rebuilt for new kernels. It's a bit of a hassle, but at least you have a working wireless.

---

