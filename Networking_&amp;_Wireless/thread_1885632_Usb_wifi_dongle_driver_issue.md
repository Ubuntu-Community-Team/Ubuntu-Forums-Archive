---
title: "Usb wifi dongle driver issue"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by linuxanon on 2011-11-23
Hey I recently picked up this inland wifi dongle and I'm having an issue installing the drivers.
[http://inlandproduct.com/prominiusbtowifidongle.aspx](http://inlandproduct.com/prominiusbtowifidongle.aspx)

The included readme.txt comes with the following installation methods
> <<Method 1>>
Runing the scripts accomplish all operations including building up modules 
from the source code, installing driver to the kernel and starting up the nic.
	1. Build up the drivers from the source code
	  make

	2. Install the driver to the kernel
          make install
          reboot

	3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
	  ifconfig wlan0 up 
	  Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name, 
                since it may change wlan0 to wlan1,etc.

<<Method 2>>
Or only load the driver module to kernel and start up nic.
	 1. Build up the drivers from the source code
	  make
         2. Copy firmware to /lib/firmware/ or /lib/firmware/(KERNEL_VERSION)/
            cp -rf firmware/RTL8192SU /lib/firmware
          or
            cp -rf firmware/RTL8192SU /lib/firmware/(KERNEL_VERSION)
          Note: This depends on whether (KERNEL_VERSION) subdirectory exists under /lib/firmware

	 3. Load driver module to kernel and start up nic.
	  ./wlan0up
          Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                after run ./wlan0up, please run ./wlan0down first, then it should 
                be ok..
	  Note: If you see the message of "unkown symbol" during ./wlan0up, it
		is suggested to build driver by <<Method 1>>.

And here's what happened when I try to run the make command
> jorge@AT5IONT-I:~$ cd ~/Downloads/linux_2.6
jorge@AT5IONT-I:~/Downloads/linux_2.6$ sudo make install
[sudo] password for jorge: 
make[1]: Entering directory `/home/jorge/Downloads/linux_2.6/HAL/rtl8192u'
make -C /lib/modules/3.0.0-13-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-13-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --silentoldconfig Kconfig
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-13-generic'
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-13-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-13-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/jorge/Downloads/linux_2.6/HAL/rtl8192u'
make: *** [install] Error 2
jorge@AT5IONT-I:~/Downloads/linux_2.6$ 


What am I doing wrong here?

---

### Post by praseodym on 2011-11-23
Did you install the compilation tools and the kernel headers before?

```
sudo apt-get install linux-headers-generic build-essential
```
Please show:

```
lsusb
lsmod
rfkill list
iwconfig
```

---

### Post by linuxanon on 2011-11-23
> jorge@AT5IONT-I:~$ sudo apt-get install linux-headers-generic build-essential
[sudo] password for jorge: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


Yeah I already have those packages up to date

> jorge@AT5IONT-I:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 017: ID 148f:5370 Ralink Technology, Corp. 
Bus 001 Device 004: ID 04d9:1203 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 005: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 007 Device 002: ID 0bc2:5031 Seagate RSS LLC 
jorge@AT5IONT-I:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
parport_pc             36962  0 
dm_crypt               23199  1 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
nvidia              11713772  40 
cdc_acm                22761  0 
snd_hda_codec_hdmi     32040  4 
psmouse                73882  0 
serio_raw              13166  0 
snd_hda_codec_realtek   330769  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_hda_intel          33390  1 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
binfmt_misc            17540  1 
asus_atk0110           18078  0 
it87                   43287  0 
hwmon_vid              12746  1 it87
coretemp               13420  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
usb_storage            57901  1 
uas                    18027  0 
xhci_hcd               82772  0 
r8169                  52788  0 
ahci                   26002  0 
libahci                26861  1 ahci
jorge@AT5IONT-I:~$ rfkill list
jorge@AT5IONT-I:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


See anything of interest?

---

### Post by praseodym on 2011-11-23
Yes, you have a stick with Ralink chipset, but you tried to install a Realtek driver ;-)
> ```
Bus 001 Device 017: ID 148f:5370 Ralink Technology, Corp. 
```
Driver attached. Install it with

```
sudo make
sudo make install
```
and reboot. Check

```
dmesg | grep rt5
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by linuxanon on 2011-11-23
Thanks for all your help so far! The installation seemed to go well, but this is what I'm getting for the checks you recommended. Doesn't look too good, from what I can tell. 

```
jorge@AT5IONT-I:~$ dmesg | grep rt5
[    5.515767] rt5370sta: Unknown symbol usb_alloc_urb (err 0)
[    5.515803] rt5370sta: Unknown symbol usb_free_urb (err 0)
[    5.515845] rt5370sta: Unknown symbol usb_alloc_coherent (err 0)
[    5.515900] rt5370sta: Unknown symbol usb_register_driver (err 0)
[    5.515989] rt5370sta: Unknown symbol usb_put_dev (err 0)
[    5.516079] rt5370sta: Unknown symbol usb_get_dev (err 0)
[    5.516127] rt5370sta: Unknown symbol usb_submit_urb (err 0)
[    5.516179] rt5370sta: Unknown symbol usb_free_coherent (err 0)
[    5.516232] rt5370sta: Unknown symbol usb_control_msg (err 0)
[    5.516295] rt5370sta: Unknown symbol usb_deregister (err 0)
[    5.516383] rt5370sta: Unknown symbol usb_kill_urb (err 0)
jorge@AT5IONT-I:~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
dm_crypt               23199  1 
ppdev                  17113  0 
bnep                   18436  2 
nvidia              11713772  40 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_hdmi     32040  4 
psmouse                73882  0 
snd_hda_codec_realtek   330769  1 
serio_raw              13166  0 
snd_hda_intel          33390  1 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110           18078  0 
binfmt_misc            17540  1 
snd                    68266  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
it87                   43287  0 
hwmon_vid              12746  1 it87
coretemp               13420  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
usb_storage            57901  1 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
xhci_hcd               82772  0 
ahci                   26002  0 
libahci                26861  1 ahci
r8169                  52788  0 
jorge@AT5IONT-I:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jorge@AT5IONT-I:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

jorge@AT5IONT-I:~$ sudo iwlist scan
[sudo] password for jorge: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by praseodym on 2011-11-23
Uninstall the driver via

```
sudo make clean
sudo make
sudo make uninstall
```
and try the driver **RT5572USB** from the Ralink-homepage (it is brand new from yesterday, even too big to attach):
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
Open the file therein **~/os/linux/config.mk** and change the following lines to [COLOR="Red"]y[/COLOR]:
```
HAS_WPA_SUPPLICANT=[COLOR="Red"]y
[/COLOR]HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR] 
```
You may also want to change the file **~/RT2870STA.dat** to your settings according to your country code, ESSID, Key, etc according to [these settings]("http://wiki.ubuntuusers.de/wlan/ralink#RT2860STA-und-Draft-N") in the grey box. After that install with
```
sudo make
sudo make install
```
reboot and check again as shown above.

It may also not work with kernel 3 according to the README, the device may be too new...

---

### Post by linuxanon on 2011-11-24
Ran the previous checks after installing the new driver 
```
dmesg | grep rt5
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```

And got a similar result

```
jorge@AT5IONT-I:~$ dmesg | grep rt5
[    5.479484] rt5572sta: Unknown symbol usb_alloc_urb (err 0)
[    5.479527] rt5572sta: Unknown symbol usb_free_urb (err 0)
[    5.479572] rt5572sta: Unknown symbol usb_alloc_coherent (err 0)
[    5.479632] rt5572sta: Unknown symbol usb_register_driver (err 0)
[    5.479730] rt5572sta: Unknown symbol usb_put_dev (err 0)
[    5.479767] rt5572sta: Unknown symbol usb_get_dev (err 0)
[    5.479806] rt5572sta: Unknown symbol usb_submit_urb (err 0)
[    5.479861] rt5572sta: Unknown symbol usb_free_coherent (err 0)
[    5.479914] rt5572sta: Unknown symbol usb_control_msg (err 0)
[    5.479978] rt5572sta: Unknown symbol usb_deregister (err 0)
[    5.480570] rt5572sta: Unknown symbol usb_kill_urb (err 0)
jorge@AT5IONT-I:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
cdc_acm                22761  0 
parport_pc             36962  0 
dm_crypt               23199  1 
ppdev                  17113  0 
nvidia              11713772  50 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_hdmi     32040  4 
psmouse                73882  0 
serio_raw              13166  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  1 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
asus_atk0110           18078  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17540  1 
snd                    68266  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
it87                   43287  0 
hwmon_vid              12746  1 it87
coretemp               13420  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
usb_storage            57901  1 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
xhci_hcd               82772  0 
r8169                  52788  0 
ahci                   26002  0 
libahci                26861  1 ahci
jorge@AT5IONT-I:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jorge@AT5IONT-I:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

jorge@AT5IONT-I:~$ sudo iwlist scan
[sudo] password for jorge: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Starting to get a little discouraged here.

---

### Post by praseodym on 2011-11-25
Obviously the device is too new (or the Linux driver too old, for kernel <=2.6.38 only). Uninstall it with
```
sudo make uninstall
```
and try the Windows driver from here
[http://www.ralinktech.com/en/04_support/support.php?sn=500](http://www.ralinktech.com/en/04_support/support.php?sn=500)
1st one in the list with ndiswrapper.

---

### Post by gordintoronto on 2011-11-25
According to this web page: [http://wiki.debian.org/rt2800usb#supported](http://wiki.debian.org/rt2800usb#supported)
you have a 148F:5370 Ralink Technology, Corp. RT5370 Wireless Adapter.

According to that page, the support has been in the kernel since 2.6.31, which entered Ubuntu a couple of years ago.

What version of Ubuntu are you using? Do you have a network manager icon on the panel? Do you understand how to connect to a wireless network with a "supported device"? I've never had to install a driver with my Wifi adapter, "it just works." 

This is one of the difficult concepts for people coming from Windows; I even returned a wireless adapter because it didn't come with a Linux driver. If I had just installed it in the machine, it would have worked fine.

---

### Post by praseodym on 2011-11-25
@gordintoronto:

I never saw this device ID before. Since kernel 3 (the client uses 11.10) the module rt2870sta was removed, only rt2800usb is present.

@linuxanon
I think you should try ndiswrapper (or wait for a new driver). But you can try to add the device ID to the driver rt2800usb:

```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf

```
This is one line, copy/paste it, reload the driver, replug the stick, and check
```

sudo modprobe -rf rt2800usb rt5370sta
sudo modprobe -v rt2800usb
dmesg | tail -n 30
iwconfig
```
If it doesnt work you only need to remove the file

```
sudo rm /etc/modprobe.d/rt2800usb.conf
```
and reboot.

---

