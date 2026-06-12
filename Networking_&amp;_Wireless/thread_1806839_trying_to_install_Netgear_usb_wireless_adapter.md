---
title: "trying to install Netgear usb wireless adapter"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by mervbit on 2011-07-18
I need help installing a usb wireless adapter onto a Natty system.

Details:
Wireless device is a Netgear WNA1000M-100ENS new from box with mini-CD that contains windows drivers
Computer:  HP Compaq dc7600 (minitower) that is connected to internet through cable until I get the wireless working.

Environment:  Natty Narwhal (11.04) (completely updated) on one partition, and Windows XP on another partition.  USB device is installed and working great on the Windows partition.  Now I just need to get it working on Natty.

What I've done so far...   Installed ndisgtk in Natty to use as a windows driver "wrapper".  But the thread that led me to do this gives command examples that require a windows driver file of the "*.inf" type.  I can't find any .inf files in my working windows directory.  They are all *.exe or dll files.  Can anybody help me with the next step?  As far as the linux command line goes, I'm a newbie.  Thanks in advance for any help.

---

### Post by chili555 on 2011-07-18
I'm glad you didn't find the .inf files; we probably don't need them. Please open a terminal and run and post:```
lsusb
```If you find out that the usb.id is like this:> ID [COLOR="Red"]0846:9040[/COLOR] NetGear, Inc. Then your device is driven by the built-in driver ar9170usb *AND* carl9170. We will need to blacklist one and load the other and see which one does the job. Both require firmware. Back in the terminal and with the ethernet connected, please do:```
sudo apt-get install linux-firmware
```Finally, it could be that both drivers are loaded already and conflicting; let's check:```
lsmod | grep 917
```Thanks.

---

### Post by mervbit on 2011-07-18
Below are the dumps for the first two commands you suggested.  It looks like the two built-in drivers you anticipated are there.  
If I have conflicting drivers, I'll need help knowing how to 'black-list' one of them.

The last one, lsmod..., didn't give any text output back to terminal.

As always--thanks for your patience.


mmc@mmc-HP-Compaq-dc7600-Convertible-Minitower:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9041 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mmc@mmc-HP-Compaq-dc7600-Convertible-Minitower:~$ sudo apt-get install linux-firmware[sudo] password for mmc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
The following packages were automatically installed and are no longer required:
  libkcmutils4 qapt-batch libclucene0ldbl kubuntu-debug-installer libqca2 libqt4-opengl libqt4-declarative libilmbase6
  libkjsembed4 oxygen-icon-theme kdebase-runtime libqt4-sql-mysql libqt4-dbus libkemoticons4 libkdecore5 phonon
  libkidletime4 libqtwebkit4 docbook-xsl shared-desktop-ontologies mysql-common odbcinst libntrack-qt4-1
  libkatepartinterfaces4 libsolid4 virtuoso-minimal libnepomuk4 appmenu-qt libkdewebkit5 libqt4-xmlpatterns libsoprano4
  libpolkit-qt-1-1 libkdnssd4 libkparts4 plasma-scriptengine-declarative libqapt1 kdelibs5-data kdoctools libvirtodbc0
  libdbusmenu-qt2 odbcinst1debian2 libqtcore4 libgif4 libopenexr6 icoutils libthreadweaver4 libnepomukutils4
  libkmediaplayer4 libntrack0 libqt4-sql libkfile4 libknewstuff3-4 libqapt-runtime libqt4-svg phonon-backend-gstreamer
  libkpty4 libstreamanalyzer0 libphonon4 libqt4-xml libknotifyconfig4 libkntlm4 libplasma3 libqt4-network libmysqlclient16
  kdelibs-bin libqtgui4 libktexteditor4 libattica0 libkio5 libkjsapi4 libstreams0 virtuoso-opensource-6.1-common
  libqt4-script plasma-scriptengine-javascript libssh-4 libaudio2 soprano-daemon kdebase-runtime-data libreadline5 libiodbc2
  libkhtml5 libkdeui5 libkdesu5 kdelibs5-plugins libmng1 virtuoso-opensource-6.1-bin ntrack-module-libnl-0 libkrosscore4
  libnepomukquery4a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by chili555 on 2011-07-18
You have:> ID 0846:[COLOR="Red"]9041[/COLOR] NetGear, Inc. I thought it was:> ID 0846:[COLOR="Red"]9040[/COLOR] NetGear, Inc. Hey, I was just off by one! Please run:```
modinfo 8192cu | grep 9041
```We will see if the correct module is already installed.


----------------

hint to chili: compat-wireless
$ modinfo rtl8192cu | grep 9041
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*

---

### Post by mervbit on 2011-07-18
Okay, did that with this result.

mmc@mmc-HP-Compaq-dc7600-Convertible-Minitower:~$ modinfo 8192cu | grep 9041
ERROR: modinfo: could not find module 8192cu

---

### Post by chili555 on 2011-07-18
Alrighty then. Time to get our inner geek on. Please go here: [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

Download the file to your desktop. Right-click it and select Extract Here. Now open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
cd Desktop/compat
```Press Tab and the remainder will fill in. Press Enter. Now do:```
./scripts/driver-select rtlwifi
make
sudo make install
sudo modprobe rtl8192cu
```If your wireless doesn't start right up, please post:```
ls /lib/firmware/rtlwifi
```Thanks.

---

### Post by mervbit on 2011-07-18
It's working!  My inner geek is just a smidge brighter now.  Thanks Chili555 --you're the best!  If I need to go somewhere now to declare this successfully resolved or give you positive feedback, just let me know.  I'm new to using this forum and don't want to step on toes. 

Thank you.
--Merv

---

### Post by chili555 on 2011-07-18
Just before you leave in a haze of euphoria, when Update Manager installs a new kernel version or linux-image as it's known in Ubuntu World, you must rebuild for the later kernel:```
cd Desktop/compat
```Press Tab and the remainder will fill in. Now do:
```
[COLOR="Red"]./scripts/driver-select restore[/COLOR]
./scripts/driver-select rtlwifi
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
sudo modprobe rtl8192cu
```Please use thread tools at the top and Mark Solved.

Glad it's working. Have fun!

---

### Post by mervbit on 2011-07-18
Thanks for the heads-up and parting instructions.  I'll keep the extracted files around for that day.

--Merv

---

### Post by pruitthall on 2011-08-05
Chili555,

Those were the best instructions I've seen on *any* Linux forum!  Many thanks from all of us using Netgear's little micro adapter.  I'm running the latest Mint and applied it.  Unlike every other suggestion offered anywhere, yours got my adapter's light to power on.  And everything shows it's up and working.  But it will *not* connect to my Linksys router for anything.  It shows the broadcast SSID, but it refuses to connect for anything!  

I know I'm close to getting connection but cannot get the thing to hookup.  When it's running in Win7 on this same laptop, no issues.  I'd be happy to post all of my LSUSB, etc. and MintWiFi outputs.  

You really seem to have an understanding of this stuff....any ideas on this one?

Many thanks in advance.

---

### Post by chili555 on 2011-08-05
Thank you for your kind comments. Let's have a peek under the hood. Please post:```
dmesg | grep 819
sudo iwlist wlan0 scan
```Thanks.

---

### Post by pruitthall on 2011-08-05
Chili,

Sorry, I didn't see 'Page 2' as an option and missed your reply.  In advance, thank you for the help.

As requested:

mint@mint ~ $ dmesg | grep 819
[    0.181900] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.181907] pci 0000:00:0a.1: PME# disabled
[    0.181933] pci 0000:00:0a.3: [10de:0271] type 0 class 0x000b40
[    0.181953] pci 0000:00:0a.3: reg 10: [mem 0xb0040000-0xb007ffff]
[    2.618199] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   28.293272] rtl8192cu: MAC address: c4:3d:c7:76:6e:b8
[   28.293282] rtl8192cu: Board Type 0
[   28.492000] usbcore: registered new interface driver rtl8192cu
[   28.673630] rtl8192cu: MAC auto ON okay!
[   28.716885] rtl8192cu: Tx queue select: 0x05
[   28.717898] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[   28.819769] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   28.819794] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   28.819799] hda_intel: Disable MSI for Nvidia chipset
[   28.819858] HDA Intel 0000:00:10.1: setting latency timer to 64

mint@mint ~ $ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

Hope that means something to you...I'm definitely stumped.

PH

---

### Post by chili555 on 2011-08-05
It means the firmware is properly loading. There may be several sizes. Let's see what you have:```
ls -al /lib/firmware/rtlwifi
```Let's see what Network Manager is doing all this time. Try to connect and do:```
sudo cat /var/log/syslog | grep etwork | tail -n25
```

---

### Post by pruitthall on 2011-08-05
Alrighty!  Here it is:

mint@mint ~ $ ls -al /lib/firmware/rtlwifi
total 257
drwxr-xr-x  2 root root    126 Apr 25 18:59 .
drwxr-xr-x 57 root root   3304 Apr 25 18:59 ..
-rw-r--r--  1 root root  13540 Nov 18  2010 rtl8192cfw.bin
-rw-r--r--  1 root root  16014 Dec 13  2010 rtl8192cufw.bin
-rw-r--r--  1 root root  20526 Feb 11 09:07 rtl8192defw.bin
-rw-r--r--  1 root root  88856 Jan 24  2011 rtl8192sefw.bin
-rw-r--r--  1 root root 122328 Nov 18  2010 rtl8712u.bin
mint@mint ~ $ 

mint@mint ~ $ sudo cat /var/log/syslog | grep etwork | tail -n25
Aug  5 19:08:45 mint NetworkManager[3161]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Aug  5 19:08:45 mint NetworkManager[3161]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Aug  5 19:08:45 mint NetworkManager[3161]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Aug  5 19:08:45 mint NetworkManager[3161]: <info> Activation (wlan1/wireless): access point 'Auto Cana' has security, but secrets are required.
Aug  5 19:08:45 mint NetworkManager[3161]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Aug  5 19:08:45 mint NetworkManager[3161]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Aug  5 19:09:51 mint NetworkManager[3161]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Aug  5 19:09:51 mint NetworkManager[3161]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Activation (wlan1/wireless): connection 'Auto Cana' has security, and secrets exist.  No new secrets needed.
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Config: added 'ssid' value 'Cana'
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Config: added 'scan_ssid' value '1'
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Config: added 'key_mgmt' value 'NONE'
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Config: added 'auth_alg' value 'OPEN'
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Config: added 'wep_key0' value '<omitted>'
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Config: added 'wep_tx_keyidx' value '0'
Aug  5 19:09:51 mint NetworkManager[3161]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  5 19:09:51 mint NetworkManager[3161]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Aug  5 19:09:51 mint NetworkManager[3161]: <info> Config: set interface ap_scan to 1
Aug  5 19:09:51 mint NetworkManager[3161]: <info> (wlan1): supplicant connection state:  disconnected -> scanning

---

### Post by pruitthall on 2011-08-05
Chili,

I'm back online.  Don't know if you got my last posting, as I'm writing this, it doesn't show up.

It *does* connect!  Found out if I got really, really close to the router, it does finally connect.  Doesn't stay connect *long* or *far* but think we're making progress.

PH

---

### Post by pruitthall on 2011-08-05
Well, wouldn't you know it.  Problem!  All the steps went fine this go around except the last command:

mint@mint ~/Desktop/compat-wireless-2011-08-04-p $ sudo modprobe rtl8192cu
WARNING: Error inserting rtl8192c_common (/lib/modules/2.6.38-8-generic/updates/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko): Invalid argument
FATAL: Error inserting rtl8192cu (/lib/modules/2.6.38-8-generic/updates/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko): Invalid argument


I'm stuck!

---

### Post by pruitthall on 2011-08-06
chili,

Follow up with where the system is at today.

>Upon reboot, the wireless light came on.  So the last command not running, apparently cleared itself up.

>Downed the machine over the evening; today, when booted, card's light came on and it did connect with router.  

>It's pretty flaky, overall, with it's communication.  I'm about 15 feet from the router and only one room over.  The laptop hits the internet slowly and haphazardly.  You can be on Firefox and some screens will load quickly, sometimes they load as slow as if you were back on dial-up.

Overall, we're *definitely* making progress.  It's talking to the kernel, it hits the router, but it seems like there are definitely *tweaks* in store, perhaps from the authors of the actual driver itself.

But it does work!

---

### Post by chili555 on 2011-08-06
Please run and post:```
lsmod
modinfo rtl8192cu
```You should have rtl8192cu, rtlwifi, mac80211 and rtl8192c-common only loaded. Let's make sure there are no other wireless modules loaded that are conflicting. Also. is your network set to WPA and WPA2 mixed mode, which is often troublesome? WPA2 only is preferred.

---

### Post by pruitthall on 2011-08-06
Chili,

Further update on today's happenings with the Netgear.  

Let the laptop go to sleep today, was out of the house a few hours.  Upon returning, it awoke normal enough but the wireless option in networking is gone; i.e. only the 'wired network' option under the network dialogue box.  So that's another issue, but I do know this:  When you reboot and when you're close it does work, so that's some consolation.

Output you requested:

mint@mint ~ $ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
r852                   17878  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               66851  0 
hp_wmi                 13418  0 
nand_ids                8547  1 nand
rtl8192cu              96574  0 
rtl8192c_common        72798  1 rtl8192cu
sparse_keymap          13666  1 hp_wmi
nv_tco                 13331  0 
rtlwifi                94463  1 rtl8192cu
nand_ecc               13070  1 nand
psmouse                73312  0 
videodev               75143  1 uvcvideo
soundcore              12600  1 snd
mtd                    26720  2 sm_common,nand
mac80211              271190  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
k8temp                 12872  0 
serio_raw              12990  0 
i2c_nforce2            12906  0 
cfg80211              165937  2 rtlwifi,mac80211
squashfs               35973  1 
aufs                  159344  3730 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
nouveau               621970  2 
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
usb_storage            43946  1 
i2c_algo_bit           13184  1 nouveau
sdhci_pci              13623  0 
uas                    17676  0 
ssb                    45942  0 
video                  18951  1 nouveau
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pata_amd               13762  0 
forcedeth              58190  0 
sata_nv                23176  0 

mint@mint ~ $ modinfo rtl8192cu
filename:       /lib/modules/2.6.38-8-generic/updates/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     C697AD67A99D3C4F97DA95C
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3359p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3358p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        rtlwifi,mac80211,rtl8192c-common
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 

Hope this helps!

PH

---

### Post by pruitthall on 2011-08-09
Chili,

Been running this, very stable, for 3 days.  A few findings:

When you reboot, all is well.  It fires up the Netgear USB card, light is on and it connects.  

When the laptop goes to sleep (sleep, not hibernate) it doesn't come back.  Light is off the Netgear, no getting it back.

Anytime you're connected, and even when you're fairly close, it's a 'hit-or-miss' type of connection.  It shows good connection in the dialogue box, but it may / may not always hit.  Some web sites connect everytime, some do not.  

Still...it's getting somewhere at least.  

PH

---

### Post by pruitthall on 2011-08-09
Forgot to add:  WEP network, not WPA at all.  Son's games only use WEP.

PH

---

### Post by chili555 on 2011-08-10
> When the laptop goes to sleep (sleep, not hibernate) it doesn't come back. Light is off the Netgear, no getting it back.This technique sometimes helps. Please open a terminal and do:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="rtl8192cu"
```Proofread, save and close gedit.

---

### Post by pruitthall on 2011-08-11
Chili,

That did help it awaken from a sleep.  So it's helping.

Connection is still major bad; sometimes it connect, sometimes it doesn't unless you get really (<3 feet) from the Linksys router.  And if you *do* get lucky and it connects, it does stay connected; that is cool.  But your speed may be halved for a minute or two, or it may hit the web quickly.  It's utterly unpredictable.

But it's sure better than *no* wireless!

Thanks again,

PH

---

### Post by mervbit on 2011-08-13
Chili, I'm the one who started this thread, and now I'm back.

How is this possible:  I got my netgear usb wireless up and running on Natty (with your instruction) on my wireless setup at home.  So I figure I'm good to go, right?  I deliver the computer to my friends thinking now it will just detect their SSID, I can put in the new pass phrase, and that should be it.

Alas... what worked so well on my own network at home has me stumped at the different locale.  It detects their network; even tries to connect; even briefly claims it has 'established' the connection.  But I pull up the browser and it's a no-go.  I've tried adjusting their router to older WEP security, different flavors of WPA security, even no security at all.  But in every situation it fails.  BTW -- I do know their router is set properly because it is feeding me this wireless as I'm doing this on my own Natty laptop.  I try to match my laptop's security settings to the desktop, but to no avail.  

I may no longer be at this location when I read any replies, so my experimentation/response will be slow going over the next weeks while school is starting where I teach.  But if you or anyone have ideas for things to try, I'm 'all ears'.

--Merv

---

### Post by pruitthall on 2011-08-13
Merv,

I've got to thank you for starting the thread!

Chili is a truly squared away helper on Linux...

Right now, I'm (thankfully!) writing this response via my MacBook Pro.  Our HP/Netgear combo in Mint's latest is 'so/so' connecting at best.  Chili's response to you was the *only* thing that even got Mint to recognize the Netgear micro.  When I reboot, wireless *is* working, but the only way I can get it to connect is to get really, really close to the router.  That does the connection bit, but the actual *using it* to surf the 'Net is problematic at best.  Some screens pop normally, some just die.  

I think Chili has steered us both in the absolute best direction, but I'm getting the feeling that the driver itself isn't ready for prime time yet.

PH

---

### Post by mervbit on 2011-08-13
Pruitthall, what you said about distances got me thinking...  that "mini" device can't have much of an antenna in it.  The fact that I'm trying to connect through two walls and about 30 feet may be what's giving me grief.  At home I was much closer to my router as I was testing everything.  We may have to experiment with moving the router closer to this machine or something.

--Merv

---

### Post by mervbit on 2011-08-13
Okay; my brain's on vacation.  I was reminded by my friend that he's been able to use his wireless from the Windows boot on his same system.  Kind of shoots down the "small antenna" theory.

This is one of those hopefully dwindling cases where Windows is still ahead of Linux.  

So the cpu box with Natty works the wireless device just fine --that verifies the box hardware and Linux drivers.  The same box on Windows works fine in the new location.  That verifies the router and hardware setup there.  So what's left to cause problems?  Different security settings is the only thing that comes to mind for me.  Maybe I should repost this on a thread that isn't marked as solved.

--Merv

---

### Post by pruitthall on 2011-08-14
Merv,

I can't proxy for Chili, but he's really good at getting back to you with some help.  

I'm in the exact same situation; the Windows side of my laptop runs just fine, period, with the micro Netgear.  In fact, I'm writing this reply via Linux Mint and the Netgear micro.  I don't think it's a security thing; I tried WPA/WPA2/WEP/No Security and it's all the same.  I'm not Chili by a LONG shot, but it behaves to me like the Linux driver isn't turning up the micro adapter to full power.  Or something along that line.

Chili's help got both of us to where our machines at least see the micro adapter and do connect, though not nearly as consistently as the Windows driver for the same.

I'll await Chili's response and see if further troubleshooting will fine tune the issue.

PH

---

### Post by chili555 on 2011-08-15
> Alas... what worked so well on my own network at home has me stumped at the different locale. It detects their network; even tries to connect; even briefly claims it has 'established' the connection. But I pull up the browser and it's a no-go.When that happens, run:```
iwconfig
```If it is actually connected to the wireless access point, it will display its name and MAC address:```
wlan0     IEEE 802.11abg  ESSID:"[COLOR="Red"]mylilrouter[/COLOR]"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: [COLOR="Red"]99:24:56:22:D7:99[/COLOR]   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  

```Then run:```
ifconfig
```Is an IP address shown?```
wlan0     Link encap:Ethernet  HWaddr 99:19:d2:22:1b:88 
          inet addr:[COLOR="Red"]192.168.1.101[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec2:1b8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1

```If so, let's see if the router gave out a valid DNS nameserver:```
ping -c3 74.125.93.103
```If you get ping returns, you are connected to the internet. Now try:```
ping -c3 www.google.com
```If you can't get ping returns from Google, you do not have a valid DNS nameserver. The quick fix is:```
sudo su
echo "nameserver 8.8.8.8" > /etc/resolv.conf
exit
```Now try again:```
ping -c3 www.google.com
```All fixed?

These tests will help us isolate where, exactly, the problem is.

---

### Post by pruitthall on 2011-08-15
Chili,

I'm connected to the Internet right now on my Mint box running the Netgear Micro.  I swear I think Merv and my problems are similar.  It's not so much that *once* you're connected there is a problem, it's actually *getting* connected (establishing an access point connection) that is the problem.  At least for me, though Merv's problem sounds similar.

Your instructions on the prior pages have been instrumental in getting Ubuntu/Mint, etc. to actually work with the Netgear micro.  That, I have no issue with.  It's stable.  But on my machine at least, the little Netgear *will NOT* connect to the router unless I'm like four feet from it.  Once I get connected, it's *okay at best*...meaning the speeds are random, it's hit or miss sometimes.  This same hardware combination in Windows 7 is utterly stable.

I don't know if this means anything or not, but the Netgear micro has a little blue LED on it.  When in Mint, this little blue light is solid, no flashes.  When in Windows 7, this little led *flashes*.  

PH

---

### Post by qkslvrwolf on 2011-08-21
I'm trying to install the netgear wna1000m on ubuntu10.04.

lsusb shows the netgear with the same output that the original poster got.

After running through the instructions for installing the kernel module, lsmod lists the rtlwifi modules.

However, when the netgear usb device is inserted, I get this back from dmesg:  

```
[ 1513.316272] usb 2-5: new high speed USB device using ehci_hcd and address 4
[ 1513.452156] usb 2-5: configuration #1 chosen from 1 choice
[ 1513.542770] rtl8192cu: MAC address: c4:3d:c7:76:94:92
[ 1513.542782] rtl8192cu: Board Type 0
[ 1513.549483] rtl8192cu:rtl92cu_init_sw_vars():<0-0> Failed to request firmware!
[ 1513.549492] rtlwifi:rtl_usb_probe():<0-0> Can't init_sw_vars.
```

Also, you keep asking people to list /lib/firmware/rtlwifi, but that directory doesn't exist for me.  So that's no doubt why it can't request the firmware.  I just don't know how to fix it...

Thanks in advance!

---

### Post by qkslvrwolf on 2011-08-21
Ok, so just in case anyone comes after me.  I was never able to get this working with the open source drivers.  However, I was able to get it working very well with Realtek's proprietary(?) drivers.  (You still have to make/make install them, so they're give you code...maybe they're not proprietary?  Whatever, their install script works really well.)

Anyone, I went to this link:  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772)

Grabbed the 8192cu linux driver zip, unzipped it, and just ran 

```
chmod +x install.sh
sudo ./install.sh
```

from the directory that was created when I unzipped it, and voila!  I have a working usb wireless nic. 

Ironic, too, considering I spent about 3 hours trying to get the compat stuff to work.  :-)

---

### Post by braja74 on 2011-12-31
Is this resolved? Because reading through the posts it didn't seem to be. I have the same issue with a Netgear WNA1000 mini usb adapter. I tried installing the Realtek driver as per the last post, but the same issue occured when the system suspends, and I have the same problem with distance (have to be within 10' of the router). Using a DDWRT router, but it works on my WIN7 laptop. 
I've been using Linux for years and this is a major issue with every box I setup. The list of acceptable WLAN devices is always antiquated and I can't honestly encourage anyone to give Linux a go as long as this remains a consistent P.I.T.***.

---

### Post by jelabarre on 2012-01-04
It certainly isn't resolved here.  I've tried this at home *and* at work, with Ubuntu 11.10, Mint 12, Fedora 16, and Mint LMDE.  Have tried it on a T23 as well as a Thinkpad A22p (the Mint12 only there).  It *sees* the wireless networks, but can never establish a connection.  The adapter works OK under Windows (tried a couple machines there, including the A22p above), so I know the hardware is good.  Even thought it was a USB 1.1 issue, so I tried it with a PCMCIA USB2 card, no improvement.
 
Tried with the Linux driver download from Realtek, still no change.  I had tried following the directions on this site at the beginning of the thread, but things didn't match.  This *is* the device we're talking about (the USB vendor/product codes match), so probably something changed between 11.04 11.10.  I have to go back and re-do the whole Ubuntu install to retest the whole process.  Would be **MUCH** easier if AwfulDepot was still carrying those PCMCIA Atheros-based wireless cards (they worked perfectly).  BestBuy has nearly *nothing* for PCMCIA cards now, certainly nothing in wireless networking cards.

---

### Post by matbluvenger on 2012-02-15
> **qkslvrwolf said:**
> Ok, so just in case anyone comes after me.  I was never able to get this working with the open source drivers.  However, I was able to get it working very well with Realtek's proprietary(?) drivers.  (You still have to make/make install them, so they're give you code...maybe they're not proprietary?  Whatever, their install script works really well.)

Anyone, I went to this link:  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772)

Grabbed the 8192cu linux driver zip, unzipped it, and just ran 

```
chmod +x install.sh
sudo ./install.sh
```

from the directory that was created when I unzipped it, and voila!  I have a working usb wireless nic. 

Ironic, too, considering I spent about 3 hours trying to get the compat stuff to work.  :-)

Holy crap this worked instantly for me! I, too, tried the compat and couldn't get it to work after a couple tries (and even a clean reinstall of 11.10.)

Thanks qkslvrwolf!

---

### Post by matbluvenger on 2012-02-16
Sad news.... after doing the chmod fix it stayed quick for a while. But then overnight it seemed to mess up again. I didn't shut down, restart, or put it to sleep, but when I woke up this morning it was creaking along.

So then I tried the compat fix.... and my computer lost complete communication with the usb network adapter. So right now I'm in the middle of a clean re-install and it recognized the adapter again. 

However, I'm expecting it to be slow again. So I have a couple questions:

1) **chili: **I noticed the advice you gave before was for 11.04... is there anything I should be doing differently for 11.10?

2) Will this fix work if I installed 11.04 instead?

3) Is there a PCI or USB wireless network adapter that anybody knows for *sure* is compatible right out of the box with either 11.04 or (preferably) 11.10?


Thanks!

---

### Post by chili555 on 2012-02-16
> 1) chili: I noticed the advice you gave before was for 11.04... is there anything I should be doing differently for 11.10?Which post number? I suggested a lot of things in four pages!

rtl8192cu is installed by default in 11.10 if that helps.

---

### Post by finastbeans on 2012-03-10
wanted to add some info to this thread... 

Background: Trying to get wna1000m usb to run, ID 0846:9041 NetGear, Inc.

* I started with 10.04 (Lucid) and could not get compat wireless to install per description
* after hours of compiling - adjusting - compiling i updated ubuntu to 10.10 (Maverick), kernel version 2.6.35-32-generic (which killed my bootloader :( ...fixed that )
* started from scratch with the instructions listed above for compat, still no blue light after the modprobe
* saw the error message in /var/log/syslog
Mar 10 22:49:45 ubuntu kernel: [ 1270.920688] rtlwifi: Firmware rtlwifi/rtl8192cufw.bin not available
Mar 10 22:49:47 ubuntu hp[13962]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Mar 10 22:49:48 ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
* at this point verified that i had latest linux-firmware and linux-formware-nonfree --> they were already up to date
* physically removed usb wireless
* found the file on the big bad internet and installed it under /lib/firmware/rtlwifi with same permissions as the other files around it:
[git.kernel.org - linux/kernel/git/firmware/linux-firmware.git/tree - rtlwifi/]("http://git.kernel.org/?p=linux/kernel/git/firmware/linux-firmware.git;a=tree;f=rtlwifi;h=97aae7b3721b48e08450c2e29b40d4d480797b5f;hb=HEAD") 
* pushed in usb wireless, and saw the blue glow for the first time, connected to my network and voila!, wireless.

...not sure of the stability of this solution, but I'm good for now.

Thanks Chili. and everyone else who posted here.
-Mike

---

### Post by starypatyk on 2012-03-23
I can also confirm that it is possible to get the NetGear WNA1000M adapter (USB ID 0846:9041) running with the Realtek drivers in Ubuntu 10.04. However, for me it was not trivial, I had to go through the following procedure, to make it work.
[LIST]
[*]I have downloaded drivers from the Realtek site: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)
[*]After unpacking I went to the drivers directory and unpacked yet another .tar.gz file there, that contains actual driver code.
[*]In the newly created directory (rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103 in the current version) I had to find the os_dep/linux/usb_intf.c file and add the following line to the "8192CUS Dongle" group (around line 150):
[/LIST]
```
    {USB_DEVICE(0x0846, 0x9041)},//NetGear WNA1000M
```
[LIST]
[*]After that I have used the standard commands to build and install the driver:
[/LIST]
```

make
sudo make install

```This works OK now. The only disadvantage is that I have to repeat compilation and installation of the drivers whenever a new kernel version arrives, since I do not know how to configure DKMS to handle this automatically.

Thanks to others who posted here. I hope that this information may help someone being in a similar situation.

Cheers, Darek

---

### Post by Natium on 2012-05-01
I confirm it works : old presario 2528ea, dongle Netgear WNA1000M, linux Mint12 and a lot of work and forums reading. 

Thanks a lot.

---

