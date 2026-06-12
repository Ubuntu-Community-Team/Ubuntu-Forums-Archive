---
title: "Headphone jack does not mute speakers after upgrade to 9.10 Karmic"
date: 2009-11-05
forum: Multimedia Software
---

### Post by melikamp on 2009-11-05
Upgraded from 9.04 to 9.10 Karmic the other day. After the upgrade the following bug emerged (was working correctly in 9.04):

Inserting the headphone jack does not mute the speakers, but the sound can be heard normally through the speakers as well as the headphones.

```

melikamp@ghash:~$ cat /etc/modprobe.d/alsa-base.conf
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
#options snd-hda-intel power_save=10 power_save_controller=N

```

```
melikamp@ghash:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by marginoferror on 2009-11-06
I have had the same problem since upgrading.

```
...:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by yellowbean on 2009-11-07
Same here. Haven't found any solution yet.

---

### Post by dsrossing on 2009-11-09
Hi Guys,
I'm pretty new to Ubuntu (just started 2 weeks ago), but i am very impressed.... especially considering the cost (nothing)! Unfortunately there are a few bugs, but this fixed it for my HP/compaq nc6220 laptop. I have Ubuntu 9.10.

1) Open a terminal window
2) Type alsamixer
3) Arrow over and highlight Headphon
4) Press m key to toggle the headphone jack sense

For more info on alsamixer, see this link: [http://en.wikipedia.org/wiki/Alsamixer](http://en.wikipedia.org/wiki/Alsamixer)

I spent about 3 hours digging around, trying a bunch of things, and learning some new terminal commands before figuring this out.
Hope that helps!

---

### Post by wileur on 2009-11-10
Hi guys,

I made a script that makes sure it's fixed all the time. It's posted a couple of days ago here:[http://ubuntuforums.org/showthread.php?t=1319424&highlight=laptop+headphone+karmic+detect](http://ubuntuforums.org/showthread.php?t=1319424&highlight=laptop+headphone+karmic+detect)

---

### Post by yellowbean on 2009-11-10
Doesn't seem to be the same problem that I'm having. Actually it seems like it's not properly detecting my heaphone jack at all. I don't have a headphone detect option in alsa-mixer and the headphone volume slider doesn't go above 0. I do get audio out of the headphones though, it's just playing out of my speakers at the same time. I suspect I need to change something in /etc/modprobe.d/alsa-base.conf. No time to look into it now, but hopefully I'll post a solution in the next day or so in case someone else has my issue.

---

### Post by rattamayhorka on 2009-11-11
i have a gateway laptop (m6809m) with a intel stac9205 and i solved it with this:

1.- read the instructions to get the the last version of the alsa project [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

2.- download the script and run it to get the last alsa snapshot

3.- edit the alsa.conf file with sudo properties like this on the terminal:
sudo gedit /etc/modprobe.d/alsa-base.conf

4.- at the end of the file add this:

options snd-hda-intel model=eapd probe_mask=1 position_fix=1

5.- restart your laptop

the trick is "model= eapd" (e)xternal (a)udio (p)ower (d)own
i hope it work for you all...

---

### Post by greg batmarx on 2009-11-15
After searching for hours for the problem-a problem that did not exist in ubuntu 9.04 but arose in the ubuntu 9.10, aka the annoying simultaneous playing of the speakers and the headphones-
I CONFIRM THAT THE SOLUTION PROVIDED BY rattamayhorka SOLVES THE PROBLEM:D:P:)

My laptop is an acer 6530g and following the steps provided,
I managed not only to listen to music from my headphones with the speakers properly muted but moreover the whole process is much smoother and automated than it used to be in ubuntu 9.04!

A big thank also for wileur for providing a useful script!
UBUNTU and UBUNTU community rock!:popcorn:

---

### Post by greg batmarx on 2009-11-15
hm...
After testing more the provided solution i found a rather annoying glitch...
The computer generates all the time a c tic-tac sound behaving like an old analog clock!

Why is this happening?
So setting " options snd-hda-intel model=eapd probe_mask=1 position_fix=1 " leads to this minor adverse effect...

---

### Post by greg batmarx on 2009-11-15
i tried this solution for this minor glitch [http://ubuntuforums.org/showthread.php?t=1313986](http://ubuntuforums.org/showthread.php?t=1313986)
but it did not work for me...
Well,i wrote alsamixer in the console and found out that the problem was the mic!
Muting the mic i got rid of this tic-tac sound and now everything is working perfect!

---

### Post by mkongwe on 2009-11-16
Thank you, you helped me big time.

---

### Post by mkongwe on 2009-11-16
thanks dsrosing..

---

### Post by dsrossing on 2009-11-16
> **mkongwe said:**
> thanks dsrosing..

No problem! It's great to have this community of folks helping each other out.

---

### Post by karan_uil on 2009-11-19
I have updated alsamixer and have a hp pavilion dv6 1211ax laptop
connecting headphones does not mute internal speakers

although DSROSSING's trick works but i then have to do it every time i boot my laptop
more over i then have to redo it if i want to use speakers again

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by jewely on 2009-11-24
Didn't work for me.
I downloaded that script likerattamayhorka said , put it in my homefolder and when i ran it nothing happened.

---

### Post by DavidArrow on 2009-12-20
I have a card Radeon HD 3450, which has HDMI audio bla bla etc...
I have the same problem, when I put the headphone, the speakers keep playing.
I'm attaching a screenshot of the command 'alsamixer', every control that I change there, it changes for the speakers and headphones, and the control 'Headph' I can change it.

---

### Post by m6a2x6 on 2010-07-18
> 1) Open a terminal window
2) Type alsamixer
3) Arrow over and highlight Headphon
4) Press m key to toggle the headphone jack sense

OMG Thank you sooo much it worked perfect here!! I have been looking for months for a solution!!

Damn it was so simple!

---

### Post by sc4bbk on 2010-10-04
position_fix=1 did it for me, codec was IDT 92HD81B1C5,thanks!

---

