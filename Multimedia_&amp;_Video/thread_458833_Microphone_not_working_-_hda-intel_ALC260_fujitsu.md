---
title: "Microphone not working - hda-intel ALC260 fujitsu"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by matt_roder on 2007-05-30
Hi folks - my first post!

I have a Fujitsu S7020D laptop.  I've successfully loaded Dapper and had my mic and sound recording working perfectly. However, I couldn't get a few other necessary things working so I upgraded to Fiesty.  I like it.

One major problem, I cannot get Skype or the Sound Recorder to record my voice.  This is important because I need skype for work.

The weird thing is that I have been able to get Ekiga to work just fine and also when I plug in my mic and turn up the "Mic/Line" volume, I can hear myself, just can't record or use skype?!?

I've done extensive research, but I have no idea where I'm coming up short.  Can someone please help?

Here is my /etc/modprobe.d/alsa-base:
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

options snd-hda-intel model=fujitsu


```

Output of lspci | grep -i "audio
```

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

```


cat /proc/asound/devices 
```

  2:        : timer
  3:        : sequencer
  4: [ 0- 6]: digital audio playback
  5: [ 0- 6]: digital audio capture
  6: [ 0- 2]: digital audio capture
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0]   : control

```

I am using:
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

/etc/esound/esd.conf
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

---

### Post by Bazzaah on 2007-05-30
What works for Skype is to change the Sound In device under Skype, Tools/Options/Sound devices. By defalut mine showed my sound card, switched to the other option and now I have perfect Skype just like I do in XP. Maybe something similar would work for the voice recorder?

---

### Post by matt_roder on 2007-05-31
thanks for the idea, but i've done that.


i've switched both SYSTEM >> ADMIN >> SOUND

Alsa and OSS

and also in skype.

anyone w/ a similar config and working set up can post their config files?

---

### Post by realstraw on 2007-05-31
I have exactly the same problem, can hear my voice from the speaker, but cannot record. I need my mic for working too :( this only happens when i upgrade edgy to feisty. The exactly problem happened to my Asus notebook too, when i upgrade from edgy to feisty, my mic is gone. It works perfect fine with edgy, any one have a solution?

---

### Post by scottfinman on 2007-06-01
Battled this problem myself and this solution worked for me:

[http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

Edit: The instructions were not applicable when taken verbatim (earlier version of ALSA perhaps?), however, toggling the settings where it suggests did indeed do it on my system.

---

### Post by matt_roder on 2007-06-03
I *REALLY* appreciate your help folks... but i've done all of this... is there any other recommendations?  Does anyone have a similar configuration and working?

If so, can you please post your config files?

Thanks,
Matt

---

### Post by matt_roder on 2007-06-09
Here is more information in case someone thinks of something, or has any input...issue still not resolved

```
   1. ################################
   2. ALSA Information Script v 0.4.28
   3. ################################
   4.  
   5. Script ran on: Sat Jun  9 01:10:59 EDT 2007
   6.  
   7.  
   8. Linux Distribution
   9. ------------------
  10.  
  11. Ubuntu 7.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 7.04"
  12.  
  13.  
  14. Kernel Information
  15. ------------------
  16.  
  17. Kernel release:    2.6.20-16-generic
  18. Operating System:  GNU/Linux
  19. Architecture:      i686
  20. Processor:         unknown
  21. SMP Enabled:       Yes
  22.  
  23.  
  24. ALSA Version
  25. ------------
  26.  
  27. Driver version:     1.0.14rc1
  28. Library version:    
  29. Utilities version:  1.0.13
  30.  
  31.  
  32. Loaded ALSA modules
  33. -------------------
  34.  
  35. snd_hda_intel
  36.  
  37.  
  38. Soundcards recognised by ALSA
  39. -----------------------------
  40.  
  41. 0 [Intel          ]: HDA-Intel - HDA Intel
  42.                      HDA Intel at 0xb0000000 irq 17
  43.  
  44.  
  45. PCI Soundcards installed in the system
  46. --------------------------------------
  47.  
  48. 00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
  49.  
  50.  
  51. Advanced information - PCI Vendor/Device/Susbsystem ID's
  52. --------------------------------------------------------
  53.  
  54. 00:1b.0 0403: 8086:2668 (rev 04)
  55.         Subsystem: 10cf:1326
  56.  
  57.  
  58. HDA-Intel Codec information
  59. ---------------------------
  60.  
  61. Codec: Realtek ALC260
  62. Address: 0
  63. Vendor Id: 0x10ec0260
  64. Subsystem Id: 0x10cf0000
  65. Revision Id: 0x100400
  66. Default PCM:
  67.    rates [0x560]: 44100 48000 96000 192000
  68.    bits [0xe]: 16 20 24
  69.    formats [0x1]: PCM
  70. Default Amp-In caps: N/A
  71. Default Amp-Out caps: N/A
  72. Node 0x02 [Audio Output] wcaps 0x11: Stereo
  73.  PCM:
  74.    rates [0x560]: 44100 48000 96000 192000
  75.    bits [0xe]: 16 20 24
  76.    formats [0x1]: PCM
  77. Node 0x03 [Audio Output] wcaps 0x211: Stereo Digital
  78.  PCM:
  79.    rates [0x560]: 44100 48000 96000 192000
  80.    bits [0x1e]: 16 20 24 32
  81.    formats [0x1]: PCM
  82. Node 0x04 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  83.  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  84.  Amp-In vals:  [0x21 0x21] [0x21 0x21] [0x21 0x21] [0x21 0x21] [0x21 0x21] [0x21 0x21] [0x21 0x21]
  85.  PCM:
  86.    rates [0x160]: 44100 48000 96000
  87.    bits [0x6]: 16 20
  88.    formats [0x1]: PCM
  89.  Connection: 7
  90.     0x12* 0x13 0x14 0x15 0x16 0x0f 0x10
  91. Node 0x05 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  92.  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  93.  Amp-In vals:  [0x1e 0x1e] [0x1e 0x1e] [0x1e 0x1e] [0x1e 0x1e] [0x1e 0x1e] [0x1e 0x1e] [0x1e 0x1e] [0x1e 0x1e]
  94.  PCM:
  95.    rates [0x160]: 44100 48000 96000
  96.    bits [0x6]: 16 20
  97.    formats [0x1]: PCM
  98.  Connection: 8
  99.     0x12* 0x13 0x14 0x15 0x16 0x07 0x0f 0x10
 100. Node 0x06 [Audio Input] wcaps 0x100391: Stereo Digital
 101.  PCM:
 102.    rates [0x160]: 44100 48000 96000
 103.    bits [0x1e]: 16 20 24 32
 104.    formats [0x1]: PCM
 105.  Connection: 1
 106.     0x19
 107. Node 0x07 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
 108.  Amp-In caps: ofs=0x23, nsteps=0x41, stepsize=0x03, mute=1
 109.  Amp-In vals:  [0x34 0x34] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x3b 0x3b] [0xa5 0xa5] [0x80 0x80] [0x80 0x80]
 110.  Connection: 8
 111.     0x12 0x13 0x14 0x15 0x16 0x17 0x0f 0x10
 112. Node 0x08 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
 113.  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 114.  Amp-In vals:  [0x00 0x00] [0x00 0x00]
 115.  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
 116.  Amp-Out vals:  [0x40 0x40]
 117.  Connection: 2
 118.     0x02 0x07
 119. Node 0x09 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
 120.  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 121.  Amp-In vals:  [0x80 0x80] [0x80 0x80]
 122.  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
 123.  Amp-Out vals:  [0x37 0x37]
 124.  Connection: 2
 125.     0x02 0x07
 126. Node 0x0a [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
 127.  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 128.  Amp-In vals:  [0x80] [0x80]
 129.  Amp-Out caps: ofs=0x23, nsteps=0x41, stepsize=0x03, mute=0
 130.  Amp-Out vals:  [0x00]
 131.  Connection: 2
 132.     0x02 0x07
 133. Node 0x0b [Audio Selector] wcaps 0x300101: Stereo
 134.  Connection: 2
 135.     0x08* 0x09
 136. Node 0x0c [Audio Selector] wcaps 0x300101: Stereo
 137.  Connection: 2
 138.     0x08* 0x09
 139. Node 0x0d [Audio Selector] wcaps 0x300101: Stereo
 140.  Connection: 2
 141.     0x08* 0x09
 142. Node 0x0e [Audio Selector] wcaps 0x300101: Stereo
 143.  Connection: 2
 144.     0x08* 0x09
 145. Node 0x0f [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
 146.  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 147.  Amp-Out vals:  [0x80 0x80]
 148.  Pincap 0x081003f: IN OUT HP EAPD Detect
 149.  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
 150.    Conn = 1/8, Color = Black
 151.  Pin-ctls: 0x00:
 152.  Connection: 1
 153.     0x08
 154. Node 0x10 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
 155.  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 156.  Amp-Out vals:  [0x00 0x00]
 157.  Pincap 0x081003f: IN OUT HP EAPD Detect
 158.  Pin Default 0xe4011110: [Both] Line Out at Sep Right
 159.    Conn = 1/8, Color = Black
 160.  Pin-ctls: 0xc0: OUT HP
 161.  Connection: 1
 162.     0x09
 163. Node 0x11 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
 164.  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 165.  Amp-Out vals:  [0x80]
 166.  Pincap 0x0810: OUT
 167.  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
 168.    Conn = 1/8, Color = Black
 169.  Pin-ctls: 0x00:
 170.  Connection: 1
 171.     0x0a
 172. Node 0x12 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
 173.  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 174.  Amp-Out vals:  [0x80 0x80]
 175.  Pincap 0x08133f: IN OUT HP Detect
 176.  Pin Default 0x03a11820: [Jack] Mic at Ext Left
 177.    Conn = 1/8, Color = Black
 178.  Pin-ctls: 0x21: IN
 179.  Connection: 1
 180.     0x0b
 181. Node 0x13 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
 182.  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 183.  Amp-Out vals:  [0x80 0x80]
 184.  Pincap 0x08133f: IN OUT HP Detect
 185.  Pin Default 0x24811121: [Jack] Line In at Sep Right
 186.    Conn = 1/8, Color = Black
 187.  Pin-ctls: 0x00:
 188.  Connection: 1
 189.     0x0c
 190. Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
 191.  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 192.  Amp-Out vals:  [0x00 0x00]
 193.  Pincap 0x08133f: IN OUT HP Detect
 194.  Pin Default 0x0321101f: [Jack] HP Out at Ext Left
 195.    Conn = 1/8, Color = Black
 196.  Pin-ctls: 0xc0: OUT HP
 197.  Connection: 1
 198.     0x0d
 199. Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
 200.  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
 201.  Amp-Out vals:  [0x80 0x80]
 202.  Pincap 0x08133f: IN OUT HP Detect
 203.  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
 204.    Conn = 1/8, Color = Black
 205.  Pin-ctls: 0x00:
 206.  Connection: 1
 207.     0x0e
 208. Node 0x16 [Pin Complex] wcaps 0x400001: Stereo
 209.  Pincap 0x0820: IN
 210.  Pin Default 0x88331122: [Fixed] CD at Ext Drive Bar
 211.    Conn = ATAPI, Color = Black
 212.  Pin-ctls: 0x00:
 213. Node 0x17 [Pin Complex] wcaps 0x400000: Mono
 214.  Pincap 0x0820: IN
 215.  Pin Default 0xb7931123: [Fixed] Aux at Oth Mobile-In
 216.    Conn = ATAPI, Color = Black
 217.  Pin-ctls: 0x00:
 218. Node 0x18 [Pin Complex] wcaps 0x400380: Mono Digital
 219.  Pincap 0x0814: OUT Detect
 220.  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
 221.    Conn = 1/8, Color = Black
 222.  Pin-ctls: 0x00:
 223.  Connection: 1
 224.     0x03
 225. Node 0x19 [Pin Complex] wcaps 0x400280: Mono Digital
 226.  Pincap 0x0824: IN Detect
 227.  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
 228.    Conn = 1/8, Color = Black
 229.  Pin-ctls: 0x00:
 230. Node 0x1a [Vendor Defined Widget] wcaps 0xf00040: Mono
 231. Node 0x1b [Volume Knob Widget] wcaps 0x600080: Mono
 232. Codec: Generic 11c1 Si3054
 233. Address: 1
 234. Vendor Id: 0x11c13026
 235. Subsystem Id: 0x11c13026
 236. Revision Id: 0x100600
 237.  
 238.  
 239. ALSA Device nodes
 240. -----------------
 241.  
 242. crw-rw---- 1 root audio 116, 9 2007-06-08 23:39 /dev/snd/controlC0
 243. crw-rw---- 1 root audio 116, 8 2007-06-08 23:39 /dev/snd/pcmC0D0c
 244. crw-rw---- 1 root audio 116, 7 2007-06-08 23:39 /dev/snd/pcmC0D0p
 245. crw-rw---- 1 root audio 116, 6 2007-06-08 23:39 /dev/snd/pcmC0D2c
 246. crw-rw---- 1 root audio 116, 5 2007-06-08 23:39 /dev/snd/pcmC0D6c
 247. crw-rw---- 1 root audio 116, 4 2007-06-08 23:39 /dev/snd/pcmC0D6p
 248. crw-rw---- 1 root audio 116, 3 2007-06-08 23:39 /dev/snd/seq
 249. crw-rw---- 1 root audio 116, 2 2007-06-08 23:39 /dev/snd/timer
 250.  
 251.  
 252. Aplay output
 253. ------------
 254.  
 255. **** List of PLAYBACK Hardware Devices ****
 256. card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
 257.  Subdevices: 0/1
 258.  Subdevice #0: subdevice #0
 259. card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
 260.  Subdevices: 1/1
 261.  Subdevice #0: subdevice #0
 262.  
 263.  
 264. Amixer output
 265. -------------
 266.  
 267. -------Mixer controls for card 0 [Intel]
 268.  
 269. Simple mixer control 'Headphone',0
 270.  Capabilities: pvolume pswitch
 271.  Playback channels: Front Left - Front Right
 272.  Limits: Playback 0 - 64
 273.  Mono:
 274.  Front Left: Playback 64 [100%] [0.00dB] [on]
 275.  Front Right: Playback 64 [100%] [0.00dB] [on]
 276. Simple mixer control 'Headphone Jack Mode',0
 277.  Capabilities: enum
 278.  Items: 'Mic 50pc bias' 'Mic 80pc bias' 'Line in' 'Line out' 'Headphone out'
 279.  Item0: 'Headphone out'
 280. Simple mixer control 'PCM',0
 281.  Capabilities: pvolume
 282.  Playback channels: Front Left - Front Right
 283.  Limits: Playback 0 - 255
 284.  Mono:
 285.  Front Left: Playback 229 [90%] [-5.20dB]
 286.  Front Right: Playback 229 [90%] [-5.20dB]
 287. Simple mixer control 'CD',0
 288.  Capabilities: pvolume pswitch
 289.  Playback channels: Front Left - Front Right
 290.  Limits: Playback 0 - 65
 291.  Mono:
 292.  Front Left: Playback 59 [91%] [24.00dB] [on]
 293.  Front Right: Playback 59 [91%] [24.00dB] [on]
 294. Simple mixer control 'Mic/Line',0
 295.  Capabilities: pvolume pswitch
 296.  Playback channels: Front Left - Front Right
 297.  Limits: Playback 0 - 65
 298.  Mono:
 299.  Front Left: Playback 52 [80%] [17.00dB] [on]
 300.  Front Right: Playback 52 [80%] [17.00dB] [on]
 301. Simple mixer control 'Mic/Line Jack Mode',0
 302.  Capabilities: enum
 303.  Items: 'Mic 50pc bias' 'Mic 80pc bias' 'Line in'
 304.  Item0: 'Mic 50pc bias'
 305. Simple mixer control 'Capture',0
 306.  Capabilities: cvolume cswitch
 307.  Capture channels: Front Left - Front Right
 308.  Limits: Capture 0 - 35
 309.  Front Left: Capture 33 [94%] [33.00dB] [on]
 310.  Front Right: Capture 33 [94%] [33.00dB] [on]
 311. Simple mixer control 'Capture',1
 312.  Capabilities: cvolume cswitch
 313.  Capture channels: Front Left - Front Right
 314.  Limits: Capture 0 - 35
 315.  Front Left: Capture 30 [86%] [30.00dB] [on]
 316.  Front Right: Capture 30 [86%] [30.00dB] [on]
 317. Simple mixer control 'Beep',0
 318.  Capabilities: pvolume pswitch
 319.  Playback channels: Front Left - Front Right
 320.  Limits: Playback 0 - 65
 321.  Mono:
 322.  Front Left: Playback 37 [57%] [2.00dB] [off]
 323.  Front Right: Playback 37 [57%] [2.00dB] [off]
 324. Simple mixer control 'Caller ID',0
 325.  Capabilities: pswitch pswitch-joined
 326.  Playback channels: Mono
 327.  Mono: Playback [off]
 328. Simple mixer control 'Input Source',0
 329.  Capabilities: enum
 330.  Items: 'Mic/Line' 'CD' 'Headphone'
 331.  Item0: 'Mic/Line'
 332. Simple mixer control 'Input Source',1
 333.  Capabilities: enum
 334.  Items: 'Mic/Line' 'CD' 'Headphone' 'Mixer'
 335.  Item0: 'Mic/Line'
 336. Simple mixer control 'Internal Speaker',0
 337.  Capabilities: pvolume pswitch
 338.  Playback channels: Front Left - Front Right
 339.  Limits: Playback 0 - 64
 340.  Mono:
 341.  Front Left: Playback 55 [86%] [-9.00dB] [off]
 342.  Front Right: Playback 55 [86%] [-9.00dB] [off]
 343. Simple mixer control 'Off-hook',0
 344.  Capabilities: pswitch pswitch-joined
 345.  Playback channels: Mono
 346.  Mono: Playback [off]
 347.  
 348.  
 349. All Loaded Modules
 350. ------------------
 351.  
 352. Module
 353. ppp_deflate
 354. zlib_deflate
 355. bsd_comp
 356. ppp_async
 357. ppp_generic
 358. slhc
 359. binfmt_misc
 360. rfcomm
 361. l2cap
 362. bluetooth
 363. vmnet
 364. vmmon
 365. ipv6
 366. ppdev
 367. i915
 368. drm
 369. speedstep_centrino
 370. cpufreq_ondemand
 371. cpufreq_powersave
 372. cpufreq_userspace
 373. cpufreq_stats
 374. freq_table
 375. cpufreq_conservative
 376. tc1100_wmi
 377. sony_acpi
 378. pcc_acpi
 379. dev_acpi
 380. container
 381. dock
 382. sbs
 383. video
 384. battery
 385. button
 386. asus_acpi
 387. i2c_ec
 388. i2c_core
 389. ac
 390. backlight
 391. airprime
 392. usbserial
 393. sbp2
 394. lp
 395. fuse
 396. ohci_hcd
 397. pcmcia
 398. joydev
 399. snd_hda_intel
 400. snd_hda_codec
 401. snd_pcm_oss
 402. snd_mixer_oss
 403. irda
 404. snd_pcm
 405. snd_seq_dummy
 406. snd_seq_oss
 407. parport_pc
 408. parport
 409. crc_ccitt
 410. wlan_scan_sta
 411. ath_rate_sample
 412. snd_seq_midi
 413. snd_rawmidi
 414. pcspkr
 415. iTCO_wdt
 416. iTCO_vendor_support
 417. yenta_socket
 418. rsrc_nonstatic
 419. ath_pci
 420. wlan
 421. snd_seq_midi_event
 422. snd_seq
 423. snd_timer
 424. snd_seq_device
 425. psmouse
 426. serio_raw
 427. pcmcia_core
 428. ath_hal
 429. snd
 430. soundcore
 431. snd_page_alloc
 432. intel_agp
 433. agpgart
 434. shpchp
 435. pci_hotplug
 436. af_packet
 437. tsdev
 438. evdev
 439. ext3
 440. jbd
 441. mbcache
 442. sg
 443. sd_mod
 444. ata_piix
 445. ide_cd
 446. cdrom
 447. ata_generic
 448. piix
 449. ohci1394
 450. ieee1394
 451. ahci
 452. libata
 453. scsi_mod
 454. generic
 455. ehci_hcd
 456. tg3
 457. uhci_hcd
 458. usbcore
 459. thermal
 460. processor
 461. fan
 462. fbcon
 463. tileblit
 464. font
 465. bitblit
 466. softcursor
 467. vesafb
 468. capability
 469. commoncap
```

---

### Post by IkimashoZ on 2007-06-13
I have exactly this same issue and in the two months since the feisty release no one has seemed to care.  Sad, because this is supposed to be one of the best supported linux releases ever.  I've been back doing all of my work in my crappy, unstable, slow WinXP, sadly.

For the information on my system see this:
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/108798](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/108798)

It was marked as a problem with alsa-utils, which was updated with the new ubuntu.  Apparently they did something to it so that people with ICH6 sound cards (which apparently isn't many of us) have this inexplicable failure of software to recieve the input that is obviously reaching the computer (but not various applications).

As I said, my solution has been to use windows, unfortunately.  However, when I get back to the states (I'm stuck in Japan for about a month and a half) I totally plan on building a new computer, and I will definitely be making sure that all the parts have open source drivers and are linux compatible.

---

