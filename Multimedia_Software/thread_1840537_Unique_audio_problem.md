---
title: "Unique audio problem?"
date: 2011-09-07
forum: Multimedia Software
---

### Post by ice24790 on 2011-09-07
First and formost, Hello everyone I am a brand newbie...just started using linux yesterday lol.

I am running the current build of ubuntu 11.
Well I wouldnt say unique lol this seems to be quite common.  Well lets begin:
My setup is a Gigabyte MA790XT-UD4P mobo with a Realtek ALC889A audio chip.  I have my 5.1 soundsystem hooked up via optical cable.

After a lot of fiddling and research I have it (i think) correctly detected.  

aplay -l reveals
```
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```nothing is muted in alsamixer and the weird thing is I can get sound, but only on vlc media player.  I have it set so it outputs to alsa audio output and the device name it states is HDA ATI SB: ALC998A Digital.  But everything else I try and play sound from whether it be banshee or youtube there is no sound.  Very frustrating!

---

### Post by JD8182 on 2011-09-07
> **ice24790 said:**
> First and formost, Hello everyone I am a brand newbie...just started using linux yesterday lol.

I am running the current build of ubuntu 11.
Well I wouldnt say unique lol this seems to be quite common.  Well lets begin:
My setup is a Gigabyte MA790XT-UD4P mobo with a Realtek ALC889A audio chip.  I have my 5.1 soundsystem hooked up via optical cable.

After a lot of fiddling and research I have it (i think) correctly detected.  

aplay -l reveals
```
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```nothing is muted in alsamixer and the weird thing is I can get sound, but only on vlc media player.  I have it set so it outputs to alsa audio output and the device name it states is HDA ATI SB: ALC998A Digital.  But everything else I try and play sound from whether it be banshee or youtube there is no sound.  Very frustrating!

Seems there is no set device..Open a Terminal.

Try: aplay -v -D hw:0,0,0 "or" aplay -v -D hw:0,0,1

---

### Post by ice24790 on 2011-09-07
0,0,0 leads to cursor to go down one line and just blink at me infinitely and 0,0,1 give me the error of "aplay: main:660: audio open error: Device or resource busy"...nothing is open besides terminal though.

---

### Post by JD8182 on 2011-09-08
> **ice24790 said:**
> 0,0,0 leads to cursor to go down one line and just blink at me infinitely and 0,0,1 give me the error of "aplay: main:660: audio open error: Device or resource busy"...nothing is open besides terminal though.


Try this sound issue tutorial, [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")(just copy and paste the commands into the terminal)... If you have tried this tutorial then please paste ( lsof | grep snd ) into the terminal and post the outcome..

---

### Post by .... on 2011-09-08
It seems like you have digital output connected to the speakers and analog output is the default output. Change to digital out in the volume control.

---

### Post by ice24790 on 2011-09-08
> **JD8182 said:**
> Try this sound issue tutorial, [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)(just  copy and paste the commands into the terminal)... If you have tried  this tutorial then please paste ( lsof | grep snd ) into the terminal  and post the outcome..
Gone through it and all I can say is it wont play a known good sound lol.  Here is the info.
 ```
gnome-set 1218        sam  mem       REG               8,33   409528   23069298 /usr/lib/libsndfile.so.1.0.23
 pulseaudi 1235        sam  mem       REG               8,33   409528   23069298 /usr/lib/libsndfile.so.1.0.23
 pulseaudi 1235        sam   22u      CHR              116,8      0t0       8573 /dev/snd/controlC0
 gconf-hel 1385        sam  mem       REG               8,33   409528   23069298 /usr/lib/libsndfile.so.1.0.23
 indicator 1437        sam  mem       REG               8,33   409528   23069298 /usr/lib/libsndfile.so.1.0.23
 firefox-b 2922        sam  mem       REG               8,33   409528   23069298 /usr/lib/libsndfile.so.1.0.23
 
```

> **.... said:**
> It seems like you have digital output connected to the speakers and analog output is the default output. Change to digital out in the volume control.
There is only one option in sound preferences and that is internal audio, 1 output, analog 5.1 output both in hardware and output.

---

### Post by ice24790 on 2011-09-08
One interesting note...I just plugged in my usb speakers and they showed up in sound preferences and play just fine with banshee.  It seems its something with my optical cable not being default as .... stated but that option isnt in preferences..

---

### Post by ice24790 on 2011-09-13
So no one has a real solution to this dilema?  USB speakers work when they are set in sound settings but the only other option is 5.1 internal analog...which doesnt push to optical...analog, digital, and usb appear in aplay -l and vlc uses spdif but thats the only program ive seen to utilize it....frustrating!

---

### Post by Pariah819 on 2011-09-13
Hello,

I would open a terminal and type "alsamixer", this will bring up a terminal version of the alsa mixer.  See if there is a channel all the way to the right called SPDIF.  If it is there make sure it is not muted.  I had a problem with an HTPC build I did a while back where this SPDIF channel did not show up in the GUI alsa mixer but it did show up in the command line one.  I had to unmute this channel to get my sound to work.

Good Luck!

---

### Post by ice24790 on 2011-09-14
> **Pariah819 said:**
> Hello,

I would open a terminal and type "alsamixer", this will bring up a terminal version of the alsa mixer.  See if there is a channel all the way to the right called SPDIF.  If it is there make sure it is not muted.  I had a problem with an HTPC build I did a while back where this SPDIF channel did not show up in the GUI alsa mixer but it did show up in the command line one.  I had to unmute this channel to get my sound to work.

Good Luck!
I have and nothing is muted.  There is no volume adjustment for it just an entry and an option to mute it or not.

---

