---
title: "Linksys RangePlus Wireless Network USB Adapter - WUSB100 ver2.0"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by tarikozket on 2011-02-10
hi folks!

i just installed the ubuntu 10.10[i have got dual boot with windows 7]. it sees my wireless network adapter and it connects to internet

**BUT**

[LIST]
[*]it's terrible slowly
[LIST]
[*]when i try ping google.com on windows command line its 150-200ms
[*]on ubuntu its 2500-3500ms
[*]when i try ping 192.168.1.1[my adsl modem] on windows command line its 1-2ms
[*]on ubuntu its 5-20ms
[/LIST]
 
[*]disconnects every 5 minutes
[LIST]
[*]and if you want to connect again you have to unplug and plug it again
[/LIST]
 
[*]sometimes not responsing and you again have to unplug and plug it again to work
[/LIST]
i looked up at internet and this forum, there is nothing i found. but other users are have got same problems i see. 

ubuntu uses the rt2800 driver

could you help us[users of wusb100]?

---
edit rt8000 to rt2800, sorry
---

---

### Post by chili555 on 2011-02-10
> ubuntu uses the rt8000 driverAre you sure? Please run and post:```
lsmod | grep rt2
lsusb
```Thanks.

---

### Post by tarikozket on 2011-02-10
> 
tarik@tarik-ubuntu:~$ lsmod | grep rt2
rt2800usb               8367  0 
rt2800lib              28897  1 rt2800usb
rt2x00usb               9779  2 rt2800usb,rt2800lib
rt2x00lib              27275  2 rt2800lib,rt2x00usb
mac80211              231541  2 rt2x00usb,rt2x00lib
cfg80211              144470  2 rt2x00lib,mac80211
crc_ccitt               1351  1 rt2800usb
led_class               2633  1 rt2x00lib

tarik@tarik-ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1737:0078 Linksys WUSB100 RangePlus Wireless USB Network Adapter ver. 2
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

...

---

### Post by chili555 on 2011-02-10
Ahh! The ever-popular, ever-pesky rt2800 drivers! You might install the updated versions:```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.37-generic
```It will probably take a reboot. Post back and let us know.

---

### Post by tarikozket on 2011-02-10
your code gave an error about founding file and i tried this one, worked

```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.37-maverick-generic
```

after that i reboot system manually. when opening there was a new item on grub "linux 2.35.25". i clicked it.

NOW


[LIST]
[*]working little bit more faster
[*]signal power is more real
[/LIST]
BUT

[LIST]
[*]still disconnecting sometimes[and if you want reconnect, still you have to unplug and plug it again]
[*]stability is not like as windows
[*]ping 192.168.1.1 is going like this
[LIST]
[*]5ms
[*]77ms
[*]4ms
[*]50ms
[*]6ms
[*]80ms
[/LIST]
[*]ping google.com is going like this
[LIST]
[*]56ms
[*]1013ms
[*]70ms
[*]1045ms
[*]45m
[*]1300ms
[/LIST]
[/LIST]
AND

[LIST]
[*]there is another problem: i'm getting sometimes black screen with "_" character on top left corner of screen and after that system rebooting itself like as windows blue screen
[/LIST]

---

### Post by chili555 on 2011-02-10
Let's create a new file:```
sudo gedit /etc/modprobe.d/rt2800usb.conf
```A new empty file will open. Add one line:```
options rt2800usb nohwcrypt=1
```Proofread, save and close gedit. Reboot.

If it's still not working as expected, please run and post:```
dmesg | grep rt2
```

---

### Post by tarikozket on 2011-02-11
disconnecting and freezing increased other things still same. here:

```
tarik@tarik-ubuntu:~$ dmesg | grep rt2
[   13.050816] Registered led device: rt2800usb-phy0::radio
[   13.050837] Registered led device: rt2800usb-phy0::assoc
[   13.050856] Registered led device: rt2800usb-phy0::quality
[   13.051160] usbcore: registered new interface driver rt2800usb
```

---

### Post by chili555 on 2011-02-11
I wonder if the freezing is really a wireless driver issue. Does this tell us anything useful?```
dmesg | grep -i warn
dmesg | grep -i error
sudo cat /var/log/syslog | grep -i error
sudo cat /var/log/syslog | grep -i warn
```Thanks.

---

### Post by leoprasanth on 2011-02-26
Tried installing 10.10 last week, the installation went too smooth an I'm so happy about it.

I also have the same problem with my WUSB100, connection gets disconnected frequently and the first message in syslon is " No probe response from AP, disconnecting"

I dont want to go to Vista, but unable to hook it up to the network is equivalent to turning it off! :( .....


Gurus .. Please help me stay on Ubuntu ..

---

### Post by cokeijo on 2011-03-09
> **tarikozket said:**
> your code gave an error about founding file and i tried this one, worked

```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.37-maverick-generic
```

after that i reboot system manually. (...) 

Hi, I was having the same issue (periodic disconnections) using the brazilian USB Wireless Intelibras WBN301. It was using the same problematic driver, and that wireless driver update you mention worked for me. 
Thanks.

---

### Post by tarikozket on 2011-06-22
I just installed latest version(11.04) and it rocks with WUSB100... :popcorn: :p

---

### Post by Cforcer on 2011-09-10
> **tarikozket said:**
> I just installed latest version(11.04) and it rocks with WUSB100... :popcorn: :p


I'm using WUSB100 rev.2 on 11.04 Ubuntu version and somehow cannot make it work... :neutral:

I really don't want to change back to Mcft, but due to my network problems, I'll probably be forced to... 

I've thought you've finally fixed those issues with wireless drivers, but I guess I was wrong...

works for like 5 seconds, but very slow... can make one search, then it disconects...

Please someone help me with that.... I'm trying to make it work whole day....

---

### Post by praseodym on 2011-09-10
Hi Cforcer,

please show the outputs of

```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Cforcer on 2011-09-11
> **praseodym said:**
> Hi Cforcer,

please show the outputs of

```
lsusb
lsmod
iwconfig
rfkill list
```


```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 009: ID 04b3:3107 IBM Corp. ThinkPad 800dpi Optical Travel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0078 Linksys WUSB100 RangePlus Wireless USB Network Adapter ver. 2
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
Module                  Size  Used by
isofs                  39571  0 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
cm4040_cs              13173  1 
joydev                 17322  0 
pcmcia                 39671  1 cm4040_cs
snd_hda_codec_analog    75442  1 
rt2870sta             410104  0 
arc4                   12473  2 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
rt2800usb              17907  0 
snd_seq_midi           13132  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
radeon                900494  3 
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
thinkpad_acpi          73750  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41704  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 radeon
cfg80211              156212  2 rt2x00lib,mac80211
tifm_7xx1              12898  0 
drm_kms_helper         40745  1 radeon
tifm_core              15040  1 tifm_7xx1
drm                   184164  5 radeon,ttm,drm_kms_helper
hid                    77084  1 usbhid
psmouse                73312  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
serio_raw              12990  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55295  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
nvram                  14035  1 thinkpad_acpi
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
tg3                   131476  0 
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
```

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
vboxnet0  no wireless extensions.
```

```

0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```

---

### Post by praseodym on 2011-09-11
There are 2 drivers loaded. Prevent the wrong from being loaded in the future and reload the right one:

```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf rt2870sta rt2800usb
sudo modprobe -v rt2870sta
sudo depmod -a

```
Re-plug your stick, shut off the power management and try to unblock wifi:

```
sudo iwconfig wlan0 power off
sudo rfkill unblock all
sudo service network-manager restart
```
Check:
```
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep rt287
```

---

### Post by Cforcer on 2011-09-13
I guess it worked... :p

Thank you very much.

```
wlan0     Ralink STA  ESSID:"TP-LINK_BAD3A0"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 74:EA:3A:BA:D3:A0   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=97/100  Signal level:-47 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


```
wlan0     Scan completed :
          Cell 01 - Address: 74:EA:3A:BA:D3:A0
                    Protocol:802.11b/g/n
                    ESSID:"TP-LINK_BAD3A0"
                    Mode:Managed
                    Channel:11
                    Quality:100/100  Signal level:-47 dBm  Noise level:-83 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```

```
[  176.912910] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  176.915861] usbcore: registered new interface driver rt2870
```

---

### Post by praseodym on 2011-09-13
Looks good, except that weird CCMP-settings with WPA. Try WPA2-AES encryption if possible for stability and security reasons.

---

### Post by treypal on 2011-10-13
I am having issues with 11.04 and the wusb100ver2.0 too.  This is my first Linux build, so I am new to all of this.  The network manager seems to find the card, and it will even find networks, but it never connects and is constantly asking for the WEP password, as if its incorrect, but its not.


Any Ideas?



Thanks in advance,

---

### Post by praseodym on 2011-10-13
Did you try the codes from #15? Just copy/paste the lines one by one.

---

### Post by treypal on 2011-10-14
Here is the check from #15.  I dont know how to put it into a code window.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sudo iwlist scan

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

---

### Post by praseodym on 2011-10-14
Ok, more info:

```
lsusb
lsmod
rfkill list
dmesg | grep rt2
```
Klick on Advanced Mode, mark the text and klick on the # Button for code-tags

---

### Post by treypal on 2011-10-14
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0781:5530 SanDisk Corp. Cruzer U3 4gb SDCZ36
Bus 001 Device 007: ID 1737:0078 Linksys WUSB100 v2 RangePlus Wireless Network Adapter [Ralink RT3070]
Bus 001 Device 005: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 006: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
```

```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
usb_storage            44173  1 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
i915                  505108  3 
binfmt_misc            17292  1 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
```


The last two didn't kick anything back out.

Thanks again!

---

### Post by praseodym on 2011-10-14
The device ID should be part of the driver from 11.04 and on.

Try:

```
sudo modprobe -v rt2870sta
sudo depmod -a
```
and replug the stick.

---

### Post by treypal on 2011-10-17
```
FATAL: Module rt2870sta not found.

```

I got this back from the first command.

Plugged the stick back in, it has a blue light, but its not showing up in the network manager.

---

### Post by praseodym on 2011-10-17
Strange, please show:

```
locate rt2870sta.ko | grep lib
grep rt28 /etc/modprobe.d/*
```

---

### Post by treypal on 2011-10-17
```
/lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

```

```
/etc/modprobe.d/blacklist.conf:blacklist rt2800usb
/etc/modprobe.d/blacklist.conf:blacklist rt2800usb

```


Thanks again!

---

### Post by praseodym on 2011-10-17
Add the device ID to the driver (this is [COLOR="Red"]one[/COLOR] line, copy/paste it):

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```
Again:

```
sudo modprobe -v rt2870sta
```

---

### Post by treypal on 2011-10-17
```
trey@trey-XG41:~$ sudo modprobe -v rt2870sta
install modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id
FATAL: Module rt2870sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt2870sta

```

hmm,

---

### Post by praseodym on 2011-10-17
Sure about 11.04, isnt it 11.10? Please show

```
uname -a
lsb_release -a
```
Oneiric lacks this module, Natty doesnt ;-)

---

### Post by treypal on 2011-10-17
11.10 your right.  Thats what I get for hijacking a thread...

---

### Post by praseodym on 2011-10-17
Ok,

I attach a modified driver, unpack it in /home and install it via:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
cd ~/modified-for-Linksys-WUSB-100-v2-2010_0709_RT2870_Linux_STA_v2.4.0.1/
sudo make
sudo make install
sudo rm /etc/modprobe.d/rt2870sta.conf
```
and reboot.

The device ID was added according to this thread:
[http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339](http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339)

---

### Post by treypal on 2011-10-17
ok, everything went fine, but still nothing.  It shows wireless networks as disconnected, the sticks blue light comes on intermittently.  but it wont find my network...


Thanks again for all your help.  I really love the speed and features of Ubuntu, I just need to figure out how to use it better...

---

### Post by praseodym on 2011-10-17
Check:

```
iwconfig
rfkill list
sudo iwlist scan
lsmod
dmesg | grep rt2
```
You may need to update the firmware via the package linux-firmware

---

### Post by treypal on 2011-10-18
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ra0       No scan results

```

```
 lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
usb_storage            44173  1 
uas                    17699  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
binfmt_misc            17292  1 
rt2870sta             570803  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 

```

```
dmesg | grep rt2
[    1.682424] usbcore: registered new interface driver rt2870
[    4.512324] <==== rt28xx_init, Status=0
[    5.523331] <==== rt28xx_init, Status=0

```

---

### Post by jawilljr on 2011-10-18
Treypal... you said you were using 11.10...correct?

If so then try these commaands:

```
sudo rmmod rt2870sta
sudo modprobe rt2800usb
```

Then try and connect.

If it works then you need to unblacklist rt2800usb.

Jerry

---

### Post by treypal on 2011-10-18
```
ERROR: Module rt2870sta is in use

```  

From the first command.

The second didn't return anything.


Also, should I be doing all of this with the stick plugged in or no?

---

### Post by jawilljr on 2011-10-18
> **treypal said:**
> ```
ERROR: Module rt2870sta is in use

```  

From the first command.

The second didn't return anything.


Also, should I be doing all of this with the stick plugged in or no?

The try this:

```
sudo rmmod -f rt2870sta
```

Then try to connect.

Jerry

---

### Post by treypal on 2011-10-18
```
ERROR: Removing 'rt2870sta': Resource temporarily unavailable
```

no return from the first code.

---

### Post by jawilljr on 2011-10-18
Ok try this:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

and on these lines:

```
blacklist rt2800usb
```

make it look like this:

```
#blacklist rt2800usb
```

All you doing is commenting those lines...

Reboot with the dongle in and try and connect.

Jerry

---

### Post by treypal on 2011-10-19
there were two "blacklist rt2800usb" in that file.  I commented out both.  When I click on the network manager, wireless shows up, but no networks.  The stick blinks its blue light, but thats about it.

---

### Post by praseodym on 2011-10-19
Blacklist the rt2870sta instead and reboot.

---

### Post by treypal on 2011-10-19
blacklisted rt2870sta, still nothing.  Wireless shows up in the network manager, but it wont find a network.

---

### Post by praseodym on 2011-10-19
Ok, check:

```
iwconfig
rfkill list
sudo iwlist scan
lsmod
iwlist chan
cat /etc/resolv.conf
route -n
dmesg | grep rt2
```

---

### Post by treypal on 2011-10-19
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
rfkill list
trey@trey-XG41:~$ sudo iwlist scan
[sudo] password for trey: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ra0       No scan results

```

```
lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
usbhid                 41905  0 
usb_storage            44173  1 
uas                    17699  0 
hid                    77367  1 usbhid
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
i915                  505108  3 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
rt2870sta             570803  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 

```

```
iwlist chan
lo        no frequency information.

eth0      no frequency information.

eth1      no frequency information.

ra0       11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)

```

The domain is my hardwire at work.
```
cat /etc/resolv.conf
# Generated by NetworkManager
domain wft.root.loc
search wft.root.loc
nameserver 170.133.9.7
nameserver 170.133.9.9
nameserver 170.133.2.37

```

```
cat /etc/resolv.conf
# Generated by NetworkManager
domain wft.root.loc
search wft.root.loc
nameserver 170.133.9.7
nameserver 170.133.9.9
nameserver 170.133.2.37
trey@trey-XG41:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.96.165.15    0.0.0.0         UG    0      0        0 eth0
10.96.165.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.96.165.15    0.0.0.0         UG    0      0        0 eth0
10.96.165.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

```

```
dmesg | grep rt2
[    2.470510] usbcore: registered new interface driver rt2870
[    4.360394] <==== rt28xx_init, Status=0
[    5.425858] <==== rt28xx_init, Status=0
```


Once again, thanks for all of your help.  I really appreciate it, I am loving the OS, and once I get the wireless to work, I am going to have a pretty sweet TV computer.

---

### Post by praseodym on 2011-10-19
Remove your current wireless profile and set up a new one (not modifying).

Check after that:

```
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by treypal on 2011-10-19
I assume you mean click on edit connections from the network manager.  I did that, deleted the profile that existed.  But It wont find any wireless networks.  I added mine by clicking add, but it still won't connect to it.

When I first installed the 11.04, it found my network, and seemed to connect, but it kept asking for the security key.  When I updated to 11.1 it quit finding the network altogether.

---

### Post by praseodym on 2011-10-19
Try Wicd instead:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Choose **ra0** as interface name and **wext** as driver. Deactivate the NM in Autostart and login again

---

### Post by treypal on 2011-10-19
How do I chose ra0 as interface and wext as driver.  There was never an option for this.

I went to startup applications and NM was not in there.  Actually the only thing that was in there is evolution alarm notify, and the wicd network manager.  Is that what needs to be disabled?  Or am I looking to disable the 'stock' NM?


Thanks,

---

### Post by praseodym on 2011-10-19
If Wicd is installed, remove the NM:

```
sudo apt-get remove --purge network-manager network-manager-gnome
```

---

### Post by treypal on 2011-10-19
ok, I removed NM.  

Restarted and opened Wicd Network Manager.  Wired network works, but it find my wireless network.  The AP is in the room with me, so I know there is signal.

---

### Post by praseodym on 2011-10-19
Do you have blanks or strange letters in your wireless key?

```
iwconfig
sudo iwlist scan
lsmod | grep rt2
dmesg | grep rt2
```
Maybe asked earlier: MAC-address filer in your router not allowing other clients?

---

### Post by treypal on 2011-10-19
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ra0       No scan results

```

```
rt2870sta             570803  1 
```

```
[    1.365980] usbcore: registered new interface driver rt2870
[    3.701696] <==== rt28xx_init, Status=0
[   11.151324] <==== rt28xx_init, Status=0
[  212.538035] <==== rt28xx_init, Status=0

```


No MAC address filtering or anything like that.  Just a standard linksys e4200, with WPA2/Personal encryption.  Wireless key is just numbers no spaces or anything weird.

---

### Post by praseodym on 2011-10-19
Maybe something went wrong (or I made a mistake in modifying the driver). Uninstall it via:

```
cd ~/modified-for-Linksys-WUSB-100-v2-2010_0709_RT2870_Linux_STA_v2.4.0.1/
sudo make clean
sudo make
sudo make uninstall
sudo depmod -a
sudo update-initramfs -u
```
Reboot and try this one (which already worked [here]("http://forum.ubuntuusers.de/post/3074357/")):

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/3074357/2010_0709_RT2870_Linux_STA_v2.4.0.1_mod2.tar.gz
tar xvf 2010_0709_RT2870_Linux_STA_v2.4.0.1_mod2.tar.gz
cd 2010_0709_RT2870_Linux_STA_v2.4.0.1_mod2
sudo make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo modprobe -v rt2870sta
```Replug the stick and check:

```
iwconfig
sudo iwlist scan
rfkill list
dmesg | grep rt2
lsmod
```
The package "linux-firmware" is installed (I am getting lost ;-) )?

---

### Post by treypal on 2011-10-20
when I do the sudo make install I get an error

```
~/2010_0709_RT2870_Linux_STA_v2.4.0.1_mod2$ sudo make install
make -C /home/trey/2010_0709_RT2870_Linux_STA_v2.4.0.1_mod2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/trey/2010_0709_RT2870_Linux_STA_v2.4.0.1_mod2/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/trey/2010_0709_RT2870_Linux_STA_v2.4.0.1_mod2/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/trey/2010_0709_RT2870_Linux_STA_v2.4.0.1_mod2/os/linux'
make: *** [install] Error 2

```

---

