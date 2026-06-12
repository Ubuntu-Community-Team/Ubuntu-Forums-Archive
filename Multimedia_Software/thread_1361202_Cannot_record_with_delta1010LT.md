---
title: "Cannot record with delta1010LT"
date: 2009-12-21
forum: Multimedia Software
---

### Post by MatyX85 on 2009-12-21
Hi all, here's my first post :)

I'm having some problems for recording with Ubuntu karmic 64bits and my delta1010lt. I use envy24control to configure the sound.
As I had a lot of problems with pulseaudio I have uninstalled it so all goes directly to alsa.
I have my piano connected to the sound card and I *do* get sound, I can hear it but it isn't being recorded. I tried using the gnome sound recorder and audacity with no luck at all. Although I have connected the piano to the input #4 (ADC3) I have all ADCs set to 127 until I get it working well (just in case, you know).
Setting the gnome sound recorder to ADC3 doesn't work.

I'm using the 2.6.31-16-generic kernel.

Can you help me, please?

---

### Post by lidex on 2009-12-21
Open this file for editing(terminal command):
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line at the bottom:
```
options snd-ice1712 model=delta1010lt
```

Save. Close. Reboot.

---

### Post by MatyX85 on 2009-12-21
> **lidex said:**
> Open this file for editing(terminal command):
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```Add this line at the bottom:
```
options snd-ice1712 model=delta1010lt
```Save. Close. Reboot.

Thanks for your answer. I've tried it but unfortunately it didn't work. Here's my /etc/modprobe.d/alsa-base.conf file (I've also added *index=0* to make it default:

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
options snd-pcsp index=-2

# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=0 power_save_controller=N index=1

options snd-ice1712 model=delta1010lt index=0
```

It is still the same thing... I can hear it perfectly but software cannot record it.

---

### Post by MatyX85 on 2009-12-21
... and this is printed when I reload the alsa's drivers:

```
$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/matias/.gvfs
      Output information may be incomplete.
Terminating processes: 3209lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/matias/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/matias/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/matias/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-hda-intel snd-ice1712 snd-ice17xx-ak4xxx snd-ak4xxx-adda snd-cs8427 snd-ac97-codec snd-i2c snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-hda-intel snd-ice1712 snd-ice17xx-ak4xxx snd-ak4xxx-adda snd-cs8427 snd-ac97-codec snd-i2c snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
```

---

### Post by lidex on 2009-12-21
Or maybe this:
```
options snd-ice1712 model=delta1010lt enable=yes index=0
```

You may want to comment out this line:
```
options snd-hda-intel power_save=0 power_save_controller=N index=1
```
and re-order it a bit so it looks like this:
```
options snd-ice1712 model=delta1010lt enable=yes index=0
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=0 power_save_controller=N index=1

```
immediately after this line:
```
options snd-usb-caiaq index=-2
```

---

### Post by lidex on 2009-12-21
Try this command or reboot:
```
sudo /etc/init.d/alsa-utils restart
```
rather than force reload

---

### Post by MatyX85 on 2009-12-21
I've just tried so but it's still the same :(. Immediately after:
```
options snd-usb-caiaq index=-2
```I added:
```
options snd-ice1712 model=delta1010lt enable=yes index=0

# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=0 power_save_controller=N index=1

```After that I've ran the command that you told me to restart alsa but the system behaves in the same way as at the beginning...

---

### Post by lidex on 2009-12-22
I would suggest now going to ```
gnome-alsamixer
```
Insert that command in an Alt+F2 run dialog. You may get some results adjusting settings there as well as "soundcard properties" in the "edit" menu.

---

### Post by MatyX85 on 2010-01-09
> **lidex said:**
> I would suggest now going to ```
gnome-alsamixer
```
Insert that command in an Alt+F2 run dialog. You may get some results adjusting settings there as well as "soundcard properties" in the "edit" menu.

Hi, sorry for my looong delay.

Using the gnome-alsamixer seems to be pretty the same as using the envy24control. I mean, doing any change in the first one is automatically applied to the other one.
I've detected *something* a bit weird, at least for me. Using the gnome-sound-recorder I've noticed that the recording level wasn't in zero. So I've changed every volume level and I see that apparently it is always recording ADC1. It doesn't matter how the other volumes are configured. If it is up, then the gnome recorder recoding level will show some audio input. Otherwise, if it is in zero, the program will show no input.

Any idea?

Thanks,

Matías.

---

### Post by RaumTrug on 2010-01-09
as your card does output & can be controlled with envy24control, I guess the driver is active & working!

have you tried using jack for recording? jack just loves the delta cards, and you can use the multiple inputs with it very well (you just have to find out the numbers...)!

without jack, the whole thing'd default to alsa, which is probably not configured so well...for example gnome-sound-recorder or audacity would use the alsa interface when pulse is not running (deinstalled) and also jack server is not running, too! maybe this could be fixed with a custom "~/.asoundrc"-file configuring input to the channels you are actually using, but that needs more work and understanding than I could provide. seems like the "pure alsa" setup for recording with your card is "borked"!

maybe you just try using jack, installing "jack meterbridge" (visual meters for jack networks) for and probing the proper input channels. you're right, envy24control is just a graphical interface for alsa-mixer-controls - but it's a very nice one ;).

maybe you try firing up a jack server with qjackctl (to get "realtime" working, edit your limits.conf, you'll find lots about it on this forums...standard "fault"), and then connect the "capture" channels (inputs) with meterbridges, or inputs from jack-capable progs like mhwaveedit (bare minimum), rezound (buggy but works), ardour (the daw for linux, complex),.....(audacity is a bit quirky....), and see if you can record this way :)

if your soundcard is cool enough (little latency), you can even use fx (distortion, echo, reverb, phaser/flanger.....) in realtime with jack, and monitor and record effected and clean at the same time!

just watch the input levels of envy24ctl and compare to jack input ports via some meter (jack meterbridge) to find out which capture number ports correspond to the cable inputs...then you connect it to the inputs of your recording app (needs jack support) and you'll go fine. for "monitoring" (hearing what you input) either connect the input ports that bear the signal of your keyboard with the output port where you connected your speaker/headphones with (this does yield a small delay depending on your jack setup, but can have fx in between), or set envy24control output to monitor mixer and raise correct levels for your inputs in the input tab (of e24ctl)...(that's what it's like for my m2496, maybe your's is a little different).

sorry that normal alsa/pulse input doesn't work, but just ask on with any question regarding jack, you know jack "loves" the m-audio delta cards ;)

"good luck!"

---

### Post by MatyX85 on 2010-01-10
Thank you very much, I will try using Jack and I'll be back when I have the results! :)

Cheers.

---

