---
title: "ubuntu &amp; sound - all versions"
date: 2010-05-16
forum: Multimedia Software
---

### Post by john1066 on 2010-05-16
I have an aspire 6930g. I've tried 9.04, 9.10 and 10.04. None of them give sound on Skype nor on Audacity. So looks like a general sound problem with Ubuntu. And (believe it or not) both Skype and Audacity run properly on Vista. Now I would really like to get off Vista and would prefer not to have to go to W7. But I do need Skype and Audacity.

Some config info
Skype on Ubuntu uses pulse audio server - no other options available. No matter what I do calls fail.
Skype on Vista uses Realtek High def Audio - works fine.
Bothe use Acer crystal webcam for video and this tests properly on both Ubuntu and Vista.

Ubuntu Audacity uses Alsa default - doesn't work.
Vista Audacity uses Microsoft sound wrapper  - works fine.

I've tried most of what has been suggested elsewhere in this forum - its actually rather depressing to see how often sound is a problem with Ubuntu - its a brilliant product otherwise.

Any suggestions.

Thanks,
John

---

### Post by lidex on 2010-05-16
For skype try this:
Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

Reboot.

For audacity:
> Audacity doesn't support PulseAudio, nor Esound for the moment. You'll have to kill or suspend pulseaudio before you use this application. Audacity uses the PortAudio  cross-platform Audio API which doesnt support pulseaudio. Some work was started on making portaudio support PulseAudio but this does not appear to be under active development currently  and does not work in it's current state.

Audacity can use OSS for sound input and sound output. By changing the 2 settings in preferences to /dev/dsp, and running audacity as

padsp audacity

you route OSS sound through pulseaudio and can have successful playback and recording with audacity. You could also set the sound input to be ALSA which (for regular users) is less likely to be blocked by another application, as recording with multiple applications at once is less commonly done

Using pasuspender to momentarily suspend pulseaudio is another way to use Audacity.

pasuspender -- audacity <argument>


---

### Post by john1066 on 2010-05-17
Thanx lidex,

Afraid that doesn't help. It looks like Skype has no connection to any of my contacts and drops the line immediately, maybe because it has no sound.

Audacity gives the following errors using oss
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)


John

---

### Post by lidex on 2010-05-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. *_Also helpful is the make/model of your PC/Laptop._*

---

### Post by john1066 on 2010-05-17
Hi lidex,

Not au fait with code tags but here is the raw output you asked for

jjs@jjs-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jjs@jjs-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 16 2010 for kernel 2.6.32-22-generic-pae (SMP).
jjs@jjs-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP77/78 HDMI
jjs@jjs-laptop:~$ 


Laptop model is Acer Aspire 6930G - with built-in Acer Crystal Eye webcam.

Thanks for your help.

John

---

### Post by lidex on 2010-05-17
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

6930 references:
[http://www.linlap.com/wiki/acer+aspire+6930g]("http://www.linlap.com/wiki/acer+aspire+6930g")
[http://www.linlap.com/wiki/acer+aspire+6930]("http://www.linlap.com/wiki/acer+aspire+6930")

---

### Post by john1066 on 2010-05-18
Hi Lidex,

Looks like 1 step backward & 1 step forward. I've lost all sound now even on the movie player. System>preferences>sound>hardware gives the following options

[LIST]
[*]off
[*]analogue stereo input
[*]digital stereo (hdmi) output
[*]digital stereo (hdmi) output + analogue stereo input
[*]analogue stereo output
[*]analogue stereo duplex
[/LIST]
Normally this is set to analogue stereo duplex
Using your instructions for the alsamixer I've selected the hda intel soundcard. The mixer has selected the NVIDIA HDMI chip and i don't see other options there nor how to change that. I have the feeling that I need to be able choose the ALC888 analogue chip and/or something to do with the RealtekALC888 codec. That seems to be what Vista is using with Skype and that works.
Any ideas.
Also is there a way I can temporarily undo the Alsamixer to get sound back on the movie player?

Thanks a million,
John

---

### Post by lidex on 2010-05-18
Can you post this output:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by john1066 on 2010-05-19
Hi Lidex,

Here's the output you asked for. Thanks.

John



jjs@jjs-laptop:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-hda-intel model=auto power_save=10 power_save_controller=N
options snd-hda-intel model=acer
jjs@jjs-laptop:~$

---

