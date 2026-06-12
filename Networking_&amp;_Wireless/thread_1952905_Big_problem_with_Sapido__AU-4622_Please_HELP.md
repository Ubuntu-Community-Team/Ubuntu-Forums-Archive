---
title: "Big problem with Sapido  AU-4622 Please HELP"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by dachuwka666 on 2012-04-05
Hello, i don't install drivers in my new card sapido AU-4622 with chip RTL8192SU.
When usb plug in:

```
lsusb:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1c4f:0003 SiGma Micro 
Bus 003 Device 002: ID 03eb:0902 Atmel Corp. 4-Port Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 002 Device 002: ID 0e0b:9063  [/COLOR]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0ac8:c302 Z-Star Microelectronics Corp. Vega USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
0e0b:9063 is that card, in other linux is wriiten AMIGO TECHNOLOGIES INC. 
I installed the drivers from the included CD for linux
but nothing happened

---

### Post by chili555 on 2012-04-05
> I installed the drivers from the included CD for linux
but nothing happenedTell us more. What is the name of the file you installed? Were there any errors or warnings? Please post:```
arch
lsb_release -rc
dmesg | grep 819
```Thanks.

---

### Post by dachuwka666 on 2012-04-05
I install drivers step by step with included manual:

```

root@softer-laptop:/home/softer/nowy/rtl8712#   in this folder is the driver

root@softer-laptop:/home/softer/nowy/rtl8712# make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-22-generic/build M=/home/softer/nowy/rtl8712  modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/softer/nowy/rtl8712/cmd/rtl871x_cmd.o
  CC [M]  /home/softer/nowy/rtl8712/cmd/rtl8712_cmd.o
  CC [M]  /home/softer/nowy/rtl8712/crypto/rtl871x_security.o
  CC [M]  /home/softer/nowy/rtl8712/debug/rtl871x_debug.o
  CC [M]  /home/softer/nowy/rtl8712/eeprom/rtl871x_eeprom.o
  CC [M]  /home/softer/nowy/rtl8712/efuse/rtl8712_efuse.o
  CC [M]  /home/softer/nowy/rtl8712/hal/rtl8712/hal_init.o
  CC [M]  /home/softer/nowy/rtl8712/hal/rtl8712/usb_ops.o
  CC [M]  /home/softer/nowy/rtl8712/hal/rtl8712/usb_ops_linux.o
  CC [M]  /home/softer/nowy/rtl8712/hal/rtl8712/usb_halinit.o
  CC [M]  /home/softer/nowy/rtl8712/io/rtl871x_io.o
  CC [M]  /home/softer/nowy/rtl8712/io/rtl8712_io.o
  CC [M]  /home/softer/nowy/rtl8712/ioctl/rtl871x_ioctl_query.o
  CC [M]  /home/softer/nowy/rtl8712/ioctl/rtl871x_ioctl_set.o
  CC [M]  /home/softer/nowy/rtl8712/ioctl/rtl871x_ioctl_linux.o
/home/softer/nowy/rtl8712/ioctl/rtl871x_ioctl_linux.c: In function ‘r871x_wx_set_priv’:
/home/softer/nowy/rtl8712/ioctl/rtl871x_ioctl_linux.c:1505: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/softer/nowy/rtl8712/ioctl/rtl871x_ioctl_rtl.o
  CC [M]  /home/softer/nowy/rtl8712/led/rtl8712_led.o
  CC [M]  /home/softer/nowy/rtl8712/mlme/ieee80211.o
  CC [M]  /home/softer/nowy/rtl8712/mlme/rtl871x_mlme.o
  CC [M]  /home/softer/nowy/rtl8712/mp/rtl871x_mp.o
  CC [M]  /home/softer/nowy/rtl8712/mp/rtl871x_mp_ioctl.o
  CC [M]  /home/softer/nowy/rtl8712/os_dep/linux/io_linux.o
  CC [M]  /home/softer/nowy/rtl8712/os_dep/linux/xmit_linux.o
  CC [M]  /home/softer/nowy/rtl8712/os_dep/linux/cmd_linux.o
  CC [M]  /home/softer/nowy/rtl8712/os_dep/linux/mlme_linux.o
  CC [M]  /home/softer/nowy/rtl8712/os_dep/linux/recv_linux.o
  CC [M]  /home/softer/nowy/rtl8712/os_intf/osdep_service.o
  CC [M]  /home/softer/nowy/rtl8712/os_intf/linux/os_intfs.o
  CC [M]  /home/softer/nowy/rtl8712/os_intf/linux/usb_intf.o
  CC [M]  /home/softer/nowy/rtl8712/pwrctrl/rtl871x_pwrctrl.o
  CC [M]  /home/softer/nowy/rtl8712/recv/rtl871x_recv.o
  CC [M]  /home/softer/nowy/rtl8712/recv/rtl8712_recv.o
  CC [M]  /home/softer/nowy/rtl8712/rf/rtl871x_rf.o
  CC [M]  /home/softer/nowy/rtl8712/rf/rtl8712_rf.o
  CC [M]  /home/softer/nowy/rtl8712/sta_mgt/rtl871x_sta_mgt.o
  CC [M]  /home/softer/nowy/rtl8712/xmit/rtl871x_xmit.o
  CC [M]  /home/softer/nowy/rtl8712/xmit/rtl8712_xmit.o
  LD [M]  /home/softer/nowy/rtl8712/8712u.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/softer/nowy/rtl8712/8712u.mod.o
  LD [M]  /home/softer/nowy/rtl8712/8712u.ko
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.32-22-generic'
root@softer-laptop:/home/softer/nowy/rtl8712# make install
install -p -m 644 8712u.ko  /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-22-generic 

```
   Linux still only detects a one wifi card

```
root@softer-laptop:/home/softer/nowy/rtl8712# airmon-ng


Interface    Chipset        Driver

wlan0        Atheros     ath5k - [phy0]

```

```
root@softer-laptop:/home/softer/nowy/rtl8712# arch
i686
root@softer-laptop:/home/softer/nowy/rtl8712# lsb_release -rc
Release:    10.04
Codename:    lucid
root@softer-laptop:/home/softer/nowy/rtl8712# dmesg | grep 819
[    0.178197] ACPI: Interpreter enabled
[    0.178197] ACPI: (supports S0 S3 S4 S5)
[    0.178197] ACPI: Using IOAPIC for interrupt routing
[    0.178197] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.253035] type=2000 audit(1333638198.251:1): initialized
[    0.535189] rtc_cmos 00:07: setting system clock to 2012-04-05 15:03:18 UTC (1333638198)
[   20.253505] Linux kernel driver for RTL8192 based WLAN cards
root@softer-laptop:/home/softer/nowy/rtl8712# 



```

---

### Post by chili555 on 2012-04-05
Looks pretty solid so far! Let's have a look at:```
lsmod | grep 8712
modinfo 8712u | grep 9063
```I wonder if 8712u actually covers your device!> Bus 002 Device 002: ID [COLOR="Red"]0e0b:9063[/COLOR]  The driver r8712u in the current version 11.10 does not.

Of course, we could adjust a few dev_id.c files...

---

### Post by dachuwka666 on 2012-04-05
```
root@softer-laptop:/home/softer/nowy/rtl8712# lsmod | grep 8712
8712u                 308146  0 
root@softer-laptop:/home/softer/nowy/rtl8712# modinfo 8712u | grep 9063
root@softer-laptop:/home/softer/nowy/rtl8712# nothing happens

```

how adjust a few dev_id.c files ??
maybe this driver is not compatible for my hardware id

---

### Post by chili555 on 2012-04-05
> maybe this driver is not compatible for my hardware id> root@softer-laptop:/home/softer/nowy/rtl8712# modinfo 8712u | grep 9063
root@softer-laptop:/home/softer/nowy/rtl8712# **nothing happens**That's exactly what you've shown! 

Is this the CD that came with the device? Otherwise, how do you know it's an RTL8192SU chipset? How wonderful of Amigo to include a driver CD that *doesn't even cover the device!*

Modifying the .c file to cover the device is purely experimental. Let me know if you'd like to proceed with the task. The alternative is to return the device and try another.

---

### Post by dachuwka666 on 2012-04-05
Yes CD came with the device, on another computer running Windows 7, the device uses net8192su.inf and using this file in ndiswrapper device works.  I'd like to try modifying the .c file to cover the device. Unless you have another idea....

---

### Post by chili555 on 2012-04-05
> the device uses net8192su.inf That's good information and I suggest we rely on it. Look in the files you extracted and find the folder os_intf/linux. We are going to amend the file *usb_intf.c* with any text editor such as gedit. Go down to the RTL8192SU section and add as I've highlighted here. All the remaning file is untouched. Be certain that spacing, brackets, etc. are perfect. Proofread twice before you save and close the text editor.```
/* RTL8192SU */
	/* Realtek */
	{USB_DEVICE(0x0BDA, 0x8174)},
	{USB_DEVICE(0x0BDA, 0x8174)},
	/* Belkin */
	{USB_DEVICE(0x050D, 0x845A)},
	/* Corega */
	{USB_DEVICE(0x07AA, 0x0051)},
	/* Edimax */
	{USB_DEVICE(0x7392, 0x7622)},
	/* NEC */
	{USB_DEVICE(0x0409, 0x02B6)},
	[COLOR="Red"]/* AMIGO */
	{USB_DEVICE(0x0E0B, 0x9063)},[/COLOR]
	
	{}
};
```Now we must recompile:```
sudo su
cd /home/softer/nowy/rtl8712   <--if not already there
make clean
make
make install
modprobe -r 8712u
modprobe 8712u
iwconfig
exit
```Any improvement?

---

### Post by dachuwka666 on 2012-04-05
something has changed 
```
root@softer-laptop:/home/softer/rtl8712# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SOLTYS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:06:4F:5F:4B:4F   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan4     unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

what to do now??

---

### Post by chili555 on 2012-04-05
I don't quite understand why you want two wireless devices. I'd click the Network Manager icon and disconnect wlan0 from SOLTYS and see if you can connect wlan4 which may be known as rtl_wifi.

Are there any interesting clues here?```
dmesg | grep 8712
sudo iwlist wlan4 scan
```

---

### Post by dachuwka666 on 2012-04-05
```
root@softer-laptop:/home/softer# dmesg | grep 8712
[    0.187123] pci 0000:02:00.0: PME# disabled
[   20.581465] register rtl8712_netdev_ops to netdev_ops
[   20.581471] 8712_usb_endpoint_descriptor(0):
[   20.581481] 8712_usb_endpoint_descriptor(1):
[   20.581491] 8712_usb_endpoint_descriptor(2):
[   20.581500] 8712_usb_endpoint_descriptor(3):
[   20.581509] 8712u : USB_SPEED_HIGH
[   31.399908] fwdbg:RTL8712 FW version 0.0.1# &#19977; 8&#26376; 11 20:37:05 CST 2010  SVN
root@softer-laptop:/home/softer# sudo iwlist wlan4 scan
wlan4     Scan completed :
          Cell 01 - Address: 00:06:4F:5F:4B:4F
                    ESSID:"SOLTYS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 02 - Address: 00:09:92:01:6B:EF
                    ESSID:"GressNet-S"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:off
                    Bit Rates:5.5 Mb/s
                    Signal level=10/100  
          Cell 03 - Address: 00:14:7F:88:1C:BF
                    ESSID:"TELMAX"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Signal level=10/100  

root@softer-laptop:/home/softer# 

```

Many thanks, it works, but but device shuts down from time to time, whether this can modify the other drivers? Something had to be uninstalled before installing the new?

---

### Post by chili555 on 2012-04-05
> Many thanks, it works, but but device shuts down from time to time, whether this can modify the other drivers? Something had to be uninstalled before installing the new?It depends on why it's shutting down. I suspect that Network Manager is trying to stop it to restart wlan0, which it thinks is default. You might remove the driver for the other card to see if it helps. Is it your intention to use this device permanently in place of the other? Why? If so, we can blacklist the other driver.

Are there any parameters we can load?```
modinfo 8712u | grep param
```

---

### Post by dachuwka666 on 2012-04-05
I have one problem, if I could somehow turn the monitor mode
```
root@softer-laptop:/home/softer# airmon-ng


Interface    Chipset        Driver

wlan4        Unknown         r871x_usb_drv
wlan0        Atheros     ath5k - [phy0]

root@softer-laptop:/home/softer# airmon-ng start wlan4


Found 11 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
1108    avahi-daemon
1112    avahi-daemon
1920    avahi-autoipd
1921    avahi-autoipd
1932    dhclient3
1995    dhclient3
4640    wpa_supplicant
4655    avahi-autoipd
4656    avahi-autoipd
4659    dhclient
4679    dhclient
Process with PID 4640 (wpa_supplicant) is running on interface wlan4
Process with PID 4679 (dhclient) is running on interface wlan4
Process with PID 1920 (avahi-autoipd) is running on interface wlan0
Process with PID 1921 (avahi-autoipd) is running on interface wlan0
Process with PID 1995 (dhclient3) is running on interface wlan0


Interface    Chipset        Driver

wlan4        Unknown         r871x_usb_drv (monitor mode enabled)
wlan0        Atheros     ath5k - [phy0]

root@softer-laptop:/home/softer# airmon-ng


Interface    Chipset        Driver

wlan4        Unknown         r871x_usb_drv
wlan0        Atheros     ath5k - [phy0]


```

---

### Post by chili555 on 2012-04-05
Sorry, I know nothing about airmon. You might temporarily unload *ath5k* to get wlan4 to work better:```
sudo modprobe -rv ath5k
```If your concern now is airmon, I can be of no further help.

You may wish to email AMIGO to tell them the driver disk doesn't cover the device and you had to get some old dude on a forum to rewrite their .c code for them!

---

### Post by dachuwka666 on 2012-04-06
Thank you for everything. After turning off the first card, the equipment is working fine

---

