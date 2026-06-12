---
title: "Help with USB Audio"
date: 2008-05-09
forum: Multimedia Software
---

### Post by schitzowolf on 2008-05-09
Looking at other posts with similar problems it seems this may be a long shot, but what the heck.  I'm trying to use a Vantec NBA-100U USB Audio adapter with ubuntu 8.04.  The sound output seems to work if I set the soud options to use "USB Audio", however I cannot get the audio capture to work (which is the primary reason for using the device (my onboard input jacks are broken).  Audacity will attempt to use the device, but no audio is actually coming through.  The included "sound recorder" gives an error - "audio capture device is invalid" when I try to run it.  anybody have any suggestions??  I should also mention that this is an Acer aspire 5100 laptop.

---

### Post by Afkpuz on 2008-05-09
First off, make your usb audio your default device.

```
asoundconf list
```

Find the name of your usb card, then

```
asoundconf set-default-card cardname
```
Replace "cardname" with the exact name of your card listed above.


Then, try it again.  It might be that your comp was looking to your computers built in sound for input.  If it still doesn't work, check and see if your cards audio inputs are even detected.


Double click on the volume icon in your system tray.  Click Edit, then preferences.  Check all the unchecked boxes.

Do you have something listed that could receive audio input, like a microphone, or line in?  If not, then your card is not fully detected and you would have to start looking into drivers.

---

### Post by schitzowolf on 2008-05-09
If I set audio capture to "USB audio" in system - preferences - sound, then it looks to the USB device for input when I press "test" (the device has an led to indicate this), but no sound is played back (even with microphone enebled in "playback" for alsamixer.  

The only "recording" option listed for the device is "PCM".  The microphone is listed under playback only.  The device has both mic and line inputs (line doesn't show up anywhere for the device).

Based on what you've already said, it looks like this may be a driver issue.

*edit* after looking again, there is an option to select either "mic" or "input 1" (presumably line in) as the "PCM Capture source"

---

