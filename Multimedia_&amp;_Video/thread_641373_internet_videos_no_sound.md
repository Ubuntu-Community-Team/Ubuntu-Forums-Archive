---
title: "internet videos no sound"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by ubunter1 on 2007-12-15
hi ive made a thread on this in the beginners forum but have managed little help and thought this may be a more appropriate forum so heres my original thread- [http://ubuntuforums.org/showthread.php?t=631681](http://ubuntuforums.org/showthread.php?t=631681)
im wondering if anyone here can help me.thanks for your time.

---

### Post by daimaru on 2007-12-15
hi there maybe i can help. just fixed my sound. the problem with mine was that all sound worked (videos mp3 etc) only flash youtube stuff or embeded videos wmv did not. 
the problem was that flash uses hardware address 0,0 for sound i guess, and my card was registered at 1,0 so it did not work. 

maybe this works for you too. but first try some stuff.

```
sudo asoundconf list
```
if you have more than one device you should set the one you want to use as default.
```
sudo asoundconf set-default-card name_of_card
```
i only had one card listed so that did not work for me but maybe this already solves it for you.

---

### Post by daimaru on 2007-12-15
what i did next was edit my 
/etc/modprobe.d/alsa-base 
and commented out usb-audio under options. 
this of course only worked becuase i use usb-audio (usb-headset).
you may have to edit the file so your soundcard (the one you want to use) 
gets loaded before the 2nd sound card gets loaded. 
that way it will take address 0. check this [link]("http://lists.linuxaudio.org/pipermail/linux-audio-user/2005-November/028365.html") for what someone else did (you will have to adjust it to reflect your hardware drivers though)

---

### Post by ubunter1 on 2007-12-15
hi, thanks for the response,it worked fine until i changed the card,but here is the terminal response from the first code- robert@robert-desktop:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
AudioPCI
robert@robert-desktop:~

the second is-  robert@robert-desktop:~$ sudo asoundconf set-default-AudioPCI
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio

robert@robert-desktop:~$ 

this is whats listed so far as your first post requires.

---

### Post by daimaru on 2007-12-15
second command should read 
```
sudo asoundconf set-default-card AudioPCI
```
with a space in between. but it probably won't work just as it did not work for me so try is one more time after that you will probably have to edit your alsa base file.

---

### Post by ubunter1 on 2007-12-15
yeah i got this- robert@robert-desktop:~$ sudo asoundconf set-default-card AudioPCI
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

i guess i need to try to edit the alsa base file like you said?:confused: .
thanks.

---

### Post by daimaru on 2007-12-15
EDIT: open your system->preferences->hardware information and locate your sound card. click on it and then select the advanced tab. check on what address your alsa.card is listed.
if you have VLC player installed you can also just open that click on preferences go to audio devices - output modules -alsa and check what it says under the audio device ( should be something like hw:0,0 or hw:1,0 hw:0,1)

yeah, before you do find out what audio driver your using (please post the output)
```
lsmod |grep audio
```then ```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.backup
sudo gedit  /etc/modprobe.d/alsa-base
```where all the options are listed add a line with your sounddriver
options snd-yourDriver index=0
save and restart. 

but hey i really don't know if this is even the problem your having with your card.

---

### Post by daimaru on 2007-12-15
check [my thread]("http://ubuntuforums.org/showthread.php?t=641304") where i explained my problem. maybe that helps the screenshot shows the hardware information and vlc stuff. 

if yours is already at 0,0 than most likely you have a totally different problem.

---

### Post by ubunter1 on 2007-12-15
in vlc it says- default, under device name.
in hardware alsa.card type-int, value0(0x0)
before i change the lines in the text,cause maybe its not the same problem.ill post a screen.

---

### Post by ubunter1 on 2007-12-15
output-

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by daimaru on 2007-12-15
yes seems like you have a different problem. probably can't help with it.
but since you asked in your other post what commands you could issue to get more info. 
```
aplay -l
lsmod |grep audio
lshw -C sound
```

maybe this way someone reading the thread can help out. sorry mate.

---

### Post by ubunter1 on 2007-12-15
alright,thanks for your help anyways.

---

### Post by daimaru on 2007-12-15
just remembered list your mozilla plugins too
```
sudo dpkg -l |grep mozilla
```

my video related plugins listed there are:
 mozilla-mplayer                            3.40-5ubuntu5                             MPlayer-Plugin for Mozilla
 totem-mozilla                              2.20.0-0ubuntu3                           Totem Mozilla plugin

---

### Post by ubunter1 on 2007-12-15
robert@robert-desktop:~$ sudo dpkg -l |grep mozilla
rc  mozilla-firefox-adblock                    0.5.3.043-3ubuntu1                   AdBlock extension for the Iceweasel and Icea
ii  mozilla-firefox-locale-en-gb               2.0.0.7+1-0ubuntu2                   Mozilla Firefox English language/region pack
ii  mozilla-helix-player                       1.0.6-3                              the helix audio and video player (browser pl
ii  mozilla-imagezoom                          0.3-1ubuntu1                         Mozilla context menu option to zoom current 
ii  mozilla-mplayer                            3.40-5ubuntu5                        MPlayer-Plugin for Mozilla
ii  totem-mozilla                              2.20.0-0ubuntu3                      Totem Mozilla plugin
robert@robert-desktop:~$

---

### Post by daimaru on 2007-12-15
lol i got the same output except for helix player. so i do hope someone can help you with this. anyways sorry i couldnt be of more help ,.

---

### Post by ubunter1 on 2007-12-15
yeah i dont use helix player so i guess ive installed it by accident:) . but thanks for your help though.

---

