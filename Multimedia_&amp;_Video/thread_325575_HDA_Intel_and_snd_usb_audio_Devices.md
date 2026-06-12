---
title: "HDA Intel and snd_usb_audio Devices"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by kylevan on 2006-12-26
Well, I received a Silverstone EB-01 for Christmahaunnakwanzaka.  I've managed to get things working in a satisfactory-ish fashion on my Edgy/GNOME install - see the end of the post for more info.  Things are co-existing pretty well with the onboard HDA/ICH6 Intel sound on my laptop.  The Silverstone uses a Texas Instruments/Burr Brown PCM2702 DAC chip, and was detected fine according to "lsusb", although it seems that one needs to boot with the device attached to get the appropriate modules loaded - hotplugging wasn't so "hot" so-to-speak.

I have added the following into my ~/.asoundrc

```
        pcm.hda-intel {
                type hw
                card 0
        }
        ctl.hda-intel {
                type hw
                card 0
        }

        pcm.usb-audio {
           type hw
           card 1
        }

        ctl.usb-audio {
           type hw
           card 1
        }

```

From further reading, this may have been totally unnecessary for use with your music players, but it is good if you wish to use "aplay" to test that each device is working properly using an easy-to-remember alias instead of "hw:0,0" etc.  I used [this wave file]("http://members.cox.net/artludwig/WavProc/overhere.wav") to test each.

```
aplay -D usb-audio overhere.wav
```
```
aplay -D hda-intel overhere.wav
```

This showed that each device was capable of playing sound through ALSA, it was just a matter of convincing other software that this was so. ](*,) 

So far I have had to disable ESD in System>Preferences>Sound.  Also, in the same dialog, I have set all devices to ALSA.  In addition, in System>Preferences>Multimedia Systems Selector (which I think you need to add from a default install through the Menu Layout preferences,) I have Selected ALSA for the Audio Output

Currently, the behaviour is basically that I select the DAC as the default sound device in System>Preferences>Sound, and then start up Rhythmbox and start it playing.  Then, if you're browsing the web or something and want to play something, it will play through the onboard sound.

Obviously this is not ideal, but I could not find a way to get the USB soundcard to basically shut the Intel sound down when it is present.  If anyone has found a solution, do post it up.

Anyway, I need to get some RCA interconnects to pipe this thing through an amp, but just plugging my Grado SR-80s into the supplied RCA-mini adapter, the sound is (subjectively) **much** better than onboard.

---

