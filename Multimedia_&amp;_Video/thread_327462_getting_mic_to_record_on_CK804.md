---
title: "getting mic to record on CK804"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by roderikk on 2006-12-29
Hi!

I've never really been interested in skype or anything but now I find myself with a headset on my ears and a microphone in front of my mouth... However, I cannot get the mic to record a sound. I get the following output from several commands:

```
roderik@edgy:/dev/snd$ cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio capture
  5: [ 1]   : control
  6: [ 0- 2]: digital audio playback
  7: [ 0- 1]: digital audio capture
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0]   : control


roderik@edgy:/dev/snd$ cat /proc/asound/pcm
01-00: USB Audio : USB Audio : capture 1
00-02: Intel ICH - IEC958 : NVidia CK804 - IEC958 : playback 1
00-01: Intel ICH - MIC ADC : NVidia CK804 - MIC ADC : capture 1
00-00: Intel ICH : NVidia CK804 : playback 1 : capture 1


roderik@edgy:/dev/snd$ cat /proc/asound/oss/devices 
  0: [0- 0]: mixer
  1:       : sequencer
  3: [0- 0]: digital audio
  4: [0- 0]: digital audio
  8:       : sequencer
 12: [0- 1]: digital audio
 16: [1- 0]: mixer
 19: [1- 0]: digital audio
 20: [1- 0]: digital audio
```

But I have no idea what to set in 'gstreamer-properties' as my pipeline. Anyone have any idea? BTW, I have no idea where the USB sound in the pcm listing comes from...

I've also been thinking in buying a usb headset, would that actually work better?

Thanks for the help!

Roderik

---

### Post by willskills on 2006-12-29
I'm having similar issues, and no one has been able to shed much light on the siuation. I grabbed a Plantronics USB headset, and I can't get that to record either......

---

### Post by roderikk on 2006-12-29
But isn't there anyone who uses skype or similar programs to talk on ubuntu? I there no list of usb devices that work (nearly) out of the box?

EDIT: Hm, it seems I was a bit too quick with posting this... as I apparently have a microphone on my logitech usb quickcam messenger which just works with skype (didn't even know this...! :-) ). (I just went into skype -> tools -> sound devices and it appears there, great!)

I can't get it to record regular stuff with the audio recorder but I am not really interested in that anyway. Thanks for the help.

---

### Post by Circlingthesun on 2007-08-29
I had the same problem. Try  opening gnome volume control. Go to Edit --> Preferences end make sure "Surround Jack Mode" is ticked. Now there should be a Surround Jack Mode drop down selector under the options  tab (with my version). Make sure you have Independent selected. For some reason the Shared option is disables the mic jack.

The mic jack at the front of my box still worked under shared mode.

Hope this helps if ure still bothered.

---

### Post by Gremlinzzz on 2007-08-29
The post was made in  Last edited by roderikk : December 29th, 2006 at 10:01 AM.
hope he solve the problem by now
:lolflag:

---

### Post by roderikk on 2007-08-30
Actually, I never did manage to solve the problem. But I will be sure to try it out as soon as I get home to test it.

Circlingthesun: Thanks!

---

