---
title: "Unable to bring back native driver r8187 after uninstallation of ndiswrapper"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-03-04
Now I realize that ndiswrapper should be the direct cause of the freezing on "Loading manual drivers ... " during the boot up. Once I uninstall ndiswrapper this problem no more exists. But I need ndiswrapper for the WLAN connection. According to what I read from this [guide]("http://ubuntuforums.org/showthread.php?t=571188") the default native realtek r8187 driver should work if an extra letter for suffix is added to the eesid name.
I try to bring back the native realtek r8187 driver but not success. I google the web for hours still cannot find a solution to bring back the native driver after uninstallation of ndiswrapper. 

So, 
would anyone please tell me how to fix the annoying problem of freezing at "Loading manual drivers ... " during the bootup
OR,
would anyone please tell me how to bring back the original driver come with Ubuntu for realtek 8187 WLAN chipset (r8187)? 

Any suggestion will be appreciated!


EDIT:
I am using ubuntu 8.10 32-bit 
uname -a 
```
Linux coppen-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linu 
``` 
lsusb ```

Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

```
lshw -C network 
```
 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:43:74:7b:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.53+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g

```
iwconfig ```

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```
lsmod |grep 818 ```
rtl8187                53248  0 
mac80211              216820  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               32392  2 rtl8187,mac80211
usbcore               149360  8 rtl8187,usbhid,ndiswrapper,usb_storage,libusual,ohci_hcd,ehci_hcd
 
```
lsmod ```
 Module                  Size  Used by
rtl8187                53248  0 
mac80211              216820  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               32392  2 rtl8187,mac80211
usbhid                 35840  0 
hid                    50560  1 usbhid
sis                    13696  1 
drm                    86056  2 sis
binfmt_misc            16904  1 
vboxdrv                71576  0 
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
pci_slot               12680  0 
sbs                    19464  0 
wmi                    14504  0 
container              11520  0 
sbshc                  13440  1 sbs
ipv6                  263972  10 
af_packet              25728  4 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ndiswrapper           196380  0 
coretemp               14080  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
evdev                  17696  11 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13444  0 
pcspkr                 10624  0 
psmouse                45200  0 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
sis190                 25476  0 
mii                    13440  1 sis190
video                  25232  0 
output                 11008  1 video
battery                18436  0 
button                 14224  0 
ac                     12292  0 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
sis_agp                15232  1 
agpgart                42184  2 drm,sis_agp
ext3                  133256  4 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  6 
crc_t10dif              9984  1 sd_mod
usb_storage            82752  0 
libusual               30356  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
sata_sis               13444  5 
pata_acpi              12160  0 
ata_generic            12932  0 
pata_sis               18436  1 sata_sis
ohci_hcd               32016  0 
ehci_hcd               43788  0 
libata                178208  4 sata_sis,pata_acpi,ata_generic,pata_sis
scsi_mod              155212  5 sd_mod,usb_storage,sr_mod,sg,libata
dock                   16656  1 libata
usbcore               149360  8 rtl8187,usbhid,ndiswrapper,usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
```

---

### Post by juan234 on 2009-03-04
I am pretty sure the driver you want is RTL8187 and you are using it...Where did you get r8187 from?  Why do you use ndiswrapper?

# modprobe rtl8187

---

### Post by afeasfaerw23231233 on 2009-03-04
Thanks for the reply. 
here's the result

sudo modprobe r8187
FATAL: Module r8187 not found.

edit: oh, sorry, it should be rtl8187. I will try it when I get my notebook.

---

### Post by afeasfaerw23231233 on 2009-03-04
Ok, I run > sudo modprobe rtl8187 and then reboot the computer. 
Here's  lshw -C network
>   *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:43:74:7b:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
It seems that no driver is installed. And I cannot access the internet via WLAN.

---

### Post by juan234 on 2009-03-04
Some please correct me if I am wrong, but if you do

#ifconfig  and see wlan0  <-that is the interface...which means that it is loaded.  

you should maybe try

#iwlist wlan0 scan

if that comes up with results then your driver is definitely loaded.  make sure your wireless encryption is off first and try.  

#dhclient wlan0

alternatively see the /etc/network/interfaces file

iface wlan0 inet static
wireless-key s:XXXXXXXXXXXXX
wireless-essid la_tuya
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0

doesn't look like a driver problem.  Hope that helps

Juan

---

### Post by afeasfaerw23231233 on 2009-03-04
Thanks for your help. The driver is loaded. But I have another suffix issue of this driver. I will post on kevdog's tutorial.

---

