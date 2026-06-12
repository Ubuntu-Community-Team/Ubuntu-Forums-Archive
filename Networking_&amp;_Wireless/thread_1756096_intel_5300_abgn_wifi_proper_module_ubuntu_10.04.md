---
title: "intel 5300 abgn wifi proper module ubuntu 10.04"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by theteju on 2011-05-11
I am posting this new thread because I am unable to find answer on the forum. 

My basic problem is, I found internet speed on my ubuntu 10.04 system is faster than my XP or windows 7 systems. Which rules out my ISP speed of internet which is rock solid. Also, My router is linksys E 3000 that is latest and greatest on the market. 

Having said that, I have been using ubuntu since more than 4 years now and this is first time I noticed that ubuntu is slower than XP.

Disabling ipv6 did not solve my problem. i edited /etc/nsswitch.conf file that also did not solve my problem.

So my question is, how to make sure that proper iwlwifi driver or module is loaded for my network card?

is this link any useful [http://wiki.debian.org/iwlagn](http://wiki.debian.org/iwlagn)

here is some info about my network card.


network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:c3:44:d2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.17 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:fe8fe000-fe8fffff



lsmod
Module                  Size  Used by
uvcvideo               57310  0 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
rfcomm                 33421  4 
binfmt_misc             6587  1 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_idt      52010  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                106911  0 
iwlcore               106050  1 iwlagn
usbhid                 36110  0 
dell_wmi                1793  0 
mac80211              205402  2 iwlagn,iwlcore
snd                    54180  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  287810  3 
drm_kms_helper         29329  1 i915
hid                    67096  1 usbhid
btusb                  10957  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop             6888  0 
dcdbas                  5422  1 dell_laptop
ricoh_mmc               2923  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
psmouse                63245  0 
soundcore               6620  1 snd
serio_raw               3978  0 
drm                   162345  4 i915,drm_kms_helper
led_class               2864  2 iwlcore,sdhci
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
cfg80211              126528  3 iwlagn,iwlcore,mac80211
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32200  4 
tg3                   109324  0 


Any help will be appreciated.

Thanks a lot in advance.

---

### Post by chili555 on 2011-05-12
iwlagn is the correct driver for your card. There may be another issue. May we see:```
ls /etc/modprobe.d
```Thanks.

---

### Post by theteju on 2011-05-12
ls /etc/modprobe.d
alsa-base.conf          blacklist-firewire.conf     blacklist-oss.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist.conf          blacklist-modem.conf        libpisock9.conf

---

### Post by chili555 on 2011-05-12
Let's try another approach. Please do:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn 11n_disable50=1 11n_disable=1
```Proofread, save and close gedit.

Reboot and tell us if your 5300 works better.

---

### Post by theteju on 2011-05-12
> **chili555 said:**
> Let's try another approach. Please do:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn 11n_disable50=1 11n_disable=1
```Proofread, save and close gedit.

Reboot and tell us if your 5300 works better.

I have made the changes , Unfortunately,, its got worst. Now its taking even longer to load the pages.

I am not good at reading logs but take a look at my /var/log/messages, I think the card is not doing n network. I am not sure.

See the attachment please.

Thanks.

is that it?

here is my iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     [COLOR="Red"]IEEE 802.11abg [/COLOR] ESSID:"meghdoot"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:C1:C0:7A:D2:90   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


It should do n networking, I think its not doing it. My router also sends 5 GHz frequency on it should pick that up. preferably.

---

### Post by theteju on 2011-05-12
I know I am being paranoid about this,

here is some more info 

dmesg | grep iwlagn
[   10.598854] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   10.598858] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   10.598962] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.598993] iwlagn 0000:0c:00.0: setting latency timer to 64
[   10.599048] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   10.675053] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.675155] iwlagn 0000:0c:00.0: irq 30 for MSI/MSI-X
[   11.977153] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   12.015384] iwlagn 0000:0c:00.0: [COLOR="RoyalBlue"]loaded firmware version 8.24.2.12[/COLOR]
[  181.342303] iwlagn 0000:0c:00.0: iwl_tx_agg_start on ra = c0:c1:c0:7a:d2:90 tid = 0
theteju@ubuntu:~$ dmesg | grep iwlagn | grep wlan0
theteju@ubuntu:~$ dmesg | grep wlan0
[   12.225848] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.753046] [COLOR="RoyalBlue"]wlan0: deauthenticating from c0:c1:c0:7a:d2:90 by local choice (reason=3)[/COLOR]
[   24.753186] wlan0: direct probe to AP c0:c1:c0:7a:d2:90 (try 1)
[   24.759182] wlan0: direct probe responded
[   24.759186] wlan0: authenticate with AP c0:c1:c0:7a:d2:90 (try 1)
[   24.761210] wlan0: authenticated
[   24.761234] wlan0: associate with AP c0:c1:c0:7a:d2:90 (try 1)
[   24.765459] wlan0: RX AssocResp from c0:c1:c0:7a:d2:90 (capab=0x411 status=0 aid=3)
[   24.765466] wlan0: associated
[   24.776884] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
theteju@ubuntu:~$ dmesg | grep cfg80211
[   10.410098] cfg80211: Calling CRDA to update world regulatory domain
[   10.504364] cfg80211: World regulatory domain updated:
[   24.261010] cfg80211: [COLOR="RoyalBlue"]Found new beacon on frequency: 5745 MHz (Ch 149) on phy0[/COLOR]


okey according to intel website. the latest firm ware is 8.83-5.1

secondly , it does find the 5 GHz channel but deauthenticates it.

Hope that helps to help.

thanks in advance.

---

### Post by chili555 on 2011-05-12
> options iwlagn 11n_disable50=1 11n_disable=1We're both learning as we go here. Please change the ones to zeros and reboot. Let us see if there is any change in the logs. I have another trick in my magic bag if that doesn't help.

---

### Post by theteju on 2011-05-12
I did replace those one with zeros

here is result

dmesg | grep wlan0
[   12.138552] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.781593] [COLOR="Red"]wlan0: deauthenticating from c0:c1:c0:7a:d2:90 by local choice (reason=3)[/COLOR]
[   25.781730] wlan0: direct probe to AP c0:c1:c0:7a:d2:90 (try 1)
[   25.980061] wlan0: direct probe to AP c0:c1:c0:7a:d2:90 (try 2)
[   25.986167] wlan0: direct probe responded
[   25.986173] wlan0: authenticate with AP c0:c1:c0:7a:d2:90 (try 1)
[   25.988127] wlan0: authenticated
[   25.988151] wlan0: associate with AP c0:c1:c0:7a:d2:90 (try 1)
[   25.992237] wlan0: RX AssocResp from c0:c1:c0:7a:d2:90 (capab=0x411 status=0 aid=4)
[   25.992243] wlan0: associated
[   25.998908] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
theteju@ubuntu:~$ dmesg | grep iwlagn
[   10.589549] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   10.589553] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   10.589663] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.589700] iwlagn 0000:0c:00.0: setting latency timer to 64
[   10.589760] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   10.740140] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.740247] iwlagn 0000:0c:00.0: irq 30 for MSI/MSI-X
[   11.878402] iwlagn 0000:0c:00.0: [COLOR="Blue"]firmware: requesting iwlwifi-5000-2.ucode[/COLOR]
[   11.926102] iwlagn 0000:0c:00.0: [COLOR="Red"]loaded firmware version 8.24.2.12
theteju@ubuntu:~$ iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     [COLOR="Red"]IEEE 802.11abgn[/COLOR]  ESSID:"meghdoot"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:C1:C0:7A:D2:90   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


here is the list of firmware under my /lib/firmware

-rw-r--r--  1 root root  335056 2010-12-14 11:25 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  150100 2010-12-14 11:25 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-12-14 11:25 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-12-14 11:25 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-12-14 11:25 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  340688 2011-05-12 15:56 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 2010-12-14 11:25 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  462280 2010-12-14 11:25 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 2011-02-11 09:26 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460912 2011-02-11 09:26 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root  463692 2011-03-03 11:00 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root  469780 2010-12-14 11:26 iwlwifi-6050-5.ucode


how can we make it request firmware from iwlwifi-5000-5.ucode instead of what it is requesting above.

again, it does see my 5 GHz channel but does not connect instead connects it to g network.

---

### Post by chili555 on 2011-05-12
> wlan0 IEEE 802.11abgn ESSID:"meghdoot"
Mode:Managed Frequency:2.437 GHz Access Point: C0:C1:C0:7A2:90
[COLOR="Red"]Bit Rate=1 Mb/s[/COLOR] Tx-Power=15 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=51/70 Signal level=-59 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0Please do:```
sudo iwconfig wlan0 rate auto
iwconfig
```Did it budge off of 1 Mb/s? I wonder if the signal strength has anything to do with it. Are you pretty far from the router/WAP?> how can we make it request firmware from iwlwifi-5000-5.ucode instead of what it is requesting above.You probably can't. Generally, the driver version and the hardware grab the firmware it needs and no other. I went through this with another driver magician just a few days ago. He renamed the firmware but, upon reboot, the wireless wouldn't work at all. Try it yourself.```
sudo mv /lib/firmware/iwlwifi-5000-2.ucode /lib/firmware/iwlwifi-5000-2.test
```You can always reverse it.

You might try a later version of iwlagn. Search for compat-wireless in Synaptic and install it. I'm sorry I can't give you the exact name; I'm on Natty.

---

### Post by jawilljr on 2011-05-12
```
how can we make it request firmware from iwlwifi-5000-5.ucode instead of what it is requesting above.
```

There is only one way I know of to use that firmware, and that is to upgrade your iwlagn drivers.

You can get upgraded drivers [from here.](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.38_stable_releases). I am using [This version](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.38/compat-wireless-2.6.38.2-2-ns.tar.bz2)

If you want to know how to install let me know.

BTW here is the relevant modinfo on iwlagn for that version:

```
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-5.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-3.ucode

```

Jerry

---

### Post by theteju on 2011-05-12
> **jawilljr said:**
> ```
how can we make it request firmware from iwlwifi-5000-5.ucode instead of what it is requesting above.
```

There is only one way I know of to use that firmware, and that is to upgrade your iwlagn drivers.

You can get upgraded drivers [from here.](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.38_stable_releases). I am using [This version](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.38/compat-wireless-2.6.38.2-2-ns.tar.bz2)

If you want to know how to install let me know.

BTW here is the relevant modinfo on iwlagn for that version:

```
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-5.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-3.ucode

```

Jerry

Yes, I want to know how to install the driver.
Thanks a lot in advance.

---

### Post by jawilljr on 2011-05-12
Ok, Download [this to your Downloads directory.](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.38/compat-wireless-2.6.38.2-2-ns.tar.bz2)

Just to make sure you can compile do this:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Then do these commands:

```
cd ~/Downloads
tar jxvf compat-wireless-2.6.38.2-2-ns.tar.bz2
cd compat-wireless-2.6.38.2-2-ns
make
sudo make install
```

Then reboot... hope I didn't forget a step.

Jerry

---

### Post by chili555 on 2011-05-12
> compat-wireless-[COLOR="Red"]2.6.38[/COLOR].2-2-ns.tar.bz2Is this the correct file if he's still on 10.04?

---

### Post by jawilljr on 2011-05-12
It will work.

Jerry

---

### Post by theteju on 2011-05-12
> **jawilljr said:**
> It will work.

Jerry

Okey sorry it took little late to update. I installed the new driver.

here is the update.

dmesg | grep iwlagn
[   10.863815] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.863819] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   10.863932] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.863969] iwlagn 0000:0c:00.0: setting latency timer to 64
[   10.864066] iwlagn 0000:0c:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   10.889674] iwlagn 0000:0c:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   10.889677] iwlagn 0000:0c:00.0: Device SKU: 0Xb
[   10.889679] iwlagn 0000:0c:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   10.889697] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.889858] iwlagn 0000:0c:00.0: irq 30 for MSI/MSI-X
[   11.383211] iwlagn 0000:0c:00.0: [COLOR="Blue"]loaded firmware version 8.83.5.1 build 33692[/COLOR]
[  200.401827] iwlagn 0000:0c:00.0: Aggregation not enabled for tid 0 because load = 2
[  212.757113] iwlagn 0000:0c:00.0: Aggregation not enabled for tid 0 because load = 3
[  218.677183] iwlagn 0000:0c:00.0: iwlagn_tx_agg_start on ra = c0:c1:c0:7a:d2:90 tid = 0
[  226.552160] iwlagn 0000:0c:00.0: iwlagn_tx_agg_start on ra = c0:c1:c0:7a:d2:90 tid = 0


dmesg | grep wlan0
[   17.116901] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.172489] [COLOR="Blue"]wlan0: deauthenticating from c0:c1:c0:7a:d2:90 by local choice (reason=3)[/COLOR]
[   30.172549] wlan0: authenticate with c0:c1:c0:7a:d2:90 (try 1)
[   30.178879] wlan0: authenticated
[   30.178923] wlan0: waiting for beacon from c0:c1:c0:7a:d2:90
[   30.204745] wlan0: beacon received
[   30.216046] wlan0: associate with c0:c1:c0:7a:d2:90 (try 1)
[   30.221824] wlan0: RX AssocResp from c0:c1:c0:7a:d2:90 (capab=0x411 status=0 aid=3)
[   30.221828] wlan0: associated
[   30.229313] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

I am sorry again consuming everyone's time. looks like the module is most uptodate. It does scan the channel but does not connect.

what is that (reason=3) ?

thank you all.

---

### Post by theteju on 2011-05-12
Okey, I am updating my story here,

My issue is solved for now many thanks to Jerry and Chill

After following Jerry's steps to install the new driver. the problem was my router's setting. I had both 5 GHZ and 2.5 GHz channels broadcast with same SSID and ubuntu was picking up 2.5 by default ingnoring 5 GHz channel.

fortunately my router support dual channel broadcast so I gave separate SSID to 5 GHz channel.

after reboot. I picked that net work and it was connected to the desired channel. but the speed was still slow. 

After that, I went in system ------> prefrences -----> Network connection 

and I set up the connection manually instead of auto DHCP.

and boom, the internet is fast.

here is my iwconfig after those changes.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"awesome"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: C0:C1:C0:7A:D2:91   
         [COLOR="Red"] Bit Rate=240 Mb/s [/COLOR]  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3195  Invalid misc:30   Missed beacon:0

pan0      no wireless extensions.

Also,, make sure your WMV is enable on router settings under Qos. I read it somewhere.

This has been a challenge. but I am happy at the end of day. I dont have to go into XP hopefully anymore. LoL

Thanks much.

---

### Post by chili555 on 2011-05-13
Awesome, indeed! Glad it's working and this thread will help many searchers trying to get N speeds in iwlagn. Great work, guys.

---

### Post by desmane on 2011-05-26
nice thread, compiling and report back if it works on my machine too. 
Will I be able to uninstall the driver?

---

### Post by chili555 on 2011-05-26
> Will I be able to uninstall the driver?Do you mean will you be able to uninstall the new driver you compiled if it doesn't work as expected? Certainly; just do:```
cd ~/Downloads/compat-wireless-2.6.38.2-2-ns
sudo make [COLOR="Red"]un[/COLOR]install
```

---

### Post by desmane on 2011-06-01
> **chili555 said:**
> Do you mean will you be able to uninstall the new driver you compiled if it doesn't work as expected? Certainly; just do:```
cd ~/Downloads/compat-wireless-2.6.38.2-2-ns
sudo make [COLOR="Red"]un[/COLOR]install
```

thank you! Driver works great though ;-) 
Nice thread!

---

### Post by tolmun on 2011-06-10
> **jawilljr said:**
> Ok, Download [this to your Downloads directory.](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.38/compat-wireless-2.6.38.2-2-ns.tar.bz2)

Just to make sure you can compile do this:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Then do these commands:

```
cd ~/Downloads
tar jxvf compat-wireless-2.6.38.2-2-ns.tar.bz2
cd compat-wireless-2.6.38.2-2-ns
make
sudo make install
```

Then reboot... hope I didn't forget a step.

Jerry

I have this issue [http://paste.ubuntu.com/623225/](http://paste.ubuntu.com/623225/) on lenovo sl500 after update lucid 10.04.

And this work flawlessly.
Thank you

---

### Post by inigopete on 2011-06-17
It's working well on 11.04 as well - I first thought to install the most recent version (compat-wireless 3.0, at time of typing) but then rapidly twigged that I needed the version that corresponded to my /lib/firmware directory. So [that same version]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.38/compat-wireless-2.6.38.2-2-ns.tar.bz2") worked for me (on 11.04) too.

Working well so far. Though I think it's installed a bunch of files I no longer need in /lib/firmware - if anyone can give me an idiot's guide to removing them (I mean, is there a "get rid of the stuff that doesn't apply to me" command) I'd really appreciate it.

Thanks!

---

### Post by chili555 on 2011-06-17
With todays large harddrives, that is, anything larger than 20 Gb, the extra firmware files are quite insignificant. It's sort of like taking a roadmap out of the glove compartment of your car so as to lighten it and improve gas mileage. 

The process is not really trivial or quick and easy but really won't do much.

---

### Post by inigopete on 2011-06-21
> **chili555 said:**
> With todays large harddrives...

That's why I asked - I'm running a Dell Mini 10v with an 8GB SSD. ;)

I haven't upgraded to a larger one because the small (fast!) drive encourages me not to clutter it up with stuff that I should keep on my NAS box or USB sticks, in other words I backup a lot more regularly. I just noticed I'm getting the "This drive has only xxx MB remaining" message a fair bit since I recompiled with the new firmware files.

Chili555, could you point me towards how complicated it might be? I don't mind if it's a lengthy automated process, I can just leave it running, it's just if it's a long iterative thing that takes a lot of interaction that I might be put off!

Thanks.

---

### Post by chili555 on 2011-06-21
Sure. Firmware is located in /lib/firmware. Open /lib/firmware in Nautilus. Your firmware is all titled iwlwifi. In a terminal, do:```
cd /lib/firmware
sudo rm -rf 3com
sudo rm -rf ar9*
etc., etc
```I am not sure I recognize all the files that are networking-related and not related to some other device. If you are not sure, I am sure you can google the answer. Do not accidentally remove firmware that is needed for some other part of your system.

Much more space consuming is the actual wireless modules themselves. For example, in my system, iwlagn is in /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwlwifi/.

If you look in /lib/modules/2.6.38-8-generic/kernel/drivers/net/ there are dozens of drivers. You could do:```
sudo rm -rf /lib/modules/2.6.38-8-generic/kernel/drivers/net/everythingthataintiwlwifi
```I know of no way to do so without going through the directory one by one.

Also, there are a lot of modules for ethernet in /lib/modules/2.6.38-8-generic/kernel/drivers/net/. rm -rf all the ones that are not your in place ethernet card.

Having laboriously done all that, you will be surprised to find that when a new kernel, called linux-image here in Ubuntuworld, is installed by Update Manager, all these unwelcome guests have returned! Please print off or jot down the process so you can repeat it.

You can also remove the old kernel in Synaptic. As well, you can clear your apt cache:```
sudo apt-get autoclean
```Be very careful. One slight mistake could, I suppose, amke your system unbootable.

---

### Post by H. Beijeman on 2011-07-24
I'm using debian, but I experienced the same problem. 

I've tried the solution posted in this thread, but I kept getting the same errors. 

Turned out the problem was "solved" in my case simply by copying iwlwifi-5000-1.ucode to iwlwifi-5000-5.ucode in the /lib/firmware directory.

---

