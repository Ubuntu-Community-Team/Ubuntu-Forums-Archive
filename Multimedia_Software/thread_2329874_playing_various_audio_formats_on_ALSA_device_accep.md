---
title: "playing various audio formats on ALSA device accepting only one input type (S32LE)"
date: 2016-07-05
forum: Multimedia Software
---

### Post by delooper on 2016-07-05
Greetings, 

I have an audio device that ALSA interprets as only accepting a 32-bit little-endian data format.   And I would like to play "normal" 16-bit music to that device.  To add one extra wrinkle: I am fairly certain this device is a 24-bit audio device.  It's the *miniDSP usbstreamer B *unit, and the product webpage describes it as 24-bit (with 32-bit internal processor). 

Is there a quick and effective way to convert the music on-the-fly, i.e. like when I call mplayer on the audio file?  Ideally it would be something that could be put into the /var/lib/alsa/asound.conf file.  Barring that, I want to drive this usb audio device by MPD, so if this could be done in the mpd config file, great. 

In case you are curious, here is the output of alsa-capabilities:

```

  1) USB Audio Class Digital alsa audio output interface `hw:1,0' - device name       = USBStreamer                                                 
 - interface name    = USB Audio                                                   
 - usb audio class   = 2 - isochronous asynchronous                                
 - character device  = /dev/snd/pcmC1D0p                                           
 - encoding formats  = S32_LE                                                      
 - monitor file      = /proc/asound/card1/pcm0p/sub0/hw_params                     
 - stream file       = /proc/asound/card1/stream0          

```

I will not be using Pulse for this application.  Ideally my sound server will only be running mpd + ALSA.  I'm running Ubuntu 16.04 if that helps.

---

### Post by soodvarun78 on 2016-07-06
You need to create an PCM Device of type plug... Please refer 
[http://www.alsa-project.org/main/index.php/Asoundrc](http://www.alsa-project.org/main/index.php/Asoundrc)

---

### Post by delooper on 2016-07-10
Thanks, it took me a while to figure out how to do what you suggested.  I created /etc/asound.conf:

> pcm.usbSTR {  type hw
  card USBStreamer
  device 0
}
pcm.usbREMAP {
  type plug
  slave.pcm usbSTR
  ttable.0.8 1
  ttable.1.9 1
}
pcm.!default {
  type plug
  slave.pcm usbREMAP
}
ctl.!default {
  type plug
  slave.pcm usbREMAP
}

This appears to do the job.  I did this on a lubuntu box that does not have Pulse installed, so that limits the possible weirdness that can come-about with having an /etc/asound.conf file...

---

