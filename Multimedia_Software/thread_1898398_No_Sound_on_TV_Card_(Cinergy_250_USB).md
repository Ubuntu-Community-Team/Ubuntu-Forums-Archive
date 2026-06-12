---
title: "No Sound on TV Card (Cinergy 250 USB)"
date: 2011-12-21
forum: Multimedia Software
---

### Post by iliis on 2011-12-21
Hi

I have a Cinergy 250 USB TV-Card that plays TV quite nicely with tvtime but without any sound.

My system:
Mythbuntu 11.10
Kernel 3.0.0-14-generic, x86_64
Mainboard: Asus F1A75-I

```
# **lsusb** | grep Cinergy
Bus 001 Device 002: ID 0ccd:0036 TerraTec Electronic GmbH Cinergy 250 Audio
```

Watching tv via tvtime works, but I get some errors:

```
# **tvtime**
Starte tvtime 1.0.2.
Lese Konfiguration aus /etc/tvtime/tvtime.xml
Lese Konfiguration aus /home/imhotep/.tvtime/tvtime.xml
Home directory /home/imhotep not ours.
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.
Found "Cinergy 250 USB : USB Audio (hw:2,0)"
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
...
[this gets repeated as long as tvtime runs]
```

As far as I can tell, this thing doesn't have sound via USB (even the manual says so). Still, I get this:


```
# **arecord -l **
**** List of CAPTURE Hardware Devices ****
Home directory /home/imhotep not ours.
card 1: Generic_1 [HD-Audio Generic], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: USB [Cinergy 250 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
# **aplay -l**
**** List of PLAYBACK Hardware Devices ****
Home directory /home/imhotep not ours.
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I first tried routing the audio in software as mentioned in [http://wiki.ubuntuusers.de/em28xx#Ton-Probleme:](http://wiki.ubuntuusers.de/em28xx#Ton-Probleme:).

```
# **arecord -D *hw:0,0* -f S16_LE -c2 -r48000  | aplay** 
arecord: main:660: audio open error: No such file or directory
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
aplay: main:660: audio open error: No such file or directory
```
I get the same message with hw:1,0 or hw:2,0 instead of hw:0,0.

I also tried sox with no success:
```
# **sox -r 32000 -t alsa hw:1,0 -t alsa hw:0,0**
sox WARN formats: can't set sample rate 32000; using 44100
sox FAIL formats: can't open output file `hw:0,0': snd_pcm_open error: No such file or directory
```

I then tried to route the audio via hardware: I directly connected the output of the TV-Card with a TRS cable with the line in of the motherboard. (The line in works flawless: When I plug in a MP3-player instead, I get sound.)

Video4Linux tells me, that the device is muted:

```
# **v4lctl -c /dev/video0 list**
attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm       | choice | PAL-DK  | NTSC    | NTSC NTSC-M NTSC-M-JP NTSC-M-KR NTSC-443 PAL PAL-BG PAL-H PAL-I PAL-DK PAL-M PAL-N PAL-Nc PAL-60 SECAM SECAM-B
input      | choice | Televis | Televis | Television Composite1 S-Video
audio mode | choice | mono    | mono    | mono stereo lang1 lang2
bright     | int    |     128 |     128 | range is 0 => 255
contrast   | int    |      64 |      64 | range is 0 => 127
color      | int    |      64 |      64 | range is 0 => 127
hue        | int    |       0 |       0 | range is -128 => 127
volume     | int    |      20 |      31 | range is 0 => 31
mute       | bool   | on      | on      |
Chroma AGC | bool   | on      | on      |
```

Unfortunately unmuting or changing the volume doesn't help.

```
# **v4l2-ctl -d /dev/video0 -c mute=0 -c volume=31**; v4lctl -c /dev/video0 list | egrep "(mute|attr)"
attribute  | type   | current | default | comment
mute       | bool   | off     | on      |
```

Interestingly, this gives an error:
```
# **v4lctl -c /dev/video0 volume mute off**
ioctl: VIDIOC_S_CTRL(id=9963781;value=31): Invalid argument
ioctl: VIDIOC_S_CTRL(id=9963785;value=0): Invalid argument
```



Some more infos:
```
# **lspci -nn | grep '\[04[80][13]\]'**
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1714]
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
```

```
# **cat /proc/asound/car*/co*** |  grep Codec
Codec: ATI R6xx HDMI
Codec: Realtek ALC892
```

```
# **lspci -nn|egrep 'ultimedia|udio|sound|AC97|ac97|EMU'**
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1714]
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
```

```
**wget http://www.alsa-project.org/alsa-info.sh && bash ./alsa-info.sh --upload;**
```
[http://www.alsa-project.org/db/?f=99d2aeb221d6b124bf6c8d39066a35d565fecfc5](http://www.alsa-project.org/db/?f=99d2aeb221d6b124bf6c8d39066a35d565fecfc5)

And yes, everything in alsamixer is on 100%.



EDIT: dmesg output when plugging in the card:
```

[   58.848048] usb 1-2: new high speed USB device number 4 using ehci_hcd
[   59.203100] IR NEC protocol handler initialized
[   59.205457] Linux video capture interface: v2.00
[   59.206863] IR RC5(x) protocol handler initialized
[   59.209160] IR RC6 protocol handler initialized
[   59.209527] em28xx: New device TerraTec Electronic GmbH Cinergy 250 USB @ 480 Mbps (0ccd:0036, interface 0, class 0)
[   59.209944] em28xx #0: chip ID is em2820 (or em2710)
[   59.211210] IR JVC protocol handler initialized
[   59.213377] IR Sony protocol handler initialized
[   59.215450] lirc_dev: IR Remote Control driver registered, major 249 
[   59.215919] IR LIRC bridge handler initialized
[   59.338616] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 36 00 10 00 26 03 9e 22 6a 34
[   59.338640] em28xx #0: i2c eeprom 10: 00 00 06 57 4e 00 00 00 60 00 00 00 02 00 00 00
[   59.338658] em28xx #0: i2c eeprom 20: 16 00 01 01 00 00 00 00 00 00 00 00 00 00 00 00
[   59.338676] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 10 01 02 01 00 00 00 00
[   59.338694] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   59.338711] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   59.338728] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 34 03 54 00 65 00
[   59.338746] em28xx #0: i2c eeprom 70: 72 00 72 00 61 00 54 00 65 00 63 00 20 00 45 00
[   59.338763] em28xx #0: i2c eeprom 80: 6c 00 65 00 63 00 74 00 72 00 6f 00 6e 00 69 00
[   59.338781] em28xx #0: i2c eeprom 90: 63 00 20 00 47 00 6d 00 62 00 48 00 00 00 22 03
[   59.338798] em28xx #0: i2c eeprom a0: 43 00 69 00 6e 00 65 00 72 00 67 00 79 00 20 00
[   59.338816] em28xx #0: i2c eeprom b0: 32 00 35 00 30 00 20 00 55 00 53 00 42 00 00 00
[   59.338833] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   59.338851] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   59.338862] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   59.338867] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   59.338874] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x8ba25695
[   59.338875] em28xx #0: EEPROM info:
[   59.338876] em28xx #0:	AC97 audio (5 sample rates)
[   59.338878] em28xx #0:	500mA max power
[   59.338879] em28xx #0:	Table at 0x06, strings=0x229e, 0x346a, 0x0000
[   59.339710] em28xx #0: Identified as Terratec Cinergy 250 USB (card=2)
[   59.368352] Registered IR keymap rc-em-terratec
[   59.368524] input: i2c IR (i2c IR (EM28XX Terratec as /devices/virtual/rc/rc0/input9
[   59.368607] rc0: i2c IR (i2c IR (EM28XX Terratec as /devices/virtual/rc/rc0
[   59.368610] ir-kbd-i2c: i2c IR (i2c IR (EM28XX Terratec detected at i2c-1/1-0030/ir0 [em28xx #0]
[   59.734158] saa7115 1-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[   60.512323] i2c-core: driver [tuner] using legacy suspend method
[   60.512326] i2c-core: driver [tuner] using legacy resume method
[   60.533130] tda9887 1-0043: creating new instance
[   60.533138] tda9887 1-0043: tda988[5/6/7] found
[   60.544133] tuner 1-0043: Tuner 74 found with type(s) Radio TV.
[   60.550622] All bytes are equal. It is not a TEA5767
[   60.550638] tuner 1-0060: Tuner -1 found with type(s) Radio TV.
[   60.554365] tuner-simple 1-0060: creating new instance
[   60.554369] tuner-simple 1-0060: type set to 37 (LG PAL (newer TAPC series))
[   60.602533] em28xx #0: Config register raw data: 0x10
[   60.626394] em28xx #0: AC97 vendor ID = 0xffffffff
[   60.642389] em28xx #0: AC97 features = 0x6a90
[   60.642397] em28xx #0: Empia 202 AC97 audio processor detected
[   61.100116] em28xx #0: v4l2 driver version 0.1.2
[   62.052516] em28xx #0: V4L2 video device registered as video0
[   62.064163] em28xx audio device (0ccd:0036): interface 1, class 1
[   62.064190] em28xx audio device (0ccd:0036): interface 2, class 1
[   62.064254] usbcore: registered new interface driver em28xx
[   62.064259] em28xx driver loaded
[   62.079994] usbcore: registered new interface driver snd-usb-audio

```

---

### Post by iliis on 2011-12-28
Huhu, anyone? What am I missing? Or whom should I rather ask?

---

### Post by iliis on 2012-01-13
Ok, I got some small progress: The Cinergy is hw2,0 and the following works insofar as I get other errors and some clicking noise (only when changing/starting/stopping something):
```

# **arecord -D hw2,0 -f S16_LE -c2 -r48000 | aplay**
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
Playing WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo

```

```

# **sox -r 48000 -t alsa hw:2,0 -t alsa hw:1,0**

hw:2,0: (alsa)

  Encoding: Signed PCM
  Channels: 2 @ 16-bit
Samplerate: 48000Hz
Replaygain: off
  Duration: unknown

In:0.0% 00:00:00.51 [00:00:00.00] Out:20.5k [     |     ]      Clip:0
sox WARN alsa: under-run
In0.00% 00:00:03.41 [00:00:00.00] Out: 160k [     |     ]      Clip:0

```

Doing it either way, tvtime now gives me this:
```

# **tvtime**
Starte tvtime 1.0.2.
Lese Konfiguration aus /etc/tvtime/tvtime.xml
Lese Konfiguration aus /home/imhotep/.tvtime/tvtime.xml
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.
Found "Cinergy 250 USB : USB Audio (hw:2,0)"

--- after a second or two, this gets repeated about 20 times: ---
ALSA lib pcm pulse.c:746:(pulse_prepare) PulseAudio: Unable to create stream: Too large

--- then this gets repeated for as long as tvtime runs: ---
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection terminated

--- after quitting (ESC): ----
Danke, dass Sie tvtime gewählt haben.
Unable to install hw paramsUnable to install hw paramsUnable to install hw paramsUnable to install hw paramsUnable to install hw paramsUnable to install hw paramsUnable to install hw params [...]

```

---

### Post by iliis on 2012-01-20
Adding some more information in the hope that it is relevant...
([http://wiki.ubuntuusers.de/Sound_Problembehebung/Audio-Fehler-Beschreibung]("http://wiki.ubuntuusers.de/Sound_Problembehebung/Audio-Fehler-Beschreibung"))

```

# **uname -r**
3.0.0-14-generic

# **cat /proc/asound/cards**
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb44000 irq 54
 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb40000 irq 16
 2 [USB            ]: USB-Audio - Cinergy 250 USB
                      TerraTec Electronic GmbH Cinergy 250 USB at usb-0000:00:12.2-2, high speed

# **aplay /usr/share/sounds/alsa/Noise.wav              **
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

[Works fine]

# **lspci -nnk | grep -iA2 audio **
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1714]
	Subsystem: ASUSTeK Computer Inc. Device [1043:84c8]
	Kernel driver in use: HDA Intel
--
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:848d]
	Kernel driver in use: HDA Intel

# **ps -C esd**
  PID TTY          TIME CMD

# **ps -C arts**
  PID TTY          TIME CMD

# **ps -C pulseaudio**
  PID TTY          TIME CMD
 1957 ?        00:00:01 pulseaudio

# **grep "^audio" /etc/group | grep "$USER" | wc -l**
0

# **lsmod | grep "snd"**
snd_usb_audio         118064  3 
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_hda_codec_realtek   330769  1 
snd_hda_codec_hdmi     32040  1 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          33390  6 
snd_hda_codec         104802  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96714  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29991  2 snd_pcm,snd_seq
snd                    68266  30 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

# **head -n 3 /proc/asound/card0/codec#0**
Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)

# **head -n 3 /proc/asound/card0/codec97#0/ac97#0-0**
head: cannot open `/proc/asound/card0/codec97#0/ac97#0-0' for reading: No such file or directory

# **head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs**
head: cannot open `/proc/asound/card0/codec97#0/ac97#0-0+regs' for reading: No such file or directory

# **asoundconf list**
asoundconf: command not found

[As I'm using PulseAudio.]


```

---

### Post by iliis on 2012-01-30
bump

---

### Post by virx on 2012-09-18
Did you got it solved?

---

### Post by iliis on 2012-09-19
Unfortunately not really, no. I got a new TV-Card instead (a Sundtek  MediaTV Pro, which has official Linux support) and it works flawlessly  so far. I abandoned the Cinergy 250 but if you find out something let me  know ;)

---

