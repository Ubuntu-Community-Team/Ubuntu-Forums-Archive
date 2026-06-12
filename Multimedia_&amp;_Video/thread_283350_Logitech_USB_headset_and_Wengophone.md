---
title: "Logitech USB headset and Wengophone"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by casperl on 2006-10-24
I run Dapper Drake.  I have a Logitech USB audio headset.  I have disabled the onboard sound in the PC BIOS.  I would like the USB headset to be the sole recording and playback device in Linux. A simple request which has led me down a rocky road toward certified insanity!

The USB headset works with standard system sounds.  Playback of sound in applications is intermittent.  Both Opera and Firefox browsers would occasionally deliver sound playback in embedded flash objects (yes, the clips do have sound!)  

My real problem is with Wengo phone.  (I gave up on Skype due to the intermittent sound availability.) Wengo phone has 3 sound devices: Input device (set to "Logitech USB Headset: USB Audio (hw:0,0), Output Device: default and Ringing Device: default.  The problem is that this default device is non-existent and delivers nothing.  > Systems > Preferences > Sound displays nothing as the default sound card.  

According to the posts below I have tried a few settings without success.  

[http://ubuntuforums.org/showthread.php?t=66865&highlight=modprobe.d%2Fsound](http://ubuntuforums.org/showthread.php?t=66865&highlight=modprobe.d%2Fsound)
[http://ubuntuforums.org/showthread.php?t=249465&highlight=modprobe.d%2Fsound](http://ubuntuforums.org/showthread.php?t=249465&highlight=modprobe.d%2Fsound)
[http://ubuntuforums.org/showthread.php?t=114551](http://ubuntuforums.org/showthread.php?t=114551)

Then I discovered this thread and set all the sound settings therein: [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

Now /etc/modules contains the line "snd-usb-audio" and /etc/modprobe.d/alsa-base contains the last line "options snd-usb-audio index=0".  These settings change nothing from the default settings.  Changing the "options snd-usb-audio index=-2" in /etc/modprobe.d/alsa-base brings up the string "Logitech USB Headphone" in all the places in WengoPhone where the Default soundcard is displayed (which would otherwise be blank), but there is the additional slight problem in that then there is no sound whatsoever!

Yes, my username is in the 'audio' group in /etc/group.

I have again restored everything to the defualt settings.  In a nutshell, the problem is that "Logitech USB Audio Headset' does not appear where applications would otherwise pick up the soundcard.  Can someone please, please enlighten me to the path to setting USB audio as the sole sound device on my system in all applications?

Presently VOIP communication over Skype or Wengo or Google Talk is as much an absolute requirement of doing business as is email.  I have been using Ubuntu now for 1 year and seven weeks, it is a great product but I have to get either Wengo (or Skype) working!

---

