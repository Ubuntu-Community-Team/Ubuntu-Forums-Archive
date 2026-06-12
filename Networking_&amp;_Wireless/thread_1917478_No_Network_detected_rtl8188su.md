---
title: "No Network detected rtl8188su"
date: 2012-01-30
forum: Networking &amp; Wireless
---

### Post by rondha on 2012-01-30
Hello!

I have been on it for a week now: I have a new usb adapter with rtl8188su and ubuntu 11.10 installed. When I first plugged the stick, it was automatically detected by Ubuntu but no wireless network was detected.
I have unsintalled and reinstalled the driver multiple times, tried the realtek driver din't work, currently using compat wireless(still no network detected). I tried removing all the realtek firmware, reboot and I got "device not ready". Downloaded and installed firmware-realtek, says "disconnected" but still no wireless network visible.

I have run thru the forum multiple times but haven't been able to find a solution either. The thing is that I was told that it was compatible with linux and that it could enter monitor mode.
Am I missing something?

Thanks!

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 004: ID 05ca:180a Ricoh Co., Ltd 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 006 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270 HSDPA/HSUPA Modem
Bus 006 Device 003: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 003 Device 005: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 002 Device 005: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter


# lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:3d:44:cb
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:aa:5b:10
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-15-generic firmware=478.104 link=no multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Wireless interface
       physical id: 3
       bus info: usb@2:3
       logical name: wlan1
       serial: 00:0f:11:13:0c:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated


$ lsmod
Module                  Size  Used by
r8712u                163310  0 
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12595  1 ppp_async
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
arc4                   12473  2 
b43                   347417  0 
mac80211              432553  1 b43
cfg80211              178838  2 b43,mac80211
joydev                 17393  0 
btusb                  18160  2 
bcma                   25587  1 b43
bluetooth             148839  23 bnep,rfcomm,btusb
snd_hda_codec_idt      60049  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
option                 25580  1 
usb_wwan               19779  1 option
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
usbserial              37203  5 option,usb_wwan
snd_seq_midi           13132  0 
psmouse                73673  0 
snd_rawmidi            25241  1 snd_seq_midi
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ssb                    55319  1 b43
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  509487  3 
pcmcia                 39822  2 b43,ssb
pcmcia_core            21511  1 pcmcia
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
wmi                    18744  1 dell_wmi
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  1 
libahci                25727  1 ahci
sky2                   49317  0 


$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common


$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist r8192e_pci
blacklist r8192se_pci
blacklist r8192u_usb


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mon0      IEEE 802.11bg  Mode:Monitor  Frequency:2.437 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by rondha on 2012-01-31
Still in my quest to connecting using my rtl8188su, 
I remove the lines
blacklist r8192e_pci
blacklist r8192se_pci
blacklist r8192u_usb
 and I found out thru this thread [http://ubuntuforums.org/showthread.php?t=1594535](http://ubuntuforums.org/showthread.php?t=1594535) that the module is "8712u.ko" and the firmware "rtl8192sfw.bin /lib/firmware/RTL8192S" while I have been using "r8712u" as the driver and "rtlwifi/rtl8712u.bin" as the firmware

Guess the question now is how to change the settings to the correct driver and firmware.
$ sudo insmod 8712u.ko
insmod: can't read '8712u.ko': No such file or directory

---

### Post by rondha on 2012-01-31
Thank you!

---

### Post by Bucky Ball on 2012-01-31
Have you gotten online with an ethernet cable and gotten updates then checked 'Additional Drivers'?

If not, do it with the dongle plugged in.

---

### Post by rondha on 2012-01-31
Yes I have gotten online and downloaded updates. The only one available in "Additional Drivers" was for a Broadcom device, no Realtek.

---

### Post by rondha on 2012-01-31
Forgot to add 
# sudo modprobe r8192s_usb
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module r8192s_usb not found.
sh: cannot create /sys/bus/usb/drivers/rtl819xU/new_id: Directory nonexistent
FATAL: Error running install command for r8192s_usb

---

### Post by Janiporo on 2012-02-10
I have RTL8191SU (id:0bda:8172) and same problem. MANY people have same issues with these Realtek usb-"cards". I figured out that when I am near router (one meter), I get signal quality 100/100. ONLY when it is 100% I get full speed.

When I go away from router, speed goes down dramatically.

These are the motherboards:
ASUS A8V-VM (yearmodel 2006 )
MSI G45M (yearmodel 2008 )

Both have latest bios.

I have noticed this "bug" effects both Ubuntu 11.10 and 12.04 alpha 2 (and I understand 11.04 also)

With my mothers new acer laptop there is absolutely no problem, so device is working.

I think almost every post anywhere around internet have the same problem. Some don't get connection at all, because they are too far away from wlan-router.

There absolutely is some kind of bug there.

Some people have working workarounds (disable 11n or power saving or ipv6) but these do not help in my case.

---

### Post by kurt18947 on 2012-02-10
I just installed a RealTek8188Csu based device (Edimax EW-7811Un), I don't know if my experience will be of any use or not.  I'm installing on Precise daily build and it was recognized -- sorta.  The blue light would come on steady and would see networks.  It would not connect and the light would not flash.  Tried manual setup, OpenDNS, everything I could think of. Iwconfig looked fine to me but no network.

 I downloaded the latest RealTek drivers for the device using another WiFi adapter then blacklisted all relevant built-in drivers and rebooted.  I then extracted the RealTek drivers to the desktop and cd'd to them.  Did 'sudo bash install.sh', let it run, rebooted again, plugged the device in and was in business.  Signal strength is fine, I don't think speed is as good as my rtl-8192SU adapters which are plug-n-play.  I don't have the skills to do forensics on the built-in driver.  It's very close but not quite there for me.

---

### Post by wildmanne39 on 2012-02-10
Hi, I notice you have a broadcom internal wireless card is there any reason you do not want to use it?
Thanks

---

