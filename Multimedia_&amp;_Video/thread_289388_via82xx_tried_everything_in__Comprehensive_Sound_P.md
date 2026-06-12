---
title: "via82xx tried everything in  Comprehensive Sound Problem Solutions Guide"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by gustavo24 on 2006-10-30
I have gone through every step in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), and still have no sound.

I tried LordRaiden's steps (1) through (4), then tried getting ALSA drivers from a fresh kernel, then tried compiling the latest version of ALSA drivers from source (being sure to include the necessary with-cards option to the configure command), and still, all visual indications are that I should have sound (yes, I checked to make sure that mute isn't turned on) but I just don't get any sound. I know that the sound card works because the machine is dual-boot and windoze sound works fine. 

I have a refurbished Gateway MX3215. I'm running Breezy. I previously installed it on an old IBM ThinkPad and sound worked great. 

Here is output from some relevant commands. Any suggestions?
Thanks.

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# grep snd /proc/modules | grep via82
snd_via82xx 29720 1 - Live 0xdca33000
gameport 15496 1 snd_via82xx, Live 0xdca2e000
snd_mpu401_uart 8064 1 snd_via82xx, Live 0xdc974000
snd_via82xx_modem 15880 0 - Live 0xdca00000
snd_ac97_codec 92832 2 snd_via82xx,snd_via82xx_modem, Live 0xdca6b000
snd_pcm 99080 4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss, Live 0xdca0e000
snd 62956 15 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event,snd_seq,snd_via82xx,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live 0xdc9c1000
snd_page_alloc 11272 3 snd_via82xx,snd_via82xx_modem,snd_pcm, Live 0xdc95c000

lspci -v
... (lots of other stuff) ...
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Gateway 2000: Unknown device 0216
        Flags: medium devsel, IRQ 209
        I/O ports at 1000 [size=256]
        Capabilities: [c0] Power Management version 2
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
        Subsystem: Gateway 2000: Unknown device 0216
        Flags: medium devsel, IRQ 209
        I/O ports at 1400 [size=256]
        Capabilities: [d0] Power Management version 2

---

### Post by Sef on 2006-10-31
Here's how I got sound on my via82xx:

I commented out 3 lines and changed the 2 to 0 in the 82viaxx line. To comment out a line, put a # before it. I commented out one line above 'options snd-via82xx-modem index=-0' and the two lines below.

```
# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0
#options snd-usb-audio index=-2
#options snd-usb-usx2y index=-2
```

Save and exit.

Then System > Preferences > Sound and changed the bottom one to 

Then changed sound capture to Via 82C686A/B 50rev.

If you don't have any sound after that, reboot and you should have sound.

---

### Post by erdbeerbauer on 2007-02-17
Hi Sef, 

I have trouble with my soundcard via82xx, too. Your solution sounds good. 
Where can I find the file, in which you commented out the lines? And what is the name of the file?
Thanks
Thomas

---

### Post by Sef on 2007-02-17
> I have trouble with my soundcard via82xx, too. Your solution sounds good.
Where can I find the file, in which you commented out the lines? And what is the name of the file?

```
gksudo gedit /etc/modprobe.d/alsa-base
```

---

