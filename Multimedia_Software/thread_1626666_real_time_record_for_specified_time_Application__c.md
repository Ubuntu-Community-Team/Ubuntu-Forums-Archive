---
title: "real time record for specified time Application / command line?"
date: 2010-11-20
forum: Multimedia Software
---

### Post by IanVaughan on 2010-11-20
Hi, I wish to record in real time, into ogg or mp3.
I want to specify I time to record for, say 2 hours.

Does anyone have suggestions for both :-
1/ Application?
2/ Command Line?

Many thanks, Ian

---

### Post by tgalati4 on 2010-11-20
sudo apt-get install sox
man rec

rec -c 2 my_two_hour_recording.ogg trim 0 7200

man at

at 3pm rec -c 2 my_two_hour_recording.ogg trim 0 7200

If this is to occur weekly, then use cron:

man crontab

---

### Post by IanVaughan on 2010-11-20
> **tgalati4 said:**
> man rec

rec -c 2 my_two_hour_recording.ogg trim 0 7200

Kudos++, many thanks.

I did a 10sec test (could hear radio steam)... played back... blank....

```

# rec -c 2 test.ogg trim 0 10
Input File     : 'default' (alsa)
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Sample Encoding: 16-bit Signed Integer PCM

In:0.00% 00:00:10.07 [00:00:00.00] Out:480k  [      |      ]        Clip:0
```

```
$ play test.ogg 

test.ogg:

 File Size: 5.02k     Bit Rate: 4.01k
  Encoding: Vorbis        Info: Processed by SoX
  Channels: 2 @ 16-bit   
Samplerate: 48000Hz      
Replaygain: off         
  Duration: 00:00:10.00  

In:100%  00:00:10.00 [00:00:00.00] Out:480k  [      |      ]        Clip:0    
Done.
```

```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 44
```

Tested Ubuntu test, worked ok :- 
```

$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```

```

$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Any ideas??
ogg problem?
I can hear other ogg files, (/usr/share/gnome-games/sounds)

---

### Post by tgalati4 on 2010-11-20
In a terminal:

gstreamer-properties

Change the default input to ALSA.  I don't think sox works with pulseaudio.

---

### Post by IanVaughan on 2010-11-20
> **tgalati4 said:**
> In a terminal:

gstreamer-properties

Change the default input to ALSA.  I don't think sox works with pulseaudio.

Ok, I changed :-
Default Input :-
  Plugin = Custom
  Device = None, (unselectable)
  Pipeline = "autoaudiosrc"

Changed to :-
  Plugin "ALSA"
  Device : Default (options are : "ALC1200 Digital" / "ALC1200 Analog")

Still the same, cant hear any output on playback!

(many thanks so far...!)

---

### Post by tgalati4 on 2010-11-20
apt-cache search alsamixer

Install any/all of those tools.

Turn up the gain/unmute the capture and mic channels.

---

### Post by IanVaughan on 2010-11-21
> **tgalati4 said:**
> apt-cache search alsamixer

Install any/all of those tools.

Turn up the gain/unmute the capture and mic channels.

```
$ apt-cache search alsamixer
alsamixergui - graphical soundcard mixer for ALSA soundcard driver
gmerlin - a multiformat media player
gnome-alsamixer - ALSA sound mixer for GNOME
alsa-utils - Utilities for configuring and using ALSA
```

alsamixergui - basic gui, and "Capture" bars where locked down near bottom.
gnome-alsamixer - nice gui.
alsa-utils - already had, is a nice gui as well.

Found that in playing with one of the other gui's, that the "Capture" bars in alsamixergui showed full.

But still nothing recorded! (I am using Audacity to record, as I can see the recording levels.)

I find the tons of settings, via many gui's, most confusing!


Gnome ALSA Mixer :-
PCM, 2xFront Mic, LFE, Mic Boos, Beep, 2x Capture (with "Rec" checkboxes) !
Then the list of names for some unknown selection!
Headphone, IEC958, IEC958 Default PCM, Channel Mode, Input Source, Input Source!!!???

Sound Preferences (Ubuntu default I think) is much more normal.
Input Tab : Connector selection : Line in, Mic 1, Mic 2.


It seems I can record "Mic" inputs, but not record "what I hear"!?
Do I have to cable a loop back from an output to a line in? How sad! Windows XP does this for me out of the box!

---

### Post by IanVaughan on 2010-11-21
Some more research has dug up :-
Understanding Sound Cards I think is well explained in  [this Thread (Karmic 9.10 Sound Control)]("http://ubuntuforums.org/showthread.php?p=8043003").

And my problem as diverted a bit from the original post/title!
Other posts cover my problem better maybe :-
1/ [Record streaming radio ??]("http://ubuntuforums.org/showthread.php?t=1622966")
2/ ["Record what you hear" with no "wave" or "mix" setting in Alsamixer]("http://ubuntuforums.org/showthread.php?t=827052")
3/ [How to record all audio output from sound card in Ubuntu 9.10 Karmic Koala]("http://ubuntuforums.org/showthread.php?t=1330728")

Athough I have not yet read through or got anything working yet, I might end this thread as Solved, and move over to an other/new thread...

Many thanks tgalati4

recordmydesktop

---

### Post by IanVaughan on 2010-11-21
I think the installing and/or the use of a/some settings of; PalseAudio solved the problem!

Rerun the rec, and now see that it too has Level bars, of which move.
Played back, and it had recorded it.
Albeit with lots of high-pitched interference! Think I've messed too much with levels, but that should just be a matter of going though the levels!

Many thanks again...

---

### Post by tgalati4 on 2010-11-22
The high-pitched squeal is probably feedback from the on-board microphone picking up the speaker sound.  You can turn down, or turn off the monitoring, as it is not needed for this type of recording.

ALSA is a bit of a mess.  Pulseaudio is supposed to make things easier, but then it hides some of the switches needed to get your hardware to work.  Once you get it figured out, take notes of the settings.  All it takes is one setting messed up and your 2-hour recording is garbage.

As long as you see sound levels changing on the command line using rec or the microphone monitor in audacity moving around the 70% level, then your recording should be good.

You can do some crazy stuff with sox:

[http://ubuntuforums.org/showthread.php?t=1576554&highlight=sox+rec](http://ubuntuforums.org/showthread.php?t=1576554&highlight=sox+rec)

---

