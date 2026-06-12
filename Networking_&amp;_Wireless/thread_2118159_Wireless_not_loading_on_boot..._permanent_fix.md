---
title: "Wireless not loading on boot... permanent fix?"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by MaynardHSH on 2013-02-20
Ok, I'm having problems with my wireless connection, I've managed to get it working but it's not been a permanent solution, maybe someone can help? I got the next information if that helps:

lspci
> 01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)


iwconfig 
> lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Connectionname"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:21:7C:57:43:31   
          Bit Rate=36 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:123   Missed beacon:0

eth0      no wireless extensions.



lsmod | grep cfg80211
> mac80211              436493  1 brcmsmac
cfg80211              178877  2 brcmsmac,mac80211
lib80211_crypt_tkip    17275  0 
lib80211               14040  1 lib80211_crypt_tkip


lsmod
> Module                  Size  Used by
arc4                   12473  2 
brcmsmac              540923  0 
mac80211              436493  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178877  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12518  1 brcmsmac
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   174313  1 
snd_hda_codec_hdmi     31775  1 
joydev                 17393  0 
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
lib80211_crypt_tkip    17275  0 
snd_seq_midi_event     14475  1 snd_seq_midi
wmi                    18744  1 acer_wmi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
cedarview_gfx         381372  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    62218  16 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    64734  1 cedarview_gfx
drm_kms_helper         32561  1 cedarview_gfx
psmouse                86520  0 
drm                   196391  3 cedarview_gfx,ttm,drm_kms_helper
uvcvideo               67203  0 
rts_pstor             353252  0 
soundcore              14635  1 snd
videodev               86588  1 uvcvideo
i2c_algo_bit           13199  1 cedarview_gfx
lib80211               14040  1 lib80211_crypt_tkip
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 cedarview_gfx
serio_raw              13027  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0 



also I tried this one and managed to connect fine (even tho my LED light doesn't work I can still connect)

> sudo modprobe -r wl && sudo modprobe brcmsmac

Any help would be appreciated :)

Edit: I'm using Ubuntu 12.04 LTS on a Gateway LT4002m noteboook.

---

### Post by chili555 on 2013-02-20
I'd love to see more details about your card:```
lspci -nn
```Is *wl* loading? May I see:```
sudo dpkg -s bcmwl-kernel-source | head -n5
```Thanks.

---

### Post by mvs1207 on 2013-02-20
I think brcmsmac is blacklisted in 12.04.  I had to remove it and use Broadcom 802.11 Linux STA wireless driver (wl) for my wireless card to work.

Ref: [http://askubuntu.com/questions/213550/ubuntu-12-10-wireless-not-working](http://askubuntu.com/questions/213550/ubuntu-12-10-wireless-not-working)

---

### Post by iponeverything on 2013-02-20
quick and dirty:

add the line: modprobe -r wl && sudo modprobe brcmsmac

before the exit 0 in your /etc/rc.local

---

### Post by chili555 on 2013-02-20
> **iponeverything said:**
> quick and dirty:

add the line: modprobe -r wl && sudo modprobe brcmsmac

before the exit 0 in your /etc/rc.localDirty indeed. If *wl* is not the proper driver for the device, why not remove it altogether? Moreover, we are not at all sure what the correct driver is until we see the card details.

---

### Post by iponeverything on 2013-02-20
correct or not, op said it was working with that module. 



> **chili555 said:**
> Dirty indeed. If *wl* is not the proper driver for the device, why not remove it altogether? Moreover, we are not at all sure what the correct driver is until we see the card details.

---

### Post by MaynardHSH on 2013-02-21
> **chili555 said:**
> I'd love to see more details about your card:```
lspci -nn
```Is *wl* loading? May I see:```
sudo dpkg -s bcmwl-kernel-source | head -n5
```Thanks.


Sure thing, here's the info. 


lspci -nn
> 00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller [8086:0bf1] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)



sudo dpkg -s bcmwl-kernel-source | head -n5
> Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 3570



> I think brcmsmac is blacklisted in 12.04. I had to remove it and use Broadcom 802.11 Linux STA wireless driver (wl) for my wireless card to work.
 I did try that one, but even when it said "installed and active" I couldn't connect.

> iponeverything 	
Re: Wireless not loading on boot... permanent fix?
quick and dirty:

add the line: modprobe -r wl && sudo modprobe brcmsmac

before the exit 0 in your /etc/rc.local 

So that would mean that I'd be using brcmsmac instead of wl? oorrrr? hehe, this is where it gets confusing for me :)

But if you need more info just let me know, and thanks for the help :)

---

### Post by chili555 on 2013-02-21
> So that would mean that I'd be using brcmsmac instead of wl? Yes, indeed. If brcmsmac works for you then that's the driver to use; however, there are certainly tidier ways to go about it. Let's find out:```
sudo modprobe -r wl
sudo modprobe brcmsmac
```Does your wireless connect? Otherwise, do:```
sudo modprobe -r brcmsmac
sudo modprobe wl
```How about now? Whichever makes your wireless work smoothly is what we will use to do a seamless, tidy fix.

In my experience, wl is preferred by your device:> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] However, your card/router/encryption combination may prefer something else. That's why we need to test.

---

### Post by MaynardHSH on 2013-02-22
Ok, I tried 
> sudo modprobe -r wl
sudo modprobe brcmsmac
and it seems that it's the one I need, it connected without problems.

whenever i tried > sudo modprobe -r brcmsmac
sudo modprobe wl

It wouldn't work. 
So now that I know which one I need, how can I make this permanent? I tried this Echo blacklist or something once, but maybe I did it poorly hehe...

---

### Post by chili555 on 2013-02-22
Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
gksudo gedit /etc/modprobe.d/blacklist.conf
```If brcmsmac or any of its dependencies are in there, remove them. ```
$ modinfo brcmsmac
<snip>
depends:        [COLOR="Red"]mac80211,bcma,brcmutil,cfg80211,cordic[/COLOR]

```Proofread, save and close gedit.

Next do:```
sudo su
echo brcmsmac >> /etc/modules
exit
```You should be all set but post back if we can help further.

Please use thread tools at the top to mark Solved.

---

### Post by MaynardHSH on 2013-02-23
Nice! I did all of it and now it works like a charm so far.. :) 
thank you so much! Really appreciate it :D

---

### Post by kanton on 2013-11-02
Thanks for this excellent guide!

---

