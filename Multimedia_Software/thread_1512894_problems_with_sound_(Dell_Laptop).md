---
title: "problems with sound (Dell Laptop)"
date: 2010-06-18
forum: Multimedia Software
---

### Post by klemi on 2010-06-18
Hello,

with the laptop of my daughter Dell studio XPS I have installed ubuntu 10.04.

After only the internal loudspeaker functioned, I have connected external boxes. After a restart I have no more sound. Following sound cards are recognised:
```
vera@vera-laptop:~$ lspci | grep -i audio 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
02:00.1 Audio device: ATI Technologies Inc RV710/730
```

Afterwards I have switched over to the actual ALSA version afterwards:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

Has clapped excellently - has also started "alsasound" and everything with regard to. Configuration proved no error message.
Then I have
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
#options snd-pcsp index=-2
options snd-hda-intel model=dell-m6
```

I have pasted the last line.

After this HowTo [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
if I have described with myself the same error message like under "Troublshooting" in the HowTo.

```
10.011678] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   10.011682] snd_hda_codec: Unknown symbol snd_ctl_add
[   10.011835] snd_hda_codec: disagrees about version of symbol snd_card_register
[   10.011837] snd_hda_codec: Unknown symbol snd_card_register
[   10.011936] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   10.011938] snd_hda_codec: Unknown symbol snd_card_proc_new
[   10.012073] snd_hda_codec: disagrees about version of symbol snd_add_device_sysfs_file
[   10.012075] snd_hda_codec: Unknown symbol snd_add_device_sysfs_file
[   10.012230] snd_hda_codec: disagrees about version of symbol snd_ctl_remove
[   10.012232] snd_hda_codec: Unknown symbol snd_ctl_remove
[   10.012331] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   10.012332] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   10.012472] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   10.012473] snd_hda_codec: Unknown symbol snd_ctl_new1
[   10.012620] snd_hda_codec: disagrees about version of symbol snd_component_ad
```

Now it is described in the How To which the "snd hda intel.ko" stand at a wrong place. However, I cannot ascertain with my actual kernel which the Locations / folder are so built up as in the Howto, because my kernel proves following folder structure:

Actual with me is given by:
```
vera@vera-laptop:/lib/modules/2.6.32-22-generic/kernel/ubuntu$ ls
aufs       dm-raid4-5  iscsitarget  ndiswrapper  rfkill
compcache  fsam7400    lirc         omnibook     rtl8192se

```

Can it be which is not quite actual the Howto HdaIntelSoundHowto here any more? Specifically the folder under ubuntu/media cannot understand I with me. 
I cannot call at the moment also installed "alsa utils" or "alsamixergui",-> if I call, e.g., "alsamixergui", then appears:

> alsamixer: function snd_cnt_open failed for deafult. No such file or directory.

What is wrong then here only?
I do not know at the moment any more further.
Am grateful around every help.

Klemi

---

### Post by lidex on 2010-06-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags (the # in toolbar)
What is the full model number?

---

### Post by klemi on 2010-06-20
```
vera@vera-laptop:~$ uname -a
Linux vera-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

```

```
vera@vera-laptop:~$ aplay -l
aplay: device_list:235: keine Soundkarten gefunden ...

```
```
vera@vera-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                          0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA

```

```
vera@vera-laptop:~$ head -n 1 /proc/asound/card*/codec#*
head: „/proc/asound/card*/codec#*“ kann nicht zum Lesen geöffnet werden: No such file or directory

```

Please - help me

Thanks

Klemi

---

### Post by lidex on 2010-06-20
Try this:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**
Still need your full model name and number.
Next this:
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

---

### Post by lkjoel on 2010-06-21
Click on [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") in my sig.
That should fix it.

---

### Post by Yellow Pasque on 2010-06-21
> **lkjoel said:**
> Click on [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") in my sig.
That should fix it.

I like and use OSS4, but I don't recommend other people use it unless they have a well-supported card with a hardware mixer. Most people (especially those with laptops) have some variant of Intel-compatible HDA/Azalia chip, and OSS4 doesn't have the same level of support for the wide array of devices using this standard that ALSA does.

---

### Post by lkjoel on 2010-06-21
Thanks for the tip!
Do you know any sound card support lists for OSS?
There are some at the top of the OSS documentation, but they do not work

---

### Post by lidex on 2010-06-22
At this point I would suggest removing the custom entry from alsa-base.conf. Then after a reboot right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

