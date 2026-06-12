---
title: "Dazzle PVC100 audio setup"
date: 2012-08-26
forum: Mythbuntu
---

### Post by alforddm on 2012-08-26
I'm not running mythbutu but this still seemed the best place to post.

Ubuntu 12.04 and mythtv (the one from the software center) and a Pinnacle Dazzle DVC100.  I have the video set up and can view the video in mythtv but for I can't figure out how to get the audio.  When using tvtime I get both video and sound so I know sound works.  

I have tried following these steps from mythwiki
> 
To choose the correct ALSA device when multiple devices are present, follow these steps:
1. Verify MythTV is able to use ALSA.
2. Find the list of ALSA device names:
aplay -L
3. Prepend "ALSA:" to the name of the device, eg "ALSA:default:CARD=nForce2"
4. Set it via the GUI or in the "settings" table for the "AudioDevice" and "AudioOutputDevice" values.
  

I have left the audio as default in the frontend and have tried 
several variations of the "ALSA:default:CARD=nForce2" using the values I given for the card by using arecord -L to setup the capture card on the backend.  I'm trying to set it up as a "USB MPEG-4 encoder device".  

Here are the outputs from arecord -l
```


**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888-VD Analog [ALC888-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC888-VD Analog [ALC888-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: DVC100 [DVC100], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and arecord -L
```


default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=SB
    HDA ATI SB, ALC888-VD Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=2
    HDA ATI SB, ALC888-VD Analog
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=2
    HDA ATI SB, ALC888-VD Analog
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=2
    HDA ATI SB, ALC888-VD Analog
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=2
    HDA ATI SB, ALC888-VD Analog
    Hardware device with all software conversions
sysdefault:CARD=DVC100
    DVC100, USB Audio
    Default Audio Device
front:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Front speakers
surround40:CARD=DVC100,DEV=0
    DVC100, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=DVC100,DEV=0
    DVC100, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=DVC100,DEV=0
    DVC100, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=DVC100,DEV=0
    DVC100, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=DVC100,DEV=0
    DVC100, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=DVC100,DEV=0
    DVC100, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Direct sample mixing device
dsnoop:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Direct sample snooping device
hw:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Direct hardware device without any conversions
plughw:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Hardware device with all software conversions

```

I'm wondering if I don't need to go back to >  Verify MythTV is able to use ALSA. but I'm not real sure how to do that.

Any help or guidance would be much appreciated.

---

### Post by nickrout on 2012-08-26
> **alforddm said:**
> I'm not running mythbutu but this still seemed the best place to post.

Ubuntu 12.04 and mythtv (the one from the software center) and a Pinnacle Dazzle DVC100.  I have the video set up and can view the video in mythtv but for I can't figure out how to get the audio.  When using tvtime I get both video and sound so I know sound works.  

I have tried following these steps from mythwiki
  

I have left the audio as default in the frontend and have tried 
several variations of the "ALSA:default:CARD=nForce2" using the values I given for the card by using arecord -L to setup the capture card on the backend.  I'm trying to set it up as a "USB MPEG-4 encoder device".  

Here are the outputs from arecord -l
```


**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888-VD Analog [ALC888-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC888-VD Analog [ALC888-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: DVC100 [DVC100], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and arecord -L
```


default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=SB
    HDA ATI SB, ALC888-VD Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=2
    HDA ATI SB, ALC888-VD Analog
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=2
    HDA ATI SB, ALC888-VD Analog
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=2
    HDA ATI SB, ALC888-VD Analog
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC888-VD Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=2
    HDA ATI SB, ALC888-VD Analog
    Hardware device with all software conversions
sysdefault:CARD=DVC100
    DVC100, USB Audio
    Default Audio Device
front:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Front speakers
surround40:CARD=DVC100,DEV=0
    DVC100, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=DVC100,DEV=0
    DVC100, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=DVC100,DEV=0
    DVC100, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=DVC100,DEV=0
    DVC100, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=DVC100,DEV=0
    DVC100, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=DVC100,DEV=0
    DVC100, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Direct sample mixing device
dsnoop:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Direct sample snooping device
hw:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Direct hardware device without any conversions
plughw:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Hardware device with all software conversions

```

I'm wondering if I don't need to go back to  but I'm not real sure how to do that.

Any help or guidance would be much appreciated.

I take it that this is a completely analogue card? If so you need to set the sound capture device in mythtv-setup|capture cards. from the look of your post it is one of these two:

hw:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Direct hardware device without any conversions
plughw:CARD=DVC100,DEV=0
    DVC100, USB Audio
    Hardware device with all software conversions

---

### Post by alforddm on 2012-08-26
It would be set under the "USB MPEG-4 encoder device" along with the video input correct?  This is what I've tried... 

ALSA:plughw:CARD=DVC100,DEV=0
and 
ALSA:hw:CARD=DVC100,DEV=0  

as well as several of the others...I've tried them with and without the DEV=0 as well as trying HW:2,0 which is the setting which works for audio in VLC.

---

### Post by nickrout on 2012-08-26
> **alforddm said:**
> It would be set under the "USB MPEG-4 encoder device" along with the video input correct?  This is what I've tried... 

ALSA:plughw:CARD=DVC100,DEV=0
and 
ALSA:hw:CARD=DVC100,DEV=0  

as well as several of the others...I've tried them with and without the DEV=0 as well as trying HW:2,0 which is the setting which works for audio in VLC.

I don't know whether this is a mpeg4 convertor or an analogue card. I guess the former if the video is working.

---

### Post by alforddm on 2012-08-27
I tried the analog card setting with both ALSA:hw:CARD=DVC100,DEV=0 and ALSA:plughw:CARD=DVC100,DEV=0, as well as hw:2,0 I get video the same as with the "USB MPEG-4 encoder device" but still no audio. 

I do get audio when playing a video file through myth so frontend sound does work.

---

### Post by alforddm on 2012-08-27
I can record from the device using...

```
arecord -d 10 -r 48000 -f S16_LE -c 2 -B 64000 -F 16000 -D hw:CARD=DVC100,DEV=0 input.wav
```

---

### Post by alforddm on 2012-08-27
OK, a bit more...using a jumper that I had forgot I had I plugged the sound in the input on my sound card instead of the dazzle.  Again I can use arecord and get sound and vlc can access the sound (when sound input is set to hw:0,0) but mythtv gets no sound.  Could pulse audio be interfering someway?  Am I setting things up wrong?

---

### Post by nickrout on 2012-08-28
> **alforddm said:**
> OK, a bit more...using a jumper that I had forgot I had I plugged the sound in the input on my sound card instead of the dazzle.  Again I can use arecord and get sound and vlc can access the sound (when sound input is set to hw:0,0) but mythtv gets no sound.  Could pulse audio be interfering someway?  Am I setting things up wrong?

do the recordings you make in myth have sound in them? mediainfo will tell you. and mplayer or the like will help tell you.

---

### Post by alforddm on 2012-08-28
If I play the recorded videos back in mythtv there is no sound.  If I try to transcode the files to view them somewhere else I either can't find the directory or they are not being encoded.  

log time

```
Aug 28 10:48:57 ubuntu mythbackend[6136]: E TVRecEvent audioinput.cpp:55 (CreateDevice) AudioIn: unknown or unsupported audio input device ' ALSA:hw:CARD=DVC100,DEV=0'
Aug 28 10:48:57 ubuntu mythbackend[6136]: E TVRecEvent NuppelVideoRecorder.cpp:765 (AudioInit) NVR(/dev/video0): Failed to create audio device:  ALSA:hw:CARD=DVC100,DEV=0
```

So...Am I inputting the audio incorrectly or is it something with myth?

---

### Post by nickrout on 2012-08-28
> **alforddm said:**
> If I play the recorded videos back in mythtv there is no sound.  If I try to transcode the files to view them somewhere else I either can't find the directory or they are not being encoded.  

log time

```
Aug 28 10:48:57 ubuntu mythbackend[6136]: E TVRecEvent audioinput.cpp:55 (CreateDevice) AudioIn: unknown or unsupported audio input device ' ALSA:hw:CARD=DVC100,DEV=0'
Aug 28 10:48:57 ubuntu mythbackend[6136]: E TVRecEvent NuppelVideoRecorder.cpp:765 (AudioInit) NVR(/dev/video0): Failed to create audio device:  ALSA:hw:CARD=DVC100,DEV=0
```

So...Am I inputting the audio incorrectly or is it something with myth?

I didn't say anything about transcoding. The filename of a recording is channid_starttime.mpg where starttime is in form YYYYMMDDHHMMSS, eg 20120829080400 about now.

Try playing that file (not some transcode) to see if there is in fact any audio there. mediainfo will also assist.

---

### Post by alforddm on 2012-08-29
From what I can tell the recordings I have are saved in /var/lib/mythtv/livetv and have a .nuv extension which mplayer won't play.  Am I looking in the wrong spot?  I looked all through the settings and didn't find another storage location.  However, if mythtv is failing to initialize the device doesn't that mean there would be no sound in the recording as well?

---

### Post by nickrout on 2012-08-29
> **alforddm said:**
> From what I can tell the recordings I have are saved in /var/lib/mythtv/livetv and have a .nuv extension which mplayer won't play.  Am I looking in the wrong spot?  I looked all through the settings and didn't find another storage location.  However, if mythtv is failing to initialize the device doesn't that mean there would be no sound in the recording as well?

OH is myth recording them as nuv? Must be something to do with them being analogue recordings. Odd that mplayer won't play them, try vlc and see what mediainfo says (how many times do I have to say that)

---

### Post by OrangeVixen on 2013-05-22
If you are using v4l2 (video4linux2) as input (/dev/video0) then you may need to run this to make sure audio is not muted:

```

v4l2-ctl --set-standard=ntsc --set-input=0 --set-ctrl=mute=0

```

Also check alsamixer:

```

alsamixer

```

Press F6 and select "DVC100" (or whatever your capture card is) and then F4 to show capture mixers and make sure that "Line" is turned up (press the left and right keys to select the mixer and press up and down keys to adjust the value).

For more reading on where I got that:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=123022](http://forums.linuxmint.com/viewtopic.php?f=42&t=123022)

I verified that with my own DVC100 and audio works in the recording.

The recording command I use (on Precise 12.04) is:

```

avconv -f "alsa" -i "hw:1,0" \
 -f "video4linux2" -video_size "768x576" -i "/dev/video0" \
 -r "40" -c:v "mpeg2video" -q "4" -flags "+ilme+ildct" -y "capture.mpg"

```

Note that I added a -q "4", it's to improve video quality, lower values produce higher quality.

The frame rate -r option is set to "40" since most of my videos are in 30d (29.97) and 40 seemed to cover that. The original was "60" but I felt that was too much.

---

