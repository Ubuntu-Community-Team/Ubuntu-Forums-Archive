---
title: "Help with AE1000"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by Rey117 on 2010-06-12
Hey guys i need help with my AE1000 Linksys usb wifi adapter I follow the instruction on this website. [http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558) and it shows up in my network  as (linksys linksys AE1000). I hook it up and it doesn't work. Can you guys help me out? Thanks in advance.

---

### Post by Rey117 on 2010-06-12
Bump

---

### Post by Rey117 on 2010-06-12
rey@rey-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0930:0200 Toshiba Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0830:0101 Palm, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Thats what i get with lsusb.

---

### Post by NightwishFan on 2010-06-12
I know less than the poster who made the tutorial so I probably will not be able to help. If possible perhaps find a supported model, should not be hard. Did you try using ifconfig and etc like at the end?

---

### Post by Rey117 on 2010-06-12
Yes I did but it lit up my adapter but on my networks it says that it is "disconnected"

---

### Post by NightwishFan on 2010-06-12
Did you reboot?

---

### Post by Rey117 on 2010-06-12
yes several times i even did the "sudo ifconfig ra0 up" and it turns on but it still says disconnected.

---

### Post by chili555 on 2010-06-12
> **Rey117 said:**
> rey@rey-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0930:0200 Toshiba Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0830:0101 Palm, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Thats what i get with lsusb.I don't see your Linksys. Was it plugged in at the time?

---

### Post by NightwishFan on 2010-06-12
Here is a link to another tutorial.
[http://swiss.ubuntuforums.org/showpost.php?p=9151032&postcount=10](http://swiss.ubuntuforums.org/showpost.php?p=9151032&postcount=10)

---

### Post by Rey117 on 2010-06-12
aw crap it wasn't hooked up here it is:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0930:0200 Toshiba Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 13b1:002f Linksys 
Bus 002 Device 006: ID 0830:0101 Palm, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Rey117 on 2010-06-12
I tried that one it didn't work for me..thanx though.

---

### Post by chili555 on 2010-06-12
Let's have a look at:```
dmesg | grep -i rt2
iwconfig
```Thanks.

---

### Post by Rey117 on 2010-06-12
OK..this is what i get:
rey@rey-laptop:~$ dmesg | grep -i rt2
[   19.513110] usbcore: registered new interface driver rt2870
[   19.733359] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   19.740669] Error: Driver 'rt2870' is already registered, aborting...
[   19.740714] usbcore: error -16 registering interface     driver rt2870
[   21.899618] <==== rt28xx_init, Status=0
[ 7981.251242] <==== rt28xx_init, Status=0
rey@rey-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

usb0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2010-06-12
Did you also try ndiswrapper? You should definitely ***not*** have both an ra0 and a wlan0. Let's see:```
lsmod | grep ndis
```If ndiswrapper is loaded, please do:```
sudo ndiswrapper -e rt2870
```Now reboot and let's see how your wireless is working.

---

### Post by Rey117 on 2010-06-12
rey@rey-laptop:~$ lsmod | grep ndis
rndis_wlan             24261  0 
rndis_host              7236  1 rndis_wlan
cdc_ether               4309  1 rndis_host
usbnet                 18052  3 rndis_wlan,rndis_host,cdc_ether
cfg80211              148386  4 rndis_wlan,iwlagn,iwlcore,mac80211
 and 
sudo ndiswrapper -e rt2870
[sudo] password for rey: 
couldn't delete /etc/ndiswrapper/rt2870: No such file or directory

---

### Post by Rey117 on 2010-06-12
No luck on the reboot

---

### Post by chili555 on 2010-06-12
> ,iwlcoreDo you have an internal wireless card, also? An Intel?

I don't understand this at all:> Error: Driver 'rt2870' is already registered, aborting...

---

### Post by Rey117 on 2010-06-12
Yes I do. but i got it working now. i had to sudo ifconfig ra0 up and bring down my wlan0 and reboot...I really really appreciate your help thank you.

---

### Post by chili555 on 2010-06-12
May I see:```
lsmod
sudo ifconfig wlan0 down
sudo iwconfig ra0 mode managed
iwconfig
```

---

### Post by chili555 on 2010-06-12
> **Rey117 said:**
> Yes I do. but i got it working now. i had to sudo ifconfig ra0 up and bring down my wlan0 and reboot...I really really appreciate your help thank you.Terrific! Glad it's working.

---

### Post by Rey117 on 2010-06-12
rey@rey-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
rfcomm                 40329  4 
ppdev                   6375  0 
sco                     9617  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11820  2 
l2cap                  34774  16 rfcomm,bnep
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   278890  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11072  0 
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_nat             5219  0 
nf_nat                 19501  1 iptable_nat
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
nf_conntrack           73934  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
iptable_mangle          3315  0 
iptable_filter          2791  0 
arc4                    1473  2 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rndis_wlan             24261  0 
rndis_host              7236  1 rndis_wlan
ip_tables              18390  3 iptable_nat,iptable_mangle,iptable_filter
usbhid                 40988  0 
x_tables               22429  2 iptable_nat,ip_tables
uinput                  8456  0 
iwlagn                121577  0 
iwlcore               124955  1 iwlagn
cdc_ether               4309  1 rndis_host
i915                  317872  3 
drm_kms_helper         30742  1 i915
rt3572sta             655227  1 
snd                    70978  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usb_storage            49833  0 
mac80211              238128  2 iwlagn,iwlcore
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  2 iwlcore,sdhci
hid                    83376  1 usbhid
usbnet                 18052  3 rndis_wlan,rndis_host,cdc_ether
ricoh_mmc               3416  0 
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
psmouse                64608  0 
btusb                  12969  2 
serio_raw               4918  0 
drm                   198770  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
cfg80211              148386  4 rndis_wlan,iwlagn,iwlcore,mac80211
soundcore               8052  1 snd
lp                      9336  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
parport                37160  2 ppdev,lp
bluetooth              58621  9 rfcomm,sco,bnep,l2cap,btusb
intel_agp              29225  2 i915
r8169                  39650  0 
mii                     5237  2 usbnet,r8169
ahci                   37646  2 
rey@rey-laptop:~$ sudo ifconfig wlan0 down
[sudo] password for rey: 
rey@rey-laptop:~$ sudo iwconfig ra0 mode managed
rey@rey-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"Pre"  Nickname:"RT3572STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1D:FE:B7:4C:10   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-53 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

usb0      no wireless extensions.

---

### Post by Rey117 on 2010-06-12
also i wonder why this 65 dollar usb adapter is weaker than my Intel wifi card? is there a way to boost it?

---

### Post by chili555 on 2010-06-12
Weaker? How so? I see no indication that one is stronger or weaker than the other.

---

### Post by Rey117 on 2010-06-13
well i click on the NetworkManager and it shows fewer and/or it shows that the APs has fewer bars that it shows on my intel wifi card

---

### Post by NightwishFan on 2010-06-13
Sometimes different drivers show different things. For example, my friends usb card shows a 15% signal and connects, whereas mine shows the same signal at around 40%. Anything less that 30% will refuse to connect, so that means my driver exaggerates signal strength.

---

### Post by chili555 on 2010-06-13
> **Rey117 said:**
> also i wonder why this 65 dollar usb adapter is weaker than my Intel wifi card? is there a way to boost it?Maybe your Intel is really not so bad.

You might try:```
sudo iwconfig ra0 txpower 15
```If it doesn't error out, keep increasing to 16, 17, etc. until it does. See if it helps.

---

### Post by Rey117 on 2010-06-14
Thanx guys for your help!

---

### Post by Hardtech on 2010-11-05
Is there any way I could get a break down of what you had to do exactly to get it to work?
I have almost no experience with Linux but id like to know more.....

---

### Post by techmik67 on 2011-01-17
[FONT=monospace]
[LIST=1]
[*]download ralink rt3572
[*]tar -C ~/Downloads/ -xf ~/Downloads/RT3572_Linux_STA_v2.5.0.0.bz2
[*]cd into the directory
[*]sed -ir -e  's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e  's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/'  ./os/linux/config.mk
[*]sed -ir -e 's!^#endif // RT2870 //!         {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870  //!' ./common/rtusb_dev_id.c
[*]sed -ir -e 's/\tusb_buffer_alloc/\tusb_alloc_coherent/' -e 's/\tusb_buffer_free/\tusb_free_coherent/' include/os/rt_linux.h
[*]sudo gedit common/rtusb_dev_id.c
[*]find
[*]{USB_DEVICE(0x1690,0x0744)}, /* 3572 */
[*]{USB_DEVICE(0x5A57,0x0284)}, /* Zinwell 3572 */
[*]{USB_DEVICE(0x167B,0x4001)}, /* 3572 */
[*]and
[*]add {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE1000 v1 */
[/LIST]
  14.    save and exit

[LIST=1]
[*]sudo make
[*]sudo make install
[*]sudo su -c "echo -e 'alias ra0 rt3572sta\nblacklist rt2800usb' > /etc/modprobe.d/rt3572sta.conf"
[*]You can add other blacklist modules, here's the list from the Ubuntu page:
[*]rt2870sta, rt2800usb, rt2860sta,  rt2x00usb, rt2x00lib, rt2870sta. Now's a good time to check 'lsmod' and  unload and blacklist any modules you find. *Also disable any other wifi  adapter. I had an Atheros. I had to add to the blacklist: ath9k,  ath9k_hw, ath9k_common.
[*]Then run:
[*]sudo modprobe ra0
[/LIST]



line 7-14 i had to add in recently, like, as in the last 2 or 3 days after "apt-get update/upgrade" to get it to work.
[/FONT]

---

### Post by judderwocky on 2011-02-21
> **techmik67 said:**
> [FONT=monospace]
[LIST=1]
[*]download ralink rt3572
[*]tar -C ~/Downloads/ -xf ~/Downloads/RT3572_Linux_STA_v2.5.0.0.bz2
[*]cd into the directory
[*]sed -ir -e  's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e  's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/'  ./os/linux/config.mk
[*]sed -ir -e 's!^#endif // RT2870 //!         {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870  //!' ./common/rtusb_dev_id.c
[*]sed -ir -e 's/\tusb_buffer_alloc/\tusb_alloc_coherent/' -e 's/\tusb_buffer_free/\tusb_free_coherent/' include/os/rt_linux.h
[*]sudo gedit common/rtusb_dev_id.c
[*]find
[*]{USB_DEVICE(0x1690,0x0744)}, /* 3572 */
[*]{USB_DEVICE(0x5A57,0x0284)}, /* Zinwell 3572 */
[*]{USB_DEVICE(0x167B,0x4001)}, /* 3572 */
[*]and
[*]add {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE1000 v1 */
[/LIST]
  14.    save and exit

[LIST=1]
[*]sudo make
[*]sudo make install
[*]sudo su -c "echo -e 'alias ra0 rt3572sta\nblacklist rt2800usb' > /etc/modprobe.d/rt3572sta.conf"
[*]You can add other blacklist modules, here's the list from the Ubuntu page:
[*]rt2870sta, rt2800usb, rt2860sta,  rt2x00usb, rt2x00lib, rt2870sta. Now's a good time to check 'lsmod' and  unload and blacklist any modules you find. *Also disable any other wifi  adapter. I had an Atheros. I had to add to the blacklist: ath9k,  ath9k_hw, ath9k_common.
[*]Then run:
[*]sudo modprobe ra0
[/LIST]



line 7-14 i had to add in recently, like, as in the last 2 or 3 days after "apt-get update/upgrade" to get it to work.
[/FONT]

I have done this multiple times, exactly according to the directions and I am still getting absolutely nowhere with this. 

I have got ra0 to recognize my wireless network, but it will not actually connect to it.

:(

---

### Post by mikebd on 2011-03-04
I followed the above instructions, and got  FATAL: Module rt3572sta not found.  Then I found this post and followed it too, and now it's up and running:
[I][http://ubuntuforums.org/showpost.php?p=10314062&postcount=2](http://ubuntuforums.org/showpost.php?p=10314062&postcount=2)
[/I]
I don't know whether both are required or whether just the last link is sufficient.

---

### Post by tim_phillips on 2011-10-24
I thought I'd update this thread with my solution. Credit should go to the bloke at [http://i2productions.com/lir/?p=228](http://i2productions.com/lir/?p=228) for posting the ralink linux drivers with the necessary corrections. My contribution is to configure them for DKMS (so it recompiles every time you update your kernel), and to package it into a deb file.

[http://timphillips.net/rt3572/rt3572-mod-dkms_1.0_all.deb.zip](http://timphillips.net/rt3572/rt3572-mod-dkms_1.0_all.deb.zip)

The deb file had to be zipped to allow me to upload it.

Tim.

---

### Post by chili555 on 2011-10-24
@tim--

I did:```
sudo apt-get install dkms patch fakeroot
```Next I did:```
sudo dpkg -i rt3572-mod-dkms_1.0_all.deb 
```Here is the result:> (Reading database ... 155249 files and directories currently installed.)
Preparing to replace rt3572-mod-dkms 1.0 (using rt3572-mod-dkms_1.0_all.deb) ...
Unpacking replacement rt3572-mod-dkms ...
Setting up rt3572-mod-dkms (1.0) ...
Error! rt3572sta_mod-1.0-1.O is already added!
Aborting.


Unable to load DKMS tarball /usr/share/rt3572_mod-dkms/rt3572_mod-1.0.dkms.tar.gz.
Common causes include: 
 - You must be using DKMS 2.1.0.0 or later to support binaries only
   distribution specific archives.
 - Corrupt distribution specific archive


dpkg: error processing rt3572-mod-dkms (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 rt3572-mod-dkms
:confused:

---

### Post by ghat on 2011-12-27
hi

This does not seem to work with oneirc ocelot ? kernel 3.0.0-14-generic ?

Anyone... 

G

---

