---
title: "No Audio Capture - Hardy amd64 - NVidia Audio"
date: 2008-07-20
forum: Multimedia Software
---

### Post by mdsharp24 on 2008-07-20
**Specs**: Ubuntu 8.04 Hardy   **AMD64**
**Audio:**
description: 	Audio device
product: 	MCP67 High Definition Audio
vendor: 	nVidia Corporation

I seem to have NO audio capture. In the gnome volume applet I have no setting for capture. I've been unable to record any sound via gtk-recordmydesktop, istanbul, xvidcap, and audacity.

Is this related to pulseaudio maybe?  Can anyone point me to some sound configuration to check and enable capture capability for this soundcard, or give me anyone advice please?

Michael

---

### Post by cotcot on 2008-07-20
Maybe it is only not yet visualised in the applet.

---> Volume applet
---> Open Volume Control
---> Edit
---> Preferences
See if line-in and microphone are checked. 

I recently got my line-in working by thicking Input Source. That gave a new tab (Option) in the Open Volume window where you can define the capture device for the Input Source.

---

### Post by Lizardpath on 2008-08-02
Hiya, I am having the same problem.  Upgraded Gutsy to Hardy a month or so ago and still can't record any sound.  I can play sound fine and can hear my voice through the speakers when I speak into the mic.  But when I click to open "soundrecorder" I get the following error message: "Your audio capture settings are invalid. Please correct them in the Multimedia settings."

(I don't know what it means by multimedia settings).  I have also tried audacity without success, it's just a really annoying problem and I can't for the life of me think of any reason for it other than defective hardware, which I really don't want to replace haha.

Interestingly since the upgrade I can no longer access alsamixer through the terminal...

Something wrong here, any help would be very much appreciated :)

AJ

---

### Post by bluemirror on 2008-10-29
I have a similar problem - trying to use Skype. Well, any sound-in really.

I can hear sound; music playback works.

I know the mic works because i can hear it, loud and clear, if i set the mic-boost volume up loud - but it comes back out the headset, and doesn't record either in skype or voice recorder. hth do i get it to capture the sound!? it did it briefly, very quietly, from "mix"... and then refused to do it again...

Volume Control is labelled "HDA nVidia (Alsa Mixer)" and i'm not sure why it's using nVidia drivers for sound - i do have nVidia graphics running (and working mostly)

Using 32bit Hardy Heron | ALSA (removed pulseAudio)

---

### Post by markbuntu on 2008-10-29
Some sound cards will not capture if the digital output is enabled. Some use the mic output for some surround sound outputs. If you do not have the mic capture options selected in the Volume Control/Preferences, they will not show up on the mixer. If you are using pulseaudio, you need to set the capture default option in the pulseaudio volume control (pavucontrol) which does not come installed on your system but is avialable in the repos.

You also need to set the correct capture device in System/Preferences/Sound/Audio Conferencing/Sound Capture. Setting this to alsa or pulseaudio will usually work but you may have to set it to your hardware sound device.

If you have an HDA device, you may need to configure it properly:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

There is more troubleshooting and setup info about sound in Ubuntu here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

