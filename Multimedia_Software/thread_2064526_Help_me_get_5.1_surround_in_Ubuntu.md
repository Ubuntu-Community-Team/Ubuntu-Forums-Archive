---
title: "Help me get 5.1 surround in Ubuntu"
date: 2012-09-29
forum: Multimedia Software
---

### Post by Groggster on 2012-09-29
I am running Ubuntu 12.04 and I cannot get the surround sound working. I am using the integrated sound card on this motherboard: [http://www.asrock.com/mb/Intel/Z77%20Extreme4/](http://www.asrock.com/mb/Intel/Z77%20Extreme4/) . I am using the Optical out port, and would like 5.1 surround sound. Stereo sound is no problem, but I can't for the life of me figure this one out. Please help me!

---

### Post by BicyclerBoy on 2012-09-29
What you want is multi-channel over iec958 S/PDIF.

The only options are AC3 & DTS.
iec958 only supports PCM stereo & matrix encoded 5.1 AC3 (DD) & DTS.

Ways to get it:
- media player needs to support pass-thru iec958 S/PDIF
- play media with either type audio track
- much more complex encoder..

The pulse audio sound server (in Ubu 12.04) now supports AC3/DTS pass-thru'

Install/run
pavucontrol
- click config tab
- select digital iec958 5.1 output
- click something tab
- tick only PCM AC3 DTS

Without the really complicated AC3 encoder..you can not test pass-thru' without a media player (VLC, mplayer etc) & media.

Some fancy media players (MythTV, XBMC, VLC ??) can encode your stereo & multi-channel FLAC/AAC/OGG into AC3 in real-time..& spit it out the S/PDIF.

---

### Post by Groggster on 2012-09-30
Nice, this seems to take me a bit closer, however, I can not choose IEC958 5.1 surround, it is'nt there. It's not in the standard Ubuntu sound settings either. I can however choose/find "Digital Stereo ( IEC958 ) Output"... That can't be right, can it?

---

### Post by BicyclerBoy on 2012-10-01
My bad advice..

The Digital Surround 5.1 (iec958/AC3) output is the alsa plugin AC3 (much more complex) encoder..
So complex I confused myself..

For AC3/DTS pass-thru' use: 
Select Digital Stereo (iec958/AC3) output + {various} inputs.

Then select "output devices" tab; this now lets you set appropriate outputs for your configuration.

Don't tick AAC MPEG or EAC3.
Small chance your AVR supports AAC.

---

### Post by Destructo47 on 2012-10-01
Open up pulseaudio's config file with this.

```
sudo gedit /etc/pulse/daemon.conf
```

Modify the section that looks like this:

```
; default-sample-format = s16le
;default-sample-rate = 44100
;default-sample-channels = 2
;default-channel-map = front-left,front-right
```

So that it looks like this:

```
; default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 6
default-channel-map = front-left,front-right,front-center,rear-left,rear-right,lfe
```

Make sure you remove the semicolons on each line in order to change things. Optionally, enable LFE remixing if the amount of bass is unsatisfactory by uncommenting the line that says

```
;enable-lfe-remixing = no
```

to

```
enable-lfe-remixing = yes
```

The first step should enable the 5.1 option under Sound settings.

---

