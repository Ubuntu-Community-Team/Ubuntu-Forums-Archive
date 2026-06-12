---
title: "Alsa auto-mute not functioning correctly on Chromebook"
date: 2013-09-14
forum: Multimedia Software
---

### Post by mike95 on 2013-09-14
Hi All,

On Samsung Chromebook running Ubuntu 12.04 using Crouton with kde and kubuntu-desktop. Pulse audio is installed.

It appears that Auto-mute for the headphones isn't configured correctly for Chromebook with DAISY-I2S sound card. Alsa is properly turning off/on the headphones but it will only  turn the speakers on when the headphones are unplugged, it will not  turn off the speakers when the headphones are plugged in. Also, whenever headphones are inserted/removed all audio is globally muted and I have to unmute it, I just use kmix for that instead of command line.

I found  this out because I wrote a quick script to toggle off the speakers  manually and set the speaker/headphone volume to decent levels.
```

amixer set 'Right Speaker Mixer Right DAC1' toggle
amixer set 'Left Speaker Mixer Left DAC1' toggle
amixer set Headphone 18
amixer set Speaker 18

```

Then wrote a quick get script that does everything above but get instead of set to see the status.

When headphones unplugged:
```

Simple mixer control 'Right Speaker Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Left Speaker Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Headphone',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 13 [42%] [-22.00dB] Playback [off]
  Front Right: 13 [42%] [-22.00dB] Playback [off]
Simple mixer control 'Speaker',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 39
  Front Left: 20 [51%] [-1.00dB] Playback [on]
  Front Right: 20 [51%] [-1.00dB] Playback [on]

```

after headphones plugged in:
```

Simple mixer control 'Right Speaker Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Left Speaker Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Headphone',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 13 [42%] [-22.00dB] Playback [on]
  Front Right: 13 [42%] [-22.00dB] Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 39
  Front Left: 20 [51%] [-1.00dB] Playback [off]
  Front Right: 20 [51%] [-1.00dB] Playback [off]

```

After unmuting through kmix:
```

Simple  mixer control 'Right Speaker Mixer Right  DAC1',0                                                                                                                  
  Capabilities: pswitch pswitch-joined  penum                                                                                                                             
  Playback channels:  Mono                                                                                                                                                
  Mono: Playback  [on]                                                                                                                                                    
Simple mixer control 'Left Speaker Mixer Left  DAC1',0                                                                                                                    
  Capabilities: pswitch pswitch-joined  penum                                                                                                                             
  Playback channels:  Mono                                                                                                                                                
  Mono: Playback  [on]                                                                                                                                                    
Simple mixer control  'Headphone',0                                                                                                                                       
  Capabilities: volume pswitch  penum                                                                                                                                     
  Playback channels: Front Left - Front  Right                                                                                                                            
  Capture channels: Front Left - Front  Right                                                                                                                             
  Limits: 0 -  31                                                                                                                                                         
  Front Left: 13 [42%] [-22.00dB] Playback  [on]                                                                                                                          
  Front Right: 13 [42%] [-22.00dB] Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 39
  Front Left: 20 [51%] [-1.00dB] Playback [on]
  Front Right: 20 [51%] [-1.00dB] Playback [on]

```

After I run the script:
```

Simple mixer control 'Right Speaker Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Speaker Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Headphone',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 18 [58%] [-11.00dB] Playback [on]
  Front Right: 18 [58%] [-11.00dB] Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 39
  Front Left: 18 [46%] [-3.00dB] Playback [on]
  Front Right: 18 [46%] [-3.00dB] Playback [on]

```

After unplugging headphones:
```
Simple mixer control 'Right Speaker Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Left Speaker Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Headphone',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 13 [42%] [-22.00dB] Playback [off]
  Front Right: 13 [42%] [-22.00dB] Playback [off]
Simple mixer control 'Speaker',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 39
  Front Left: 20 [51%] [-1.00dB] Playback [off]
  Front Right: 20 [51%] [-1.00dB] Playback [off]

```

After unmuting through kmix:
```

Simple mixer control 'Right Speaker Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Left Speaker Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Headphone',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 13 [42%] [-22.00dB] Playback [on]
  Front Right: 13 [42%] [-22.00dB] Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 39
  Front Left: 20 [51%] [-1.00dB] Playback [on]
  Front Right: 20 [51%] [-1.00dB] Playback [on]

```

So  it appears that the auto-mute is targeting the "Speaker", which I've  found is really like the "Master" on most other systems, when it should  be targeting the left/right auto mixers. I have no idea how to fix this.

Additional Issue:
After powering down the Chromebook completely, starting up, and logging in to Ubuntu the sound starts muted. But if I only log out of Ubuntu into ChromeOS and then restart Ubuntu the sound will stay on.

I've  searched for solutions on this forum and elsewhere, other users had  issues with ubuntu not auto-muting when headphones inserting but it  wasn't on chromebook and the solution was an intel specific solution  with alsa, I cannot use this solution because chromebook is running on  ARM with a DAISY-I2S sound card.

Does anyone have thoughts or solutions for this issue?


Here is my alsa info from the alsa-info.sh script incase that's useful.
```
!!################################
!!ALSA Information Script v 0.4.62
!!################################

!!Script ran on: Sat Sep 14 12:15:05 UTC 2013


!!Linux Distribution
!!------------------

Ubuntu 12.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.3 LTS)"


!!DMI Information
!!---------------

Manufacturer:      
Product Name:      
Product Version:   
Firmware Version:  


!!Kernel Information
!!------------------

Kernel release:    3.4.0
Operating System:  GNU/Linux
Architecture:      armv7l
Processor:         armv7l
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.25
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [DAISYI2S       ]: DAISY-I2S - DAISY-I2S
                      DAISY-I2S


!!PCI Soundcards installed in the system
!!--------------------------------------



!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------



!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116,  6 Sep 14 07:14 /dev/snd/controlC0
crw-rw---- 1 root audio 116,  5 Sep 14 07:14 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116,  4 Sep 14 07:14 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116,  3 Sep 14 07:14 /dev/snd/pcmC0D1c
crw-rw---- 1 root audio 116,  2 Sep 14 07:14 /dev/snd/pcmC0D1p
crw------- 1 root root  116,  1 Sep 14 07:14 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 Sep 14 07:14 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 14 07:14 .
drwxr-xr-x 3 root root 200 Sep 14 07:14 ..
lrwxrwxrwx 1 root root  12 Sep 14 07:14 platform-sound.8 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: DAISYI2S [DAISY-I2S], device 0: Playback HiFi-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DAISYI2S [DAISY-I2S], device 1: Capture HiFi-1 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: DAISYI2S [DAISY-I2S], device 0: Playback HiFi-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DAISYI2S [DAISY-I2S], device 1: Capture HiFi-1 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [DAISYI2S]

Card hw:0 'DAISYI2S'/'DAISY-I2S'
  Mixer name    : ''
  Components    : ''
  Controls      : 83
  Simple ctrls  : 79
Simple mixer control 'Headphone',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 18 [58%] [-11.00dB] Playback [on]
  Front Right: 18 [58%] [-11.00dB] Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 39
  Front Left: 18 [46%] [-3.00dB] Playback [on]
  Front Right: 18 [46%] [-3.00dB] Playback [on]
Simple mixer control 'Linein',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 5
  Mono: 5 [100%] [20.00dB]
Simple mixer control 'Linein Mode',0
  Capabilities: enum
  Items: 'Stereo' 'Differential'
  Item0: 'Stereo'
Simple mixer control 'Linein Mux',0
  Capabilities: enum
  Items: 'INA' 'INB'
  Item0: 'INA'
Simple mixer control 'Lineout',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 0 [0%] [-62.00dB] Playback [on]
  Front Right: 0 [0%] [-62.00dB] Playback [on]
Simple mixer control 'Lineout Mode',0
  Capabilities: enum
  Items: 'Stereo' 'Differential'
  Item0: 'Stereo'
Simple mixer control 'ADCL',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 15 [100%] [3.00dB]
Simple mixer control 'ADCL Boost',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%] [0.00dB]
Simple mixer control 'ADCR',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 15 [100%] [3.00dB]
Simple mixer control 'ADCR Boost',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%] [0.00dB]
Simple mixer control 'Biquad1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Biquad2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'DAI1 DAC Filter',0
  Capabilities: enum
  Items: 'Off' 'Elliptical-HPF-16k' 'Butterworth-HPF-16k' 'Elliptical-HPF-8k' 'Butterworth-HPF-8k' 'Butterworth-HPF-Fs/240'
  Item0: 'Off'
Simple mixer control 'DAI1 Filter Mode',0
  Capabilities: enum
  Items: 'Voice' 'Music'
  Item0: 'Music'
Simple mixer control 'DAI2 DAC Filter',0
  Capabilities: enum
  Items: 'Off' 'Elliptical-HPF-16k' 'Butterworth-HPF-16k' 'Elliptical-HPF-8k' 'Butterworth-HPF-8k' 'Butterworth-HPF-Fs/240'
  Item0: 'Off'
Simple mixer control 'DAI2 Filter Mode',0
  Capabilities: enum
  Items: 'Voice' 'Music'
  Item0: 'Voice'
Simple mixer control 'DAI3 DAC Filter',0
  Capabilities: enum
  Items: 'Off' 'Elliptical-HPF-16k' 'Butterworth-HPF-16k' 'Elliptical-HPF-8k' 'Butterworth-HPF-8k' 'Butterworth-HPF-Fs/240'
  Item0: 'Off'
Simple mixer control 'DMIC1 Left',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'DMIC1 Right',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'EQ1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'EQ1 Mode',0
  Capabilities: enum
  Items: 'Default'
  Item0: 'Default'
Simple mixer control 'EQ2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'EQ2 Mode',0
  Capabilities: enum
  Items: 'Default'
  Item0: 'Default'
Simple mixer control 'External MIC',0
  Capabilities: enum
  Items: 'None' 'MIC1' 'MIC2'
  Item0: 'MIC2'
Simple mixer control 'HDMI',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left ADC Mixer IN1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left ADC Mixer IN2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left ADC Mixer MIC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left ADC Mixer MIC2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Left Headphone Mixer IN1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Headphone Mixer IN2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Headphone Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Left Headphone Mixer MIC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Headphone Mixer MIC2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Headphone Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Lineout Mixer IN1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Lineout Mixer IN2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Lineout Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Lineout Mixer MIC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Lineout Mixer MIC2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Lineout Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Speaker Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Speaker Mixer Mono DAC2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Speaker Mixer Mono DAC3',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Left Speaker Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'MIC1',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 20
  Mono: 20 [100%] [20.00dB]
Simple mixer control 'MIC1 Boost',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 2
  Mono: 0 [0%] [0.00dB]
Simple mixer control 'MIC1 External Mic',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'MIC2',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 20
  Mono: 20 [100%] [20.00dB]
Simple mixer control 'MIC2 Boost',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 2
  Mono: 1 [50%] [20.00dB]
Simple mixer control 'MIC2 External Mic',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Receiver',0
  Capabilities: volume volume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 31
  Mono: 0 [0%] [-62.00dB] Playback [on]
Simple mixer control 'Receiver Mixer IN1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Receiver Mixer IN2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Receiver Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Receiver Mixer MIC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Receiver Mixer MIC2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Receiver Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right ADC Mixer IN1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right ADC Mixer IN2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right ADC Mixer MIC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right ADC Mixer MIC2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Right Headphone Mixer IN1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Headphone Mixer IN2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Headphone Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Headphone Mixer MIC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Headphone Mixer MIC2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Headphone Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Right Lineout Mixer IN1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Lineout Mixer IN2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Lineout Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Lineout Mixer MIC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Lineout Mixer MIC2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Lineout Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Speaker Mixer Left DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Speaker Mixer Mono DAC2',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Speaker Mixer Mono DAC3',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Right Speaker Mixer Right DAC1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!--------------

--startcollapse--
state.DAISYI2S {
    control.1 {
        iface MIXER
        name 'EQ1 Mode'
        value Default
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Default
        }
    }
    control.2 {
        iface MIXER
        name 'EQ2 Mode'
        value Default
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Default
        }
    }
    control.3 {
        iface MIXER
        name 'Headphone Volume'
        value.0 18
        value.1 18
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -6700
            dbmax 300
            dbvalue.0 -1100
            dbvalue.1 -1100
        }
    }
    control.4 {
        iface MIXER
        name 'Speaker Volume'
        value.0 18
        value.1 18
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 39'
            dbmin -5900
            dbmax 1200
            dbvalue.0 -300
            dbvalue.1 -300
        }
    }
    control.5 {
        iface MIXER
        name 'Receiver Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -6200
            dbmax 800
            dbvalue.0 -6200
        }
    }
    control.6 {
        iface MIXER
        name 'Lineout Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -6200
            dbmax 800
            dbvalue.0 -6200
            dbvalue.1 -6200
        }
    }
    control.7 {
        iface MIXER
        name 'Headphone Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.8 {
        iface MIXER
        name 'Speaker Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.9 {
        iface MIXER
        name 'Receiver Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.10 {
        iface MIXER
        name 'Lineout Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.11 {
        iface MIXER
        name 'MIC1 Volume'
        value 20
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 20'
            dbmin 0
            dbmax 2000
            dbvalue.0 2000
        }
    }
    control.12 {
        iface MIXER
        name 'MIC2 Volume'
        value 20
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 20'
            dbmin 0
            dbmax 2000
            dbvalue.0 2000
        }
    }
    control.13 {
        iface MIXER
        name 'MIC1 Boost Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 2'
            dbmin 0
            dbmax 3000
            dbvalue.0 0
        }
    }
    control.14 {
        iface MIXER
        name 'MIC2 Boost Volume'
        value 1
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 2'
            dbmin 0
            dbmax 3000
            dbvalue.0 2000
        }
    }
    control.15 {
        iface MIXER
        name 'Linein Volume'
        value 5
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 5'
            dbmin -600
            dbmax 2000
            dbvalue.0 2000
        }
    }
    control.16 {
        iface MIXER
        name 'ADCL Volume'
        value 15
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 15'
            dbmin -1200
            dbmax 300
            dbvalue.0 300
        }
    }
    control.17 {
        iface MIXER
        name 'ADCR Volume'
        value 15
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 15'
            dbmin -1200
            dbmax 300
            dbvalue.0 300
        }
    }
    control.18 {
        iface MIXER
        name 'ADCL Boost Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 3'
            dbmin 0
            dbmax 1800
            dbvalue.0 0
        }
    }
    control.19 {
        iface MIXER
        name 'ADCR Boost Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 3'
            dbmin 0
            dbmax 1800
            dbvalue.0 0
        }
    }
    control.20 {
        iface MIXER
        name 'EQ1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'EQ2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.22 {
        iface MIXER
        name 'Biquad1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'Biquad2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.24 {
        iface MIXER
        name 'DMIC1 Left Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.25 {
        iface MIXER
        name 'DMIC1 Right Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.26 {
        iface MIXER
        name 'MIC1 External Mic Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.27 {
        iface MIXER
        name 'MIC2 External Mic Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.28 {
        iface MIXER
        name 'DAI1 Filter Mode'
        value Music
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Voice
            item.1 Music
        }
    }
    control.29 {
        iface MIXER
        name 'DAI2 Filter Mode'
        value Voice
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Voice
            item.1 Music
        }
    }
    control.30 {
        iface MIXER
        name 'DAI1 DAC Filter'
        value Off
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Off
            item.1 Elliptical-HPF-16k
            item.2 Butterworth-HPF-16k
            item.3 Elliptical-HPF-8k
            item.4 Butterworth-HPF-8k
            item.5 Butterworth-HPF-Fs/240
        }
    }
    control.31 {
        iface MIXER
        name 'DAI2 DAC Filter'
        value Off
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Off
            item.1 Elliptical-HPF-16k
            item.2 Butterworth-HPF-16k
            item.3 Elliptical-HPF-8k
            item.4 Butterworth-HPF-8k
            item.5 Butterworth-HPF-Fs/240
        }
    }
    control.32 {
        iface MIXER
        name 'DAI3 DAC Filter'
        value Off
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Off
            item.1 Elliptical-HPF-16k
            item.2 Butterworth-HPF-16k
            item.3 Elliptical-HPF-8k
            item.4 Butterworth-HPF-8k
            item.5 Butterworth-HPF-Fs/240
        }
    }
    control.33 {
        iface MIXER
        name 'Linein Mode'
        value Stereo
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Stereo
            item.1 Differential
        }
    }
    control.34 {
        iface MIXER
        name 'Lineout Mode'
        value Stereo
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Stereo
            item.1 Differential
        }
    }
    control.35 {
        iface MIXER
        name 'Right ADC Mixer MIC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.36 {
        iface MIXER
        name 'Right ADC Mixer MIC2 Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.37 {
        iface MIXER
        name 'Right ADC Mixer IN1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.38 {
        iface MIXER
        name 'Right ADC Mixer IN2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.39 {
        iface MIXER
        name 'Left ADC Mixer MIC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.40 {
        iface MIXER
        name 'Left ADC Mixer MIC2 Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.41 {
        iface MIXER
        name 'Left ADC Mixer IN1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.42 {
        iface MIXER
        name 'Left ADC Mixer IN2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.43 {
        iface MIXER
        name 'Right Lineout Mixer Left DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.44 {
        iface MIXER
        name 'Right Lineout Mixer Right DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.45 {
        iface MIXER
        name 'Right Lineout Mixer MIC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.46 {
        iface MIXER
        name 'Right Lineout Mixer MIC2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.47 {
        iface MIXER
        name 'Right Lineout Mixer IN1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.48 {
        iface MIXER
        name 'Right Lineout Mixer IN2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.49 {
        iface MIXER
        name 'Left Lineout Mixer Left DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.50 {
        iface MIXER
        name 'Left Lineout Mixer Right DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.51 {
        iface MIXER
        name 'Left Lineout Mixer MIC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.52 {
        iface MIXER
        name 'Left Lineout Mixer MIC2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.53 {
        iface MIXER
        name 'Left Lineout Mixer IN1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.54 {
        iface MIXER
        name 'Left Lineout Mixer IN2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.55 {
        iface MIXER
        name 'Receiver Mixer Left DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.56 {
        iface MIXER
        name 'Receiver Mixer Right DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.57 {
        iface MIXER
        name 'Receiver Mixer MIC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.58 {
        iface MIXER
        name 'Receiver Mixer MIC2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.59 {
        iface MIXER
        name 'Receiver Mixer IN1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.60 {
        iface MIXER
        name 'Receiver Mixer IN2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.61 {
        iface MIXER
        name 'Right Speaker Mixer Left DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.62 {
        iface MIXER
        name 'Right Speaker Mixer Right DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.63 {
        iface MIXER
        name 'Right Speaker Mixer Mono DAC2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.64 {
        iface MIXER
        name 'Right Speaker Mixer Mono DAC3 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.65 {
        iface MIXER
        name 'Left Speaker Mixer Left DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.66 {
        iface MIXER
        name 'Left Speaker Mixer Right DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.67 {
        iface MIXER
        name 'Left Speaker Mixer Mono DAC2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.68 {
        iface MIXER
        name 'Left Speaker Mixer Mono DAC3 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.69 {
        iface MIXER
        name 'Right Headphone Mixer Left DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.70 {
        iface MIXER
        name 'Right Headphone Mixer Right DAC1 Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.71 {
        iface MIXER
        name 'Right Headphone Mixer MIC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.72 {
        iface MIXER
        name 'Right Headphone Mixer MIC2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.73 {
        iface MIXER
        name 'Right Headphone Mixer IN1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.74 {
        iface MIXER
        name 'Right Headphone Mixer IN2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.75 {
        iface MIXER
        name 'Left Headphone Mixer Left DAC1 Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.76 {
        iface MIXER
        name 'Left Headphone Mixer Right DAC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.77 {
        iface MIXER
        name 'Left Headphone Mixer MIC1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.78 {
        iface MIXER
        name 'Left Headphone Mixer MIC2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.79 {
        iface MIXER
        name 'Left Headphone Mixer IN1 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.80 {
        iface MIXER
        name 'Left Headphone Mixer IN2 Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.81 {
        iface MIXER
        name 'Linein Mux'
        value INA
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 INA
            item.1 INB
        }
    }
    control.82 {
        iface MIXER
        name 'External MIC'
        value MIC2
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 None
            item.1 MIC1
            item.2 MIC2
        }
    }
    control.83 {
        iface MIXER
        name 'HDMI Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
isl29018
industrialio
sbs_battery
btmrvl_sdio
btmrvl
i2c_dev
rtc_s3c
bluetooth
zram
zsmalloc
fuse
nf_conntrack_ipv6
nf_defrag_ipv6
ip6table_filter
xt_mark
ip6_tables
mwifiex_sdio
mwifiex
cfg80211
uvcvideo
videobuf2_vmalloc
hid_logitech_dj
hid_logitech_hidpp
joydev


!!ALSA/HDA dmesg
!!--------------

[    1.696727] asoc: HiFi <-> samsung-i2s.0 mapping ok
[    1.697294] input: DAISY-I2S HDMI Jack as /devices/sound.8/sound/card0/input2
[    1.697435] input: DAISY-I2S Headphone Jack as /devices/sound.8/sound/card0/input3
[    1.697573] input: DAISY-I2S Mic Jack as /devices/sound.8/sound/card0/input4
[    1.697911] Netfilter messages via NETLINK v0.30.
--
[    1.726373] cpufreq_interactive: monitoring input on Cypress APA Trackpad (cyapa)
[    1.726403] ALSA device list:
[    1.726408]   #0: DAISY-I2S
--
[  846.040867] call mali.0  returned 0 after 20 usecs
[  846.040882] calling  card0-HDMI-A-1  @ 11916, parent: card0
[  846.040890] call card0-HDMI-A-1  returned 0 after 0 usecs
[  846.040899] calling  card0-eDP-1  @ 11916, parent: card0
--
[  846.079773] call max98095-en.9  returned 0 after 0 usecs
[  846.079784] calling  sound.8  @ 11916, parent: none
[  846.080469] call sound.8  returned 0 after 661 usecs
[  846.080482] calling  gpio-keys.7  @ 11916, parent: none
--
[  846.473549] call gpio-keys.7  returned 0 after 38 usecs
[  846.473572] calling  sound.8  @ 11916, parent: none
[  846.473585] call sound.8  returned 0 after 4 usecs
[  846.473621] calling  max98095-en.9  @ 11916, parent: none
--
[  846.752123] call card0-eDP-1  returned 0 after 0 usecs
[  846.752131] calling  card0-HDMI-A-1  @ 11916, parent: card0
[  846.752139] call card0-HDMI-A-1  returned 0 after 0 usecs
[  846.752151] calling  mali.0  @ 11916, parent: platform

```

---

### Post by mike95 on 2013-09-14
Might just have to delete this post, found that there is an issue with state changes in crouton, will work on figuring out how to get the alsa CRAS plugin installed and working.

[https://github.com/dnschneid/crouton/issues/343](https://github.com/dnschneid/crouton/issues/343)

---

