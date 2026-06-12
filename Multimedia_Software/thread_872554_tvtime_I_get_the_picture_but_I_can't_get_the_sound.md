---
title: "tvtime: I get the picture but I can't get the sound working"
date: 2008-07-28
forum: Multimedia Software
---

### Post by Perastikos on 2008-07-28
Dear Ubuntu community,

I installed today tvtime in Ubuntu Hardy (8.04.1). I got the picture working but I couldn&#8217;t get the sound working in tvtime.

---------------------------------------

[SIZE="4"]**INFORMATION:**[/SIZE]

uname -r
```
2.6.24-19-generic
```

lspci -nn
```
06:01.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
```

lspci -v
```
06:01.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: KWorld Computer Co. Ltd. Unknown device 7253
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at febef800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
```

lsmod
```
Module                  Size  Used by
saa7134               131920  3 saa7134_dvb,saa7134_alsa
saa7134_dvb            16652  0 
saa7134_alsa           15424  1
```

etc/modprobe.d/options *(something strange: I get the picture working in tvtime with all tuners IDs >=54)*
```
options saa7134 card=17 tuner=54
```

etc/modules
```
saa7134-dvb
saa7134_alsa
```

---------------------------------------

I ran tvtime and then I gave in the terminal the below command:
```
sox -c 1 -w -r 32000 -t alsa hw:1 -t alsa hw:0
```

I got in the terminal the following dynamic messages but I couldn't get the sound working in tvtime:
```
Input File     : 'hw:1' (alsa)
Sample Size    : 16-bit (2 bytes)
Sample Encoding: signed (2's complement)
Channels       : 1
Sample Rate    : 32000

Time: 29:35.87 [00:00.00] of 00:00.00 (0.00%) Samples out: 78.3M Clips: 0
```

I ran also in the terminal the below commands but I couldn't get the sound working in tvtime:
```
sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp
arecord -c 2 -f S16_LE -r 32000 -B 0 -F 0 -D hw:1 | aplay -
```

I played also with the alsamixer options but I couldn't get the sound working in tvtime.
Could someone help me solve my problem? 

Thanks in advance.

---

### Post by Cresho on 2008-07-28
alrighty, im pretty much a pro with this.  I even have my tvtime to record television.  (Yes this is possible through transcode)

anyway, first off, here is my checklist.

1.  in system, prefference, sound, are you using "alsa advanced linux sound architecture"? also alsa mixer but the one with the option to unmute the line-in? and volume up.

2.  is your line out from your kworld going into your line in of your audio card?

3.  make sure you are using an alsa mixer. Make sure you have unmuted your analog mix, unmuted and full volume as well as your line in. unmuted and full volume.  the key here on my sound card is analog mix.  yours I dont know.

are you using the digital through the pci slot or analog?

Sorry for these stupid questions but I find that looking at the easy stuff first is the way to go before we dive into the harder stuff.

my background
-------------
2 television cards both working and in order
1. kworld 115 with high definition (me-tv software) working using digital 5.1 for atsc signal and analog for television through tvtime
2. avermedia stereo running with tvtime also all the bells and whistles with transcode for recording television, or my old vcr home movies through line in or video in.

---

### Post by Perastikos on 2008-07-28
First of all, thanks for the answer pal.

1. I'm uploading a screenshot of the Sound Preferences:
[[IMG]http://img183.imageshack.us/img183/1730/screenshotvs3.th.jpg[/IMG]](http://img183.imageshack.us/img183/1730/screenshotvs3.jpg)

2. I'm using only a tv cable whose one edge is connected to an external tv antenna and the other edge is connected to the pci tv card. The line out from the kworld is not going into the line in of my audio card.

3. I'm using the analog through the pci slot.

By the way, on Windows Vista I can get both picture and sound working.

---

### Post by Cresho on 2008-07-28
look down one

---

### Post by Cresho on 2008-07-28
WOW  what Am I saying.  here is the real deal.


```
#!/bin/bash
tvtime
sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

```

the dsp1 can be 2 or 3 or 0 depending where your dig is located.

This works on my system and yes I unplugged the line in and out from my soundcard to my video card.

---

### Post by Perastikos on 2008-07-28
tvtime -x
```
  -x, --mixer=DEVICE[:CH]    The mixer device and channel to control.
                             (defaults to /dev/mixer:line)

                             Valid channels are:
                                 vol, bass, treble, synth, pcm, speaker, line,
                                 mic, cd, mix, pcm2, rec, igain, ogain, line1,
                                 line2, line3, dig1, dig2, dig3, phin, phout,
                                 video, radio, monitor

```

tvtime -x /dev/mixer:line1 (The sound is not working. Also, I cannot change the volume.)
```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/stavros/.tvtime/tvtime.xml
```

tvtime -x /dev/mixer:dig1 (The sound is not working. I can change the volume only between 99% and 100% but NO SOUND.)
```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/stavros/.tvtime/tvtime.xml
```

---

### Post by Perastikos on 2008-07-28
> **Cresho said:**
> WOW  what Am I saying.  here is the real deal.


```
#!/bin/bash
tvtime
sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

```

the dsp1 can be 2 or 3 or 0 depending where your dig is located.

This works on my system and yes I unplugged the line in and out from my soundcard to my video card.

I ran the above script and I got the below messages in the terminal:
```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/stavros/.tvtime/tvtime.xml
```

I can change the volume but the sound is NOT working at the moment.

---

### Post by Cresho on 2008-07-28
ohh ya do a 


ls -l /dev/dsp1

or change the 1 to another number and look to see if your digital pci audio is running somewhere

tell me is you see any problems

mines says

ls -l /dev/dsp1
crw-rw----+ 1 root audio 14, 19 2008-07-28 01:48 /dev/dsp1

---

### Post by Perastikos on 2008-07-28
ls -l /dev/dsp1
```
crw-rw----+ 1 root audio 14, 19 2008-07-28 10:04 /dev/dsp1
```

I changed the 1 to another number (0, 2, 3 etc) but the sound is not working.

---

### Post by Cresho on 2008-07-28
what card exactly are you running and what install instructions did you use?

---

### Post by Perastikos on 2008-07-28
I own a [Philips HEPC 7511 desktop PC](http://support.thetechguys.com/layout.aspx?ID={6b89afd8-26da-4f58-b195-3c525f26f7a7}&CatID={e4aaa592-ade7-4a6a-a1bb-d07af656e33e}) which has a built-in [Philips TV Card]("http://support.thetechguys.com/layout.aspx?ID={242bc113-800d-46a5-8589-4cffd340dfe3}&CatID={e4aaa592-ade7-4a6a-a1bb-d07af656e33e}"). I don't know the model of the Philips TV Card.

I followed a guide (which is written in my mother tongue Greek) for Philips SAA7133/SAA7135 chips.

---

### Post by Cresho on 2008-07-29
So far at the moment, I recomment using the analog line ouf.......if it has one.  Without the model number, it is difficult to figure out what modules you may need to run to get it running properly.

one last try

ls -l /dev/dspls -l /dev/dsp

let me know what it says.

if you decide to run the analog, here is a script i use to auto enable and disable the audio.  if you want the script to record tv, i can post that too.

modify this to your needs.  this setting is very specific to my hardware

#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --vbidevice=/dev/vbi0 --device=/dev/video1 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;

---

### Post by jrstravino on 2009-05-15
> **Perastikos said:**
> tvtime -x
```
  -x, --mixer=DEVICE[:CH]    The mixer device and channel to control.
                             (defaults to /dev/mixer:line)

                             Valid channels are:
                                 vol, bass, treble, synth, pcm, speaker, line,
                                 mic, cd, mix, pcm2, rec, igain, ogain, line1,
                                 line2, line3, dig1, dig2, dig3, phin, phout,
                                 video, radio, monitor

```

tvtime -x /dev/mixer:line1 (The sound is not working. Also, I cannot change the volume.)
```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/stavros/.tvtime/tvtime.xml
```

tvtime -x /dev/mixer:dig1 (The sound is not working. I can change the volume only between 99% and 100% but NO SOUND.)
```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/stavros/.tvtime/tvtime.xml
```


sox -r 22000 -x -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

-x instead of-w

"22000" for fast audiorate

sound working :p

---

