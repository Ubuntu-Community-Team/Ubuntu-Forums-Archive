---
title: "Recording with arecord -need help"
date: 2010-12-26
forum: Multimedia Software
---

### Post by arvindp3 on 2010-12-26
I am trying to record audio using arecord but have succeeded so far only in getting a wav file with very very feeble sound.  My system plays audio and video well.  Just the recording is not working properly.   I guess some tuning of ALSA parameter may be needed.  Can anyone help with suggestions?

Ubuntu 9.10

Advanced Linux Sound Architecture Driver Version 1.0.20.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Elitegroup Computer Systems Device 2633
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fea38000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfea38000 irq 16

I have used alsamixer to open muted channels.

It is a dual boot system. On Windows, Audacity records perfectly, so I suppose the audio card/controller is capable of recording.  On Ubuntu, Audacity, Sound recorder and arecord all have problems -- I haven't been able to record very well on Ubuntu.

I am not sure whether ALSA and Pulseaudio both are supposed to be installed.  At least I see both of them in menu.  Often I have suspected some kind of intereference between these two.

Have tried various arecord parameters.  

I found this excellent tip and followed it but still haven't succeeded in getting more than a feeble sound output.
[http://carthick.wordpress.com/2007/11/26/linux-recording-soundcard-output-using-arecord/](http://carthick.wordpress.com/2007/11/26/linux-recording-soundcard-output-using-arecord/)

Any experience or help with arecord is appreciated.

Thanks

---

### Post by Jose Catre-Vandis on 2011-01-26
I am in the same boat as you, it records but very very low volume. I don't get a Capture Source back from amixer, just Capture Switch and Capture volume, so can't see where to change the source from Mic to Mix. :(

---

### Post by lidex on 2011-01-27
So your basic problem is the mic level. Look at the screen below.
This is gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```
Note the 'mic boost' element

---

### Post by Jose Catre-Vandis on 2011-01-29
Thanks Lidex, but not trying to record from mic, that works fine, trying to record sound output from the PC. All advice is to change the capture source to Mix, but I don't have a Mix in my list of sources (also not using PulseAudio, so no Monitor option)

```
~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
~$ arecord -L
null
    Discard all samples (playback) or generate zero samples (capture)
default
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Hardware device with all software conversions
```

~/.asoundrc
```
pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm "dmix:NVidia"
        capture.pcm "dsnoop:NVidia"
    }
}
```

```
~$ amixer contents
numid=16,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=15,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=64,step=0
  : values=61
  | dBscale-min=-64.00dB,step=1.00dB,mute=0
numid=4,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=3,iface=MIXER,name='Headphone Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=64,step=0
  : values=56,56
  | dBscale-min=-64.00dB,step=1.00dB,mute=0
numid=21,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=213,213
  | dBscale-min=-51.00dB,step=0.20dB,mute=0
numid=2,iface=MIXER,name='Front Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=1,iface=MIXER,name='Front Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=64,step=0
  : values=61,61
  | dBscale-min=-64.00dB,step=1.00dB,mute=0
numid=7,iface=MIXER,name='Mic Boost'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=3,step=0
  : values=1,1
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=6,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=5,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=28,28
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=8,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=9,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=23,23
  | dBscale-min=-13.50dB,step=1.50dB,mute=0
numid=14,iface=MIXER,name='IEC958 Default PCM Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=10,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x00]
numid=17,iface=MIXER,name='IEC958 Playback Con Mask',index=1
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x00]
numid=11,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0x00 AES2=0x00 AES3=0x00]
numid=18,iface=MIXER,name='IEC958 Playback Pro Mask',index=1
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0x00 AES2=0x00 AES3=0x00]
numid=12,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x00 AES2=0x00 AES3=0x00]
numid=19,iface=MIXER,name='IEC958 Playback Default',index=1
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x00 AES2=0x00 AES3=0x00]
numid=13,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=20,iface=MIXER,name='IEC958 Playback Switch',index=1
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
```

---

### Post by Jose Catre-Vandis on 2011-01-29
Well I have been scouring the interweb all day on this, and finally found a workaround, [http://www.swview.org/node/213](http://www.swview.org/node/213) which uses a clever (and kudos to the author!) custom .asoundrc to write the sound out to a file. Only problem with this is that it will do it to all sounds played, so you have to swap .asoundrc files everytime you want to record? Not tried it yet, but would be good if there was a switch, say in the mixer for it?

[EDIT] Tested this out and it does just work, but is a bit flaky. can only use aplay to play sounds, vlc / audacious won't work. More testing.

Also found this page which certainly helps, but I can't get it to work!

[http://wiki.audacityteam.org/index.php?title=Recording_audio_playing_on_the_computer](http://wiki.audacityteam.org/index.php?title=Recording_audio_playing_on_the_computer)

and this is a great page about alsa

[http://www.sabi.co.uk/Notes/linuxSoundALSA.html](http://www.sabi.co.uk/Notes/linuxSoundALSA.html)

---

### Post by lidex on 2011-01-29
What is the make/model of this computer?

---

### Post by Jose Catre-Vandis on 2011-01-29
> **lidex said:**
> What is the make/model of this computer?

For me, it's an Asus EB1012 "Nettop" PC

Alsa-Info Script output here:

[http://www.alsa-project.org/db/?f=ea68ec059bb7f61488a8f1f4d9963d2239009edd](http://www.alsa-project.org/db/?f=ea68ec059bb7f61488a8f1f4d9963d2239009edd)

---

### Post by lidex on 2011-01-29
> **Jose Catre-Vandis said:**
> For me, it's an Asus EB1012 "Nettop" PC

Alsa-Info Script output here:

[http://www.alsa-project.org/db/?f=ea68ec059bb7f61488a8f1f4d9963d2239009edd](http://www.alsa-project.org/db/?f=ea68ec059bb7f61488a8f1f4d9963d2239009edd)

Try this in a Terminal:
```
echo "options snd-hda-intel model=asus-mode3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Jose Catre-Vandis on 2011-01-29
No, sorry been there, tried asus-mode1 - mode6, and every option listed under ALC662 in the database, still no capture options (unless of course, I guess I revert to pulse audio) but this should be available in the hardware, no?

Currently running along on model=auto, also not having an option gives the same thing.

I also tried the physical option of plumbing the headphone socket to the mic socket, but I got some nasty clicking from the speakers, so dropped that as an idea.

---

### Post by lidex on 2011-01-29
What about this control:
```
Simple mixer control 'Pre-Amp',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 9
  Front Left: 0 [0%]
  Front Right: 0 [0%]
```

---

### Post by Jose Catre-Vandis on 2011-01-29
I added the pre-amp in because output sound levels were a bit low, compared to previous PCs (using the same speakers) but it doesn't make any difference. i put the changes into .asoundrc, and have since removed the entries, however the pre-amp persists in the mixer settings ?


This page more or less gives an answer using jack.

[http://sysphere.org/~anrxc/j/archives/2009/04/19/recording_sound_from_alsa_with_jack/index.html](http://sysphere.org/~anrxc/j/archives/2009/04/19/recording_sound_from_alsa_with_jack/index.html)

Was able to record audacious mp3 playback using Audacity and arecord, but its hellish fiddly.

---

### Post by Jose Catre-Vandis on 2011-02-06
I thought I had better come back and update on this one (real world issues taken hold over the last two weeks)

Have been unable to compile and install alsa with the snd_aloop module, (and severely buggered my sound setup in the process!) which I believe is what is required in order to capture sounds coming through from the web. I may try again on a clean system.

Only been able to capture sounds using jack when jack output is enabled within the playing application. The .asoundrc settings crap out or the application refuses to play if left as alsa playback. That said, jack_capture is a neat little command line tool.

When natty comes around, I may leave pulse-audio in place, and then use pulse to capture all my onboard sounds.

---

### Post by super1285 on 2011-10-04
That's odd, I'm running Ubuntu 11.04 and am having problems recording ANYTHING. I tried "lidex's" code above in hopes of finding my input capabilities but it resulted in me recording PC audio!  I'm running Audacity with a copy of a cd track and tried to record over top of it but it just ended up recording the original cd track.  
Thought this might be of some help.

---

