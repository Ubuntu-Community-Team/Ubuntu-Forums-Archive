---
title: "Laptop: no sound in speakers, but have sound in headphones"
date: 2013-07-11
forum: Multimedia Software
---

### Post by HousieMousie2 on 2013-07-11
Just did a clean install of 13.04 - complete hard drive reformat.  Fully updated.

Headphones work, speakers don't.

Interesting point:  If I boot with heaphones plugged in and unplug them **during** the start-up chimes/tones, the speakers will play the start-up chimes/tones, but nothing else after that, so it is not hardware failure.

Nothing is muted in alsamixer, or Kmix.  Master Channel, in Kmix is Built-in Audio Analog Sterio.

The short version:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
```
cat /proc/asound/card0/codec#* | grep Codec 
Codec: Conexant CX20585

```
```
lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```
```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k3.8.0-26-generic.

```
```
cat /proc/asound/devices
  1:        : sequencer
  2: [ 0- 0]: digital audio playback
  3: [ 0- 0]: digital audio capture
  4: [ 0- 0]: hardware dependent
  5: [ 0]   : control
 33:        : timer

```

The long version:
[http://www.alsa-project.org/db/?f=25bc76456e827660a46895b2d174e6801c1d289e]("http://www.alsa-project.org/db/?f=25bc76456e827660a46895b2d174e6801c1d289e")

Restarting alsa has no effect.

I am puzzled since sound worked fine in 12.04 (Ubuntu and Kubuntu) when they were first installed and for some time after that.  (This is not my machine, I was not informed when the audio stopped working, so I cannot say at what point it stopped working in 12.04.)

Also wondering if there should be a Digital as well as the Analog... only seeing Analog.

Thank you for any and all help.

---

### Post by SeijiSensei on 2013-07-11
Take a look in System Settings > Multimedia > Phonon > Audio Hardware Setup and see what options you have for the Connector.  I have a laptop plugged into a audio receiver using a mini-phono to RCA plug cable.  Each time I reboot I have to reset the Connector to "Speakers" to get it to use the phono jack.  It defaults to "Analog Output" each time I boot; I haven't been able to find how to make that setting permanent.  I've looked in .kde and .config/kde.org and cannot find any obvious way to fix it.

This wasn't a problem in versions before 13.04 if I recall correctly.

I would have stayed with 12.04 if it had supported MTP so I could connect my Android phone.

---

### Post by HousieMousie2 on 2013-07-11
Thank you for the reply.  Unfortunately there is only one option under Connector and that is Analog Output.

I still wonder why there is not a Digital entry in any of the audio GUIs and only in certain console outputs.

Anyway, thank you again!


PS.  Ran across this earlier in my hunt for answers... have you tried?

```
pacmd set-default-sink
```

---

### Post by HousieMousie2 on 2013-07-15
Could still use some help here, if anyone has any ideas?

---

### Post by Yellow Pasque on 2013-07-15
File a bug. Apport will grab the pulseaudio info in addition to the alsa info:
```
ubuntu-bug audio
```

---

### Post by HousieMousie2 on 2013-07-15
Thank you, Temujin.  I will give that a try and report back tomorrow, when I have access to the machine again.

---

