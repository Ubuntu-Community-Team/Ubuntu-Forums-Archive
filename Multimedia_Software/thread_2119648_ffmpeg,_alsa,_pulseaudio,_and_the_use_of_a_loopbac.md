---
title: "ffmpeg, alsa, pulseaudio, and the use of a loopback device"
date: 2013-02-24
forum: Multimedia Software
---

### Post by kevdog on 2013-02-24
I'm at the point I'm just frustrated

Goal: Screencasting with the use of ffmpeg for capture and combining audio sources of the built-in microphone and the actual sound from the soundcard

What I have working so far is that I can screencast with ffmpeg which records the desktop video and audio from the built-in mic (laptop).  what I'd like to do is also add the pcm sound produced via the soundcard.

I've got both pulseaudio and alsa, and I've read up on the use of loopback devices, but this is the point I get really confused.  Do I create an alsa loop back device via use of snd_aloop, or a pulse audio loop device.  Once the loop back device is configured, how do I redirect the input from the microphone and the output from the screen back to the looback devices input -- or can I?  ffmpeg screen caputure works on the command line and pavucontrol doesn't see when its actually running and recording input.  

Any input would be helpful.

---

### Post by kevdog on 2013-02-25
Ok -- although no one is chiming in with any answers, I'll try to be as informative as I can.

Just some background for people that don't know.  In Ubuntu and most systems, there are usually by default 2 sound servers or utilities that manage your audio -- ALSA and Pulse Audio.  ALSA does the much lower level functions, Pulse Audio sits on top of ALSA and does much more of the high level stuff.  Guides out on the internet, usually either address ALSA or Pulse.  Don't get the two confused, they are not interchangeable.

With each sound device, there is usually an input channel, and an output channel. ffmpeg and RecordMyDesktop and other similar utilities by default record from the input channel of the selected device.  The reason by default, the audio is recorded by default using these utilities, is because the sound is being output on the output channel, and not the input channel.  A loopback device is a virtual method of creating a system sound card that takes as input the output of a different card.  The output of one sound card becomes the input for the virtual sound card.

It's possible to create a virtual sound card using either ALSA or PulseAudio.  In found working with PulseAudio to be much easier than with ALSA.  For those interested in creating a loopback virtual card with ALSA, I found this post to be very informative: [https://bbs.archlinux.org/viewtopic.php?pid=765075](https://bbs.archlinux.org/viewtopic.php?pid=765075)  The only problem with this post is that I could only get the aplay and arecord utilities to make use of the loop back device.  Although the virtual loopback devices were shown within alsa, I couldn't get ffmpeg to actually record anything through the loopback device.  I'm sure there is probably a method to make the ALSA loopback card work, however I eventually gave up after about 2 days worth of trying.

Just some useful utilities:
aplay -l --> This lists the available sound cards on the system as detected through ALSA.  
Example:
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
These same devices should also show using the alsamixer utility and then pushing F6 where the sound cards are displayed. Usually the default card (as in the example above) is listed as card 0, and subsequently the other devices are listed as card 1, card 2, etc.  Card 0 is considered the default card.  It's possible to reorder the cards however.  Using udev, a file can be created within /etc/modprobe.d.  You can name the file whatever your want, however here is an example (I named the file alsa-base.conf)
```

more /etc/modprobe.d/alsa-base.conf 
#specifying order of Sound Card at Bood

#options snd slots=snd_hda_intel,snd_hda_codec_hdmi,snd_aloop
#options snd_hda_intel index=0
#options snd_hda_codec_hdmi=1
#options snd_aloop=2


```
I would uncomment out the lines if I wanted to reorder the devices.  You can see however from the example above, the snd_aloop device driver is referenced --> this is the ALSA virtual loopback device.  The alsa loopback device can be loaded manually via:
```

sudo modprobe snd_aloop

```
or if using udev, creating a file within the /etc/modules-load.d directory and listing the driver.  Here is another example:
```

more /etc/modules-load.d/alsa-loop-device.conf 
#Load alsa loop back driver at boot
#snd_aloop

```

After the ALSA virtual sound card is created, a ~/.asoundrc (user basis) wound need to be created or modification of the /etc/asound.conf (system wide) file would need to be performed that would specify the input for this loopback device.  I would direct the user to the Arch Wiki link given above for an example of how to do this.  There are multiple examples on the internet, however I would ensure one ensure verification of the correct hardware identifiers in each example (Card Numbers as listed by aplay -l).

If using ffmpeg, the input sound device can either be referenced using the actual card input stream or using pulse audio.  Here is examples of both methods:
```

Direct access using hardware:
ffmpeg -f alsa -ac 2 -i hw:0,0 -acodec libmp3lame -ab 128k ~/Videos/outpulse.mp3

Access via pulse audio:
ffmpeg -f alsa -ac 2 -i pulse -acodec libmp3lame -ab 128k ~/Videos/outpulse.mp3


```

Pulse Audio
A virtual pulse audio loopback device is created via:
```
pactl load-module module-loopback
```

or via by adding this module to the /etc/pulse/default.pa file.  I'm uncertain whether this module additionally needs to be added to the /etc/pulse/system.pa file.  If in doubt, it could additionally be specified in this file as well.

pavucontrol is the GUI utility used to control the various input, output and recording devices.  I would suggest you take a look around at the GUI to familiarize yourself with the various tabs.  After the pulse virtual device driver is loaded is possible to loop the virtual sound card input to the output of an existing sound card. If wanting to add multiple sources of input (ie a microphone and the system sound), you would need to create two virtual pulse audio loopback devices, and then link each card to a corresponding input.  Ensure Under the Recording tab, you choose Show: All Streams from the DropDown combination box.  You could then choose the output stream you would like to serve as input.  Listed in this dropdown box are usually sound cards with also monitors of the sound cards.  I'm uncertain what the Monitor choice refers to.   

Please note that volumes of the various microphones may need to be adjusted from either in alsamixer or within pavucontrol.  This is important if you would like to use the microphone as an input device being that this device is often either muted or the volume turned way down.  

Hopefully this small writeup is helpful to anyone trying to do similar things such as using ffmpeg for screencasting.

---

### Post by VirusCollector on 2013-06-18
This post is beautiful and you are beautiful. This fixes all of my wretched problems. Thank you.

Edit: Okay well not all of them. But it's the best lead I've had yet.

---

