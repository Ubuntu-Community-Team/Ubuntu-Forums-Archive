---
title: "wireless netWork not showing up"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by rhythmiccycle on 2011-12-29
I.just reinstalled  Ubuntu 11 on my laptop. When I click on the wireless icon on top no networks show up. right clicking has the same effect as left clicking.

I opened the driver there its no broodcom thing there like there was with older versions of Ubuntu I installed on the laptop.f

---

### Post by wildmanne39 on 2011-12-29
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by rhythmiccycle on 2011-12-29
```

mike@mike-ME051:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux mike-ME051 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
mike@mike-ME051:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:01c9]
	Kernel driver in use: b44
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
	Kernel driver in use: b43-pci-bridge
mike@mike-ME051:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
mike@mike-ME051:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mike@mike-ME051:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  8 bnep,rfcomm
snd_hda_codec_idt      60049  1 
joydev                 17393  0 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
arc4                   12473  2 
b43                   318816  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
mac80211              393459  1 b43
cfg80211              172392  2 b43,mac80211
snd_seq_midi           13132  0 
psmouse                73673  0 
snd_rawmidi            25241  1 snd_seq_midi
i915                  505159  3 
binfmt_misc            17292  1 
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
b44                    31443  0 
ssb                    50682  2 b43,b44
mike@mike-ME051:~$ 


```

---

### Post by wildmanne39 on 2011-12-29
Hi, it shows you have the right driver so let's dig a little deeper, please post the output of with your wired connection disconnected:
```
nm-tool
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by rhythmiccycle on 2011-12-30
Thanks, this code was run off line

```

mike@mike-ME051:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:15:C5:66:67:C4

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:14:A5:C7:5B:F9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


mike@mike-ME051:~$ sudo iwlist scan
[sudo] password for mike: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

mike@mike-ME051:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
mike@mike-ME051:~$

```

---

### Post by wildmanne39 on 2011-12-30
Hi, there was no output from the last two commands? you did enter your password right?

Please post:
```
lsmod | grep b43
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by rhythmiccycle on 2011-12-30
I noticed that there was no out put, but I entered the code. I'll try again and post it. Btw thank you, I love Ubuntu because of the forum, I help people too when I can. thank wildmanne39

---

### Post by rhythmiccycle on 2011-12-30
here it is offline 

```


mike@mike-ME051:~$ lsmod | grep b43
b43                   318816  0 
mac80211              393459  1 b43
cfg80211              172392  2 b43,mac80211
ssb                    50682  2 b43,b44
mike@mike-ME051:~$ cat /etc/modprobe.d/blacklist.conf
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
mike@mike-ME051:~$ 


```

---

### Post by wildmanne39 on 2011-12-30
Hi, I am doing a little research I will get back to you in a few minutes.
Thanks

---

### Post by wildmanne39 on 2011-12-30
Hi, open synaptic package manager if you have it installed, if not open software center and make sure the packages with the green squares are the only packages installed under broadcom.

Is this a clean install or an upgrade? did you have any problems during the install?

This command should have given output and it is important that we see it:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
After you entered it and the other command that started with sudo did you type your password? it will not show the password in the terminal, just type it then hit enter.
Thanks

---

### Post by rhythmiccycle on 2012-01-04
sorry for taking so long. I installed synaptic, and then installed the programs you marked in the picture.

this is a clean install

```
mike@mike-ME051:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
[sudo] password for mike: 
Jan  4 19:01:58 mike-ME051 kernel: [    1.447149] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  4 19:01:58 mike-ME051 NetworkManager[538]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  4 19:01:59 mike-ME051 kernel: [   20.559059] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
Jan  4 19:02:00 mike-ME051 kernel: [   20.679437] Registered led device: b43-phy0::tx
Jan  4 19:02:00 mike-ME051 kernel: [   20.679813] Registered led device: b43-phy0::rx
Jan  4 19:02:00 mike-ME051 kernel: [   20.681003] Registered led device: b43-phy0::radio
Jan  4 19:02:00 mike-ME051 NetworkManager[538]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan  4 19:02:00 mike-ME051 NetworkManager[538]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan  4 19:02:00 mike-ME051 NetworkManager[538]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  4 19:02:00 mike-ME051 NetworkManager[538]: <info> (wlan0): now managed
Jan  4 19:02:00 mike-ME051 NetworkManager[538]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  4 19:02:00 mike-ME051 NetworkManager[538]: <info> (wlan0): bringing up device.
Jan  4 19:02:00 mike-ME051 NetworkManager[538]: <warn> (wlan0): firmware may be missing.
Jan  4 19:02:00 mike-ME051 NetworkManager[538]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  4 19:02:00 mike-ME051 NetworkManager[538]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0/ssb0:0/net/wlan0, iface: wlan0)
Jan  4 19:02:00 mike-ME051 kernel: [   21.177958] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
Jan  4 19:02:00 mike-ME051 kernel: [   21.177965] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
Jan  4 19:02:00 mike-ME051 kernel: [   21.177969] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Jan  4 19:02:00 mike-ME051 NetworkManager[538]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  4 19:13:35 mike-ME051 NetworkManager[538]: <info> kernel firmware directory '/lib/firmware' changed
Jan  4 19:13:39 mike-ME051 NetworkManager[538]: <info> (wlan0): firmware may now be available
Jan  4 19:13:39 mike-ME051 NetworkManager[538]: <info> (wlan0): device state change: unavailable -> unavailable (reason 'none') [20 20 0]
Jan  4 19:13:39 mike-ME051 NetworkManager[538]: <info> (wlan0): bringing up device.
Jan  4 19:13:39 mike-ME051 kernel: [  719.204122] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Jan  4 19:13:39 mike-ME051 NetworkManager[538]: <info> (wlan0): preparing device.
Jan  4 19:13:39 mike-ME051 NetworkManager[538]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan  4 19:13:39 mike-ME051 kernel: [  719.256872] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  4 19:13:39 mike-ME051 dbus[511]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan  4 19:13:39 mike-ME051 dbus[511]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan  4 19:13:39 mike-ME051 NetworkManager[538]: <info> wpa_supplicant started
Jan  4 19:13:40 mike-ME051 NetworkManager[538]: <info> (wlan0): supplicant interface state: starting -> ready
Jan  4 19:13:40 mike-ME051 NetworkManager[538]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  4 19:13:40 mike-ME051 NetworkManager[538]: <info> (wlan0): supplicant interface state: ready -> inactive

```

---

### Post by rhythmiccycle on 2012-01-04
Installing via  synaptic WORKED!!!!
thanks.

BTW,

in the picture you attached, what is the thing on the right of your desktop that show all the info about your PC????

---

### Post by wildmanne39 on 2012-01-04
Hi, you are one of the people that have issues installing the firmware for one reason or another and this is the way around the problem.

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and run the code one line at a time:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
watch for errors, and after it is completed unplug your wired connection and reboot.
Thanks

---

### Post by wildmanne39 on 2012-01-04
Hi, that is called a conky, they take some time to set up, it is not done automatcally with a program, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by irkan on 2012-09-07
spent more than an hour trying fix this problem, thank you for posting it [[COLOR=#DD4814]**Wild Man**[/COLOR]]("http://ubuntuforums.org/member.php?u=508533") :D. 
- i uninstalled all the broadcom files using synaptic
- downloaded your zip file
- ran the commands posted by you, and it worked without a reboot even!

cheers

---

### Post by johnhartel on 2013-01-01
i have the same problem have to hard wire to my other laptop to get on the internet ejohn@john-Latitude-D610:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux john-Latitude-D610 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:52:46 UTC 2012 i686 i686 i686 GNU/Linux
john@john-Latitude-D610:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Latitude D610 [1028:0182]
    Kernel driver in use: tg3
--
03:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card [1028:0003]
    Kernel driver in use: b43-pci-bridge
john@john-Latitude-D610:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

john@john-Latitude-D610:~$ rfkill list all
john@john-Latitude-D610:~$ lsmod
Module                  Size  Used by
snd_seq_dummy          12686  0 
bnep                   17707  2 
rfcomm                 37276  0 
bluetooth             183228  10 bnep,rfcomm
b43                   347284  0 
snd_intel8x0           33106  2 
snd_ac97_codec        105616  1 snd_intel8x0
radeon                820734  3 
joydev                 17161  0 
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80163  2 snd_intel8x0,snd_ac97_codec
mac80211              461161  1 b43
snd_seq_midi           13132  0 
ttm                    75534  1 radeon
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         47303  1 radeon
drm                   238768  5 radeon,ttm,drm_kms_helper
cfg80211              175375  2 b43,mac80211
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gpio_ich               13159  0 
dell_laptop            17161  0 
pcmcia                 39509  0 
soundcore              14599  1 snd
psmouse                84843  0 
i2c_algo_bit           13197  1 radeon
bcma                   34483  1 b43
snd_page_alloc         14036  2 snd_intel8x0,snd_pcm
microcode              18209  0 
serio_raw              13031  0 
dcdbas                 14054  1 dell_laptop
lpc_ich                16925  0 
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
ppdev                  12817  0 
mac_hid                13037  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             31968  1 
video                  18847  0 
lp                     13299  0 
parport                40753  3 ppdev,parport_pc,lp
ssb                    50087  1 b43
tg3                   130448  0

---

