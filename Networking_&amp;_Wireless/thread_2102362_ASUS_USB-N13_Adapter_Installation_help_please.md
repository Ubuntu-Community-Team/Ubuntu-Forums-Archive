---
title: "ASUS USB-N13 Adapter Installation help please"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by Andrew F in Australia on 2013-01-07
Hi All,

Would appreciate any help that you could provide to get an installation up and running.

I bought the above adapter as it was sold as being recognised out of the box (nope) 

Comes with clear installation instructions that didn't work, given in a powerpoint file and separately as a text file with the driver.  The instructions below make sense, but

```
lsusb gives
Bus 002 Device 006: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]

```THIS CRASHES ON MY SYSTEM AT THE FIRST HURDLE (below)

??Did I compile (sudo make) in the correct folder??

```
harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715$ dir
RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715

harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715$ cd RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/

harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715$ dir
android_reference_codes  driver      readme.txt        wpa_supplicant_hostapd
document         install.sh  ReleaseNotes.doc

harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715$ cd driver

harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver$ dir
rtl8192_8188CU_linux_v3.0.2164.20110715
rtl8192_8188CU_linux_v3.0.2164.20110715.tar.gz
USB-N13\ Linux\ Driver\ Quick\ Start.txt

harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver$ cd rtl8192_8188CU_linux_v3.0.2164.20110715/

harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715$ dir
autoconf_rtl8192c_usb_linux.h  core  ifcfg-wlan0  Kconfig   os_dep  wlan0dhcp
clean                   hal   include      Makefile  runwpa

harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715$ sudo make
[sudo] password for harold-music: 
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-21-generic/build M=/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
make[1]: *** No rule to make target `dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make: *** [modules] Error 2
harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715$ sudo make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-21-generic/build M=/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
make[1]: *** No rule to make target `dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make: *** [modules] Error 2
harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715$


```** INSTALLATION INSTRUCTIONS PACKAGED WITH THE DRIVER**

```
 Installation instructions for the Legacy rt73 module
[http://rt2x00.serialmonkey.com]


==================
Build Instructions
==================

    1. Unpack the driver sources and go to the Module directory:
          $ tar -xvzf rt73-cvs-daily.tar.gz
          $ cd ./rt73-cvs-YYYYMMDDHH/Module

    2. Compile the driver sources:
          $ make

    3. Install the driver (as root):
          # make install


====================
INVOCATION
====================
Load the driver:

    $ modprobe rt73 [ifname=<name>] [debug=<mask>] [firmName=<file>]

    <name> is the name of the device and defaults to "wlan%d". If more
    than one adapter is installed, successive devices will be named
    wlan0, wlan1, etc. If you wish to use a different scheme - say
    eth*, and there are already wired ethernet devices named eth0 and
    eth1, then specifying <name> as "eth%d" gives the adapter the name
    "eth2".

    <mask> is a decimal or hex number. See TESTING file. Ignored if
    driver compiled without debug support.

    <file> is the name of a firmware file and defaults to "rt73.bin"
    if omitted. Only the basename - not the full path - may be
    specified.

Start it up:

    $ ifup wlan0        # If using Debian - or
    $ ifconfig wlan0 up
    $ iwlist wlan0 scan

If everything is ok, you should see a list of surrounding Access
Points. It means you can jump to the configuration section. Otherwise,
check out the following install notes...

_________
NOTES:

* Firmware file (rt73.bin)

    The rt73 chipset uses a firmware file which is loaded in device
    memory using the kernel firmware_class facility. 'make install'
    copy the firmware file to the standard firmwares location:
    /lib/firmware.

    However some linux distributions divert from the standard and e.g.
    use /lib/firmware/<KERNEL_VERSION>. If this is your case, you will
    have to manually move the firmware file to the right location.
    If you have problems with firmware loading, please ask on your
    distro's support media (forum, etc).

* Driver alias

    rt73 uses wlan* as its modprobe alias. This means you can have
    several devices and they will be named wlan0, wlan1, etc.

    If for some reason you want this interface number 'static' (e.g.
    if you have several wlan devices and their numbers change on
    reboot) you can change the rt73 alias in /etc/modprobe.d/ralink
    (2.6 kernels) or /etc/modules.conf (2.4 kernels) back to wlan0 (or
    wlan1, etc).

    However the proper way to achieve this purpose is to use a udev
    rule based on the wlan MAC address, for example:
    KERNEL=="wlan*", SYSFS{address}=="00:de:ad:be:ef:00", NAME="wlan0"
    (See:
     http://www.reactivated.net/writing_udev_rules.html#example-netif)

* Module parameters

    You can load the rt73 module with two optional parameters:
       firmName=<FILE_NAME>  Use another firmware file.
       debug=<DEBUG_MASK>    Set debug verbosity (see below).


==============================
Wireless Station Configuration
==============================

The wlan interface should be configured using standard wireless
extension tools.

GUI CONFIG:

    If you're looking for a GUI config tool we provide RutilT on our
    download page
    [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads].

MANUAL CONFIG:

    1. Set the interface mode and bring it up
          # iwconfig wlan0 mode managed
          # ifconfig wlan0 up

    2. Set your target network / Access Point
       If you just want to join a wireless network, set its ESSID:
          # iwconfig wlan0 essid <ESSID>
       If you want to associate with a specific AP, set its MAC
       address:
          # iwconfig wlan0 ap <BSSID>

    3. Set encryption if needed

       a) WEP (802.11b)
          Choose the authentication mode (open/restricted):
             # iwconfig wlan0 key open
          Or:
             # iwconfig wlan0 key restricted
          Set the encryption key:
             # iwconfig wlan0 key <KEY>

       b) WPA (802.11g)
          Set the authentication mode:
             # iwpriv wlan0 set AuthMode=WPAPSK
          Set the encryption key:
             # iwpriv wlan0 set WPAPSK=<KEY>
          Set the encryption type:
             # iwpriv wlan0 set EncrypType=TKIP

       c) WPA2 (802.11i)
          Set the authentication mode:
             # iwpriv wlan0 set AuthMode=WPA2PSK
          Set the encryption key:
             # iwpriv wlan0 set WPAPSK=<KEY>
          Set the encryption type:
             # iwpriv wlan0 set EncrypType=AES

    4. Check that you're associated with an AP
          # iwconfig wlan0

If everything's ok, you can now configure the wlan0 interface
statically or dynamically (DHCP). If you need more wireless config
details and examples (Adhoc mode e.g.), see iwpriv_usage.txt (included
in driver sources). Otherwise, read the following config notes...

_________
NOTES:

* Auto-load on boot

    If you want your device to come up on boot the best is to use your
    specific linux distribution's tools (boot scripts, etc).
    If you need support doing so, ask on your distro's support media.

* wpa_supplicant

    wpa_supplicant is a userland WPA/WPA2/802.1X layer. This driver is
    not compatible with it. As most wpa_supplicant features are
    embedded into our driver, you should not need it though.
    If you need to use a feature that only wpa_supplicant provides:
       - either use our next-generation rt2x00 driver which
         is compatible with wpa_supplicant
       - or patch wpa_supplicant to make it work with rt73 (more info:
         http://mjh.name/Ralink_rt73_wpa_supplicant_rt2x00_wpa2)


==================
Misc. information
==================

* hostapd

    hostapd allows your wlan device to act like an Access Point. Legacy
    drivers are _not_ compatible with it, but our next-generation
    rt2x00 drivers are.

* Network auditing

    Our drivers allow you to peform in-depth wireless network auditing.
    Most of the following settings require that you bring the
    interface down beforehand.

    You can set a custom MAC address as you would do for any other
    ethernet interface:
       # ifconfig wlan0 hw ether <MAC_ADDRESS>

    You can put your wlan interface in promiscuous mode as you would
    do for any other interface:
       # ifconfig wlan0 promisc

    You can put your interface in monitor mode and have it listen to all
    802.11 frames around:
       # iwconfig wlan0 mode monitor

    You can also inject 802.11 frames on the fly. To enable injection,
    run:
       # iwpriv wlan0 rfmontx 1

* Testing / debugging

    If you experience any driver related problem you can ask for
    support on our mailing list or our legacy driver forum.
    Before asking for help, read the TESTING file and follow its
    advice. Do *not* post messages like: "wlan does not work. please
    help!".

```Two conflicting instructions as well to make life difficult.
        ```
 USB-N13 Linux Driver quick start            
        This driver only supports kernel 2.618~2.6.38, your linux is suggested to be Software Development mode that can be correctly built.         
 
        *Before installing driver, please check installed compile, make tool and kernel source code. 
          Otherwise, you need to connect to Internet and use yum to install. 
         
                step1.Modify "enable=1" to "0" in /etc/yum.repos.d/fedora-updates.repo   and  /etc/yum.repos.d/fedora-updates-testing.repo 
                step2.#yum install gcc 
                step3.#yum install make 
                step4.#uname -r 
                step5.#yum install kernel-devel 
                Note: You must install the same version kernel of setp4.                 
  
        *Start install driver 
 
               1.tar -zxvf  rtl8192_8188CU_linux_v3.0.2164.20110715.tar.gz 
               2.Compile driver 
                   #make 
               3.Insert the driver to kernel 
                   #make install 
               4.Reboot system 
                   #reboot 
               5.Active Interface 
                   #ifconfig wlan0 up 
               6.sitesurvey  
                   #iwlist wlan0 scan 
 
 
        *Uninstall driver 
 
               1. #make uninstall 
               2. #reboot 
```

---

### Post by Andrew F in Australia on 2013-01-11
THanks to the anonymous forum member who tried to help to install this over IRC

SHort answer: >> The errors were coming from  driver was looking for folders that were non-existent, the self-installing script breaks a lot of dependencies so that the card wasn't recognised.

We got close to getting it to work then time beat us.

Have reformatted/reinstalled 12.04 instead of 12.10 (buggy still on my computer) and the adapter recognises but doesn't connect.

Will try to reconnect again today.  The notes that come with the driver say it's supported for Kernels 2.0.?? -> 2.6.??  (ie: not for the current 3.2??)   I don't know if this makes a difference or not.

AF

---

### Post by steeldriver on 2013-01-11
It looks to me like the basic problem is that you are trying to build it in a directory that has a space in the filename, which the Makefile is picking up via $PWD - this is a perennial problem with 'make' and the result is that it's breaking the filename into pieces and it thinks that the back half is the build target (instead of the real build target i.e. 'modules')

You *may* be able to get it to build if you move the source to a more sensible directory e.g. ~/src

However if it's for kernel 2.x then the chances of getting it to build AND work on 3.x are slim, I think - you would be better off looking for a kernel 3.x package on the Realtek website and trying to build that

```
harold-music@haroldmusic-GA-970A-D3:/media/Data/Wireless dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715$ sudo make
[sudo] password for harold-music: 
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-21-generic/build M=/media/Data/[COLOR=Red]Wireless dongle[/COLOR]/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
make[1]: *** No rule to make target `[COLOR=Red]dongle/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715[/COLOR]'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make: *** [modules] Error 2

```

---

### Post by Andrew F in Australia on 2013-01-14
THanks Steeldriver.

Makes sense.

I'm still fighting with it.

WIll give it a go.

Regards,

AF

---

### Post by ahallubuntu on 2013-01-14
I have compiled the Realtek driver for 8192CU many times in 12.04 (and 12.10) and it works fine.  But you are trying to compile an old driver, "rtl8192_8188CU_linux_v3.0.2164.20110715" See the date at the end - July 15, 2011?.  That predates the release of Ubuntu 12.04 in April 2012.

Download the latest driver for RTL8192CU from Realtek's website. Start here:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Follow these instructions so you blacklist the old driver and load the new one:

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

Restart the computer after you've done all that.  Do this command

```
sudo lshw -C network
```

and look for the driver "8192cu" in the section for the wireless card.  If it says "rtl8192cu" then you are still using the old driver.  The new one when installed is called "8192cu" .

---

### Post by Andrew F in Australia on 2013-01-14
Absolutely Brilliant Steeldriver and Ahallubuntu

Works like a charm.  (I was later trying to install current driver)  Same problem, however.

I can't thank you both enough.

Regards,

AF

---

