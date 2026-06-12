---
title: "Broadcom BCM4313 stopped working after Pangolin install (incl. on older ubuntu)"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by michaelmestre on 2012-05-01
I have a very strange problem with my wireless card.
I was running a 11.04 version of Ubuntu with no problem whatsoever.
I installed a new Pangolin on another partition. Everything was working fine.
Then after a few hours, the _Broadcom BCM4313 stopped working_.. not only on Pangolin, but also on 11.04.

In both cases, the interface seems to be there, but cannot be activated. It is not hardware disabled (in such a case, the system displays this as such), but trying to switch it on produces no effect :(

It is possible that the card itself stopped working properly, but I suspect a firmware problem due to the Pangolin driver.
The wired connection works fine.

Is there any way I can get my wireless interface back online ?

Thank you very much for your help.

PS: the interface shows up in lspci -nn as:
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

---

### Post by praseodym on 2012-05-01
Hi,

please show
> 
lsmod
iwconfig
rfkill list

---

### Post by chili555 on 2012-05-01
If kindly old Dr. Chili were the kind of person to curse, he'd start now. Your device is claimed by *three* competing drivers. We have some work to do. First, let's try to get bcmwl-kernel-source going:
```
sudo su
apt-get install --reinstall bcmwl-kernel-source
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
echo wl >> /etc/modules
exit

```
If all this goes without drama, reboot and let us have your report.

I think there is a very slight possibility that one of the two that we blacklisted is correct. I hope I'm wrong.

---

### Post by michaelmestre on 2012-05-01
[praseodym]("http://ubuntuforums.org/member.php?u=1411497"):
Sure. Here you go:

**lsmod**
-----------------------------------------
Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60251  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
lib80211_crypt_tkip    17275  0 
snd_seq_midi           13132  0 
intel_ips              17753  0 
psmouse                72919  0 
serio_raw              13027  0 
snd_hda_intel          32765  7 
wl                   2646601  0 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_rawmidi            25424  1 snd_seq_midi
lib80211               14040  2 lib80211_crypt_tkip,wl
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                733693  0 
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  23 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
ttm                    65344  1 radeon
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
hp_accel               25728  0 
i915                  414603  8 
lis3lv02d              19268  1 hp_accel
input_polldev          13648  1 lis3lv02d
drm_kms_helper         45466  2 radeon,i915
mac_hid                13077  0 
drm                   197692  6 radeon,ttm,i915,drm_kms_helper
mei                    36570  0 
i2c_algo_bit           13199  2 radeon,i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
r8169                  56321  0 
-------------

**iwconfig**
-------------
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.
-------------

**rfkill list **

-------------
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

---

### Post by michaelmestre on 2012-05-01
[chili555]("http://ubuntuforums.org/member.php?u=35909"):

I performed the steps you wrote down, and it seems that nothing has changed.

---

### Post by chili555 on 2012-05-01
How about these steps?```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
```If it works, we can tweak a file and make it permanent.

---

### Post by michaelmestre on 2012-05-01
I tried that, and now it seems that it says "hardware disabled" all the time even when I press the Wireless Disable/Enable key on my keyboard.

---

### Post by praseodym on 2012-05-01
This module is only shown with "rfkill":

> echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
Reboot.

---

### Post by michaelmestre on 2012-05-02
> **praseodym said:**
> This module is only shown with "rfkill":


Reboot.
No change, still not working.

---

### Post by michaelmestre on 2012-05-02
My problem was solved by reactivating Bluetooth, which I had turned off.
Wireless then became available again (my laptop is an HP Pavilion DM4, by the way).
:popcorn:


This may be a bug.. Bluetooth and WIFI shouldn't be linked, or at least if they are linked in hardware, the user should be notified about the need to reactivate one to be able to use the other.
:mad:

---

### Post by ts3 on 2012-05-02
> **michaelmestre said:**
> This may be a bug.. Bluetooth and WIFI shouldn't be linked, or at least if they are linked in hardware, the user should be notified about the need to reactivate one to be able to use the other.

It's a bug, I filed one for 12.04 here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/962621](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/962621), there are others for other ubuntu versions.  I have the same BCM4313 wireless card by the way.  There's also an upstream bug report (link in launchpad) but nothing has been happening lately as far as I can tell.

---

