---
title: "Sound problems: Live TV ok, recordings not"
date: 2008-08-24
forum: Mythbuntu
---

### Post by zeno23 on 2008-08-24
I'm running MythTV on Mythbuntu. When I go to "Watch TV" there will be a brief burst of sound from the channel it's set to, and then there will be silence. If I change the channel, the sound will return and everything will work as expected.

When I record videos, the resulting files don't seem to have sound at all.

I've got everything unmuted and at a proper level in alsamixer. I've both sound options (output device and mixer device) set to Alsa: Default. I'm using internal volume with Master Mixer Volume set to 100, PCM Mixer Volume set to 80.

Any thoughts? :confused:

---

### Post by wyliecoyoteuk on 2008-08-24
First thoughts:
what sound card, what version of Ubuntu, MythTV, alsa, etc, might help

---

### Post by zeno23 on 2008-08-24
Software is up-to-date as per the apt-get repository.

Motherboard is a Gigabyte [GA-M61PME-S2]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=2755") (rev 2.0), and I'm using integrated audio.

---

### Post by wyliecoyoteuk on 2008-08-24
What TV card?

---

### Post by zeno23 on 2008-08-24
DViCO FusionHDTV 5 RT Gold (PCI card)

---

### Post by volkswagner on 2008-08-24
Any info in /var/log/mythtv/mythfrontend.log  ?

What is the output of 

```
aplay -l
```

You may have more joy using the 

ALSA:hw:0,0

rather than Alsa:default.  You can replace the 0,0 for your "card,device" numbers found in aplay -l.

---

### Post by zeno23 on 2008-08-24
No luck with ASLA:hw:0,0.

However, here's some info from the log:```

2008-08-24 16:45:29.482 TV: Attempting to change from None to WatchingRecording
2008-08-24 16:45:29.491 Using protocol version 40
2008-08-24 16:45:29.563 DPMS Deactivated 
2008-08-24 16:45:29.581 Opening audio device 'default'. ch 2(2) sr 44100
2008-08-24 16:45:29.582 Opening ALSA audio device 'default'.
2008-08-24 16:45:29.670 Mixer unable to find control Master 1
2008-08-24 16:45:29.670 mixer unable to find control Master 1
```
"Mixer unable to find control Master 1" seems to repeat quite a bit throughout the log whenever --- I suppose --- I go to "Watch TV."

Here is the error info regarding ALSA:hw:0,0:```

2008-08-24 19:23:14.185 Opening audio device 'hw:0,0'. ch 2(2) sr 44100
2008-08-24 19:23:14.185 Opening ALSA audio device 'hw:0,0'.
ALSA lib conf.c:3843:(parse_args) Unknown parameter 1
ALSA lib conf.c:3969:(snd_config_expand) Parse arguments error: No such file or directory
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0,0
2008-08-24 19:23:14.230 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: 'hw:0,0'
```

And the output of aplay -l:```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by DemonBob on 2008-08-24
Do you have an option to set it too /dev/dsp?

I have a giga-byte motherboard and i have to set it to /dev/dsp, and the mixer device to /dev/mixer.

---

### Post by zeno23 on 2008-08-24
Thanks for the suggestion, but still no luck. Switching to /dev/mixer eliminates the "Mixer unable to..." messages in the log file, but the same sound problems persist.

Here is the frontend log when I watch a recorded video:```
2008-08-24 21:21:46.717 TV: Attempting to change from None to WatchingRecording
2008-08-24 21:21:46.721 DPMS Deactivated 
2008-08-24 21:21:46.737 Using protocol version 40
2008-08-24 21:21:46.758 Opening audio device '/dev/dsp'. ch 2(2) sr 44100
2008-08-24 21:21:46.759 Opening OSS audio device '/dev/dsp'.
2008-08-24 21:21:46.820 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-08-24 21:21:46.911 OSD Theme Dimensions W: 640 H: 480
2008-08-24 21:21:47.652 TV: Changing from None to WatchingRecording
2008-08-24 21:21:47.659 Realtime priority would require SUID as root.
2008-08-24 21:21:47.756 Video timing method: USleep with busy wait
2008-08-24 21:22:07.980 TV: Attempting to change from WatchingRecording to None
```

---

### Post by volkswagner on 2008-08-25
Using ALSA:hw:0,0 I assume you are using analog output.

You may want to create an .asoundrc text file in your /home/username folder.

put the following in it.

```
pcm.!default {
type hw
card 0
device 0
} 
```

you should still have mixer=default

---

### Post by zeno23 on 2008-08-25
Thanks --- I did what you suggest, but the problems persist without changing.

Here is a snippet from the backend log:```
2008-08-25 14:05:28.393 TVRec(2): ASK_RECORDING 2 0 0 0
2008-08-25 14:05:28.566 TVRec(2): Changing from None to RecordingOnly
2008-08-25 14:05:28.572 TVRec(2): HW Tuner: 2->2
2008-08-25 14:05:28.656 SampleRate: Attempted to add a rate 44100 Hz, which is not in the list of allowed rates.
strange error flushing buffer ... 
2008-08-25 14:05:28.728 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-08-25 14:05:28.735 Started recording: Lola, Érase una Vez: channel 1014 on cardid 2, sourceid 1
2008-08-25 14:05:28.798 MainServer::HandleAnnounce Playback
2008-08-25 14:05:28.802 adding: mythbox as a client (events: 0)
2008-08-25 14:05:28.803 MainServer::HandleAnnounce FileTransfer
2008-08-25 14:05:28.805 adding: mythbox as a remote file transfer
2008-08-25 14:05:28.807 RemoteFile::openSocket(control socket): 
			Could not connect to server "" @ port -1
2008-08-25 14:05:28.808 RemoteFile::openSocket(file data socket): 
			Could not connect to server "" @ port -1
2008-08-25 14:05:28.808 RingBuffer::RingBuffer(): Failed to open remote file ()
```

The last three entries (from RemoteFile to RingBuffer) repeat quite a bit in the log. 

(4th entry; 14:05:28.656): Would this line be related to the silent recordings?

---

### Post by zeno23 on 2008-08-26
Any other suggestions? Are there any MythTV settings that, if incorrectly configured, could cause these results? I would expect them bundled with Mythbuntu, but are there any codecs I should try downloading?

---

### Post by newlinux on 2008-08-26
do you have the dvico card setup as a V4L tuner or a DVB tuner? I haven't read through this whole thread in detail so sorry if this is already answered. If you have it setup as a v4L check your recording profile audio settings. start with your liveTV profile and get that to work and then propogate working settings to other profiles...

---

### Post by zeno23 on 2008-08-26
It's set as a V4L tuner. I've changed all the recording profiles to match the live TV profile, and that had no noticeable effect.

The problem, summed up: audio in live TV works only after I change the channel. Scheduled recordings have no sound at all. Whatever "RingBuffer" is, it might be related.

---

