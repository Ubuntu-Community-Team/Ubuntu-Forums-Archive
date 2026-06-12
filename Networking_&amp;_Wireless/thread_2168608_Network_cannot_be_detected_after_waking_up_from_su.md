---
title: "Network cannot be detected after waking up from suspend"
date: 2013-08-18
forum: Networking &amp; Wireless
---

### Post by nisargshah on 2013-08-18
Hello, I use Ubuntu 12.04.2. I've observed that after I wake up my laptop from suspend mode and attach an ethernet cable with active internet connection, the OS does not detect any network and the 'Wired network' section (which comes after clicking on networking icon on top-right corner) is greyed out. I have to restart the laptop to get it detected. Is there any bug? Can I fix it? Any help would be appreciated.

Thanks in advance!
Nisarg Shah

---

### Post by praseodym on 2013-08-18
Please check the outputs of:
```

lsmod
lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```

---

### Post by dictodude on 2013-08-18
This has happened to me before too. It is a known bug that has been fixed in ubuntu 13. Upgrading is the best way, and youll also get the benifits of ubuntu 13 too!  Thanks! Hope i helped!

---

### Post by nisargshah on 2013-08-19
> **praseodym said:**
> Please check the outputs of:
```

lsmod
lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```
Here's the output -
```

nisarg@niz-ThinkPad-T61:~$ lsmod
Module                  Size  Used by
snd_hda_codec_analog    75395  1 
joydev                 17393  0 
pcmcia                 39826  0 
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_intel          32719  2 
snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
binfmt_misc            17292  1 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
nvram                  14029  1 thinkpad_acpi
iwl4965               117406  0 
tpm_tis                18308  0 
iwl_legacy             71187  1 iwl4965
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27465  0 
mac80211              436493  2 iwl4965,iwl_legacy
pcmcia_rsrc            18367  1 yenta_socket
wmi                    18744  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
btusb                  17948  2 
snd                    62218  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             158447  23 rfcomm,bnep,btusb
psmouse                86520  0 
serio_raw              13027  0 
mac_hid                13077  0 
i915                  428056  3 
cfg80211              178877  3 iwl4965,iwl_legacy,mac80211
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                140131  0 
nisarg@niz-ThinkPad-T61:~$ lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv'
rfcomm                 38139  12 
mac80211              436493  2 iwl4965,iwl_legacy
btusb                  17948  2 
bluetooth             158447  23 rfcomm,bnep,btusb
mac_hid                13077  0 
cfg80211              178877  3 iwl4965,iwl_legacy,mac80211
usbhid                 41937  0 
hid                    77428  1 usbhid
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci

```
> **dictodude said:**
> This has happened to me before too. It is a  known bug that has been fixed in ubuntu 13. Upgrading is the best way,  and youll also get the benifits of ubuntu 13 too!  Thanks! Hope i  helped!
I cannot afford an upgrade right now :(.

---

### Post by SeijiSensei on 2013-08-19
> **nisargshah said:**
> I cannot afford an upgrade right now :(.

He's talking about [upgrading your version of Ubuntu to 13.04]("http://www.ubuntu.com/download/desktop/upgrade").  That costs you nothing except the time involved to run the upgrade and fix any little problems that arise.  If you have a metered Internet connection, then you would have to pay for the bandwidth involved while downloading the upgrade.

---

### Post by nisargshah on 2013-08-19
> **SeijiSensei said:**
> He's talking about [upgrading your version of Ubuntu to 13.04]("http://www.ubuntu.com/download/desktop/upgrade").  That costs you nothing except the time involved to run the upgrade and fix any little problems that arise.  If you have a metered Internet connection, then you would have to pay for the bandwidth involved while downloading the upgrade.
That's why I said I can't afford an upgrade. My college internet connection limits me to 500mb per day and doesn't allow to download single file more than 500mb.

---

### Post by praseodym on 2013-08-19
Force the following modules to be unloaded while suspending:
```

sudo touch /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module
gksudo gedit /etc/pm/config.d/00sleep_module
```
Add these line:

```
SUSPEND_MODULES="$SUSPEND_MODULES btusb iwl4965 usbhid" 
```
Save, close the editor and try suspend. Additional modules (left column!) of the "grep" command may be added accordingly.

---

### Post by nisargshah on 2013-08-20
You mean I should run first two commands and write the 00sleep_module file and then try suspending my laptop? And what do you mean by *'Additional modules (left column!) of the "grep" command may be added accordingly.'*?

---

### Post by nisargshah on 2013-08-20
You mean I should run first two commands and write the 00sleep_module file and then try suspending my laptop? And what do you mean by *'Additional modules (left column!) of the "grep" command may be added accordingly.'*?

---

### Post by praseodym on 2013-08-20
Yes, put them into the same line as described.

---

### Post by nisargshah on 2013-08-22
I switched to Unity 2D (because my laptop was damn slow) and the problem does not exist here. As for Unity 3D, I'll have to test it.

---

