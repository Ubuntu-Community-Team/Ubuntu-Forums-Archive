---
title: "Can't record audio"
date: 2008-10-30
forum: Multimedia Software
---

### Post by Amaroq on 2008-10-30
Hey guys, I recently installed ubuntustudios-audio, and have been having fun with the goodies it installed for me when I did so. I've been playing around in Mixxx and I kinda like it so far.

Unfortunately, it doesn't have a save or record option. I assume it's for live mixing. A friend of mine showed me a link that describes how to record sound on linux.
[http://carthick.wordpress.com/2007/11/26/linux-recording-soundcard-output-using-arecord/](http://carthick.wordpress.com/2007/11/26/linux-recording-soundcard-output-using-arecord/)

I went through it and followed its instructions, making sure to substitute things when possible. The result was a ten second long, blank wav file. A click when it started playing, but absolutely no sound in it at all.

I've tried quite a few things to try to record sound, but nothing seems to be working. And before you point me to the official instructions on audio capture with Ubuntu, I already have the ability to record on my mic. I just can't seem to record sounds produced by my own computer.

I'm on Ubuntu 8.04, with an ASUS M3A32-MVP Deluxe motherboard using the ADI AD1988 onboard audio.

Here's the output of 'amixer contents'. Following the instructions in the above link, I changed the values of numids 33, 34, and 35 to 4.

```
numid=37,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=36,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=39,step=0
  : values=39
  | dBscale-min=42949614.46dB,step=1.50dB,mute=0
numid=11,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=38,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=255,255
  | dBscale-min=42949621.96dB,step=0.20dB,mute=0
numid=25,iface=MIXER,name='Front Mic Boost'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=3,step=0
  : values=0,0
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=16,iface=MIXER,name='Front Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=15,iface=MIXER,name='Front Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=42949638.46dB,step=1.50dB,mute=0
numid=6,iface=MIXER,name='Front Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=1,iface=MIXER,name='Front Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=39,step=0
  : values=39,39
  | dBscale-min=42949614.46dB,step=1.50dB,mute=0
numid=7,iface=MIXER,name='Surround Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=2,iface=MIXER,name='Surround Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=39,step=0
  : values=0,0
  | dBscale-min=42949614.46dB,step=1.50dB,mute=0
numid=8,iface=MIXER,name='Center Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=3,iface=MIXER,name='Center Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=39,step=0
  : values=0
  | dBscale-min=42949614.46dB,step=1.50dB,mute=0
numid=9,iface=MIXER,name='LFE Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=4,iface=MIXER,name='LFE Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=39,step=0
  : values=0
  | dBscale-min=42949614.46dB,step=1.50dB,mute=0
numid=18,iface=MIXER,name='Line Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=17,iface=MIXER,name='Line Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=42949638.46dB,step=1.50dB,mute=0
numid=14,iface=MIXER,name='CD Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=13,iface=MIXER,name='CD Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=42949638.46dB,step=1.50dB,mute=0
numid=26,iface=MIXER,name='Mic Boost'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=3,step=0
  : values=3,3
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=20,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=19,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=42949638.46dB,step=1.50dB,mute=0
numid=12,iface=MIXER,name='Mono Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=28,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=30,iface=MIXER,name='Capture Switch',index=1
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=32,iface=MIXER,name='Capture Switch',index=2
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=27,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=54,step=0
  : values=54,54
  | dBscale-min=42949614.46dB,step=1.50dB,mute=0
numid=29,iface=MIXER,name='Capture Volume',index=1
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=54,step=0
  : values=54,54
  | dBscale-min=42949614.46dB,step=1.50dB,mute=0
numid=31,iface=MIXER,name='Capture Volume',index=2
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=54,step=0
  : values=54,54
  | dBscale-min=42949614.46dB,step=1.50dB,mute=0
numid=24,iface=MIXER,name='Analog Mix Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=23,iface=MIXER,name='Analog Mix Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=42949626.46dB,step=1.50dB,mute=0
numid=22,iface=MIXER,name='Beep Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,on
numid=21,iface=MIXER,name='Beep Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=15,step=0
  : values=15,0
  | dBscale-min=42949627.96dB,step=3.00dB,mute=0
numid=39,iface=MIXER,name='Digital Capture Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=120,step=0
  : values=60,60
  | dBscale-min=42949642.96dB,step=0.50dB,mute=0
numid=33,iface=MIXER,name='Input Source'
  ; type=ENUMERATED,access=rw------,values=1,items=5
  ; Item #0 'Front Mic'
  ; Item #1 'Line'
  ; Item #2 'Mic'
  ; Item #3 'CD'
  ; Item #4 'Mix'
  : values=4
numid=34,iface=MIXER,name='Input Source',index=1
  ; type=ENUMERATED,access=rw------,values=1,items=5
  ; Item #0 'Front Mic'
  ; Item #1 'Line'
  ; Item #2 'Mic'
  ; Item #3 'CD'
  ; Item #4 'Mix'
  : values=4
numid=35,iface=MIXER,name='Input Source',index=2
  ; type=ENUMERATED,access=rw------,values=1,items=5
  ; Item #0 'Front Mic'
  ; Item #1 'Line'
  ; Item #2 'Mic'
  ; Item #3 'CD'
  ; Item #4 'Mix'
  : values=4
numid=10,iface=MIXER,name='Side Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=5,iface=MIXER,name='Side Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=39,step=0
  : values=0,0
  | dBscale-min=42949614.46dB,step=1.50dB,mute=0
```

If it helps any, here's the contents of my .asoundrc file. (I made it while following those instructions.)
```
pcm.copy
{
	type plug
	slave
	{
		pcm hw
	}
	route_policy copy
}
```

lspci gives me the following two audio devices:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device

(Wait a minute, since when do video cards have audio?)

---

