---
title: "Wireless unpredictable with Ubuntu 12.04"
date: 2012-07-04
forum: Networking &amp; Wireless
---

### Post by salmanmanekia on 2012-07-04
Hi All,

I am new to ubuntu and am facing problem with wireless connection. My wireless works sometimes . Sometime it just keeps asking for credential without connecting. Also when i try to connect it also hangs my vdsl 2 router and then i have to restart that so atleast it works for my windows machine. By the way the wired connection works.

Below are the relevant details which i saw are being provided by the people having th same problem on other threads. 

> muhammad@muhammad-ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux muhammad-ubuntu 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux
> muhammad@muhammad-ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:135b]
    Kernel driver in use: iwl3945
--
05:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
    Subsystem: Hewlett-Packard Company Device [103c:30bb]
    Kernel driver in use: e1000e> muhammad@muhammad-ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000
Bus 001 Device 006: ID 0c76:0005 JMTek, LLC. Transcend Flash disk> muhammad@muhammad-ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.> 
muhammad@muhammad-ubuntu:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no> muhammad@muhammad-ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
usb_storage            39646  1 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13516  1 
joydev                 17393  0 
snd_hda_codec_conexant    52516  1 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10962290  33 
arc4                   12473  2 
r852                   17901  0 
sm_common              16737  1 r852
psmouse                72919  0 
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
iwl3945                73152  0 
mtd                    35584  2 sm_common,nand
serio_raw              13027  0 
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
iwl_legacy             71134  1 iwl3945
r592                   17808  0 
btusb                  17912  0 
nand_ecc               13070  1 nand
mac80211              436455  2 iwl3945,iwl_legacy
snd_timer              28931  2 snd_pcm,snd_seq
memstick               15857  1 r592
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth             158438  11 rfcomm,bnep,btusb
video                  19068  0 
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
wmi                    18744  1 hp_wmi
snd                    62064  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
e1000e                140005  0 Please feel free to ask if you want me to provide more detail. I am new to ubuntu and i hope i can solve this thing and it wont be like my webcan problem for which i did not found any solutions ( [http://ubuntuforums.org/showthread.php?p=12051231#post12051231](http://ubuntuforums.org/showthread.php?p=12051231#post12051231) )

---

### Post by gordintoronto on 2012-07-04
Try this: [http://ubuntuforums.org/showthread.php?t=1876275](http://ubuntuforums.org/showthread.php?t=1876275)

Does Google not work where you live?

---

### Post by salmanmanekia on 2012-07-04
thanks...google does work .dont you have any schools in ur area where thy teach you to read...read carefully two details
1 : I am NEWBIE (i.e not confident/comfartable with ubuntu)
2 : Most importantly,  i mentioned that i have searched other threads and saw people giving the following details..what do you think did i went through each of the threads here..until i encountered the one which had similar issues as mine..I googled it..
Thanks for the first useful line...second line shows you are too busy thinking you are too smart and you do pretty good at annoying people and wasting there time..

---

### Post by salmanmanekia on 2012-07-04
> Try this: [http://ubuntuforums.org/showthread.php?t=1876275](http://ubuntuforums.org/showthread.php?t=1876275)

Does Google not work where you live?

Did not work

---

### Post by wildmanne39 on 2012-07-04
Hi please try:
```
sudo rmmod -f iwl3945

sudo modprobe iwl3945 swcrypto=1
```
do not reboot, if it work we will need to make it permanent.
Thanks

---

### Post by salmanmanekia on 2012-07-05
> **wildmanne39 said:**
> Hi please try:
```
sudo rmmod -f iwl3945

sudo modprobe iwl3945 swcrypto=1
```do not reboot, if it work we will need to make it permanent.
Thanks

Thank you wildmanne. It works..Lets make it permanent.

---

### Post by wildmanne39 on 2012-07-05
Hi, your welcome! please do:
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
A new empty file will open, paste this one line into the file.

```
options iwl3945 swcrypto=1
```

Proofread, save and close gedit, then reboot.

Please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by salmanmanekia on 2012-07-06
> **wildmanne39 said:**
> Hi, your welcome! please do:
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
A new empty file will open, paste this one line into the file.

```
options iwl3945 swcrypto=1
```

Proofread, save and close gedit, then reboot.

Please use thread tools at the top of the page to mark the thread solved.
Thanks
It doesnot work. After the reboot the same problem reoccurs. I have checked both your temporary and permenant solution couple of times. temporary solution always seems to work while the solution  mentioned in your latest thread never works.. 

> muhammad@muhammad-ubuntu:/etc/modprobe.d$ cat iwl3945.conf
options iwl3945 swcrypto=1

---

### Post by wildmanne39 on 2012-07-06
Hi, please post the contents of:
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
Thanks

---

### Post by salmanmanekia on 2012-07-06
> **wildmanne39 said:**
> Hi, please post the contents of:
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
Thanks
Hello 

Please see the contents...

> 
muhammad@muhammad-ubuntu:/etc/modprobe.d$ cat iwl3945.conf
options iwl3945 swcrypto=1 			 		

---

### Post by wildmanne39 on 2012-07-06
Hi, [COLOR="Red"]$[/COLOR] in the name of the file should have been this [COLOR="Red"]/[/COLOR] with no spaces. 

Please copy and paste the file name then reboot, see if that fixes the issue.
Thanks

---

### Post by salmanmanekia on 2012-07-06
Sorry. I am not understanding you. Through the terminal i am browsing to the location to > etc/modprobe.d/ and then seeing the content with cat command.
Here it is

> muhammad@muhammad-ubuntu:/$ cd etc/modprobe.d/
muhammad@muhammad-ubuntu:/etc/modprobe.d$ cat iwl3945.conf
options iwl3945 swcrypto=1> Hi, [COLOR=Red]$[/COLOR] in the name of the file should have been this [COLOR=Red]/[/COLOR] with no spaces. Its the linux behaviour that shows the $ and the space. :S

Also, here are the content of the directory.
> 
muhammad@muhammad-ubuntu:/etc/modprobe.d$ ls -la
total 76
drwxr-xr-x   2 root root  4096 Jul  6 11:26 .
drwxr-xr-x 143 root root 12288 Jul  6 11:45 ..
-rw-r--r--   1 root root  2507 Feb 16 05:03 alsa-base.conf
-rw-r--r--   1 root root   325 Mar 18  2011 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Mar 18  2011 blacklist.conf
-rw-r--r--   1 root root   108 May 23 16:35 blacklist-cups-usblp.conf
-rw-r--r--   1 root root   210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r--   1 root root   661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Feb 16 05:03 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Jun 24 17:31 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 Mar 18  2011 blacklist-watchdog.conf
-rw-r--r--   1 root root   127 Apr 22 10:31 dkms.conf
**-rw-r--r--   1 root root    27 Jul  6 11:26 iwl3945.conf**
**-rw-r--r--   1 root root    27 Jul  6 01:59 iwl3945.conf~**
-rw-r--r--   1 root root   157 Apr 13 01:33 nvidia-current_hybrid.conf
-rw-r--r--   1 root root   165 May  8 02:32 nvidia-current-updates_hybrid.conf
lrwxrwxrwx   1 root root    47 Jun 24 19:18 nvidia-graphics-drivers.conf -> /etc/alternatives/i386-linux-gnu_nvidia_modconf
-rw-r--r--   1 root root    30 May 18 11:02 vmwgfx-fbdev.conf


---

### Post by wildmanne39 on 2012-07-06
Hi, I see, I wanted you to copy and paste the command into the terminal then it would ask for your password and the file will open with the contents, that is why I thought the $ is in the name.

I would still like to see the contents of the file with the command copied and pasted into the terminal so I can make sure it is were we need it to be.

It is almost 4 a.m. here so I am going off line until tomorrow.

---

### Post by salmanmanekia on 2012-07-06
Hi,
No problem. Please see my comments when you have the time for it..

> muhammad@muhammad-ubuntu:/$ gksudo gedit /etc/modprobe.d/iwl3945.conf

---

### Post by wildmanne39 on 2012-07-06
Hi, please post the contents of:
```
cat /etc/modprobe.d/blacklist.conf
```
when you can not connect post the output of:
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etork | tail -n75
```
Thanks

---

### Post by salmanmanekia on 2012-07-06
Please see the output of both the commands
> 
muhammad@muhammad-ubuntu:/$ cat /etc/modprobe.d/blacklist.conf
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


and> 

muhammad@muhammad-ubuntu:/$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etork | tail -n75
[sudo] password for muhammad: 
Jul  6 19:10:41 muhammad-ubuntu wpa_supplicant[874]: Trying to associate  with 00:1a:9f:c0:05:d9 (SSID='salmanmanekia' freq=2437 MHz)
Jul  6 19:10:41 muhammad-ubuntu kernel: [11028.871033] wlan0: authenticated
Jul  6 19:10:41 muhammad-ubuntu kernel: [11028.871525] wlan0: associate with 00:1a:9f:c0:05:d9 (try 1)
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: scanning -> authenticating
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: authenticating -> associating
Jul  6 19:10:41 muhammad-ubuntu wpa_supplicant[874]: Associated with 00:1a:9f:c0:05:d9
Jul  6 19:10:41 muhammad-ubuntu kernel: [11028.885405] wlan0: RX AssocResp from 00:1a:9f:c0:05:d9 (capab=0x431 status=0 aid=1)
Jul  6 19:10:41 muhammad-ubuntu kernel: [11028.885410] wlan0: associated
Jul  6 19:10:41 muhammad-ubuntu kernel: [11028.887044] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: associating -> associated
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: associated -> 4-way handshake
Jul  6 19:10:41 muhammad-ubuntu wpa_supplicant[874]: WPA: Key negotiation completed with 00:1a:9f:c0:05:d9 [PTK=CCMP GTK=TKIP]
Jul  6 19:10:41 muhammad-ubuntu wpa_supplicant[874]:  CTRL-EVENT-CONNECTED - Connection to 00:1a:9f:c0:05:d9 completed (auth)  [id=0 id_str=]
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: 4-way handshake -> completed
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.   Connected to wireless network 'salmanmanekia'.
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): device state change: config -> ip-config (reason 'none') [50  70 0]
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info>  Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul  6 19:10:41 muhammad-ubuntu NetworkManager[778]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul  6 19:10:41 muhammad-ubuntu dhclient: Listening on LPF/wlan0/00:18:de:45:7c:d5
Jul  6 19:10:41 muhammad-ubuntu dhclient: Sending on   LPF/wlan0/00:18:de:45:7c:d5
Jul  6 19:10:41 muhammad-ubuntu dhclient: DHCPREQUEST of 84.250.117.216 on wlan0 to 255.255.255.255 port 67
Jul  6 19:10:42 muhammad-ubuntu NetworkManager[778]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul  6 19:10:42 muhammad-ubuntu NetworkManager[778]: <info>  Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul  6 19:10:42 muhammad-ubuntu NetworkManager[778]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul  6 19:10:43 muhammad-ubuntu NetworkManager[778]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jul  6 19:10:43 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): device state change: ip-config -> activated (reason 'none')  [70 100 0]
Jul  6 19:10:43 muhammad-ubuntu NetworkManager[778]: <info> Policy  set 'salmanmanekia' (wlan0) as default for IPv4 routing and DNS.
Jul  6 19:10:43 muhammad-ubuntu NetworkManager[778]: <info> Activation (wlan0) successful, device activated.
Jul  6 19:10:43 muhammad-ubuntu NetworkManager[778]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul  6 19:10:53 muhammad-ubuntu kernel: [11039.632051] wlan0: no IPv6 routers present
Jul  6 19:11:02 muhammad-ubuntu NetworkManager[778]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul  6 19:11:02 muhammad-ubuntu NetworkManager[778]: <info>  Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul  6 19:11:02 muhammad-ubuntu NetworkManager[778]: <info>  Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul  6 19:11:02 muhammad-ubuntu NetworkManager[778]: <info>  Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul  6 20:30:38 muhammad-ubuntu kernel: [15824.492065] ieee80211 phy1:  wlan0: No probe response from AP 00:1a:9f:c0:05:d9 after 500ms,  disconnecting.
Jul  6 20:30:38 muhammad-ubuntu wpa_supplicant[874]: CTRL-EVENT-DISCONNECTED bssid=00:1a:9f:c0:05:d9 reason=4
Jul  6 20:30:38 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: completed -> disconnected
Jul  6 20:30:38 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: disconnected -> scanning
Jul  6 20:30:40 muhammad-ubuntu wpa_supplicant[874]: Trying to  authenticate with 00:1a:9f:c0:05:d9 (SSID='salmanmanekia' freq=2437 MHz)
Jul  6 20:30:40 muhammad-ubuntu kernel: [15827.130333] wlan0: authenticate with 00:1a:9f:c0:05:d9 (try 1)
Jul  6 20:30:40 muhammad-ubuntu wpa_supplicant[874]: Trying to associate  with 00:1a:9f:c0:05:d9 (SSID='salmanmanekia' freq=2437 MHz)
Jul  6 20:30:40 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: scanning -> associating
Jul  6 20:30:41 muhammad-ubuntu kernel: [15827.132334] wlan0: authenticated
Jul  6 20:30:41 muhammad-ubuntu kernel: [15827.132527] wlan0: associate with 00:1a:9f:c0:05:d9 (try 1)
Jul  6 20:30:41 muhammad-ubuntu wpa_supplicant[874]: Associated with 00:1a:9f:c0:05:d9
Jul  6 20:30:41 muhammad-ubuntu kernel: [15827.146586] wlan0: RX ReassocResp from 00:1a:9f:c0:05:d9 (capab=0x431 status=0 aid=1)
Jul  6 20:30:41 muhammad-ubuntu kernel: [15827.146591] wlan0: associated
Jul  6 20:30:41 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: associating -> associated
Jul  6 20:30:41 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: associated -> 4-way handshake
Jul  6 20:30:41 muhammad-ubuntu wpa_supplicant[874]: WPA: Key negotiation completed with 00:1a:9f:c0:05:d9 [PTK=CCMP GTK=TKIP]
Jul  6 20:30:41 muhammad-ubuntu wpa_supplicant[874]:  CTRL-EVENT-CONNECTED - Connection to 00:1a:9f:c0:05:d9 completed  (reauth) [id=0 id_str=]
Jul  6 20:30:41 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: 4-way handshake -> completed
Jul  6 20:34:14 muhammad-ubuntu kernel: [16040.492073] ieee80211 phy1:  wlan0: No probe response from AP 00:1a:9f:c0:05:d9 after 500ms,  disconnecting.
Jul  6 20:34:14 muhammad-ubuntu wpa_supplicant[874]: CTRL-EVENT-DISCONNECTED bssid=00:1a:9f:c0:05:d9 reason=4
Jul  6 20:34:14 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: completed -> disconnected
Jul  6 20:34:14 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: disconnected -> scanning
Jul  6 20:34:16 muhammad-ubuntu wpa_supplicant[874]: Trying to  authenticate with 00:1a:9f:c0:05:d9 (SSID='salmanmanekia' freq=2437 MHz)
Jul  6 20:34:16 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: scanning -> authenticating
Jul  6 20:34:16 muhammad-ubuntu wpa_supplicant[874]: Trying to associate  with 00:1a:9f:c0:05:d9 (SSID='salmanmanekia' freq=2437 MHz)
Jul  6 20:34:16 muhammad-ubuntu kernel: [16042.969494] wlan0: authenticate with 00:1a:9f:c0:05:d9 (try 1)
Jul  6 20:34:16 muhammad-ubuntu kernel: [16042.971564] wlan0: authenticated
Jul  6 20:34:16 muhammad-ubuntu kernel: [16042.971999] wlan0: associate with 00:1a:9f:c0:05:d9 (try 1)
Jul  6 20:34:16 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: authenticating -> associating
Jul  6 20:34:16 muhammad-ubuntu kernel: [16042.986120] wlan0: RX ReassocResp from 00:1a:9f:c0:05:d9 (capab=0x431 status=0 aid=1)
Jul  6 20:34:16 muhammad-ubuntu kernel: [16042.986128] wlan0: associated
Jul  6 20:34:16 muhammad-ubuntu wpa_supplicant[874]: Associated with 00:1a:9f:c0:05:d9
Jul  6 20:34:16 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: associating -> associated
Jul  6 20:34:16 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: associated -> 4-way handshake
Jul  6 20:34:16 muhammad-ubuntu wpa_supplicant[874]: WPA: Key negotiation completed with 00:1a:9f:c0:05:d9 [PTK=CCMP GTK=TKIP]
Jul  6 20:34:16 muhammad-ubuntu wpa_supplicant[874]:  CTRL-EVENT-CONNECTED - Connection to 00:1a:9f:c0:05:d9 completed  (reauth) [id=0 id_str=]
Jul  6 20:34:16 muhammad-ubuntu NetworkManager[778]: <info>  (wlan0): supplicant interface state: 4-way handshake ->  completed

Thank you

---

### Post by wildmanne39 on 2012-07-07
Hi, please do:
```
sudo rmmod -f iwl3945 swcrypto=1

sudo modprobe iwl3945
```
does it work like this also.
Thanks

---

### Post by salmanmanekia on 2012-07-07
> **wildmanne39 said:**
> Hi, please do:
```
sudo rmmod -f iwl3945 swcrypto=1

sudo modprobe iwl3945
```does it work like this also.
Thanks

> muhammad@muhammad-ubuntu:~$ sudo rmmod -f iwl3945 swcrypto=1
[sudo] password for muhammad: 
ERROR: Removing 'swcrypto=1': No such file or directory
muhammad@muhammad-ubuntu:~$ sudo modprobe iwl3945

It shows the error after the first command but after the second command it does connect.

Thank YOU

---

### Post by wildmanne39 on 2012-07-07
Hi, try:
```
sudo su 
echo iwl3945 >> /etc/modules 
exit
```
Then reboot and see if it comes on if not we will add a little script that should make it work.
Thanks

---

### Post by salmanmanekia on 2012-07-07
> **wildmanne39 said:**
> Hi, try:
```
sudo su 
echo iwl3945 >> /etc/modules 
exit
```Then reboot and see if it comes on if not we will add a little script that should make it work.
Thanks

Does not comes on on the reboot . Thank you

---

### Post by wildmanne39 on 2012-07-07
Hi, alright then let's do:
```
gksudo gedit /etc/rc.local
```
Add your these lines above exit 0:
```
rmmod -f iwl3945
modprobe iwl3945
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working now.
Thanks

---

### Post by salmanmanekia on 2012-07-07
> **wildmanne39 said:**
> Hi, alright then let's do:
```
gksudo gedit /etc/rc.local
```Add your these lines above exit 0:
```
rmmod -f iwl3945
modprobe iwl3945
```Proofread carefully, save and close gedit. Reboot and tell us if it's working now.
Thanks

Doesnt work .. :( Thnxs

---

### Post by wildmanne39 on 2012-07-07
Hi, copy and paste this command into the terminal then post the contents of the folder here:
```
gksudo gedit /etc/rc.local
```
Thanks

---

### Post by salmanmanekia on 2012-07-07
> **wildmanne39 said:**
> Hi, copy and paste this command into the terminal then post the contents of the folder here:
```
gksudo gedit /etc/rc.local
```Thanks

Please see the contents of the files.. Thanks 

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rmmod -f iwl3945
modprobe iwl3945
exit 0

---

### Post by wildmanne39 on 2012-07-07
Hi, edit that file to this please:
```
rmmod -r iwl3945
rfkill unblock all
modprobe iwl3945
exit 0 
```

---

### Post by salmanmanekia on 2012-07-07
This did not work either.. Now the file contents look something like this

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rmmod -r iwl3945
rfkill unblock all
modprobe iwl3945
exit 0

---

### Post by wildmanne39 on 2012-07-08
Hi the idea that I have is change this file
```
gksudo gedit /etc/rc.local
```
to read:
```
rmmod -f iwl3945
rfkill unblock all
modprobe iwl3945
exit 0 
```
if that does not work I have no further suggestion I am afraid.

---

### Post by salmanmanekia on 2012-07-09
Hi,

Thanks for all your time and effort..The solution which you posted  a few days ago ( [http://ubuntuforums.org/showpost.php?p=12077609&postcount=6](http://ubuntuforums.org/showpost.php?p=12077609&postcount=6) ) worked temporarily. I wonder that we have address the right issue but were not able to solve it. I have this feeling that i should consider these few commands and modify and tweek it a bit so it works. Anyways all my thoughts can be naive because of my very limited experience with Ubuntu. What would you recommend as a next step from here. Because i have to solve this as it causes alot of trouble and makes the ubuntu experience unpleasent.

---

### Post by wildmanne39 on 2012-07-09
Hi, please do:
```
rm /etc/rc.local
```
Then try:
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
remove:
```
options iwl3945 swcrypto=1
```
add:
```
options iwl3945 disable_hw_scan=0
```
Proofread, save and close gedit, then reboot.
Thanks

---

### Post by salmanmanekia on 2012-07-10
This didnt work either. One thing, which can be helpful and i what i didnot mentioned earlier. As my computer starts not only the device/wireless isnt detected by the laptop but it also disables the device meaning all the lights on the device turn on and the connection to my other laptop(windows  based) is lost too. The device again starts to function correctly after a few restarts. One more thing i am wondering we have made a few changes during the last few days so is it possible that those changes override each other and in the end does not have any effect at all.. Thank you

---

### Post by wildmanne39 on 2012-07-10
Hi, can you still connect by running the commands that I gave you in the beginning?

We did change a couple of things that we could undo but they did not seem to make any difference.
Thanks

---

### Post by salmanmanekia on 2012-07-10
I tried now but it did not work. I think so previously it worked in the case that the device was still on but my computer wasnt able to connect and after giving this command it connected. But now i tried by unplugging the internet wire and restarting the machine and i noticed that as soon as i gave the password the device was off 'i.e all lights on' and then when i gave the commands it made no difference.

---

### Post by wildmanne39 on 2012-07-10
Hi, let's clean up a little please do:
```
sudo rm /etc/rc.local
```
Then:
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
Remove:
```
options iwl3945 disable_hw_scan=0
```
Add:
```
options iwl3945 swcrypto=1
```
Proofread, save and close gedit, then reboot.
Does it connect if you use the commands now?
Thanks

---

### Post by salmanmanekia on 2012-07-10
No difference. Exactly the same behaviour as explained in my previous post

---

### Post by wildmanne39 on 2012-07-10
Hi, I am afraid that I am out of idea's.

---

