---
title: "No wireless on a Dell Vostro A840 in ANY version of Ubuntu"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by richkevi on 2009-05-28
Hello All,

I am a teacher in China and recently my laptop started overheating so I purchased a second one here locally with Ubuntu Linux pre-installed...

I made a system restore cd before reformatting it to have windows XP and Linux since I use linux personally but prefer windows for classroom work/projections.

In the process of installing windows they notified me that I had used my Product key too many times and told me to buy another copy of windows, (which will happen when pigs fly...)

So I proceeded to return it to the nearly original state from the cd I created.  All was well except the wireless is not working.  I scoured the resources here and tried about everything that was posted with no change.

So I then reloaded from another Ubuntu 8.04 cd that I had without any more success.

Next I downloaded the latest 9.04 version of Ubuntu and saw great improvements in other areas but still can not connect to the wireless internet.

At this point I have tried enabling the Alternate "madwifi" driver for Atheros wireless LAN card and then rebooted, and also checked for the /etc/modprobe.d/blacklist-ath_pci.conf and commented out the list for # blacklist ath_pci...

but no change, so I went back into the hardware drivers and deactivated the Alternate drivers again.

I have read that everything works in PCLinusOS which I am downloading the iso as a possible experiment, but I like this version of Linux and do not want to "bail" at this point...

Some useful information follows:

My chipset is 
kevin@kevin:~$ lspci | grep Atheros
0c:00.0 Network controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

My kernel is
kevin@kevin:~$ cat /boot/grub/menu.lst | grep Ubuntu
title        Ubuntu 9.04, kernel 2.6.28-11-generic
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
title        Ubuntu 9.04, memtest86+

More info:
kevin@kevin:~$ lsmod
Module                  Size  Used by
isofs                  39844  1 
udf                    87716  0 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
i915                   65540  2 
drm                    96296  3 i915
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         435636  4 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_pcm,snd_seq
ath5k                 126724  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lbm_cw_mac80211       227364  1 ath5k
lbm_cw_cfg80211        73760  2 ath5k,lbm_cw_mac80211
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class              12036  1 ath5k
pcmcia                 44748  0 
wlan_scan_sta          21376  1 
soundcore              15200  1 snd
psmouse                61972  0 
video                  25360  0 
iTCO_wdt               19108  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ath_rate_sample        20608  1 
intel_agp              34108  1 
dcdbas                 15264  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                 10496  0 
serio_raw              13316  0 
output                 11008  1 video
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42696  3 drm,intel_agp
ath_pci               217912  0 
wlan                  238064  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312160  3 ath_rate_sample,ath_pci
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


Network info:

kevin@kevin:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wifi0
       version: 01
       serial: 00:17:c4:4e:5c:38
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:8d:a7:18
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=172.16.32.103 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1a:fe:46:79:1d:94
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

 the contents of /etc/network/interfaces
auto lo
iface lo inet loopback

kevin@kevin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

After all that has been tried in the past week os so... I am unsure/unwilling to do any more experimenting on my own now without some coaching.  This installation is fairly clean with the exception that I have installed the backports for this version of Linux.

I hope that I have not included too much useless information in this post... :-)

So any kind Soul that is willing to try to help me get the wireless working, I thank you in advance and am more grateful than words can express!

Also, I am a little dumb when it comes to directions so they would need to be fairly clear step-by-step...

Sincerely,

Kevin

---

### Post by dmizer on 2009-05-29
> **richkevi said:**
> led_class 12036 1 ath5k

There's your problem. You'll need to blacklist the ath5k module.

See here: [http://ubuntuforums.org/showpost.php?p=5673157&postcount=9](http://ubuntuforums.org/showpost.php?p=5673157&postcount=9)

---

### Post by richkevi on 2009-05-29
Thank you so much for your help!

in the /etc/modprobe.d/   directory I have both a blacklist, and blacklist.conf file where I have added blacklist ath5k at the end of the file. Then I have rebooted with my network cable unplugged to test the wireless and for the first time it is actually searching...  but after about 45 seconds it gets a red x and no connection.

looking at the wireless properties I have a wireless connection called TP-LINK and it is set for automatic DHCP and no security.  Mode is ad-hoc and the MTU is automatic. 

Should I be following the steps in your link to  Grab this driver:[http://snapshots.madwifi.org/madwifi...0080801.tar.gz](http://snapshots.madwifi.org/madwifi...0080801.tar.gz)  and install the madwifi?

Thanks again for your help!!! 

Kevin

---

### Post by dmizer on 2009-05-29
> **richkevi said:**
> Should I be following the steps in your link to  Grab this driver:[http://snapshots.madwifi.org/madwifi...0080801.tar.gz](http://snapshots.madwifi.org/madwifi...0080801.tar.gz)  and install the madwifi?

I am unsure, because I do not have your card. I've never had to do this, but I would want to know how to reverse the change if necessary.

---

### Post by richkevi on 2009-06-02
I just wanted to update the post...

Over the weekend I reloaded using the Ubuntu cd that came with the computer and went through all the steps that I found on [http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work/)  since his solution was very well written and seemed to be helping others... but I still had no success.

Then I tried ndwrappers with no success.  Then I reloaded a second time with a version I have on a Dell Inspiron 1721 that successfully loads the wireless drivers, but still no success.

So I reloaded for a third time the latest version of Ubuntu 9.04 that I had downloaded a week earlier.

I installed the back ports.

then the Ubuntu built essentials package, this will allow the program to compile:

sudo apt-get install build-essential

Then I installed WICD Network Manager

wget [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg)
sudo apt-key add wicd.gpg
sudo apt-get update
sudo apt-get install wicd
wicd-client -n

Then I downloaded the madwifi snapshot:

wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)

Untaedr (unzip) the newly downloaded file:

tar xvf madwifi-hal-0.10.5.6-current.tar.gz

Went into the newly created directory:

cd madwifi-hal-0.10.5.6-r3879-20081204

Then compiled the package:

make

Then install the package:

sudo make install

Then I went into /etc/modules  and made sure that ath_pci  was listed for loading.

In the /etc/modprobe.d/blacklist.conf  file I have  blacklist ath_hal

I made sure that the drivers were not loaded in the system/hardware utility.

Then I rebooted and for the first time... I had a choice in Wicd!

I put in the specific ip addresses, subnet, gateway, and dns server settings for the school and now I am able to connect!

I hope that this will help some other user out there that has tried everything they could find.  If not then please don't give up and be persistant!

Sincerely,

Kevin  :-)

---

