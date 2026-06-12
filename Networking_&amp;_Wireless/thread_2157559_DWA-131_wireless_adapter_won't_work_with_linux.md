---
title: "DWA-131 wireless adapter won't work with linux"
date: 2013-06-25
forum: Networking &amp; Wireless
---

### Post by linuxnoob12232 on 2013-06-25
I just bought a DWA-131 usb adapter so I could connect to the internet, but I have no clue how to set it up

---

### Post by DeathByDenim on 2013-06-25
Theoretically, it should just work the moment you plug it in, but I take it that it didn't do anything, eh? Does it show anything when you open a terminal and type
```
iwconfig
```

Otherwise, there's a write-up about somebody else that managed to get the DWA-131 going. It's three years old though. You can find it here:
[http://ukstokes.com/blog/2010/05/12/d-link-dwa-131-and-ubuntu/](http://ukstokes.com/blog/2010/05/12/d-link-dwa-131-and-ubuntu/)
It boils down to either using ndiswrapper or compiling the drivers yourself.

---

### Post by linuxnoob12232 on 2013-06-25
All it says is 

lo             no wireless connections

eth0         no wireless connections

---

### Post by DeathByDenim on 2013-06-25
Yeah, it looks like it isn't detected then and you'll have to go through all of the steps in the link I sent you.

Actually, there seems to be a shorter step-by-step instruction set right on this forum by matthewp131:
[http://ubuntuforums.org/showthread.php?t=1457505&p=9690593#post9690593](http://ubuntuforums.org/showthread.php?t=1457505&p=9690593#post9690593)

---

### Post by linuxnoob12232 on 2013-06-25
[COLOR=#000000]When I try to do this, I type make install, and it says "cannot stat '8712u.ko': No such file or directory"[/COLOR]

---

### Post by DeathByDenim on 2013-06-26
Hmm, strange. I don't know how to fix that. I don't have a DWA-131 myself, so I can't test it for you.

However, I've read that the drivers should be available in Ubuntu since version 10.04 though, so I'm not sure why it isn't just being autodetected...
Does it appear when you type
```
lsusb
```
And what does this command say:
```
lsmod
```

---

### Post by linuxnoob12232 on 2013-06-26
** lsusb**
Bus 001 Device 002: ID 2001:330d D-Link Corp. 
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 004 Device 002: ID 045e:0095 Microsoft Corp. IntelliMouse Explorer 4.0 (IntelliPoint)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**lsmod**
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
snd_hda_codec_via      45850  1 
asus_atk0110           17390  0 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
mac_hid                13037  0 
snd                    56485  15 snd_hwdep,snd_timer,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
kvm_amd                50336  0 
kvm                   376505  1 kvm_amd
k8temp                 12842  0 
serio_raw              13031  0 
i2c_nforce2            12876  0 
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
pata_acpi              12886  0 
usb_storage            47684  0 
nouveau               834513  4 
mxm_wmi                12893  1 nouveau
firewire_ohci          35292  0 
firewire_core          61718  1 firewire_ohci
i2c_algo_bit           13197  1 nouveau
video                  18894  1 nouveau
crc_itu_t              12627  1 firewire_core
wmi                    18590  2 mxm_wmi,nouveau
floppy                 55441  0 
ttm                    71289  1 nouveau
drm_kms_helper         47545  1 nouveau
drm                   228489  6 ttm,drm_kms_helper,nouveau
forcedeth              61777  0 
pata_amd               13761  0 
ahci                   25507  2

---

### Post by DeathByDenim on 2013-06-26
Hmm, so it does show up in lsusb, but the driver doesn't seem to be loaded.
Can you try
```
sudo modprobe rtl8192cu
```
and then check iwconfig and lsmod again?

---

### Post by linuxnoob12232 on 2013-06-26
**lsusb**
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 003: ID 2001:330d D-Link Corp. 
Bus 004 Device 002: ID 045e:0095 Microsoft Corp. IntelliMouse Explorer 4.0 (IntelliPoint)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**iwconfig**
lo        no wireless extensions.


eth0      no wireless extensions.

---

### Post by kurt18947 on 2013-06-27
I suspect the O.P. has a newer version DWA-131.  The original DWA-131 used a Realtek RTL8192SU chipset that worked great with Ubuntu -- plug it in and it worked.  I have one and was recommending the model as a "plug & play" linux WiFi adapter.   Dlink then introduced a 'new and improved' DWA-131 ver.2 or ver.b.  This is NOT plug 'n' play and there's no simple way I'm aware of to tell the difference short of reading the label on the device.   If I were the O.P. and could return the DWA-131, I would do so.  The TrendNet TEW-649UB is a twin of the original DWA-131 and still uses the Realtek RTL-8192SU chip AFAIK.  Here is a thread that discusses the newer DWA-131:

[http://ubuntuforums.org/showthread.php?t=2121020&page=5&highlight=DWA-131](http://ubuntuforums.org/showthread.php?t=2121020&page=5&highlight=DWA-131)

---

