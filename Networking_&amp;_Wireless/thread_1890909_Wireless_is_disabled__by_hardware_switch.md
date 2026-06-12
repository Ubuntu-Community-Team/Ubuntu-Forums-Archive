---
title: "Wireless is disabled  by hardware switch"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by grvpande on 2011-12-04
I know that i am not the first who is writing about this issue as my wifi is not working in 11.10, and showing wireless is disable by hardware switch.. I just want to tell you that what I have done till yet.


this is the output of the " lshw -C network"
    *-network DISABLED
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 88:25:2c:b9:d2:10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-13-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:f0100000-f0103fff

and also the rfkill unblock all is not working and still showing the following::

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


There are a lot of comments all over the Internet and i am very confused to choose any of them as I dont want to go with all and spoil my laptop.

Many of you have solved this problem already so please help me to solve this

thanks

---

### Post by praseodym on 2011-12-04
Hi,

please show
```
lsmod
```
What computer is that?

---

### Post by grvpande on 2011-12-04
the output is 

Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12595  1 ppp_async
option                 21205  3 
usb_wwan               19779  1 option
usbserial              37203  9 option,usb_wwan
bnep                   17923  2 
rfcomm                 38408  12 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_realtek   254125  1 
**dell_laptop            13519  0 **
**dcdbas                 14098  1 dell_laptop**
uvcvideo               67271  0 
usbhid                 41905  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  2 
hid                    77367  1 usbhid
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
rtl8192ce              75448  0 
rtl8192c_common        69519  1 rtl8192ce
snd_seq_midi           13132  0 
rtlwifi                95614  1 rtl8192ce
btusb                  18160  2 
mac80211              393459  3 rtl8192ce,rtl8192c_common,rtlwifi
bluetooth             148839  23 bnep,rfcomm,btusb
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
i915                  505108  3 
cfg80211              172392  2 rtlwifi,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
r8169                  43104  0 

it's a dell mini 10 series, i have made the lines bold above

thanks

---

### Post by praseodym on 2011-12-04
Can you load the module "dell_wmi"?

```
sudo modprobe -v dell_wmi
```

---

### Post by grvpande on 2011-12-05
no it is giving error like this:

FATAL: Module del_wmi not found.


should I install it or what, what will be the next step..

thanks

---

### Post by praseodym on 2011-12-05
Try:

```
sudo rfkill unblock all
rfkill list #control
```
Any buttons/switches/keys/key combinations (e.g. Fn+F2)?

---

### Post by grvpande on 2011-12-05
nothing happend, I tried fn+F2 as that is the only way to start it with keyboard. the result of the commands was :

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by praseodym on 2011-12-05
Was it a typo?
> FATAL: Module del_wmi not found.
The module is named del[COLOR="Red"]l[/COLOR]_wmi.

---

### Post by grvpande on 2011-12-06
oops, sorry I wrote it wrong, the output of that command is below:


root@gaurav-Inspiron-1018:/home/gaurav# modprobe -v dell_wmi
[B]insmod /lib/modules/3.0.0-13-generic/kernel/drivers/input/sparse-keymap.ko 
insmod /lib/modules/3.0.0-13-generic/kernel/drivers/platform/x86/wmi.ko 
insmod /lib/modules/3.0.0-13-generic/kernel/drivers/platform/x86/dell-wmi.ko 
FATAL: Error inserting dell_wmi (/lib/modules/3.0.0-13-generic/kernel/drivers/platform/x86/dell-wmi.ko): No such device[/B]
root@gaurav-Inspiron-1018:/home/gaurav# 


thanks

---

### Post by praseodym on 2011-12-06
Ok,

two other methods:

1) Try to reset the BIOS to manufacturer settings, after that
```
sudo rfkill unblock all
```
in the booted system.

2) Something serious:

Blacklist the module "dell_laptop":

```
echo "blacklist dell_laptop" | sudo tee /etc/modprobe.d/blacklist-dell.conf
```
and reboot. If _nothing_ works after that, restart (hard reset) the computer while holding the SHIFT-button pressed to get into the GRUB2 bootloader, choose "recovery mode" there and remove the file and reboot via

```
rm /etc/modprobe.d/blacklist-dell.conf
reboot
```

---

