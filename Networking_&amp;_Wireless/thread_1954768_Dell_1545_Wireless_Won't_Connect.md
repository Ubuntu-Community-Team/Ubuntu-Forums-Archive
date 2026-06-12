---
title: "Dell 1545 Wireless Won't Connect"
date: 2012-04-08
forum: Networking &amp; Wireless
---

### Post by gflam on 2012-04-08
Hi I've been through a lot of different threads here and have already tried a million things but for the life of me can't get wireless working on this dell inspiron 1545. Yesterday my 3 year old Toshiba went up literally in smoke leaving me laptop less until my gf offered me her old dell to use. I pulled my hdd out of my toshiba and installed it on this dell and all was good until i realized i couldn't connect to wireless.

I've run the following commands as i've seen it needed in other threads so here's some info before i list what i've done

**lspci -nn gave this as the last line**
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

**george@george-Satellite-A305:/$ jockey-text -l**
firmware:b43 - Broadcom B43 wireless driver (Proprietary, Disabled, Not in use)
kmod:wl - Broadcom STA wireless driver (Proprietary, Enabled, In use) [auto-install]

**Now for a few things i've tried already**
Did the easy one go into system > administration > additional drivers and have activated the sta one as you can see from jockey-text -l

did this command sudo rfkill unblock all

and just many other things i'm blanking on

**Current situation**: Currently if i go off of ethernet and select wifi icon in my top bar it says wireless networks disconnected and that is greyed out

If there's anything else needed let me know but can anyone help me get my wireless working. Any help would be greatly appreciated.

---

### Post by chili555 on 2012-04-08
How about letting us see the results of these commands:```
lsmod | grep wl
dmesg | grep wl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by gflam on 2012-04-08
K sorry wasn't sure what you needed from those i got

george@george-Satellite-A305:/$ lsmod | grep wl
wl                   1959533  0 
lib80211                5058  2 lib80211_crypt_tkip,wl

george@george-Satellite-A305:/$ dmesg | grep wl
[   21.392943] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.399563] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.399577] wl 0000:0c:00.0: setting latency timer to 64

george@george-Satellite-A305:/$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Thank you for the reply

---

### Post by praseodym on 2012-04-08
Hi,

deactivate the Broadcom-STA driver, uninstall it, and download the firmware by hand:
```
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe b43
```

---

### Post by chili555 on 2012-04-08
Well; it all looks just perfect! Let's dig a bit deeper. Please run and post:```
iwconfig
sudo iwlist eth1 scan
```This assumes the wireless interface is eth1, which you should see from *iwconfig*. It may be wlan0; if it is, then post:```
sudo iwlist wlan0 scan
```Frankly, I don't see much wrong!

EDIT: I see praseodym is on the case. Bye.

---

### Post by gflam on 2012-04-08
george@george-Satellite-A305:/$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth3      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

george@george-Satellite-A305:/$ sudo iwlist eth1 scan
[sudo] password for george: 
eth1      Interface doesn't support scanning.

eth2 is what is connected right now so i didn't run that last command you had just cause you said it assumed eth1 which doesn't support scanning apparently

Holding off to try praseodym suggestion for a few though

---

### Post by chili555 on 2012-04-08
> Holding off to try praseodym suggestion for a few though> EDIT: I see praseodym is on the case. Bye. There ya go!

---

### Post by GrandpaLeaman on 2012-04-08
I have to agree with Prasoedym. I am running the Dell BCM4311 card and have never had success with the sta driver. I always use the Ubuntu documentation for installing the b43 driver. You can find it here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by gflam on 2012-04-08
okay then i'll try what prasoedym suggested now fingers crossed :)

---

### Post by gflam on 2012-04-08
Unfortunately still not working although closer now it scans and finds my networks however i select my rooms network and it will just show the up and down animation for wifi

I then tried my universities network it did the same thing however at one point it went to the upward only animation but then disconnected after some time. 

I connected to both fine on my evo 3d phone though so it's still not working for some reason. I also gave it a reboot and turned wifi on and off using the keyboard and gave it a few more tries but got the same everytime

---

### Post by gflam on 2012-04-08
I followed what GrandpaLeaman linked and in the end when i went to system > administration > additional drivers and selected the b43 driver it ran and tried to install and in the end i got SystemError: installArchives() failed

Still can't get wireless working :(

---

### Post by praseodym on 2012-04-09
Please check now:

```
iwconfig
lsmod
sudo iwlist scan
dmesg | egrep 'b43|wl'
rfkill list
```

---

### Post by gflam on 2012-04-09
**george@george-Satellite-A305:/$ iwconfig**
lo        no wireless extensions.

eth2      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

** george@george-Satellite-A305:/$ lsmod**
Module                  Size  Used by
binfmt_misc             6599  1 
vmnet                  42813  13 
vsock                  39716  0 
vmci                   67840  1 vsock
vmmon                  61066  0 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_idt      54951  1 
arc4                    1165  2 
joydev                  8767  0 
b43                   168681  0 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
i915                  296139  4 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
uvcvideo               55943  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              231959  1 b43
drm_kms_helper         30200  1 i915
dell_laptop             5730  0 
dell_wmi                2788  0 
dcdbas                  5402  1 dell_laptop
videodev               43194  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
drm                   168124  4 i915,drm_kms_helper
snd                    49102  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              144758  2 b43,mac80211
led_class               2633  1 b43
i2c_algo_bit            5168  1 i915
psmouse                59027  0 
serio_raw               4022  0 
soundcore                880  1 snd
video                  18712  1 i915
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
intel_agp              26566  2 i915
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40492  0 
ahci                   19326  2 
libahci                21728  1 ahci
ssb                    39320  1 b43
sky2                   45127  0 

**george@george-Satellite-A305:/$ sudo iwlist scan**
[sudo] password for george: 
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Network is down

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

** george@george-Satellite-A305:/$ dmesg | egrep 'b43|wl'**
[    1.065552] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.065570] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   21.783462] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   21.867394] Registered led device: b43-phy0::tx
[   21.867412] Registered led device: b43-phy0::rx
[   21.867433] Registered led device: b43-phy0::radio
[   21.941308] udev[441]: renamed network interface wlan0 to wlan1
[ 5800.031465] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[ 5800.931126] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 5800.931186] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf69fc004)
[ 5800.931198] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 5800.931216] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[ 5800.935083] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

**george@george-Satellite-A305:/$ rfkill list**
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

**george@george-Satellite-A305:/$ **

I see in rfkill list those are soft blocked i'm guessing that's my issue? should i do rfkill unblock all? I'll wait for a reply so i don't break anything :) but i think that's what i should do next right

---

### Post by praseodym on 2012-04-09
Try to reset the BIOS.

---

### Post by gflam on 2012-04-09
On my phone at the moment so haven't actually gone into the bios yet but I'm a bit noobish sorry what exactly should I reset there I'll go into my bios when home and see if its obvious but if not could you please give me a bit more detail thanks so much for the help thus far

---

### Post by praseodym on 2012-04-09
In most BIOSes its F9 to reset and F10 to save&exit.

---

### Post by gflam on 2012-04-09
Well i went into my bios but wasn't sure what i was supposed in there so i booted back up.

When i booted i hit the wifi icon and it said device not ready firmware missing or whatever so i went into system > administration > additional drivers and selected the b43 one to activate but got the installArchives() failed error again so i went and did the following again

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source

right after i did that one i was about to cd to my desktop and download the tar but wifi connected so i came here to say i was up but as soon as i logged in wifi dropped and now i can't get connected again so i'm very confused what's up now and had to go back to ethernet just to post this reply but i did browse back to the thread using wifi so i'd say we're very close but something is still not right

Anyway wasn't sure what i was supposed to reset still in my bios or what exactly i'm supposed to do when i'm in the bios

**Figured i'd post the outputs as well from what you originally suggested**
**george@george-Satellite-A305:/$ sudo modprobe -rfv wl**
FATAL: Module wl not found.
**george@george-Satellite-A305:/$ sudo apt-get remove --purge bcmwl-kernel-source**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  emerald-infinity-theme metacity-showtime-theme icon-eco-theme gtk-eco-theme
  icon-tropical-theme gtk-orange-theme gnome-eco-theme icon-bamboo-zen-theme
  emerald-tropical-theme gtk-split-theme metacity-step-into-freedom-theme
  gtk-wild-shine-theme gtk-infinity-theme emerald-wild-shine-theme
  gtk-balanzan-theme metacity-exotic-theme wallpaper-infinity-theme
  wallpaper-balanzan-theme gnome-showtime-theme icon-airlines-theme
  gnome-ellanna-theme encfs icon-step-into-freedom-theme metacity-orange-theme
  wallpaper-exotic-theme wallpaper-step-into-freedom-theme
  metacity-ellanna-theme gnome-bamboo-zen-theme icon-exotic-theme
  wallpaper-orange-theme libgdata1.4-cil icon-ellanna-theme libtext-glob-perl
  gnome-exotic-theme libdate-calc-perl metacity-tropical-theme
  metacity-eco-theme gnome-orange-theme metacity-bamboo-zen-theme
  libcarp-clan-perl wallpaper-split-theme banshee-extensions-common
  emerald-ubuntu-sunrise-theme icon-wild-shine-theme icon-infinity-theme
  icon-balanzan-theme gnome-infinity-theme gnome-split-theme
  metacity-airlines-theme librlog5 wallpaper-eco-theme gnome-tropical-theme
  libalut0 emerald-step-into-freedom-theme wallpaper-showtime-theme
  gnome-wild-shine-theme emerald-exotic-theme gnome-airlines-theme
  gtk-ellanna-theme emerald-orange-theme libnet-ip-perl libnet-dns-perl
  metacity-infinity-theme metacity-balanzan-theme wallpaper-bamboo-zen-theme
  metacity-wild-shine-theme gtk-ubuntu-sunrise-theme
  gtk-step-into-freedom-theme libfile-find-rule-perl
  gnome-ubuntu-sunrise-theme icon-split-theme wallpaper-ubuntu-sunrise-theme
  split-theme gtk-tropical-theme icon-showtime-theme gtk-bamboo-zen-theme
  emerald-showtime-theme emerald-bamboo-zen-theme gnome-balanzan-theme
  wallpaper-tropical-theme icon-ubuntu-sunrise-theme metacity-split-theme
  gtk-showtime-theme gtk-airlines-theme libdigest-hmac-perl
  bisigi-cursor-theme metacity-ubuntu-sunrise-theme wallpaper-airlines-theme
  wallpaper-ellanna-theme step-into-freedom-theme wallpaper-wild-shine-theme
  libnumber-compare-perl gnome-step-into-freedom-theme gtk-exotic-theme
  libbit-vector-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firmware-b43legacy-installer (4.178.10.4-4) ...
Not supported card here (PCI id 14e4:4315)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)[B]
george@george-Satellite-A305:/$ cd ~/Desktop/
george@george-Satellite-A305:~/Desktop$ wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)[/B]
--2012-04-09 12:46:02--  [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 99011 (97K) [application/octet-stream]
Saving to: `2480236-Broadcom_Firmware.tar.gz'

100%[======================================>] 99,011       194K/s   in 0.5s    

2012-04-09 12:46:03 (194 KB/s) - `2480236-Broadcom_Firmware.tar.gz' saved [99011/99011]

**george@george-Satellite-A305:~/Desktop$ sudo tar xvf ./2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/**
b43/
b43legacy/
b43/b0g0initvals5.fw
b43/b0g0bsinitvals5.fw
b43/a0g0initvals5.fw
b43/a0g1initvals5.fw
b43/a0g0bsinitvals5.fw
b43/a0g1bsinitvals5.fw
b43/b0g0initvals9.fw
b43/b0g0bsinitvals9.fw
b43/a0g0initvals9.fw
b43/a0g1initvals9.fw
b43/a0g0bsinitvals9.fw
b43/a0g1bsinitvals9.fw
b43/n0initvals11.fw
b43/n0bsinitvals11.fw
b43/n0absinitvals11.fw
b43/lp0initvals13.fw
b43/lp0bsinitvals13.fw
b43/b0g0initvals13.fw
b43/b0g0bsinitvals13.fw
b43/a0g1initvals13.fw
b43/a0g1bsinitvals13.fw
b43/lp0initvals14.fw
b43/lp0bsinitvals14.fw
b43/lp0initvals15.fw
b43/lp0bsinitvals15.fw
b43/ucode5.fw
b43/ucode9.fw
b43/ucode11.fw
b43/ucode13.fw
b43/ucode14.fw
b43/ucode15.fw
b43/pcm5.fw
b43legacy/a0g0bsinitvals5.fw
b43legacy/b0g0initvals2.fw
b43legacy/b0g0initvals5.fw
b43legacy/b0g0bsinitvals2.fw
b43legacy/a0g1initvals5.fw
b43legacy/a0g0initvals2.fw
b43legacy/a0g1bsinitvals5.fw
b43legacy/a0g0initvals5.fw
b43legacy/b0g0bsinitvals5.fw
b43legacy/a0g0bsinitvals2.fw
b43legacy/pcm5.fw
b43legacy/pcm4.fw
b43legacy/ucode11.fw
b43legacy/ucode5.fw
b43legacy/ucode4.fw
b43legacy/ucode2.fw
[B]george@george-Satellite-A305:~/Desktop$ sudo modprobe b43
george@george-Satellite-A305:~/Desktop$ [/B]

---

### Post by praseodym on 2012-04-09
Reboot?

---

### Post by gflam on 2012-04-09
well going to my bios required a reboot so i have rebooted numerous times but i'll do another just for kicks

** Edit**
After the reboot same thing it tries to connect but never connects to my wireless i just get the upwards wifi animation where it looks like it's going to connect and then it disconnects

**Edit 2**
Tried a few more things and then ran those commands you asked for last time so here's my updated info now

**george@george-Satellite-A305:/$ iwconfig**
lo        no wireless extensions.

eth2      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"UDel"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

**george@george-Satellite-A305:/$ lsmod**
Module                  Size  Used by
binfmt_misc             6599  1 
vmnet                  42813  13 
vsock                  39716  0 
vmci                   67840  1 vsock
vmmon                  61066  0 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_idt      54951  1 
arc4                    1165  2 
b43                   168681  0 
uvcvideo               55943  0 
joydev                  8767  0 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
dell_wmi                2788  0 
videodev               43194  1 uvcvideo
snd_seq_midi            4588  0 
v4l1_compat            13359  2 uvcvideo,videodev
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
i915                  296139  4 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231959  1 b43
drm_kms_helper         30200  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop             5730  0 
drm                   168124  4 i915,drm_kms_helper
cfg80211              144758  2 b43,mac80211
led_class               2633  1 b43
dcdbas                  5402  1 dell_laptop
intel_agp              26566  2 i915
i2c_algo_bit            5168  1 i915
psmouse                59027  0 
snd                    49102  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18712  1 i915
serio_raw               4022  0 
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40492  0 
ahci                   19326  2 
ssb                    39320  1 b43
libahci                21728  1 ahci
sky2                   45127  0 
**george@george-Satellite-A305:/$ sudo iwlist scan**
[sudo] password for george: 
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Device or resource busy

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

**george@george-Satellite-A305:/$ dmesg | egrep 'b43|wl'**
[    1.097851] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.097864] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   22.086117] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   22.162537] Registered led device: b43-phy0::tx
[   22.162557] Registered led device: b43-phy0::rx
[   22.162578] Registered led device: b43-phy0::radio
[   22.181574] udev[521]: renamed network interface wlan0 to wlan1
[   60.817255] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   66.369354] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   66.369361] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[   66.369365] b43-phy0: Controller RESET (DMA error) ...
[   66.369373] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   66.369377] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[   66.369380] b43-phy0: Controller RESET (DMA error) ...
[   66.592449] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   72.133297] b43-phy0: Controller restarted
[   72.142258] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   72.147477] bridge-wlan1: device is wireless, enabling SMAC
[   72.147481] bridge-wlan1: up
[   72.147483] bridge-wlan1: attached
[   72.157515] bridge-wlan1: disabling the bridge
[   72.168042] bridge-wlan1: down
[   72.168050] bridge-wlan1: detached
[   79.942255] wlan1: authenticate with 00:24:6c:0f:ef:e0 (try 1)
[   79.956036] wlan1: authenticated
[   79.956279] wlan1: associate with 00:24:6c:0f:ef:e0 (try 1)
[   80.153044] wlan1: associate with 00:24:6c:0f:ef:e0 (try 2)
[   80.193544] wlan1: RX AssocResp from 00:24:6c:0f:ef:e0 (capab=0x421 status=0 aid=8)
[   80.193548] wlan1: associated
[   80.194298] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   86.786161] wlan1: authenticate with 00:24:6c:0f:ef:e0 (try 1)
[   86.984036] wlan1: authenticate with 00:24:6c:0f:ef:e0 (try 2)
[   87.184047] wlan1: authenticate with 00:24:6c:0f:ef:e0 (try 3)
[   87.388032] wlan1: authentication with 00:24:6c:0f:ef:e0 timed out
[   90.657014] wlan1: no IPv6 routers present
**george@george-Satellite-A305:/$ rfkill list**
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
**george@george-Satellite-A305:/$ **

---

### Post by gflam on 2012-04-11
Any other ideas praseodym or am i basically screwed? lol

Would updating from 10.10 be a chance? i know support just ended for it but would that help my issue do you think?

---

### Post by chili555 on 2012-04-11
Would you please try:```
sudo modprobe -r b43
sudo modprobe b43 pio=1
sudo iwlist wlan1 scan
```Any improvement? If so, we can make it permanent.

---

### Post by gflam on 2012-04-11
Still just get the upward animation from wifi but it never connects it does that for a while and then disconnects anyway here's the output from what you asked for
```
**george@george-Satellite-A305:/$ sudo modprobe -r b43**
**george@george-Satellite-A305:/$ sudo modprobe b43 pio=1**
**george@george-Satellite-A305:/$ sudo iwlist wlan1 scan**
wlan1     Scan completed :
          Cell 01 - Address: 00:24:6C:10:8E:A2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"UDel Press"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000900ace916
                    Extra: Last beacon: 1176ms ago
                    IE: Unknown: 000A5544656C205072657373
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:24:6C:10:8E:A6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"UDel Help"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000900acea8c
                    Extra: Last beacon: 1176ms ago
                    IE: Unknown: 00095544656C2048656C70
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 30:46:9A:40:FE:1C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"pluto123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004df81b81af
                    Extra: Last beacon: 1064ms ago
                    IE: Unknown: 0008706C75746F313233
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B0001031047001025AC728CC524116AFDA226EFE963BEBE1021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081100000000000000000000000000000000000000
          Cell 04 - Address: 00:24:6C:10:8E:50
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"UDel"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001419069a55
                    Extra: Last beacon: 11388ms ago
                    IE: Unknown: 00045544656C
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0504030A0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:24:6C:10:8E:51
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"UDel Secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001419069bc7
                    Extra: Last beacon: 11388ms ago
                    IE: Unknown: 000B5544656C20536563757265
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0504030A0000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 06 - Address: 00:24:6C:10:8E:56
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"UDel Help"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000141905066c
                    Extra: Last beacon: 11492ms ago
                    IE: Unknown: 00095544656C2048656C70
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0504040A0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: 00:24:6C:10:86:90
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"UDel"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005ca882180
                    Extra: Last beacon: 1228ms ago
                    IE: Unknown: 00045544656C
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0504090A0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: 00:24:6C:10:86:96
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"UDel Help"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005c9ebe606
                    Extra: Last beacon: 11468ms ago
                    IE: Unknown: 00095544656C2048656C70
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0504090A0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 09 - Address: C0:3F:0E:4F:B9:60
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-19 dBm  
                    Encryption key:on
                    ESSID:"Deliver Beer to Room 201B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000147665c9192
                    Extra: Last beacon: 1116ms ago
                    IE: Unknown: 001944656C69766572204265657220746F20526F6F6D2032303142
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001019F191383CFE0C24C72939EF2A22E62C1021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: 48:5B:39:52:D4:F6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-6 dBm  
                    Encryption key:on
                    ESSID:"THE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a30468e183
                    Extra: Last beacon: 1112ms ago
                    IE: Unknown: 000C5448455F494E5445524E4554
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD850050F204104A00011010440001021041000100103B00010310470010485B3952D4F6485B3952D4F6092CA468102100074153555354656B1023000F576972656C65737320526F7574657210240007574C35323067751042000234351054000800060050F2040001101100144153555320576972656C65737320526F75746572100800020088
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: 00:24:6C:10:8E:A1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"UDel Secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000900ab52f2
                    Extra: Last beacon: 1280ms ago
                    IE: Unknown: 000B5544656C20536563757265
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010019000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 12 - Address: 2E:22:64:D6:EE:73
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=ffffff37ff6c0237
                    Extra: Last beacon: 700ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020011000000
          Cell 13 - Address: 94:44:52:C6:0A:44
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"wifibop"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007500adb61
                    Extra: Last beacon: 992ms ago
                    IE: Unknown: 000777696669626F70
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDB50050F204104A0001101044000102103B00010310470010775B6680BFDE11D38D2F944452C60A441021001A42656C6B696E20496E7465726E6174696F6E616C2C20496E632E1023001B53757266204E33303020576972656C657373204E20526F757465721024000A463744363330312076331042000E32303130343752363332363831311054000800060050F20400011011001B53757266204E33303020576972656C657373204E20526F75746572100800020086
                    IE: Unknown: DD1E00904C336E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 14 - Address: 02:28:C8:F5:1A:F5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"HPD110a.76BCE3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000c6a4e18457
                    Extra: Last beacon: 11072ms ago
                    IE: Unknown: 000E485044313130612E373642434533
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0103
                    IE: Unknown: 32043048606C
          Cell 15 - Address: 94:44:52:8C:89:F7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"Belkin.39F7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000157d06818d
                    Extra: Last beacon: 700ms ago
                    IE: Unknown: 000B42656C6B696E2E33394637
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060D0400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060D0400000000000000000000000000000000000000
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B00010310470010000000000000000110009444528C89F71021001242656C6B696E20436F72706F726174696F6E1023000A4637443133303120763110240007312E30302E32321042000E31323130323347313132333533371054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084
          Cell 16 - Address: 00:24:6C:0E:83:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"UDel"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007dbfb3181
                    Extra: Last beacon: 11068ms ago
                    IE: Unknown: 00045544656C
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0504040A0000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 17 - Address: 00:24:6C:0E:83:F1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"UDel Secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007dbfb32f2
                    Extra: Last beacon: 11068ms ago
                    IE: Unknown: 000B5544656C20536563757265
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0504040A0000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 18 - Address: 00:24:6C:0E:83:F6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"UDel Help"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007dbfb3605
                    Extra: Last beacon: 11068ms ago
                    IE: Unknown: 00095544656C2048656C70
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0504040A0000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 19 - Address: F4:EC:38:DD:AC:30
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"home_1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    ESSID:"\x06\x00\x19\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Mode:Unknown/bug
                    Extra:tsf=000000002fcb31f6
                    Extra: Last beacon: 11036ms ago
                    IE: Unknown: 0006686F6D655F31
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 331A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 341606001900000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 20 - Address: 00:24:6C:10:86:10
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:off
                    ESSID:"UDel"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000055bdb5180
                    Extra: Last beacon: 11032ms ago
                    IE: Unknown: 00045544656C
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0504040A0000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 21 - Address: 00:24:6C:10:86:11
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"UDel Secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000055bdb52fd
                    Extra: Last beacon: 11032ms ago
                    IE: Unknown: 000B5544656C20536563757265
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0504040A0000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 22 - Address: 00:24:6C:10:86:12
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"UDel Press"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000055bdb549b
                    Extra: Last beacon: 11032ms ago
                    IE: Unknown: 000A5544656C205072657373
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 23 - Address: C0:3F:0E:58:A5:62
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000087e74c2b377
                    Extra: Last beacon: 232ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001041CD9F03EB54FCA40080A7C1A237B6601021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 24 - Address: 00:24:6C:0F:EF:E0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"UDel"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f9dd4180
                    Extra: Last beacon: 10724ms ago
                    IE: Unknown: 00045544656C
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0504030A0002
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 25 - Address: 00:24:6C:0F:EF:E1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"UDel Secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f9dd42f3
                    Extra: Last beacon: 10724ms ago
                    IE: Unknown: 000B5544656C20536563757265
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0504030A0000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0019000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 26 - Address: 00:24:6C:0F:EF:E2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"UDel Press"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f9dd449c
                    Extra: Last beacon: 10724ms ago
                    IE: Unknown: 000A5544656C205072657373
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 27 - Address: 00:24:6C:0F:EF:E6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:off
                    ESSID:"UDel Help"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f9dd4612
                    Extra: Last beacon: 10724ms ago
                    IE: Unknown: 00095544656C2048656C70
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0504030A0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 28 - Address: 00:24:6C:10:8F:F0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"UDel"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000039df7db48
                    Extra: Last beacon: 516ms ago
                    IE: Unknown: 00045544656C
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 29 - Address: 00:24:6C:10:8F:F1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"UDel Secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000039df7dd8d
                    Extra: Last beacon: 516ms ago
                    IE: Unknown: 000B5544656C20536563757265
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 30 - Address: 00:24:6C:10:8F:F2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"UDel Press"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000039df7dffa
                    Extra: Last beacon: 512ms ago
                    IE: Unknown: 000A5544656C205072657373
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 31 - Address: 00:14:6C:F6:FF:7C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Get Yo Own Wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009ca5dc1b7
                    Extra: Last beacon: 120ms ago
                    IE: Unknown: 000F47657420596F204F776E2057696669
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101000EFF7F
                    IE: Unknown: DD1A00037F030100000000146CF6FF7C02146CF6FF7C64002C010E08
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 32 - Address: 00:24:6C:10:8E:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"UDel"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000900ace606
                    Extra: Last beacon: 1176ms ago
                    IE: Unknown: 00045544656C
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0504000A0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 33 - Address: 00:24:6C:10:86:91
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UDel Secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005ca8822f2
                    Extra: Last beacon: 1228ms ago
                    IE: Unknown: 000B5544656C20536563757265
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0504090A0000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 34 - Address: 00:24:6C:10:86:92
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UDel Press"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005ca882491
                    Extra: Last beacon: 1228ms ago
                    IE: Unknown: 000A5544656C205072657373
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 35 - Address: 02:21:01:BC:48:BB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"HPD110a.90D966"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000062316d42b3
                    Extra: Last beacon: 744ms ago
                    IE: Unknown: 000E485044313130612E393044393636
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0103
                    IE: Unknown: 32043048606C
          Cell 36 - Address: 00:16:B6:BA:43:0D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003aedf7d18a
                    Extra: Last beacon: 712ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
          Cell 37 - Address: 00:24:36:A9:7C:1B
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Nathan's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cc583b4180
                    Extra: Last beacon: 604ms ago
                    IE: Unknown: 00164E617468616E27732057692D4669204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016D0320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F20700010106002436A97C1C
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 38 - Address: 00:24:6C:10:8F:F6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"UDel Help"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000039df7e2ae
                    Extra: Last beacon: 512ms ago
                    IE: Unknown: 00095544656C2048656C70
                    IE: Unknown: 01079618A43048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 39 - Address: 00:24:6C:0F:ED:C1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"UDel Secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008ec295419
                    Extra: Last beacon: 504ms ago
          Cell 40 - Address: 00:24:6C:0F:ED:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
```

---

### Post by praseodym on 2012-04-12
The module "dell_laptop" may be buggy, especially, if "dell_wmi" is loaded, too. Blacklist the 1st one:

```
echo "blacklist dell_laptop" | sudo tee /etc/modprobe.d/blacklist-dell.conf
```and reboot.

---

### Post by gflam on 2012-04-12
After running that command and doing sudo reboot to reboot i was connected to wifi when i logged in. I hit firefox and it sat there trying to load for a while and (only saw a white screen) and then i got the no internet connection page from firefox then the wifi disconnected after that.

So closer i think but still no cigar :(

---

### Post by gflam on 2012-04-16
Anything else to try? i'm still stuck on ethernet :/

---

### Post by gflam on 2012-04-20
Guess I'm stuck on ethernet :(

---

