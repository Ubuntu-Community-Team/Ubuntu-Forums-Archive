---
title: "wifi card doesnt show up"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by asad12 on 2011-09-05
I am new to the ubuntu i am trying to solve the problem with wireless troubleshooting guide. but i am going nowhere. anyhelp would be apperciated thanks
i am running xubuntu, thanks


lshw -c network
> *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:d0:59:d9:63:90
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.8 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:c0200000-c0200fff ioport:6400(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlan0
       serial: 00:08:10:76:7c:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-11-generic firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn

lsusb
> Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:3370 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lsmod
> Module                  Size  Used by
savage                 35490  2 
drm                   184164  3 savage
vesafb                 13449  1 
snd_intel8x0           33213  3 
thinkpad_acpi          73750  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rt2800usb              17907  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
rt2800lib              43824  1 rt2800usb
rt2x00usb              19693  1 rt2800usb
ppdev                  12849  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
nsc_ircc               23199  0 
yenta_socket           27230  0 
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
pcmcia_rsrc            18292  1 yenta_socket
lp                     13349  0 
psmouse                73312  0 
parport_pc             32111  1 
irda                  185091  1 nsc_ircc
video                  18951  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
snd                    55295  16 snd_intel8x0,thinkpad_acpi,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvram                  14035  1 thinkpad_acpi
parport                36746  3 ppdev,lp,parport_pc
shpchp                 32345  0 
soundcore              12600  1 snd
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
crc_ccitt              12595  2 rt2800lib,irda
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
e100                   40108  0 
floppy                 60032  0 

---

### Post by asad12 on 2011-09-06
hello, i am stuck plz help

---

### Post by praseodym on 2011-09-06
Hi,

can you show:

```
uname -a
iwconfig
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
modinfo rt2800usb | grep 3370
modinfo rt2870sta | grep 3370
sudo iwlist scan
```

---

### Post by praseodym on 2011-09-06
Ok,

I checked the "modinfo"s in a virtual machine, module rt2800usb contains the device-IDs you need.

Please check additionally to the other outputs

```
dmesg | egrep 'rt2|firm|radio|switch'
```

---

### Post by asad12 on 2011-09-06
@praseodym , heres the commands u requested

>  asad@asad-laptop:~$ uname -a
Linux asad-laptop 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux
asad@asad-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
asad@asad-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
asad@asad-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
asad@asad-laptop:~$ modinfo rt2800usb | grep 3370
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
asad@asad-laptop:~$ modinfo rt2870sta | grep 3370
asad@asad-laptop:~$ sudo iwlist scan
[sudo] password for asad: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

asad@asad-laptop:~$ dmesg | egrep 'rt2|firm|radio|switch'
[    0.000000] APIC: switched to apic NOOP
[    0.009674] SMP alternatives: switching to UP code
[   22.976505] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   24.442823] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
[   24.442829] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
[   25.315683] Registered led device: rt2800usb-phy0::radio
[   25.315891] Registered led device: rt2800usb-phy0::assoc
[   25.316456] Registered led device: rt2800usb-phy0::quality
[   25.323585] usbcore: registered new interface driver rt2800usb
[   27.303734] Console: switching to colour frame buffer device 128x48
[   29.655276] phy0 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset.
asad@asad-laptop:~$ 


---

### Post by asad12 on 2011-09-08
can somebody plz help out . what to do next

---

### Post by lkjoel on 2011-09-08
Try this:
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "NXL6DO"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by asad12 on 2011-09-08
i tried , not working
> asad@asad-laptop:~$ sudo ifconfig wlan0 down
[sudo] password for asad: 
Sorry, try again.
[sudo] password for asad: 
asad@asad-laptop:~$ sudo dhclient -r wlan0
asad@asad-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
asad@asad-laptop:~$ sudo iwconfig wlan0 essid "NXL6DO"
asad@asad-laptop:~$ sudo iwconfig wlan0 mode Managed
asad@asad-laptop:~$ sudo dhclient wlan0
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory


---

### Post by fdrake on 2011-09-08
> 
[ 29.655276] phy0 -> rt2x00lib_request_firmware: [COLOR="Red"]Error - Current firmware does not support detected chipset.[/COLOR]


have you tried to do a reinstall/update/upgrade to get a newer firmware available?

```

sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
sudo aptitude update && sudo aptitude upgrade

```
reboot and test otherwise we may have to install it manually

edit : link to how to:
[http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working](http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working)

---

### Post by praseodym on 2011-09-09
The driver is attached, save it on your Desktop, unpack it by right-click->unpack here and install it:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
cd ~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO
sudo make
sudo make install
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf rt2800usb
sudo modprobe -v rt5370sta
sudo depmod -a
sudo update-initramfs -u
```
Replug your stick and check:

```
iwconfig
sudo iwlist scan
lsmod
rfkill list
dmesg | egrep 'rt5|rt3|rt2'
```

---

### Post by asad12 on 2011-09-10
i did everything i can, i am not sure what to do next, its still not working. Let me know what to do next

> asad@asad-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:d0:59:d9:63:90
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.8 latency=66 maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:c0200000-c0200fff ioport:6400(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
asad@asad-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:3370 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
asad@asad-laptop:~$ sudo apt-get install --reinstall linux-headers-generic build-essential dkms
[sudo] password for asad: 
Sorry, try again.
[sudo] password for asad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/80.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 157020 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu1 (using .../build-essential_11.5ubuntu1_i386.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.1.1.2-5ubuntu1 (using .../dkms_2.1.1.2-5ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-generic 2.6.38.11.26 (using .../linux-headers-generic_2.6.38.11.26_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Processing triggers for man-db ...
Setting up build-essential (11.5ubuntu1) ...
Setting up dkms (2.1.1.2-5ubuntu1) ...
Setting up linux-headers-generic (2.6.38.11.26) ...
asad@asad-laptop:~$ cd ~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO
asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo make
make -C tools
make[1]: Entering directory `/home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
/home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-11-generic/build SUBDIRS=/home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.o
/home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.c:415:13: warning: unused variable ‘pObj’
  LD [M]  /home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
see include/linux/module.h for more information
  LD [M]  /home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
cp -f /home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko /tftpboot
asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo make install
make -C /home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-11-generic
make[1]: Leaving directory `/home/asad/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'
asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist rt2800usb
asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo modprobe -rf rt2800usb
asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo modprobe -v rt5370sta
insmod /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt5370sta.ko 
FATAL: Error inserting rt5370sta (/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo depmod -a

asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ lsmod
Module                  Size  Used by
savage                 35490  2 
drm                   184164  3 savage
vesafb                 13449  1 
snd_intel8x0           33213  3 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
thinkpad_acpi          73750  1 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
pcmcia                 39671  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
yenta_socket           27230  0 
nsc_ircc               23199  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            18292  1 yenta_socket
irda                  185091  1 nsc_ircc
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
ppdev                  12849  0 
snd                    55295  16 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
parport_pc             32111  1 
video                  18951  0 
crc_ccitt              12595  1 irda
psmouse                73312  0 
nvram                  14035  1 thinkpad_acpi
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
e100                   40108  0 
floppy                 60032  0 
asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ rfkill list
asad@asad-laptop:~/Desktop/angepasster-2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ dmesg | egrep 'rt5|rt3|rt2'
[   23.130006] rt5370sta: module license 'unspecified' taints kernel.
[   23.138560] rt5370sta: Unknown symbol usb_alloc_urb (err 0)
[   23.139573] rt5370sta: Unknown symbol usb_free_urb (err 0)
[   23.140423] rt5370sta: Unknown symbol usb_alloc_coherent (err 0)
[   23.141484] rt5370sta: Unknown symbol usb_register_driver (err 0)
[   23.142837] rt5370sta: Unknown symbol usb_put_dev (err 0)
[   23.143231] rt5370sta: Unknown symbol usb_get_dev (err 0)
[   23.143949] rt5370sta: Unknown symbol usb_submit_urb (err 0)
[   23.145051] rt5370sta: Unknown symbol usb_free_coherent (err 0)
[   23.146409] rt5370sta: Unknown symbol usb_control_msg (err 0)
[   23.147715] rt5370sta: Unknown symbol usb_deregister (err 0)
[   23.149587] rt5370sta: Unknown symbol usb_kill_urb (err 0)
[  505.669290] rt5370sta: Unknown symbol usb_alloc_urb (err 0)
[  505.669957] rt5370sta: Unknown symbol usb_free_urb (err 0)
[  505.671070] rt5370sta: Unknown symbol usb_alloc_coherent (err 0)
[  505.676698] rt5370sta: Unknown symbol usb_register_driver (err 0)
[  505.678400] rt5370sta: Unknown symbol usb_put_dev (err 0)
[  505.678980] rt5370sta: Unknown symbol usb_get_dev (err 0)
[  505.680002] rt5370sta: Unknown symbol usb_submit_urb (err 0)
[  505.689888] rt5370sta: Unknown symbol usb_free_coherent (err 0)
[  505.691438] rt5370sta: Unknown symbol usb_control_msg (err 0)
[  505.697724] rt5370sta: Unknown symbol usb_deregister (err 0)
[  505.700236] rt5370sta: Unknown symbol usb_kill_urb (err 0)
[  592.967907] rt5370sta: Unknown symbol usb_alloc_urb (err 0)
[  592.969127] rt5370sta: Unknown symbol usb_free_urb (err 0)
[  592.970247] rt5370sta: Unknown symbol usb_alloc_coherent (err 0)
[  592.971735] rt5370sta: Unknown symbol usb_register_driver (err 0)
[  592.973875] rt5370sta: Unknown symbol usb_put_dev (err 0)
[  592.974457] rt5370sta: Unknown symbol usb_get_dev (err 0)
[  592.975479] rt5370sta: Unknown symbol usb_submit_urb (err 0)
[  592.977364] rt5370sta: Unknown symbol usb_free_coherent (err 0)
[  592.978897] rt5370sta: Unknown symbol usb_control_msg (err 0)
[  592.981021] rt5370sta: Unknown symbol usb_deregister (err 0)
[  592.983407] rt5370sta: Unknown symbol usb_kill_urb (err 0)


---

### Post by praseodym on 2011-09-10
Ok, uninstall the driver via:

```
sudo make uninstall
sudo make clean
```

Try the attached one with module rt3370sta

---

### Post by lkjoel on 2011-09-11
Could you please give the output of this Terminal command?
```
lsusb -v

```

---

### Post by asad12 on 2011-09-11
heres the out put for lsusb -v 
also, i found the cd driver for this card, which say install path for rt2070,
i have been reading this thread 
[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)
he tries to manipulate and patch the stuff, i really cant figure it out

> asad@asad-laptop:~$ uname -a
Linux asad-laptop 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux
asad@asad-laptop:~$ lsusb -v

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 002: ID 148f:3370 Ralink Technology, Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x3370 
  bcdDevice            1.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
asad@asad-laptop:~$ 



---

### Post by lkjoel on 2011-09-11
So is this a wireless card or a wireless stick?

---

### Post by asad12 on 2011-09-12
usb wireless card, so i think a stick

---

### Post by praseodym on 2011-09-12
Did you try the driver I attached?

---

### Post by lkjoel on 2011-09-12
Try this:
```
sudo modprobe rt2800usb

```

---

### Post by asad12 on 2011-09-12
tried nothing happened
> asad@asad-laptop:~$ sudo modprobe rt2800usb
[sudo] password for asad: 
asad@asad-laptop:~$ 



---

### Post by lkjoel on 2011-09-12
OK, try this:
```
sudo rmmod rt2800usb

```

---

### Post by asad12 on 2011-09-12
i get an error
> asad@asad-laptop:~$ sudo rmmod rt2800usb
[sudo] password for asad: 
ERROR: Module rt2800usb does not exist in /proc/modules

---

