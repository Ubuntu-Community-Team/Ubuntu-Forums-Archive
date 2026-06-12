---
title: "lose to the antenna in ubuntu"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by mohammadamingh on 2011-08-27
hello my friends


i use wireless connection for connect to internet in ubuntu.

every thing is good until i insert my user and password in LEAP
after this i lose the antenna.

i have  two questions :
what is reason this problem?
and
how it insert my user and password? 

tip:
my laptop is vaio cw26fg and my usb adapter is alfa AWUS036H


thank you very much

---

### Post by praseodym on 2011-08-27
Hello,

which Ubuntu version do you use? Please post the following outputs:

```
uname -a
lsusb
lsmod
dmesg | egrep 'rtl8|rt2'
rfkill list
iwconfig
```

---

### Post by mohammadamingh on 2011-08-27
dear Praseodym thank you 

i use ubuntu 11.04 32bit
and
i do it and my output is:

root@ubuntu:~# uname -a
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

-----------------------------------------------------------------------------------------------------------

root@ubuntu:~# lsusb
Bus 002 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 003: ID 062a:0003 Creative Labs 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 05ca:18b5 Ricoh Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

-----------------------------------------------------------------------------------------------------------

root@ubuntu:~# lsmod
Module                  Size  Used by
r8187l                143325  0 
rtl8187                56206  0 
eeprom_93cx6           12653  1 rtl8187
rfcomm                 38125  8 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
btusb                  18160  2 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27479  4 
nvidia              10675438  44 
snd_hda_codec_realtek   255820  1 
arc4                   12473  4 
iwlagn                284569  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
iwlcore               148965  1 iwlagn
mac80211              257001  3 rtl8187,iwlagn,iwlcore
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
psmouse                73312  0 
videodev               75143  1 uvcvideo
snd_timer              28659  2 snd_pcm,snd_seq
serio_raw              12990  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sony_laptop            34432  0 
cfg80211              156212  4 rtl8187,iwlagn,iwlcore,mac80211
video                  18951  0 
intel_ips              17769  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
coretemp               13283  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
libahci                25548  1 ahci
sdhci_pci              13623  0 
sky2                   49172  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

-------------------------------------------------------------------------------------------------------------------

root@ubuntu:~# dmesg | egrep 'rtl8|rt2'
[  139.086430] ieee80211 phy1: hwaddr 00:c0:ca:3a:6f:fa, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  139.105441] rtl8187: Customer ID is 0xFF
[  139.105495] Registered led device: rtl8187-phy1::radio
[  139.105547] Registered led device: rtl8187-phy1::tx
[  139.105613] Registered led device: rtl8187-phy1::rx
[  139.106757] rtl8187: wireless switch is on
[  139.106806] usbcore: registered new interface driver rtl8187
[  139.124233] rtl8187L: Initializing module
[  139.124236] rtl8187L: Wireless extensions version 22
[  139.124238] rtl8187L: Initializing proc filesystem
[  139.124283] usbcore: registered new interface driver rtl8187L

-------------------------------------------------------------------------------------------------------------------

root@ubuntu:~# rfkill list
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

----------------------------------------------------------------------------------------------------------------------

root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"EnGenius"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"EnGenius"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:6F:55:26:16   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:14   Missed beacon:0

root@ubuntu:~#

---

### Post by praseodym on 2011-08-27
There are two drivers loaded for your stick:
```
r8187l 143325 0
rtl8187 56206 0 
```

unload both and reload the right one:

```
sudo modprobe -rf r8187l rtl8187
sudo modprobe -v rtl8187
sudo service network-manager restart
```

Your Intel-Wireless-card works properly?

Controls:
```
iwconfig
cat /etc/udev/rules.d/70-persistent-net.rules
sudo iwlist scan
lsmod
dmesg | egrep 'r8|rtl8'
```
P.S.: Why do you use the "root"-user? You shouldnt do that, use "sudo" instead

---

### Post by mohammadamingh on 2011-08-27
my Intel-Wireless-card works properly and find the antenna


and my output :




ali@ubuntu:~$ sudo modprobe -rf r8187l rtl8187
[sudo] password for ali: 

----------------------------------------------------------------------------------------------------

ali@ubuntu:~$ sudo modprobe -v rtl8187
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko 

-----------------------------------------------------------------------------------------------------

ali@ubuntu:~$ sudo service network-manager restart
network-manager start/running, process 2005

-----------------------------------------------------------------------------------------------------

ali@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"EnGenius"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"EnGenius"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:6F:55:26:16   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:12   Missed beacon:0

-----------------------------------------------------------------------------------------------------

ali@ubuntu:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4380 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="54:42:49:03:ab:3c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x422c (iwlagn)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:14:47:14:50", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0bda:0x8187 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:c0:ca:3a:6f:fa", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
ali@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

wlan1     Scan completed :
          Cell 01 - Address: 00:02:6F:55:26:16
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"EnGenius"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000033f2075181
                    Extra: Last beacon: 248ms ago
                    IE: Unknown: 0008456E47656E697573
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010030FF7F

--------------------------------------------------------------------------------------------------

ali@ubuntu:~$ lsmod
Module                  Size  Used by
rtl8187                56206  0 
eeprom_93cx6           12653  1 rtl8187
rfcomm                 38125  8 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
btusb                  18160  2 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27479  4 
nvidia              10675438  44 
snd_hda_codec_realtek   255820  1 
arc4                   12473  4 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
iwlagn                284569  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               148965  1 iwlagn
intel_ips              17769  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              257001  3 rtl8187,iwlagn,iwlcore
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
psmouse                73312  0 
serio_raw              12990  0 
cfg80211              156212  4 rtl8187,iwlagn,iwlcore,mac80211
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sony_laptop            34432  0 
video                  18951  0 
coretemp               13283  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
sky2                   49172  0 
firewire_ohci          31504  0 
libahci                25548  1 ahci
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci

---------------------------------------------------------------------------------------------------------------------

ali@ubuntu:~$ dmesg | egrep 'r8|rtl8'
[   60.790414] ieee80211 phy1: hwaddr 00:c0:ca:3a:6f:fa, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   60.806468] rtl8187: Customer ID is 0xFF
[   60.806512] Registered led device: rtl8187-phy1::radio
[   60.806545] Registered led device: rtl8187-phy1::tx
[   60.806568] Registered led device: rtl8187-phy1::rx
[   60.806946] rtl8187: wireless switch is on
[   60.806983] usbcore: registered new interface driver rtl8187
[   60.832296] rtl8187L: Initializing module
[   60.832298] rtl8187L: Wireless extensions version 22
[   60.832300] rtl8187L: Initializing proc filesystem
[   60.832334] usbcore: registered new interface driver rtl8187L
[  211.077388] usbcore: deregistering interface driver rtl8187L
[  211.077440] rtl8187L: Exiting
[  211.101331] usbcore: deregistering interface driver rtl8187
[  222.736298] ieee80211 phy2: hwaddr 00:c0:ca:3a:6f:fa, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  222.757740] rtl8187: Customer ID is 0x00
[  222.757812] Registered led device: rtl8187-phy2::radio
[  222.758034] Registered led device: rtl8187-phy2::tx
[  222.758095] Registered led device: rtl8187-phy2::rx
[  222.759582] rtl8187: wireless switch is on
[  222.759786] usbcore: registered new interface driver rtl8187
ali@ubuntu:~$ 




tip: 

dear Praseodym i must turn laptop wireless key on because adapter is off until laptop wireless be turn on and after it adapter find the antenna.i solved the problem with WIFI-RADAR software but while i insert IP Adress and Gateway in Wifi Profile it can not connect to  this IP and always connect to deafult IP .therefore i decide use ubuntu network manager again.

---

### Post by praseodym on 2011-08-27
Ok, prevent the "wrong" module from loading again in future:

```
echo "blacklist r8187l" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
You stick (wlan1) is now connected. Try:

```
sudo iwconfig wlan1 rate auto
iwconfig #control
```
Do you want to use both devices or only the stick if plugged in? Maybe the drivers rtl8187 and iwlagn disturb each other. In this case you can unload iwlagn if the stick is plugged in via a little script:

```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Add the following:

```
# UDEV-rule für external WLAN-sticks
# unloads/loads modules for int. WLAN-card

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-stick recognized, onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf iwlagn"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-stick removed, onboard-card activated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe iwlagn"

LABEL="rules_end"
```
save, close, and reload udev:

```
sudo service udev reload
```
then re-plugin the stick.

---

### Post by mohammadamingh on 2011-08-27
i do and my output:


ali@ubuntu:~$ echo "blacklist r8187l" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for ali: 
blacklist r8187l

-----------------------------------------------------------------------

ali@ubuntu:~$ sudo iwconfig wlan1 rate auto
ali@ubuntu:~$ iwconfig #control
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"EnGenius"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"EnGenius"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

--------------------------------------------------------------------------
          
ali@ubuntu:~$ gksu gedit /etc/udev/rules.d/10-wlan-stick.rules

(gedit:1991): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NHKZ0V': No such file or directory

(gedit:1991): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1991): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Q7E50V': No such file or directory

(gedit:1991): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

-------------------------------------------------------------------------------

ali@ubuntu:~$ sudo service udev reload
ali@ubuntu:~$

---

### Post by praseodym on 2011-08-27
Did you copy/paste the lines into the empty file that opened? Replugged the stick?

---

### Post by mohammadamingh on 2011-08-27
> **praseodym said:**
> Did you copy/paste the lines into the empty file that opened? Replugged the stick?


yes

i copy/paste the line in empty file and save it

---

### Post by praseodym on 2011-08-27
Can you show seperately with and without stick:

```
iwconfig
sudo iwlist scan
lsmod
```

---

### Post by mohammadamingh on 2011-08-27
i hope that you want this information


and output in various states :





in state laptop Wireless key is off and adapter is on:


ali@ubuntu:~$ sudo -i
[sudo] password for ali: 
root@ubuntu:~# ifconfig wlan1 up
root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
---------------------------------------------------          
root@ubuntu:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:15:6D:FC:0E:44
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000157c181
                    Extra: Last beacon: 1840ms ago
                    IE: Unknown: 0008494E5445524E4554
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD26000C42000000011E0000000000660203FF0F55424E5400000000000000000000000000000000
          Cell 02 - Address: 00:15:6D:A0:4F:F3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"wwlan inter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000446be15a77
                    Extra: Last beacon: 1252ms ago
                    IE: Unknown: 000B77776C616E20696E746572
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD26000C42000000011E0000000000660203FF0F55424E5400000000000000000000000000000000
-------------------------------------------------------------------------
root@ubuntu:~# lsmod
Module                  Size  Used by
rtl8187                56206  0 
eeprom_93cx6           12653  1 rtl8187
rfcomm                 38125  0 
sco                    17779  0 
bnep                   17785  0 
l2cap                  48656  4 rfcomm,bnep
btusb                  18160  0 
bluetooth              65565  5 rfcomm,sco,bnep,l2cap,btusb
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
nvidia              10675438  44 
joydev                 17322  0 
snd_hda_codec_hdmi     27479  4 
snd_hda_codec_realtek   255820  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
uvcvideo               66851  0 
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
videodev               75143  1 uvcvideo
psmouse                73312  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              12990  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 rtl8187
sony_laptop            34432  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18951  0 
snd                    55295  14  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              17769  0 
cfg80211              156212  2 rtl8187,mac80211
coretemp               13283  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sky2                   49172  0 
libahci                25548  1 ahci
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
root@ubuntu:~# 

=============================================================================

---

### Post by mohammadamingh on 2011-08-27
in state laptop Wireless key is on and adapter is off:



li@ubuntu:~$ sudo -i
[sudo] password for ali: 
root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"EnGenius"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Encryption key:eek:ff
          Power Management:eek:ff
-----------------------------------------------------------          
root@ubuntu:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:15:6D:A0:4F:F3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:eek:ff
                    ESSID:"wwlan inter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044790ee5d1
                    Extra: Last beacon: 1256ms ago
                    IE: Unknown: 000B77776C616E20696E746572
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD26000C42000000011E0000000000660203FF0F55424E5400000000000000000000000000000000
          Cell 02 - Address: 00:02:6F:55:26:16
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:eek:ff
                    ESSID:"EnGenius"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036800d0181
                    Extra: Last beacon: 1936ms ago
                    IE: Unknown: 0008456E47656E697573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010030FF7F
------------------------------------------------------------------
root@ubuntu:~# lsmod
Module                  Size  Used by
rtl8187                56206  0 
eeprom_93cx6           12653  1 rtl8187
rfcomm                 38125  8 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
btusb                  18160  2 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
nvidia              10675438  44 
joydev                 17322  0 
snd_hda_codec_hdmi     27479  4 
snd_hda_codec_realtek   255820  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
uvcvideo               66851  0 
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
videodev               75143  1 uvcvideo
psmouse                73312  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              12990  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 rtl8187
sony_laptop            34432  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18951  0 
snd                    55295  14   snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              17769  0 
cfg80211              156212  2 rtl8187,mac80211
coretemp               13283  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sky2                   49172  0 
libahci                25548  1 ahci
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
root@ubuntu:~# 
=========================================================================

---

### Post by mohammadamingh on 2011-08-27
in state laptop Wireless key is on and adapter is off:
 
 
 ali@ubuntu:~$ sudo -i
 [sudo] password for ali: 
 root@ubuntu:~# iwconfig
 lo        no wireless extensions.
 
 eth0      no wireless extensions.
 
 wlan0     IEEE 802.11abg  ESSID:"EnGenius"  
           Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
           Tx-Power=15 dBm   
           Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
           Encryption key:eek:ff
           Power Management:eek:ff
 --------------------------------------------------          
 root@ubuntu:~# sudo iwlist scan
 lo        Interface doesn't support scanning.
 
 eth0      Interface doesn't support scanning.
 
 wlan0     Interface doesn't support scanning : Device or resource busy
 --------------------------------------------------
 root@ubuntu:~# lsmod
 Module                  Size  Used by
 iwlagn                284569  0 
 iwlcore               148965  1 iwlagn
 rtl8187                56206  0 
 eeprom_93cx6           12653  1 rtl8187
 rfcomm                 38125  8 
 sco                    17779  2 
 bnep                   17785  2 
 l2cap                  48656  16 rfcomm,bnep
 btusb                  18160  2 
 bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
 nls_iso8859_1          12617  1 
 nls_cp437              12751  1 
 vfat                   17335  1 
 fat                    55505  1 vfat
 usb_storage            43946  1 
 uas                    17676  0 
 binfmt_misc            13213  1 
 parport_pc             32111  0 
 ppdev                  12849  0 
 nvidia              10675438  44 
 joydev                 17322  0 
 snd_hda_codec_hdmi     27479  4 
 snd_hda_codec_realtek   255820  1 
 arc4                   12473  2 
 snd_hda_intel          24140  2 
 snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
 snd_hwdep              13274  1 snd_hda_codec
 uvcvideo               66851  0 
 snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
 snd_seq_midi           13132  0 
 snd_rawmidi            25269  1 snd_seq_midi
 videodev               75143  1 uvcvideo
 psmouse                73312  0 
 snd_seq_midi_event     14475  1 snd_seq_midi
 serio_raw              12990  0 
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
 mac80211              257001  3 iwlagn,iwlcore,rtl8187
 sony_laptop            34432  0 
 snd_timer              28659  2 snd_pcm,snd_seq
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
 video                  18951  0 
 snd                    55295  14    snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
 intel_ips              17769  0 
 cfg80211              156212  4 iwlagn,iwlcore,rtl8187,mac80211
 coretemp               13283  0 
 soundcore              12600  1 snd
 snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
 lp                     13349  0 
 parport                36746  3 parport_pc,ppdev,lp
 usbhid                 41704  0 
 hid                    77084  1 usbhid
 ahci                   21591  2 
 firewire_ohci          31504  0 
 sdhci_pci              13623  0 
 firewire_core          56138  1 firewire_ohci
 sky2                   49172  0 
 libahci                25548  1 ahci
 crc_itu_t              12627  1 firewire_core
 sdhci                  22720  1 sdhci_pci
 root@ubuntu:~# 
 
 
 
 i'm sorry praseodym for  i be enter as root user because i have not any way!

---

### Post by mohammadamingh on 2011-08-28
everyone can help me,please.

---

### Post by praseodym on 2011-08-28
Something else running in the background?

```
ps aux | grep 'Network|wpa|wicd'
```
please.

---

### Post by mohammadamingh on 2011-08-28
Thank you

and my output :


ali@ubuntu:~$ ps aux | grep 'Network|wpa|wicd'
ali       1931  0.0  0.0   4156   856 pts/0    S+   00:32   0:00 grep --color=auto Network|wpa|wicd
ali@ubuntu:~$

---

### Post by praseodym on 2011-08-28
Sorry, typo:

ps aux | [COLOR="Red"]e[/COLOR]grep 'Network|wpa|wicd'

---

### Post by mohammadamingh on 2011-08-28
I do and this is output:


ali@ubuntu:~$ ps aux | egrep 'Network|wpa|wicd'

root       748  0.0  0.1  19808  5692 ?        Ssl  02:00   0:00 NetworkManager
root       866  0.0  0.0   5172  2396 ?        S    02:00   0:00 /sbin/wpa_supplicant -u -s
ali       1853  0.0  0.0   4156   856 pts/0    S+   02:04   0:00 egrep --color=auto Network|wpa|wicd
ali@ubuntu:~$

---

### Post by praseodym on 2011-08-28
Strange...Lets check the other driver we blacklisted (its an older one, but sometimes it works better):

```
sudo modprobe -rf rtl8187
sudo modprobe -v r8187l
sudo service network-manager restart
```

---

### Post by mohammadamingh on 2011-08-28
I runed codes in Terminal and after this iner laptop wireless is finding the antenna now,

in other word I'm see two antenna groups but  i can not connect to antenna group that be find by iner wireless laptop because those are weak .


and my output:

ali@ubuntu:~$ sudo modprobe -rf rtl8187
[sudo] password for ali: 
--------------------------------------------------------------------------------
ali@ubuntu:~$ sudo modprobe -v r8187l
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/r8187l.ko 
---------------------------------------------------------------------------------
ali@ubuntu:~$ sudo service network-manager restart
network-manager start/running, process 2255
ali@ubuntu:~$

---

### Post by praseodym on 2011-08-28
Can you show:

```
iwconfig
sudo iwlist scan
dmesg | grep r8
lsmod
```

---

### Post by mohammadamingh on 2011-08-29
output:


ali@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"wwlan inter"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:6D:A0:4F:F3   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0
-------------------------------------------------------------------------------

ali@ubuntu:~$ sudo iwlist scan
[sudo] password for ali: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:15:6D:A0:4F:F3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"wwlan inter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000638a882181
                    Extra: Last beacon: 268ms ago
                    IE: Unknown: 000B77776C616E20696E746572
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD26000C42000000011E0000000000660203FF0F55424E5400000000000000000000000000000000

-------------------------------------------------------------------------

ali@ubuntu:~$ dmesg | grep r8

------------------------------------------------------------------------

ali@ubuntu:~$ lsmod
Module                  Size  Used by
rfcomm                 38125  8 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
btusb                  18160  2 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
rtl8187                56206  0 
eeprom_93cx6           12653  1 rtl8187
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27479  4 
nvidia              10675438  44 
arc4                   12473  2 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
uvcvideo               66851  0 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               75143  1 uvcvideo
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
psmouse                73312  0 
mac80211              257001  1 rtl8187
sony_laptop            34432  0 
intel_ips              17769  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
coretemp               13283  0 
video                  18951  0 
cfg80211              156212  2 rtl8187,mac80211
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
firewire_ohci          31504  0 
libahci                25548  1 ahci
sky2                   49172  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
ali@ubuntu:~$ 



I have a question:

I insert internet username and password in LEAP of Wireless Security
is it true?

---

### Post by praseodym on 2011-08-29
In wireless security you have to insert the wireless key which is set in your router interface. You rebootet your system, so the driver rtl8187 is loaded again. First, try it with this one. Still no encryption in your network:

```
wlan1 Scan completed :
Cell 01 - Address: 00:15:6D:A0:4F:F3
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=43/70 Signal level=-67 dBm
Encryption key: [COLOR="Red"]off[/COLOR]
ESSID:"wwlan inter"
```
Try WPA2-AES if possible.

---

### Post by mohammadamingh on 2011-08-29
Dear Praseodym 

I don't know any thing about  wireless key and I have username and password that I always insert to LEAP.

see the below photo and explain about wireless key,please.

[ATTACH]201041[/ATTACH]

---

### Post by praseodym on 2011-08-29
If you have no encryption then choose "none". But I recommend using WPA2 if possible.

---

### Post by mohammadamingh on 2011-08-29
I made a wireless connection (image-1)
and it did not connect to the wwlan inter(image-2) because I inserted username and password.
if select None Security then connect to antenna.


[ATTACH]201060[/ATTACH]

[ATTACH]201061[/ATTACH]

---

### Post by mohammadamingh on 2011-08-30
](*,)](*,)](*,)

help me,please

---

### Post by bkratz on 2011-08-30
> **mohammadamingh said:**
> I made a wireless connection (image-1)
and it did not connect to the wwlan inter(image-2) because I inserted username and password.
if select None Security then connect to antenna.


[ATTACH]201060[/ATTACH]

[ATTACH]201061[/ATTACH]



Did you change the wireless A/P (access point) too? Just changing you wireless device without changing the access point won't do anything except prevent you from connecting. Usually you have to connect with a cable to access these features.

---

### Post by mohammadamingh on 2011-08-30
Thank

but I have a wireless device that I connectd it to laptop by USB cable and I always use a access point antenna for connect to internet, 

and I can not connect to internet again!

---

