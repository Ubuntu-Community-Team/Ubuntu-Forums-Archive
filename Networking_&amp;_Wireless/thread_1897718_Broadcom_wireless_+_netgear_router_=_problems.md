---
title: "Broadcom wireless + netgear router = problems?"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by Kralizec on 2011-12-19
I have a laptop (Toshiba Satellite A605) that has a Broadcom BCM4313 and I'm connecting it to a Netgear WNR1000v2 wireless router with WPA-PSK security.
The problem is that randomly the wireless connection will drop out; it will reconnect a few minutes later, relatively painlessly.

Things of note:
[LIST]
[*]Using the wl driver for wifi; the proprietary driver caused no networks to show up.
[*]Other laptops work fine on this network
[*]This laptop works fine on other networks
[*]This laptop experienced the same exact problem when using Windows 7
[*]The router is set up to give this laptop a static IP; the above facts led me to believe there may have been an IP conflict.
[/LIST]

One possibility I haven't explored yet is the fact that the laptop is 802.11n capable but the router is 802.11n draft-ready. I'll set the router up to only do b/g and see if that fixes anything.

Does anyone here have any other ideas?

---

### Post by Kralizec on 2011-12-19
Halp?

---

### Post by Kralizec on 2011-12-20
Last cry for help. Anybody?

---

### Post by TBABill on 2011-12-20
Can you post the output of lsmod in a terminal?

---

### Post by Kralizec on 2011-12-20
```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  8 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17693  0 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
bcma                   20219  0 
arc4                   12529  2 
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
snd_hda_intel          33390  4 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  566827  8 
brcmsmac              631693  0 
drm_kms_helper         42558  1 i915
brcmutil               17837  1 brcmsmac
drm                   236290  4 i915,drm_kms_helper
snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              462092  1 brcmsmac
i2c_algo_bit           13423  1 i915
wmi                    19256  0 
psmouse                73882  0 
intel_ips              18089  0 
cfg80211              199587  2 brcmsmac,mac80211
serio_raw              13166  0 
sparse_keymap          13890  0 
crc_ccitt              12667  1 brcmsmac
toshiba_bluetooth      12807  0 
mei                    41480  0 
binfmt_misc            17540  1 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 

```

Interestingly, I don't see any driver for the wireless card listed... But was on the Internet when this was run. Maybe I don't understand what the output of lsmod is?

---

### Post by TBABill on 2011-12-20
Looks like the driver bcma is conflicting with brcmsmac. Can you ```
sudo rmmod bcma
```Then ```
sudo rmmod brcmsmac
``` Then ```
sudo modprobe brcmsmac
```If that works and you are able to connect, then you need to blacklist bcma by doing ```
gksudo gedit /etc/modprobe.d/blacklist.conf
```And add the following to the end of the file, restart and see if it's working properly: ```
blacklist bcma
```

---

### Post by Kralizec on 2011-12-20
> **TBABill said:**
> If that works and you are able to connect
I'm not sure you understand my problem. The machine connects fine to other networks, and even connects to the one in question. The problem is that it gets randomly disconnected **from only this one network.** Additionally, the same problem existed when the machine ran Windows.

However, I will still try your suggestions.

---

### Post by TBABill on 2011-12-20
I should have said "If you are still able to connect..."

---

