---
title: "Broadcom BCM43142 Driver not working on 13.04"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by ryan516 on 2013-07-09
My driver is not working on my Ubuntu 13.04 non-modified. I know going under the software tab in system settings, going to additional drivers and activating it should work, but when I click apply it will revert back to not using the wireless driver at all. It says this device is not working, but while it was installing and running off the live CD it worked just fine. Please help!

---

### Post by ryan516 on 2013-07-10
Hello?

---

### Post by ryan516 on 2013-07-10
Hello?

---

### Post by snowpine on 2013-07-10
Hi Ryan, I am assuming you've read the Ubuntu Wiki instructions here? [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Maybe you can walk us through step-by-step, copy&pasting the terminal output/errors, beginning with the "identifying your chipset" step?

---

### Post by ryan516 on 2013-07-10
Output from lspci -vvnn | grep 14e4:
0.7:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

Edit: It can use the wl driver according to the article.

---

### Post by snowpine on 2013-07-10
If wl doesn't work then maybe give b43 a try? The article suggests that both are a possibility for your card.

---

### Post by ryan516 on 2013-07-10
Under the Software & Updates tab it's giving me the WL driver, but when I activate it with the apply button it reverts back to not using it. It says device not working underneath the section in additional drivers.

---

### Post by ryan516 on 2013-07-10
Update: b43 is not working either

---

### Post by Hadaka on 2013-07-10
Hi, please post the output of..
```
rfkill list all
lsmod
uname -a
```
thanks.

---

### Post by ryan516 on 2013-07-10
rfkill list all: 0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

lsmod: (I will only list the modules)
parport_pc
ppdev
rfcomm
bnep
joydev
coretemp
ghash_clmulni_intel
cryptd
dell_wmi
sparse_keymap
dell_laptop
dcdbas
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
videodev
btusb
bluetooth
snd_hda_codec_hdmi
mac_hid
snd_hda_codec_cirrus
i915
wmi
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_page_alloc
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
video
snd_seq
drm_kms_helper
snd_seq_device
snd_timer
snd
drm
i2c_algo_bit
psmouse
soundcore
microcode
mei
lpc_ich
serio_raw
lp
parport
ums_realtek
usb_storage
r8169
ahci
libahci

uname-a:
Linux ryan-Inspiron-3520 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Hadaka on 2013-07-10
give this a try..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by ryan516 on 2013-07-10
Update: I solved the issue by myself, when I got the Wi-fi driver, I installed the b43 driver for Oneric Ocelot, not Raring Ringtail

---

### Post by Hadaka on 2013-07-10
Glad its working, please mark your thread solved
how to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

