---
title: "{Solved] Hauppage Wintv pvr 150"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by MeKino on 2008-04-18
Here's how I FINALLY found a way to make this work.

1. Install ivtv-utils and xawtv
2. Insert card
3. plug in aerial (mine's from a cable receiver - so only 1 "channel")
4. open terminal and enter dmesg | grep ivtv

this should indicate that the card has been detected.
[   49.658774] ivtv:  Start initialization, version 1.1.0
[   49.658985] ivtv0: Initializing card #0
[   49.658993] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   49.706250] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   49.812749] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   49.812751] ivtv0: Reopen i2c bus for IR-blaster support
[   50.495947] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   50.857090] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   51.997974] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   52.017180] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   52.025264] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   52.025289] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   52.025308] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   52.025326] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   52.025352] ivtv0: Registered device radio0 for encoder radio
[   52.025355] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   52.025383] ivtv:  End initialization
[   61.110223] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   61.307030] ivtv0: Encoder revision: 0x02060039

at this point I opened VLC but there was no picture.

5. go back to terminal and enter  scantv -c /dev/video0 -C /dev/vbi0 -o ~/.xawtv
because I live in the UK I chose PAL I and western-europe option.
This now displayed a list of channels and frequencies.
A signal was detected on 855.25 MHz

6. Open VLC and select File -> Open Capture Device
open PVR tab and change Frequency from -1 to "whatever" (in my case 855250 - has to be in kHz)
7.  Select Advanced Options and change Channel from -1 to 0 (tuner)
8 Click Ok...

You should now see a TV channel with sound!

p.s. I sometimes had strange vertical lines & no sound but these disappeared after a reboot.
For the last few days all has been working well & I can save to disc with no problems.

Next thing I need to work out is how to set up an automatic recording...

I hope somebody finds this useful. I am still new to all this and if you find it doesn't work for you then I may not be able to offer any further help - all I can say is that it does work!

---

### Post by MeKino on 2008-04-19
and now I can record directly to a file using (in the terminal):

vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=855250 :pvr-bitrate=-1 :pvr-caching=300 :pvr-width=-1 :pvr-height=-1 :pvr-framerate=-1 :pvr-keyint=-1 :pvr-bframes=-1 :pvr-bitrate-peak=-1 :pvr-bitrate-mode=0 :pvr-audio-bitmask=-1 :pvr-audio-volume=-1 :pvr-channel=0 --sout file/mpeg1:///home/username/vlcmovie.mpg

which I saved as a shell script vlcrecord. 

I can record anytime using a crontab, eg:

# m h  dom mon dow   command
# start recording tv
10 14 19 4 6 export DISPLAY=:0 && /usr/bin/vlcrecord

# stop recording 30 minutes later
40 14 9 4 6 killall vlc

which is pretty much everything I wanted to accomplish (goodbye M$)!!

---

### Post by MikeCheck on 2008-05-16
If you don't have a cable box, do you have to change the frequency each time you want to change the channel?

---

### Post by MeKino on 2008-05-17
There is a utility called something like MonkeyRemote (you may have to Google it) which might do.

Alternatively, it should be possible to write a script which could run from the terminal but as it's something I don't need I've not tried to do. There are probably others on the forum who know more about vlc.

---

### Post by Porpoise on 2008-07-06
Just to add a further dimension to this thread, it's also possible to change inputs and TV channels using v4l2-ctl:

To select inputs:
```

v4l2-ctl --set-input=0    #for Tuner 1
v4l2-ctl --set-input=1    #S-Video 1
v4l2-ctl --set-input=2    #Composite 1
v4l2-ctl --set-input=3    #S-Video 2
v4l2-ctl --set-input=4    #Composite 2

```If using the Tuner as input, then to select channels:
```

v4l2-ctl -f 711.250    #Frequency: 11380 (711.250000 MHz) (BBC 1)
v4l2-ctl -f 655.250    #Frequency: 10484 (655.250000 MHz) (BBC 2)
v4l2-ctl -f 631.250    #Frequency: 10100 (631.250000 MHz) (ITV 1)
v4l2-ctl -f 679.250    #Frequency: 10868 (679.250000 MHz) (CHA 4)

```Then, to record with VLC (this command also enables viewing the stream whilst recording):
```

 vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'

```

Hope this might help others trying to record and view using VLC with this card.

There is also a utility called TV-Viewer which offers a GUI for changing channels.

---

