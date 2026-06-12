---
title: "Mplayer not working with ATI HDMI"
date: 2009-01-06
forum: Multimedia Software
---

### Post by Numenor on 2009-01-06
Wonder if any of you fine peeps can help me out here; I've got most of the way myself but now Mplayer has me stumped.  The background is this:

I have a self-built PC with a Powercolor HD4870 card, and after running Vista for a couple of months I finally got around to installing Ubuntu 8.10.  Initially I could not get a peep of audio out over HDMI, but found a really useful tutorial that someone had taken the time to type up and can now get sound in X (and apps such as Totem).

Mplayer, on the other hand, is ignoring the existence of the HDMI audio device.  I've loaded it up via the GUI and set the audio output to ALSA, then told found that in the device dropdown my card wasn't listed (output from aplay -l shows it as card 0, device 3). In Mplayer I am only given the options of hw=0.0, hw=0.1 and hw=0.2, none of which work (obviously, since they're wrong).

So I overtyped it, forcing it to concede that hw=0.3 existed.  Rather clever, I thought, until I started playback of a video file.  I got the sound I was after, albeit delayed by a second, but unfortunately I also got numerous occurrences of this error message popping up every second:

[AO_ALSA] Unable to find simple control 'Master',0.

thus making the file unwatchable.  

I'm inclined to think this is Mplayer being awkward, but could simply be caused by an underlying driver issue.  Looking in Ubuntu's Sound Preferences, under Default Mixer Tracks, there are no tracks listed at all.  No Master, no PCM, nothing.

Any help anyone can give me will be much appreciated.

---

### Post by markbuntu on 2009-01-06
The only thing you can select for hdmi output is IEC958 which is to turn on or off the digital output. 
Try this, Open the panel volume control and choose file/change device and choose the ati (hdmi) device then go to edit/preferences and select IEC958 which is the only thing there. There will now be a IEC958 switch in the volume control, select it. Restart mplayer and check if mplayer can now see the hdmi. You may need to select as3 passthrough in mplayer to get this to work.

---

### Post by Numenor on 2009-01-07
Thanks for your suggestions.

I've already selected the IEC958 box in the volume control preferences - before I did that I couldn't get any sound from anything at all.  Afterward, I can get sound through the Sound Preferences test buttons, and various applications.

I'll try the as3 passthrough, as you suggest.  But how do I do that? Is it a setting in /etc/mplayer/mplayer.conf or can it be done through the GUI?

By the way, just for further information, I downloaded VLC after I posted last night, and tested that.  It detected ALSA device 0.3 easily, and the audio is working fine.  I'd still prefer to use Mplayer though, so I do still want to pursue this.

---

### Post by markbuntu on 2009-01-07
The ac3 passthrough option is int eh mplayer preferences menus somewhere. There was a problem with mplayer not letting go of the ac3 passthrough after it is closed. I am not sure if any update has fixed that problem in the version in the repository but it has been fixed.

---

### Post by Numenor on 2009-01-07
Thanks!!  It seems to be working fine now.

Now all I have to do is configure libass... but that's no problem, I've done it on my other computer so I can just copy the settings from that.

Many thanks for your help.

---

