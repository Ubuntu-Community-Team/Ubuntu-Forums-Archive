---
title: "WLAN unstable ( BCM4313 )"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by thyriel on 2012-10-27
Hello,

hope someone can help me out with this.
Playing around with Xubuntu 12.10 (32bit) on an Alienware m17x R3 Laptop.

Wifi is somehow unstable. It runs "idle" for hours withour getting a disconnect, but every minute or so when theres heavy load on the connection it drops and reconnects.

Its also working fine on the Windows installation, so id guess its not a "Router" Problem (but have to mention the "Router" is a HTC One X Phone, so not much to setup there except encryption. But tried around with WPA2 and WEP128, both the same)

lspci -nn | grep 'Wireless'
```
0d:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

ifconfig
```
wlan0     Link encap:Ethernet  HWaddr c0:18:85:4c:8b:d3  
          inet addr:192.168.1.185  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c218:85ff:fe4c:8bd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69334144 (69.3 MB)  TX bytes:7660795 (7.6 MB)

```

iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:"HTCX"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1E:B0:94:B6:59:D1   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:59   Missed beacon:0

```
-> that "Retry long limit:7" and "Tx excessive retries:7" dont look good to me ?

lsmod -> cant find anything related to wlan in the output:
```
Module                  Size  Used by
snd_hda_codec_hdmi     31423  2 
snd_hda_codec_idt      59761  1 
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  16 
bnep                   17707  2 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
aesni_intel            17938  0 
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
arc4                   12473  2 
brcmsmac              503651  0 
mac80211              461161  1 brcmsmac
brcmutil               14355  1 brcmsmac
cfg80211              175375  2 brcmsmac,mac80211
cordic                 12487  1 brcmsmac
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32515  8 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  17950  0 
bluetooth             183228  22 rfcomm,bnep,btusb
microcode              18209  0 
psmouse                84843  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
joydev                 17161  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13031  0 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
snd_timer              24411  2 snd_pcm,snd_seq
videobuf2_memops       13184  1 videobuf2_vmalloc
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  457161  2 
radeon                820703  1 
snd                    61991  25 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                16925  0 
ttm                    75534  1 radeon
bcma                   34483  1 brcmsmac
wmi                    18590  1 dell_wmi
drm_kms_helper         45271  2 radeon,i915
drm                   230463  6 radeon,i915,ttm,drm_kms_helper
rts_pstor             346736  0 
i2c_algo_bit           13197  2 radeon,i915
mei                    35796  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
video                  18847  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
atl1c                  36175  0 
```

dmesg|grep 'wlan'
-> shows a ton of identical blocks like this:
```
[ 2253.210386] wlan0: authenticated
[ 2253.212214] wlan0: associate with 1e:b0:94:b6:59:d1 (try 1/3)
[ 2253.415792] wlan0: associate with 1e:b0:94:b6:59:d1 (try 2/3)
[ 2253.619383] wlan0: associate with 1e:b0:94:b6:59:d1 (try 3/3)
[ 2253.822965] wlan0: association with 1e:b0:94:b6:59:d1 timed out
[ 2254.785296] wlan0: authenticate with 1e:b0:94:b6:59:d1
[ 2254.786703] wlan0: send auth to 1e:b0:94:b6:59:d1 (try 1/3)
[ 2254.800030] wlan0: authenticated

```

sudo lshw -C network
```
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:18 memory:c6400000-c6403fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: c0:18:85:4c:8b:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.5.0-17-generic firmware=N/A ip=192.168.1.185 link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by chili555 on 2012-10-27
> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] Ahhhh! The tricky 4727! There are lots of opinions about how to get this going. The driver you are using, brcmsmac is one of them but not the most often recommended. I suggest you blacklist it and try the STA driver just to find out:```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
apt-get install bcmwl-kernel-source
exit
```Reboot and let us have your report.

---

### Post by thyriel on 2012-10-27
That did it, your a hero :)

dmesg shows no more entries for wlan, iwconfig gives no strange retry counts, and best of all: it stays connected even when downloading something \\:D/


Just in case someone else will be in need of this, id guessed according to Mr.Google that
```
apt-get install brcmwl-kernel-source
```
should be
```
apt-get install bcmwl-kernel-source
```
after he returned an error with brcmwl

---

### Post by chili555 on 2012-10-27
> Just in case someone else will be in need of this, id guessed according to Mr.Google that
Code:

apt-get install brcmwl-kernel-source

should be
Code:

apt-get install bcmwl-kernel-source

Indeed. Sorry for the mis-step. Glad it's working.

---

