---
title: "Microphone issues with Logitech QuickCam Pro 9000 under Jaunty"
date: 2009-09-19
forum: Multimedia Software
---

### Post by glickboy on 2009-09-19
Hey everyone, I have tried googling this issue for hours and searching the forums, and the irc channels with to no avail.  I'm hoping someone here can help me...

I cant seem to get my Logitech QuickCam Pro 9000 microphone working.  I bought this because I heard that it worked great with Linux.
When I open up Volume Control in gnome, it shows up as muted, and when I click to un-mute it, as soon as I close the window or change to a different device and change back, it is muted again.  When i try to open the device in Audacity it says that it is unable to open the device.  And why i try to record a sound using gnome sound-recorder I get nothing but silence.  I tried Alsa-mixer to no avail.  I am truly stuck at this point. If anyone could help me resolve this issue, I would be most grateful.   

Sincerely

---

### Post by Andrews222 on 2009-10-24
And I thought it was just me (I am pretty new to Linux).
I am experiencing exactly the same issue.
After much research, I think I understand that every audio capability is "routed through" this "PulseAudio Server" and perhaps that's why Audacity can't open the input device (microphone)?!?  it appears to want to use ALSA, effectively going around the PA server?

In any case, can't get the mic to function in ANY application - much less Skype - which is my intention.

The device is recognized on the USB and the video works.  Just can't seem to get audio from the microphone.  I have no idea what else to try and I'm hoping someone will respond.

Thanks.

---

### Post by Andrews222 on 2009-10-24
Wow,

How could I have missed this ABSOLUTELY TERRIFIC guide.
[Jaunty 9.04 Sound Solutions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1130384") 

Solved everything!

---

### Post by Andrews222 on 2009-10-25
Doh!

Started celebrating too early.  While the guide was extremely helpful, and got the sound "system" set up quite well.  Both Skype (Beta) and Audacity are recording, and playing back, nothing but static.  Sound Recorder is working perfectly AND the volume control w/n the PulseAudio system displays the input from my USB mic(Logitech Pro 9000) perfectly.

SO, it seems that Skype and Audacity are listening to the wrong thing (stream?!?).

I'm planning on uninstalling Skype and re-installing to see if (magically) the thing will work - kind of like the ole' Windows days.

Any thoughts are appreciated.

---

### Post by Robbyx on 2009-12-23
Is the sound working from the mic working for you? I have just bought it and there is no sound, but there is a picture.

---

### Post by Xnyper on 2010-05-12
Just in case anybody is wondering, My QuickCam Pro 9000 works for audio and video without setup in Lucid.  Skype only found one device (pulseaudio) but when I went into sound settings and selected the camera as input mechanism of choice everything ran well.

---

