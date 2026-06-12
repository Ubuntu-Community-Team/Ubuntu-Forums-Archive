---
title: "Can't get audio working; HDMI audio or Onboard"
date: 2012-01-30
forum: Mythbuntu
---

### Post by Meph1st0 on 2012-01-30
Ultimately I'd like to get HDMI audio working through my Geforce GT520 but I'm reading online that many people are having a hard time getting it working with that particular card.

But I can't even get my onboard audio working either.  If it's easier to troubleshoot that first then I'd be happy to go that route.

I'm running mythbuntu 11.10


aplay -l shows:
```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

aplay -L
```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    Front speakers
surround40:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=VT82xx,DEV=1
    HDA VIA VT82xx, ALC662 rev1 Digital
    Direct sample mixing device
dsnoop:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=VT82xx,DEV=1
    HDA VIA VT82xx, ALC662 rev1 Digital
    Direct sample snooping device
hw:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=VT82xx,DEV=1
    HDA VIA VT82xx, ALC662 rev1 Digital
    Direct hardware device without any conversions
plughw:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=VT82xx,DEV=1
    HDA VIA VT82xx, ALC662 rev1 Digital
    Hardware device with all software conversions
```

lspci | grep Audio
```
02:00.1 Audio device: nVidia Corporation HDMI Audio stub (rev a1)
03:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:05.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:05.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:05.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
```

cat /proc/asound/cards
 ```
0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xfebfc000 irq 65
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5
 2 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf7000000
 3 [CX180          ]: CX23418 - CX18-0
                      CX23418 #0 Hauppauge HVR-1600 TV/FM Radio/Line-In Capture
```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.24.
```

cat /proc/driver/nvidia/version
```
NVRM version: NVIDIA UNIX x86 Kernel Module  290.10  Wed Nov 16 19:27:25 PST 2011
GCC version:  gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
```

alsamixer has everything unmuted
pulseaudio is installed and pavucontrol doesn't show my hdmi output but it does show the analog output.

I had upgraded the nvidia video cards by downloading it off their website.  So the nvidia drivers are 290.10.

I don't have any ~/.asoundrc file configured.

Any ideas from anyone would be hugely appreciated.

---

### Post by larsolav on 2012-01-30
I don't know if this is true in general, but for me to see the HDMI audio listed after installing a HDMI graphics card I had to disable the on-board audio in bios. Maybe it could work for you too?

---

### Post by rodercot on 2012-01-30
you aplay -l is not even listing the nvidia card. Do you have a /etc/modprobe.d/sound.conf file from an old install by chance or an /etc/asound.conf?

 Install the Nvidia Card, disable on-board audio completely, make sure the bios is set to find the PCI-E card first and then reboot and repost your aplay -l, aplay -L and

 look in dmesg to see if the snd-hda-intel is being loaded for your card you should see something along the probing card 7, 8 , 9 etc.. 

 then post the output of

 grep 'eld_valid' /proc/asound/NVidia/eld*  (note you may need to change the "NVidia" to card0 or card1 to get output from this command)

 if you do not get a valid ID you will not get sound period. this needs to be hooked up via HDMI to an rcvr or a TV or a monitor)

 Dave

---

### Post by Meph1st0 on 2012-01-30
Gentlemen,

To be honest I originally had the onboard audio disabled in the Bios and could see the HDMI sound card in aplay -l but couldn't get it to work.  So that's when I decided to update the nvidia drivers to the latest 290.10 version.  When I did that the HDMI audio disappeared and when I ran aplay -l it showed nothing, same goes for aplay -L.  So at that point I pretty much gave up on hdmi audio and decided to reenable the onboard audio to see if I could get that working instead.  

So that's how I got to the point where HDMI audio is not showing in aplay -l but the onboard audio is.  In the code snippet in my original post you can see that the lspci | grep Audio command does show the HDMI card but it doesn't appear anywhere else.

Rodercot,

This is a clean install of 11.10 so I don't have an /etc/modprobe.d/sound.conf file from an old install.

see the following from dmesg | grep hda

dmesg | grep hda
```
[   86.702272] hda-intel: spurious response 0x40018d:0x0, last cmd=0x924011
[   86.702293] hda-intel: spurious response 0x40018f:0x0, last cmd=0x924011
[   86.702314] hda-intel: spurious response 0x400001:0x0, last cmd=0x924011
[   86.702335] hda-intel: spurious response 0x400000:0x0, last cmd=0x924011
[   86.702355] hda-intel: spurious response 0x400300:0x0, last cmd=0x924011
[   86.702377] hda-intel: spurious response 0xf00000:0x0, last cmd=0x924011
[   86.702398] hda-intel: spurious response 0xf00040:0x0, last cmd=0x924011
[   86.702418] hda-intel: spurious response 0xf00000:0x0, last cmd=0x924011
[   86.702439] hda-intel: spurious response 0x20010b:0x0, last cmd=0x924011
[   86.702460] hda-intel: spurious response 0x20010b:0x0, last cmd=0x924011
[   86.702480] hda-intel: spurious response 0xf00000:0x0, last cmd=0x924011
[   86.702502] hda-intel: spurious response 0xf00000:0x0, last cmd=0x924011
[   86.702522] hda-intel: spurious response 0xf00000:0x0, last cmd=0x924011
[   86.702543] hda-intel: spurious response 0x1014010:0x0, last cmd=0x924011
[   86.702564] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.702585] hda-intel: spurious response 0x1011012:0x0, last cmd=0x924011
[   86.702605] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.702626] hda-intel: spurious response 0x1016011:0x0, last cmd=0x924011
[   86.702647] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.702668] hda-intel: spurious response 0x1a19830:0x0, last cmd=0x924011
[   86.702689] hda-intel: spurious response 0x24:0x0, last cmd=0x924011
[   86.702710] hda-intel: spurious response 0x411111f0:0x0, last cmd=0x924011
[   86.702731] hda-intel: spurious response 0x20:0x0, last cmd=0x924011
[   86.702751] hda-intel: spurious response 0x181303f:0x0, last cmd=0x924011
[   86.702772] hda-intel: spurious response 0x20:0x0, last cmd=0x924011
[   86.702793] hda-intel: spurious response 0x411111f0:0x0, last cmd=0x924011
[   86.702814] hda-intel: spurious response 0x20:0x0, last cmd=0x924011
[   86.702835] hda-intel: spurious response 0x593301f0:0x0, last cmd=0x924011
[   86.702856] hda-intel: spurious response 0x20:0x0, last cmd=0x924011
[   86.702877] hda-intel: spurious response 0x40041e01:0x0, last cmd=0x924011
[   86.702897] hda-intel: spurious response 0x20:0x0, last cmd=0x924011
[   86.702918] hda-intel: spurious response 0x144e120:0x0, last cmd=0x924011
[   86.702938] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.702960] hda-intel: spurious response 0x18490662:0x0, last cmd=0x924011
[   86.702980] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703001] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703022] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703043] hda-intel: spurious response 0xb:0x0, last cmd=0x924011
[   86.703064] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703084] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703106] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703126] hda-intel: spurious response 0x11:0x0, last cmd=0x924011
[   86.703147] hda-intel: spurious response 0x1:0x0, last cmd=0x924011
[   86.703170] hda-intel: spurious response 0xc:0x0, last cmd=0x924011
[   86.703188] hda-intel: spurious response 0x2:0x0, last cmd=0x924011
[   86.703209] hda-intel: spurious response 0xb02:0x0, last cmd=0x924011
[   86.703230] hda-intel: spurious response 0x1:0x0, last cmd=0x924011
[   86.703251] hda-intel: spurious response 0xd:0x0, last cmd=0x924011
[   86.703272] hda-intel: spurious response 0x2:0x0, last cmd=0x924011
[   86.703293] hda-intel: spurious response 0xb03:0x0, last cmd=0x924011
[   86.703313] hda-intel: spurious response 0x1:0x0, last cmd=0x924011
[   86.703334] hda-intel: spurious response 0xe:0x0, last cmd=0x924011
[   86.703355] hda-intel: spurious response 0x2:0x0, last cmd=0x924011
[   86.703376] hda-intel: spurious response 0xb04:0x0, last cmd=0x924011
[   86.703397] hda-intel: spurious response 0x1734:0x0, last cmd=0x924011
[   86.703418] hda-intel: spurious response 0x9:0x0, last cmd=0x924011
[   86.703438] hda-intel: spurious response 0x1b1a1918:0x0, last cmd=0x924011
[   86.703459] hda-intel: spurious response 0x15141d1c:0x0, last cmd=0x924011
[   86.703480] hda-intel: spurious response 0x16:0x0, last cmd=0x924011
[   86.703501] hda-intel: spurious response 0xa:0x0, last cmd=0x924011
[   86.703522] hda-intel: spurious response 0x1b1a1918:0x0, last cmd=0x924011
[   86.703543] hda-intel: spurious response 0x15141d1c:0x0, last cmd=0x924011
[   86.703563] hda-intel: spurious response 0xb16:0x0, last cmd=0x924011
[   86.703584] hda-intel: spurious response 0x34:0x0, last cmd=0x924011
[   86.703605] hda-intel: spurious response 0x1:0x0, last cmd=0x924011
[   86.703626] hda-intel: spurious response 0x6:0x0, last cmd=0x924011
[   86.703647] hda-intel: spurious response 0xe0160:0x0, last cmd=0x924011
[   86.703667] hda-intel: spurious response 0x1:0x0, last cmd=0x924011
[   86.703688] hda-intel: spurious response 0x60160:0x0, last cmd=0x924011
[   86.703709] hda-intel: spurious response 0x1:0x0, last cmd=0x924011
[   86.703730] hda-intel: spurious response 0x1e0160:0x0, last cmd=0x924011
[   86.703752] hda-intel: spurious response 0x1:0x0, last cmd=0x924011
[   86.703772] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703792] hda-intel: spurious response 0xb:0x0, last cmd=0x924011
[   86.703813] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703834] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703855] hda-intel: spurious response 0x1003c:0x0, last cmd=0x924011
[   86.703876] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703896] hda-intel: spurious response 0x10034:0x0, last cmd=0x924011
[   86.703917] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703938] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703959] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.703980] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704016] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704036] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704048] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704067] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704088] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704109] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704129] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704150] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704171] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704192] hda-intel: spurious response 0x24:0x0, last cmd=0x924011
[   86.704212] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704233] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704254] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704275] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704296] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704317] hda-intel: spurious response 0xa:0x0, last cmd=0x924011
[   86.704338] hda-intel: spurious response 0x1b1a1918:0x0, last cmd=0x924011
[   86.704358] hda-intel: spurious response 0x15141d1c:0x0, last cmd=0x924011
[   86.704379] hda-intel: spurious response 0xb16:0x0, last cmd=0x924011
[   86.704400] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704421] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704442] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704463] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704483] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704504] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704525] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704548] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704567] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704587] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704608] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704629] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704650] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704670] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704691] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704712] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704733] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704754] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704775] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704795] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704816] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704837] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704858] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704879] hda-intel: spurious response 0x34040:0x0, last cmd=0x924011
[   86.704900] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.704920] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.704942] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704962] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.704983] hda-intel: spurious response 0x34040:0x0, last cmd=0x924011
[   86.705004] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.705024] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.705045] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705067] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705087] hda-intel: spurious response 0x34040:0x0, last cmd=0x924011
[   86.705108] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.705129] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705149] hda-intel: spurious response 0x40:0x0, last cmd=0x924011
[   86.705170] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705191] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705212] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705233] hda-intel: spurious response 0x80051f09:0x0, last cmd=0x924011
[   86.705254] hda-intel: spurious response 0x80:0x0, last cmd=0x924011
[   86.705274] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705295] hda-intel: spurious response 0x80:0x0, last cmd=0x924011
[   86.705316] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705337] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705358] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705378] hda-intel: spurious response 0x80:0x0, last cmd=0x924011
[   86.705399] hda-intel: spurious response 0x80:0x0, last cmd=0x924011
[   86.705420] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705441] hda-intel: spurious response 0x80051f09:0x0, last cmd=0x924011
[   86.705462] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705483] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705503] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705524] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705545] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705566] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705587] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705607] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705628] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705650] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705670] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705704] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705712] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705734] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705790] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705792] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705816] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705818] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705837] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705857] hda-intel: spurious response 0x50:0x0, last cmd=0x924011
[   86.705878] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705901] hda-intel: spurious response 0x4011:0x0, last cmd=0x924011
[   86.705921] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705942] hda-intel: spurious response 0x50:0x0, last cmd=0x924011
[   86.705963] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.705983] hda-intel: spurious response 0x4011:0x0, last cmd=0x924011
[   86.706004] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706025] hda-intel: spurious response 0x50:0x0, last cmd=0x924011
[   86.706045] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706070] hda-intel: spurious response 0x4011:0x0, last cmd=0x924011
[   86.706087] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706108] hda-intel: spurious response 0x50:0x0, last cmd=0x924011
[   86.706129] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706151] hda-intel: spurious response 0x4011:0x0, last cmd=0x924011
[   86.706170] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706191] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706212] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706233] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706254] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706275] hda-intel: spurious response 0x80:0x0, last cmd=0x924011
[   86.706296] hda-intel: spurious response 0x80:0x0, last cmd=0x924011
[   86.706316] hda-intel: spurious response 0x80051f17:0x0, last cmd=0x924011
[   86.706343] hda-intel: spurious response 0x270300:0x0, last cmd=0x924011
[   86.706358] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706378] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706405] hda-intel: spurious response 0x80:0x0, last cmd=0x924011
[   86.706456] hda-intel: spurious response 0x80:0x0, last cmd=0x924011
[   86.706458] hda-intel: spurious response 0x10:0x0, last cmd=0x924011
[   86.706483] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.706485] hda-intel: spurious response 0x20:0x0, last cmd=0x924011
[   86.706503] hda-intel: spurious response 0x0:0x0, last cmd=0x924011
[   86.780131] hda-intel: spurious response 0x0:0x0, last cmd=0x670d81
[   86.780149] hda-intel: spurious response 0x0:0x0, last cmd=0x670d81
[   86.780170] hda-intel: spurious response 0x0:0x0, last cmd=0x670d81
[   86.780190] hda-intel: spurious response 0x0:0x0, last cmd=0x670d81
[   86.836514] hda-intel: spurious response 0x4011:0x0, last cmd=0x3a0000
[   86.836532] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836552] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836573] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836594] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836615] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836636] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836656] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836677] hda-intel: spurious response 0x80:0x0, last cmd=0x3a0000
[   86.836704] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836719] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836740] hda-intel: spurious response 0x4015:0x0, last cmd=0x3a0000
[   86.836761] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[   86.836781] hda-intel: spurious response 0x52:0x0, last cmd=0x3a0000
[   86.836802] hda-intel: spurious response 0x4015:0x0, last cmd=0x3a0000
```

Also:
```
jbrown@browndvr:/etc/modprobe.d$ grep 'eld_valid' /proc/asound/NVidia/eld*
grep: /proc/asound/NVidia/eld*: No such file or directory
jbrown@browndvr:/etc/modprobe.d$ grep 'eld_valid' /proc/asound/card0/eld*
grep: /proc/asound/card0/eld*: No such file or directory
jbrown@browndvr:/etc/modprobe.d$ grep 'eld_valid' /proc/asound/card1/eld*
grep: /proc/asound/card1/eld*: No such file or directory
```

This is hooked up via HDMI to the TV.  I've also run a standard audio cable to an audio-in port on the TV from the onboard audio.

---

### Post by rodercot on 2012-01-30
So your aplay -l with the card installed and the 290.10 is showing nothing?

 have you looked at the HDaudio file on the nview forums.

 [ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)

 What your describing is new to me. Is this a NEW card. 

 Are you sure that your on board audio is disabled in the bios as well as your on-board video. If there is an igp or igd setting for memory set it to 256 or higher in the bios and check to make sure the bios is allowing your PCI-E video card (GT520) to use an IRQ and reboot. post your cat /proc/interrupts and look and see if you are getting a irq conflict.

 Sorry if you posted but what motherboard are you using? Another suggestion is to install alsa 1.0.24.2 and try it (you can use the alsa upgrade redux script)

 Dave

---

### Post by nickrout on 2012-01-30
I have not read all the words in this thread, but have you scanned for audio devices in mythfrontend setup?

---

### Post by Meph1st0 on 2012-01-31
The aplay -l with the card installed and the 290.10 is showing the onboard audio only.  

I have in fact looked at the HDaudio file on the nview forums and to be honest I couldn't get through it.  A lot of it was over my head.  It does mention that there was a change with GT 520 and any future cards after it that seemed curious.  I think it said it only had one codec.  But I don't really understand what that means.

Snippet from that document:
> This configuration was introduced in the GeForce GT 520 and NVS4200M, and will be used by most GPUs released after those.

This configuration is unique in that it contains a single codec, and there are fewer converters than pin-complexes. Each connector the GPU supports has its own pin-complex. Each pin-complex contains a mux to select which converter to receive audio from.

Each 8-channel converter supports 2, 4, 6, or 8-channel streams.

There may be as many audio streams concurrently active as there are converters present in the codec.

Historically, this configuration was not well supported by the ALSA kernel driver. See GeForce 520 Codec Architecture Support for details on when this was fixed. This document assumes that you are using a kernel that includes this fix; without it, a few cases will work, but most will not, and hence any attempt to use such hardware without the patch will result in frustration.

The card is new to me, but I don't know if it is technically a new card in general.  Don't know when it was released.

The onboard audio is not disabled in the BIOS.  It was when I had first started; before I installed 290.10.  But then after installing 290.10 and seeing that my HDMI audio dissappeard from aplay -l I chose to reenable it in the BIOS.  I can redisable it if you'd like.  The motherboard doesn't have onboard video.

Since the HDMI audio disappeared from aplay -l when I installed 290.10.  Why don't it uninstall 290.10 and go back to the nvidia-current drivers (which I think were 280.something)?  What do you think of that idea?  If you think it's a good idea then how would I go about doing it exactly?  Should I just use the additional drivers utility and activate the nvidia-current drivers option?

I'll have to check the /proc/interrupts file when I get home from work tonight.

The motherboard is as follows:
ASRock 4CoreDual-SATA2 LGA 775 VIA PT880 Pro/PT880 Ultra ATX Intel Motherboard [http://www.newegg.com/Product/Produc...82E16813157115](http://www.newegg.com/Product/Produc...82E16813157115)

How do I find the alsa upgrade redux script?

Nickrout,
I have used the scan for audio devices in the mythfrontend setup section.  It only shows Alsa:default as an option.  With that selected I still don't hear anything.  Speakers are turned up and powered on.  Using headphones on the front panel doesn't work either.

I have used the onboard audio in the past as well, I'm certain that it's not broken.

Thanks again for your help guys I really appreciate it.

---

### Post by Meph1st0 on 2012-01-31
Here's another snippet of information from that HDaudio document from the nview forums.

> 10.11. GeForce 520 Codec Architecture Support
GeForce 520 and newer contain a new codec architecture that required an enhancement to the ALSA driver. This was implemented by the following commit:

[http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commit;h=384a48d71520ca569a63f1e61e51a538bedb16df](http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commit;h=384a48d71520ca569a63f1e61e51a538bedb16df)

Kernel Status:

&#8226;In linux kernel 3.1-rc1 and later. 

Does this mean that I should upgrade my kernel to 3.1-rc1?

Currently I think I'm on kernel 3.0.0 generic or something.  (I'm at work so I can't confirm that).

---

### Post by nickrout on 2012-01-31
> **Meph1st0 said:**
> 
Nickrout,
I have used the scan for audio devices in the mythfrontend setup section.  It only shows Alsa:default as an option.  With that selected I still don't hear anything.  Speakers are turned up and powered on.  Using headphones on the front panel doesn't work either.



Are you sure you scrolled through them all?

---

### Post by Meph1st0 on 2012-01-31
> **nickrout said:**
> Are you sure you scrolled through them all?

Truthfully no, I didn't scroll through them all.  But I would expect before even getting to that point I would need to be able to get audio in VLC, youtube, or some other multimedia program before fussing with the audio settings in mythfrontend.

I've tried using the command line to test it too: 

```
speaker-test -c 2 -r 48000 -D hw:1,9
or
aplay -D hw:1,9 some_file.wav
```

substituting hw:1,9 with the proper card,device numbers.

But I'll give your suggestion a try when I get home from work tonight.

Thanks

---

### Post by rodercot on 2012-01-31
if you have no cards displayed on aplay for the NVIDIA Card then mythfrontend is just gonna error out because the card is not being seen by alsa. I think you should disable the onboard audio because with the spurious errors in your post above makes me think you have an irq conflict possibly. 

 290.10 drivers may or may not have an affect on your situation. You can roll back to 280.13. What ppa did you use to get the 290.10 driver to begin with. 

 ALSA - Google alsa script redux it will be the first link. That is not the proper way to install alsa BUT it works just note that if you update your kernel later then you will have to re-compile and re-install alsa. 

 I would upgrade alsa first to the latest and see if it can find your 520 with the on-board audio disabled. if the 520 does not get seen by aplay after doing this then you can look at the kernel option. if you want to roll back to 280.13 then you will have to remove nvidia-current driver by which means you installed it, but I really do not think the driver is your issue. 290.10 is newer and should have support for 520 cards.

 rgds,

 Dave

---

### Post by nickrout on 2012-01-31
There is a list of what cards are supported by which d rivers in the driver readme ```
zless /usr/share/doc/nvidia-current/README.txt.gz
```

The readmes are also online at nvidia.com.

---

### Post by Meph1st0 on 2012-02-01
Okay, here's the latest update from last night's troubleshooting.  I decided to restore a clonezilla backup to a point where I was at before I loaded the nvidia 290.10 drivers.  I figured after doing this I'd be able to see my hdmi audio in the aplay -l list.  Lo and behold, it wasn't there either.  So loading the 290.10 drivers isn't what caused my hdmi audio to disappear from that list.  I hadn't used any PPA to load 290.10.  I had just downloaded it from Nvidia's website and installed it.

So, then I decided to upgrade my kernel to 3.1.10.  This was before your post, rodercot, suggesting I upgrade Alsa before upgrading my kernel.  After upgrading my kernel I couldn't even boot back into a graphical environment anymore so I simply booted back up into kernel 3.0.15 Generic again and then did the alsa upgrade using the redux script.  (pretty cool script)  After that got upgraded I rebooted and redissabled the onboard audio and made sure to boot back into kernel 3.0.15 Generic.

When I upgraded the Alsa drivers the HDMI audio was now shown in aplay -l.  Progress right?!?  It, in fact, showed two codecs too. One at hw:0,3 and another at hw:0,7.  In some of the posts I'd read online people were having more success using the hw:0,7 as their default in the .asoundrc file.  I didn't do that yet though.  Instead I thought I'd at least try the speaker-test -c 2 -r 48000 -D hw:0,7 command to test it.  It returned an error that I don't remember at the moment.

So we're to the point where we have the hdmit audio in aplay -l but it still won't work.  Maybe that's progress.

I get the feeling though that rodercot is correct in saying that there might be an IRQ conflict.  I haven't had to troubleshoot IRQ issues since Windows 95.  I wouldn't even know where to begin in Ubuntu.

I will repost again once I get home and can look at that error message I got when I did the speaker-test.

---

### Post by rodercot on 2012-02-01
ok the card is now seen - now go into (type) alsamixer and unmute (press M) the card if you have not already and then issue the grep eld from my previous post after a reboot. That is why I mentioned to check the interrupts earlier. Also check dmesg and see if it is now polling the sound card.
 
 Dave

---

### Post by nickrout on 2012-02-01
Now that aplay -l shows the hdmi outputs, you should be able to choose the correct one after scanning for audio devices in the frontend setup.

---

### Post by Meph1st0 on 2012-02-02
This is hands down the strangest problem I've ever had.  Sorry about going so long without responding.  Here's the latest.  Since I last posted I had upgraded Alsa and reported that I could see the hdmi audio in aplay -l.  I still could not get audio to work though using the speaker-test command.

I went into mythfrontend setup and scanned for audio devices.  It showed two HDMI devices, one was hw:0,3 and the other was hw:0,7.  I tried both of them.  To test them I went and attempted to play a video.  No audio.  But the weirdest thing was when I'd press esc to stop the video, the screen would go black and mythfrontend would crash.

So I rebooted.  Suddenly the HDMI audio was no longer shown in aplay -l.  weird, right? So I rebooted and decided to remove my Hauppauge HVR 1600.  This, due to the potential of having an IRQ conflict. I had previously read that this card can conflict with other cards.  I had previously confirmed that it was in fact conflicting with my video card at boot up because it would hog all the virtual memory thus preventing the video card from initializing.  This was solved by adding vmalloc=256M to the Grub boot command. But I removed it anyway.  When I rebooted I saw HDMI audio again in aplay -l.  HAHA! Seems I found the problem. right?...wrong.

I went back into mythfrontend and tried to play a video and mythfrontend crashed again.  reboot...no more hdmi audio listed in aplay -l.  Reboot again...hdmi audio is shown once again.

Here's what I got so far:
```
jbrown@browndvr:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jbrown@browndvr:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
jbrown@browndvr:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.25.
Compiled on Feb  1 2012 for kernel 3.0.0-15-generic (SMP).
jbrown@browndvr:~$ uname -r
3.0.0-15-generic
jbrown@browndvr:~$ speaker-test -c 2 -r 48000 -D hw:0,3

speaker-test 1.0.24.2

Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted
jbrown@browndvr:~$ speaker-test -c 2 -r 48000 -D hw:0,7

speaker-test 1.0.24.2

Playback device is hw:0,7
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted
```

I could try the mythtv scan for audio devices again but I'm sure that mythfrontend will just crash after watching some video....without sound.

Completely at a loss right now....still.

---

### Post by rodercot on 2012-02-03
IF you do not get the card working in linux FIRST it will not work in any other application.

 IN the hdmi audio link from nvidia it says exactly what I am saying to you; here is a line from that file.

 "For HDMI audio to work, both monitor_present and eld_valid must be 1. Furthermore, there will typically be evidence of at least some supported audio formats."
 
 The audio formats he is talking about in the link are noted from the other output tests he suggests checking out. deeper than you need to go to fix this.

 please post your cat /proc/interrupts output
 
 grep the eld file upon reboot with aplay -l showing the card is present.

 go into alsamixer and unmute the sound card after you post the above and I can comment.

 Dave

---

### Post by Meph1st0 on 2012-02-03
Okay, here are the outputs your were looking for:

```
jbrown@browndvr:~$ grep 'eld_valid' /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid           0
/proc/asound/NVidia/eld#0.1:eld_valid           0
jbrown@browndvr:~$ grep 'eld_valid' /proc/asound/card0/eld*
/proc/asound/card0/eld#0.0:eld_valid            0
/proc/asound/card0/eld#0.1:eld_valid            0
jbrown@browndvr:~$ grep 'eld_valid' /proc/asound/card1/eld*
grep: /proc/asound/card1/eld*: No such file or directory
jbrown@browndvr:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jbrown@browndvr:~$ cat /proc/interrupts output
            CPU0       CPU1
   0:         43          0   IO-APIC-edge      timer
   1:          2          0   IO-APIC-edge      i8042
   5:          0          0   IO-APIC-edge      MPU401 UART
   6:          3          0   IO-APIC-edge      floppy
   7:          0          0   IO-APIC-edge      parport0
   8:          0          0   IO-APIC-edge      rtc0
   9:          0          0   IO-APIC-fasteoi   acpi
  12:          4          0   IO-APIC-edge      i8042
  14:     241653          0   IO-APIC-edge      pata_via
  15:          0          0   IO-APIC-edge      pata_via
  18:   10074562          0   IO-APIC-fasteoi   cx88[0], cx88[0]
  20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
  21:      29025          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb4, sata_via
  22:      12542          0   IO-APIC-fasteoi   uhci_hcd:usb3
  23:     135299          0   IO-APIC-fasteoi   uhci_hcd:usb5, eth0
  24:     154384          0   IO-APIC-fasteoi   nvidia
  25:          9          0   IO-APIC-fasteoi   snd_hda_intel
  64:          0          0   PCI-MSI-edge      aerdrv, PCIe PME, pciehp
 NMI:          0          0   Non-maskable interrupts
 LOC:    3948712    4867113   Local timer interrupts
 SPU:          0          0   Spurious interrupts
 PMI:          0          0   Performance monitoring interrupts
 IWI:          0          0   IRQ work interrupts
 RES:    3539223    2514895   Rescheduling interrupts
 CAL:        466        376   Function call interrupts
 TLB:       3600       3013   TLB shootdowns
 TRM:          0          0   Thermal event interrupts
 THR:          0          0   Threshold APIC interrupts
 MCE:          0          0   Machine check exceptions
 MCP:        269        269   Machine check polls
 ERR:          0
 MIS:          0
cat: output: No such file or directory
jbrown@browndvr:~$
```

I hope that helps.  I don't see anything that stands out to me.  both spdif outputs are unmuted in alsamixer.

---

### Post by rodercot on 2012-02-03
OK, we have to figure out why you have no valid id's. The wiki for hdaudio pass through shows 520gt card working with kernels 2.635+ and alsa 1.0.24. it seems weird that eld is not reporting a positive integer like 0.0, 1.0 etc... unless this is something to do with the gt 520 architecture. I do not see any irq issues.

 now can you post the output from 
 
 ls -F /proc/asound/card0

 and

 cat /proc/asound/card0/eld#0.0

 cat /proc/asound/card0/eld#0.1

 and post dmesg lines regarding the nvidia card and hda 

 EDIT - Do you still have the NVIDIA Prop driver installed and running it needs to be either from the .run or the restricted drivers applet.

---

### Post by Meph1st0 on 2012-02-03
Okay here's the output of what you asked for:

```
jbrown@browndvr:/proc/driver$ ls -F /proc/asound/card0
codec#0  eld#0.0  eld#0.1  id  pcm3p/  pcm7p/
jbrown@browndvr:/proc/driver$ cat /proc/asound/card0/eld#0.0
monitor_present         0
eld_valid               0
jbrown@browndvr:/proc/driver$ cat /proc/asound/card0/eld#0.1
monitor_present         0
eld_valid               0
jbrown@browndvr:/proc/driver$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
GCC version:  gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3)
jbrown@browndvr:/proc/driver$ dmesg | grep hda
[   14.739221] snd_hda_intel 0000:02:00.1: PCI INT B -> GSI 25 (level, low) -> IRQ 25
[   14.739225] hda_intel: Disabling MSI
[   14.739256] snd_hda_intel 0000:02:00.1: setting latency timer to 64
[   14.739261] snd_hda_intel 0000:02:00.1: PCI: Disallowing DAC for device
[   17.776011] ALSA hda_intel.c:834 azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   18.784008] ALSA hda_intel.c:1563 Codec #0 probe error; disabling it...
[   19.824008] ALSA hda_intel.c:873 hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x000f0000
jbrown@browndvr:/proc/driver$ dmesg | grep nvidia
[   13.678838] nvidia: module license 'NVIDIA' taints kernel.
[   19.842809] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   19.842819] nvidia 0000:02:00.0: setting latency timer to 64
jbrown@browndvr:/proc/driver$
```

As you can see I'm back to running the nvidia_current 280.13 drivers.  There aren't anymore of those spurious response statements in dmesg.

---

### Post by rodercot on 2012-02-03
I am not sure on that error. my suggestion

 Take that dmesg report and post it on the nvidia linux forums. 

 As an option activate the x-swat ppa and upgrade to the 290.10 driver and try it that. The x-swat ppa will install some other files needed that you would not get from installing from the .run nvidia 290.10 download. make sure you have ppa-purge installed prior to installing anything from the x-swat ppa, that way if something breaks you can remove it easily. if you install the x-swat ppa then you can just run 

 sudo apt-get update
 sudo apt-get upgrade and install the few files 

 then run 

 apt-cache policy nvidia-current 

 and you should see the 290.10 or newer driver as a cadidate for installation and if you do then you can do a 

 sudo apt-get install nvidia-current

 if it complains that nvidia-current is already installed then deactivate the nvidia current driver from the applet and recheck the apt-apt cache policy and then sudo apt-get install nvidia-current. you also want to install after that is complete sudo apt-get install libvdpau1 and libvdpau-dev, it might say that libvdpau1 is the newest that is fine but you need to install vdpau to use HD in myth.

 your card maybe new enuff that you need to have newer drivers then what you have AND you might need the 3.3rc1 kernel. but I would try the above first. Your eld should be supplying a list of features about your coard capabilities AND what monitor (hdmi) device and eld is active.

 Your HDMI connection is to a tv or a rcvr and you are connected to that device currently while you are testing right.

 Dave

---

