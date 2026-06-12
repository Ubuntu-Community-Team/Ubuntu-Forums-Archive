---
title: "Can't get all programs to use USB Audio"
date: 2008-04-26
forum: Multimedia Software
---

### Post by noerrorsfound on 2008-04-26
I've set everything in *System --> Preferences --> Sound* to USB Audio, but Firefox and games such as Doom 3 and America's Army still play using my speakers instead of my USB headset.

I followed the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") and inserted:
```
options snd-usb-audio index=0
options snd-intel8x0 index=1
```
...at the end of */etc/modprobe.d/alsa-base*, but that only resulted in making the programs that use speaker sound to not be able to use sound at all. The programs that used the headset still worked.

Now I've commented those lines out so I can at least have sound in all programs, even if some of them output to the wrong audio device.

In addition to getting everything to use my headset, I would like to not have to change preferences each time I want to switch devices. How can I get it functioning how it does in Windows, where plugging in my headset will take over audio output, but unplugging it will switch back to the speakers automatically? I think that's how most users want things to work, so I'm not sure why it should even be necessary to change it in Sound Preferences each time.

---

### Post by grashdur on 2008-04-30
I have a simple workaround -- this is not so much for you, as I think you just want the USB solution, but for others with this issue: I have the same problem, as VLC media player for example won't use my USB headset. I just plug old-fashioned headphones into the audio jack and the sound is fine. (I'm using in-the-ear headphones from a Walkman). Hope this is useful to somebody.

---

### Post by brodae on 2008-04-30
I however didn't have an old pair of headphones, so I set up PulseAudio. In a minute, I'm going to post my comprehensive guide to setting up and using PulseAudio in this forum catergory, so please read it there.

---

