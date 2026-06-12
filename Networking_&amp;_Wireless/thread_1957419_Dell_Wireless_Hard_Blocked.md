---
title: "Dell Wireless Hard Blocked"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by ZeroZeroZero on 2012-04-12
Hi,

The wireless on my Dell Inspiron 1018 (Dual booted Windows and Ubuntu) seems to have stopped working after I pressed the wireless button (F2) on the keyboard.

Pressing it again does not seem to re-enable it.

This has happened before and booting it into Windows and press F2 normally re-enables the wireless.

This time, however, (after updating to 12.04) the wireless is disabled again when I boot back into Ubuntu.

Here's my outputs:

rfkill list
```
me@sInspiron-1018:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
4: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
5: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

(Interestingly, after I enable the wireless in Windows and go back to Linux, dell-wifi hard blocked is listed as no. Despite this, phy0 is still hard blocked and the wireless is still disabled)

iwconfig:
```
me@sInspiron-1018:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```

ifconfig
```

me@sInspiron-1018:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 5c:26:0a:10:c9:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66912 (66.9 KB)  TX bytes:66912 (66.9 KB)

```

lspci -nn
```

me@sInspiron-1018:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

```

lsmod
```

me@sInspiron-1018:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
dell_laptop            13671  0 
bnep                   17830  2 
rfcomm                 38139  16 
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
binfmt_misc            17292  1 
joydev                 17393  0 
iptable_nat            13016  0 
nf_nat                 24959  1 iptable_nat
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
nf_conntrack           73847  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
iptable_filter         12706  0 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21974  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_realtek   174055  1 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          32765  3 
rtl8192ce             127376  0 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
rtlwifi               107553  1 rtl8192ce
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
btusb                  17912  2 
psmouse                87140  0 
bluetooth             158438  23 bnep,rfcomm,btusb
serio_raw              13027  0 
mac80211              436455  2 rtl8192ce,rtlwifi
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 rtlwifi,mac80211
i915                  414568  3 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
usb_storage            39646  2 ums_realtek
uas                    17699  0 
r8169                  56321  0 
```

I have tried (thanks to some of the advice in other threads)

1) As mentioned above, booting into Windows and pressing the hardware switch - which works until I boot back into Ubuntu.
2) rmmod dell-laptop and then attempting to unblock/press the switch
3) Reinstalling my wireless driver rtl8192ce

Any help or advice would be greatly appreciated.

Thanks

---

### Post by roelforg on 2012-04-12
Is there maybe some small and hidden non-keyboard switch on the case?
The "hard-locked" means a mechanical switch locked it.
HP laptops have that switch on a weired spot making it easy to switch it w/o noticing, maybe you have something like that as well.

---

### Post by ZeroZeroZero on 2012-04-12
> **roelforg said:**
> Is there maybe some small and hidden non-keyboard switch on the case?
The "hard-locked" means a mechanical switch locked it.
HP laptops have that switch on a weired spot making it easy to switch it w/o noticing, maybe you have something like that as well.

Thanks for responding

I have had a quick look around the laptop for any other switches but I can't seem to find anything.

When I go into Windows the wireless is disabled until I press F2 which is what made me think that it was this switch that was the problem.

---

### Post by roelforg on 2012-04-12
> **ZeroZeroZero said:**
> Thanks for responding
 
I have had a quick look around the laptop for any other switches but I can't seem to find anything.
 
When I go into Windows the wireless is disabled until I press F2 which is what made me think that it was this switch that was the problem.
 
I think the windows driver has a part in this.

---

### Post by ZeroZeroZero on 2012-04-12
> **roelforg said:**
> I think the windows driver has a part in this.

Does the windows driver influence the Linux drivers? Or does it not fully unblock the wireless card?

---

### Post by chili555 on 2012-04-12
Please try:```
sudo modprobe -r dell-laptop
sudo rfkill unblock all
rfkill list all
```Any improvement? If so, let's blacklist *dell-laptop*:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by ZeroZeroZero on 2012-04-12
> **chili555 said:**
> Please try:```
sudo modprobe -r dell-laptop
sudo rfkill unblock all
rfkill list all
```Any improvement? If so, let's blacklist *dell-laptop*:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```

Thanks but sadly it still isn't working.

rfkill list all:
```
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes
```

Interestingly, when I boot it up and enter into settings (before Ubuntu loads), it has the Wireless set as enabled. I don't know whether that means anything.

---

### Post by chili555 on 2012-04-12
> Interestingly, when I boot it up and enter into settings (before Ubuntu loads), it has the Wireless set as enabled.??? Meaning what? Can you hold down the F2 button as it boots and it works? Now that *dell-laptop* is not loaded, what does F2 do?```
rfkill list all
```Now press F2.```
rfkill list all
```Any change?

---

### Post by ZeroZeroZero on 2012-04-12
Problem's fixed, though I'm not quite sure how it happened.

I booted into Windows, enabled the wireless and then rebooted into an older version of Linux.

Then the wireless worked and it connected. Then I rebooted it again into 12.04 and then it worked there too.

Thanks for all your help. Seems like the issue was something to do with the latest update.

---

### Post by roelforg on 2012-04-12
> **ZeroZeroZero said:**
> Problem's fixed, though I'm not quite sure how it happened.

I booted into Windows, enabled the wireless and then rebooted into an older version of Linux.

Then the wireless worked and it connected. Then I rebooted it again into 12.04 and then it worked there too.

Thanks for all your help. Seems like the issue was something to do with the latest update.

This'll answer the question if the win drivers influence the linux ones as well.
Hardware makers can add proprietary interfaces to their hw (just look at the oss noveau vs. closed source nvidia drivers) most hw-makers only write drivers for win as it has 90% of all desktops.
As such most lin drivers started by reverse-engineering the win ones,
but noone's perfect so bugs exist.
Besides that source of info, the only other sources are docs publised by the hw-maker that often omit proprietary interfaces.
It could be that (as the fn-alt2 is software) some part of installing triggers the card to lock.
But noone knows how...

---

### Post by blueshead on 2012-04-12
try fn+f2..

---

### Post by frank cox on 2012-10-11
> **roelforg said:**
> Is there maybe some small and hidden non-keyboard switch on the case?
The "hard-locked" means a mechanical switch locked it.
HP laptops have that switch on a weired spot making it easy to switch it w/o noticing, maybe you have something like that as well.

Everything that had a beginning has a cause, a wiser wallpaper.

---

