---
title: "Lenovo IdeaPad Z580 - Laptop (Bluetooth Problem)"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by Oussama001 on 2013-01-13
Hi,

The problem I'm having with my pc is that I can't use bluetooth in ubuntu, it says "No bluetooth adapter detected"
Please help !

EDIT: I forgot to specify: I'm using ubuntu 12.10 in a dual boot with Win7, and the problem is not present on Windows.

---

### Post by tgalati4 on 2013-01-13
Is bluetooth turned on in BIOS?  What is your FN switch that turns wireless on and off?  You might have to cycle through to turn it on:  Wifi on--bluetooth off; wifi off--bluetooth off; Wifi off--bluetooth on.

---

### Post by Oussama001 on 2013-01-14
> **tgalati4 said:**
> Is bluetooth turned on in BIOS?  What is your FN switch that turns wireless on and off?  You might have to cycle through to turn it on:  Wifi on--bluetooth off; wifi off--bluetooth off; Wifi off--bluetooth on.

In the BIOS i have both on:
```
oussama@oussama-Lenovo:~$ rfkill list 
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```I have only FN+F5 which enables/disables the wireless. This can be also done in the control panel to set it ON/OFF
But the bluetooth does'nt work at all and always says "Turned Off" whether i enable it or disable it, i think it needs such a driver to make it know that it exists..

I used to use bluetooth on my desktop, and these problems occur to me only on this laptop, i think a driver is missing in my ubuntu..

Please help :-

---

### Post by tgalati4 on 2013-01-14
What modules are loaded on your system?

```
lsmod
```

---

### Post by Oussama001 on 2013-01-14
```
oussama@oussama-Lenovo:~$ lsmod
Module                  Size  Used by
vmnet                  50395  13 
vsock                  47445  0 
vmci                   80409  1 vsock
vmmon                  69896  0 
bbswitch               13172  0 
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  4 
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep
binfmt_misc            17260  1 
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_realtek    63493  1 
joydev                 17161  0 
arc4                   12473  2 
coretemp               13168  0 
kvm                   357806  0 
aesni_intel            17938  2 
cryptd                 15614  1 aesni_intel
snd_hda_intel          32515  6 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
aes_i586               16956  1 aesni_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
microcode              18209  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
ideapad_laptop         13670  0 
sparse_keymap          13658  1 ideapad_laptop
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
rts5139               281367  0 
psmouse                84843  0 
serio_raw              13031  0 
wmi                    18590  0 
snd                    61991  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13037  0 
iwlwifi               348544  0 
mac80211              461161  1 iwlwifi
i915                  457181  6 
drm_kms_helper         47303  1 i915
drm                   238768  7 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
soundcore              14599  1 snd
video                  18847  1 i915
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
lpc_ich                16925  0 
cfg80211              175375  2 iwlwifi,mac80211
mei                    35796  0 
uvcvideo               71277  1 
videobuf2_core         32070  1 uvcvideo
videodev               95841  3 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
r8169                  55976  0 

```

---

### Post by tgalati4 on 2013-01-14
What is the bluetooth chip that is currently detected?

After a fresh boot, open a terminal:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Cut and paste any bluetooth messages.

Also,

```
 lsusb -vv
```

Don't paste the entire output, just any bluetooth-related items.

---

### Post by Oussama001 on 2013-01-14
```

oussama@oussama-Lenovo:~$ dmesg | more
[   22.321108] Bluetooth: Core ver 2.16
[   22.321157] NET: Registered protocol family 31
[   22.321159] Bluetooth: HCI device and connection manager initialized
[   22.321339] Bluetooth: HCI socket layer initialized
[   22.321341] Bluetooth: L2CAP socket layer initialized
[   22.321351] Bluetooth: SCO socket layer initialized
[   22.323783] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.323786] Bluetooth: BNEP filters: protocol multicast
[   22.330313] Bluetooth: RFCOMM TTY layer initialized
[   22.330317] Bluetooth: RFCOMM socket layer initialized
[   22.330319] Bluetooth: RFCOMM ver 1.11


```

Concerning the other command i didn't find anything about bluetooth..

---

### Post by tgalati4 on 2013-01-16
You are not the only one experiencing this problem.  A quick google search:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1028827](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1028827)

No work-arounds posted.  Try spinning an Ubuntu nightly and see if the updated kernel fixes it.

Here's a page dedicated to your machine:

[http://www.linlap.com/lenovo_ideapad_z580](http://www.linlap.com/lenovo_ideapad_z580)

Send an email to Lenovo with the above references.

---

