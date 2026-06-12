---
title: "No input from M-Audio Fast Track Pro in Pulseaudio"
date: 2011-11-26
forum: Multimedia Software
---

### Post by wilper_ on 2011-11-26
Hi,
I searched the forum and found lots of threads regarding the Fast Track Pro USB sound interface, however no one seems to be having the same problem as I do.

**I can't record sound using Pulse audio.** But playback works fine. Also I can record just fine if I use Jack (+Ardour).

Just using Jack is not satisfactory, as I can't use e.g. Google Hangout with that.

The FTP is the only audio interface in the computer.  

If I open the sound preferences it is listed in the Hardware tab as "M-Audio Fast Track Pro   1 Output   Analog Stereo Output",  I can change the profile, but not to anything with duplex.

The Input tab lists no sound devices for input at all.

-

So, the audio input is definitely there, since it works in Jack, but it isn't picked up by Pulse audio.  I'm running Ubuntu 11.10, I haven't installed any special drivers but rely on the standard usb-audio stuff.

Any ideas?

```

wip@humlan:/proc/asound$ cat cards 
 1 [Pro            ]: USB-Audio - FastTrack Pro
                      M-Audio FastTrack Pro at usb-0000:00:1d.3-2, full speed

wip@humlan:/proc/asound$ cat devices 
  1:        : sequencer
  2: [ 1- 0]: raw midi
  3: [ 1- 1]: digital audio playback
  4: [ 1- 1]: digital audio capture
  5: [ 1- 0]: digital audio playback
  6: [ 1]   : control
 33:        : timer

wip@humlan:/proc/asound/card1$ cat pcm0p/info
card: 1
device: 0
subdevice: 0
stream: PLAYBACK
id: USB Audio
name: USB Audio
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

wip@humlan:/proc/asound/card1$ cat pcm1p/info
card: 1
device: 1
subdevice: 0
stream: PLAYBACK
id: USB Audio
name: USB Audio #1
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

wip@humlan:/proc/asound/card1$ cat pcm1c/info
card: 1
device: 1
subdevice: 0
stream: CAPTURE
id: USB Audio
name: USB Audio #1
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1


```

---

