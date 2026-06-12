---
title: "ASUS X550L inbuilt microphone not working"
date: 2014-11-02
forum: Multimedia Software
---

### Post by doylefermi on 2014-11-02
The microphone of my ASUS X550L doesnt work.

However the camera works fine, with the package 'cheese'.

Also, on inserting a headset with microphone, ubuntu reads the input well and it works.

However, in the case of inbuilt mic, it doesnt work. On switching it OFF and then ON, the bars show up for a second, but disappears soon.

Am ready to post any outputs from terminal. Please do help me. Thank you in advance.

Output of:-

```
lsusb -v
```

[http://pastebin.com/RcXECdMi](http://pastebin.com/RcXECdMi)

---

### Post by vivichrist on 2014-11-23
I think it's something like, you have to add the line 'option snd-hda-intel model=inv-dmic' to a new .conf file in /etc/modprobe.d/

basically the internal mic and external mic need to be swapped around because the internal mic is actually the external mic etc.

you can name the .conf file whatever you want, usually something indicative. use sudo... for super user privileges.

---

### Post by doylefermi on 2014-11-25
I have the following files in /etc/modprob.d/
alsa-base.conf              blacklist-rare-network.conf
ath3k.conf                  blacklist-watchdog.conf
blacklist-ath_pci.conf      dkms.conf
blacklist.conf              fbdev-blacklist.conf
blacklist-firewire.conf     iwlwifi.conf
blacklist-framebuffer.conf  mic.conf
blacklist-modem.conf        mlx4.conf
blacklist-oss.conf          vmwgfx-fbdev.conf

I modified alsa-base.conf and added your lines:
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
**options snd-hda-intel model=inv-dmic**
options snd-hda-intel model=asus

```

What else has to be done? The issue isn't solved yet. Could you make yourself clear in your procedure : To simply make a .conf file and add the above line. What difference is it gonna make?

---

### Post by vivichrist on 2014-12-07
um... yeah I'm also having this problem and in the same manner I couldn't fix it other than to open the PulseAudio Volume Control and switch the internal mic for external mic :(

a lot of asus laptops have this very same issue as they have the same sound chip. I haven't tried all of the different 'model=' options yet and you can only assign one so what you have in the above is a bit bung but you have the right idea. :)

---

### Post by doylefermi on 2014-12-08
How to select between internal and external??

---

### Post by vivichrist on 2014-12-10
As you can see there is a combo box and you just select the other option (Microphone (unplugged)) as they are the wrong labelled. And click the enable button (the green tick). Tap the plastic screen surrounds to see the meter rise and fall ensuring the mic has some volume. etc.

---

### Post by doylefermi on 2014-12-10
As u told, the mic shows its recieving input. But I dont see any green tick and also it reverts back automatically to internal mic after some time. Any help?

---

### Post by vivichrist on 2014-12-14
I guess my icons are different... there are three buttons: "Mute audio", "Lock channels together" and "Set as fallback". I mean the "Set as fallback" button. Yeah and you mite need to set this every time you reboot :(  Set the Microphone(unplugged) as fallback and turn off internal as fallback.

edit: actually yes you are right. this reverts back to internal... :/

---

### Post by Zebra_ on 2015-02-01
Sorry to necro, but has this been resolved yet? I am having the exact same issue [http://ubuntuforums.org/showthread.php?t=2263055&p=13217929#post13217929](http://ubuntuforums.org/showthread.php?t=2263055&p=13217929#post13217929)

---

### Post by bogdan16 on 2015-02-02
Hi,
This issue was resolving by me on a ASUS x550L with the following steps:
1. Install driver from your CD (Realtek)
2. [FONT=arial]Control Panel -> Hardware and Sound -> Sound -> Recording -> Select Microphone and click down on Configure -> On the left side top you will see [/FONT][FONT=arial]Advanced speech options. From there you can configure much better if you enter in Advanced from the down windows.

I hope it helps. [/FONT]

---

### Post by vivichrist on 2015-02-10
bogdan16 you are talking about Windows?

---

### Post by justananomaly on 2015-02-10
> **bogdan16 said:**
> Hi,
This issue was resolving by me on a ASUS x550L with the following steps:
1. Install driver from your CD (Realtek)
2. [FONT=arial]Control Panel -> Hardware and Sound -> Sound -> Recording -> Select Microphone and click down on Configure -> On the left side top you will see [/FONT][FONT=arial]Advanced speech options. From there you can configure much better if you enter in Advanced from the down windows.

I hope it helps. [/FONT]

I have an Asus Q550LF and mine did not come with a CD. Can you share these files? I am having this same issue.

---

