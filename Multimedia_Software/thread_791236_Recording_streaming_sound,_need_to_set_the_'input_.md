---
title: "Recording streaming sound, need to set the 'input source'"
date: 2008-05-12
forum: Multimedia Software
---

### Post by vdawg on 2008-05-12
Hello!

So basically, I am trying to rip sound that it playing through my soundcard (it's an audio clip from a movie), and when I enable the capture switch on my ALSA settings, I only have a choice of "line", "Front Mic" or "Mic" for my Input sources.

So just have a look right at the end... I need to change the value for input source to master for this to be able to work right?

```

vic@puter:~$ amixer contents
numid=18,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=17,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=64,step=0
  : values=64
  | dBscale-min=42949608.96dB,step=1.00dB,mute=0
numid=3,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=19,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=255,255
  | dBscale-min=42949621.96dB,step=0.20dB,mute=0
numid=7,iface=MIXER,name='Front Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=6,iface=MIXER,name='Front Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=25,25
  | dBscale-min=42949638.46dB,step=1.50dB,mute=0
numid=2,iface=MIXER,name='Front Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=1,iface=MIXER,name='Front Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=64,step=0
  : values=64,64
  | dBscale-min=42949608.96dB,step=1.00dB,mute=0
numid=9,iface=MIXER,name='Line Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=8,iface=MIXER,name='Line Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=25,25
  | dBscale-min=42949638.46dB,step=1.50dB,mute=0
numid=5,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=4,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=25,25
  | dBscale-min=42949638.46dB,step=1.50dB,mute=0
numid=11,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=10,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=42949659.46dB,step=1.50dB,mute=0
numid=13,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x00]
numid=14,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0x00 AES2=0x00 AES3=0x00]
numid=15,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x00 AES2=0x00 AES3=0x00]
numid=16,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=20,iface=MIXER,name='Digital Capture Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=120,step=0
  : values=120,120
  | dBscale-min=42949642.96dB,step=0.50dB,mute=0
numid=12,iface=MIXER,name='Input Source'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  : values=2
vic@puter:~$ 

```

On 7.10, I had this "Capture Source" option on my amixer. Check it out:

```

numid=24,iface=MIXER,name='Capture Source'
  ; type=ENUMERATED,access=rw------,values=2,items=8
  ; Item #0 'Mic'
  ; Item #1 'CD'
  ; Item #2 'Video'
  ; Item #3 'Aux'
  ; Item #4 'Line'
  ; Item #5 'Mix'
  ; Item #6 'Mix Mono'
  ; Item #7 'Phone'
  : values=5,5

```

anyways, this new setup is annoying, how do I rip sound now without having to buy a cable that takes the output sound and plugs it back into line in?

help!

---

### Post by vdawg on 2008-05-12
*bump*

---

### Post by vdawg on 2008-05-13
So I figured out a temporary solution using avidemux to rip audio.

[http://www.avidemux.org/admWiki/index.php?title=Save_only_audio](http://www.avidemux.org/admWiki/index.php?title=Save_only_audio)

> 
This is a quick guide for if you want to save only the audio from a file. This is very simple, but quite useful.

   1. Load the video file.
   2. Optional: Set the A & B positions if you want only a portion of the audio track.
   3. From the side panel, Audio section, choose the audio codec you want to use - e.g. MP3, Vorbis, WAV, AAC, or Copy if you just want to extract a piece of the original soundtrack.
   4. Configure the options for your audio codec using the Configure button.
   5. Go the menu: Audio -> Save.
   6. Save the audio file. 

A note of warning: using that method will save the raw audio track. If it is AAC or Vorbis, you will end up with an unplayable file as they need a container to be playable. 


I would still like to know how to actually be able to rip audio directly off my soundcard ... bleh :p

---

### Post by vdawg on 2008-05-22
Well this time around I would like to rip a song that playes in a flash player...

All I want to do is to be able to capture from the Master or PCM instead of the standard Line/Mic options...

---

