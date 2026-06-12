---
title: "Recording audio playback and microphone"
date: 2010-01-12
forum: Multimedia Software
---

### Post by thlh on 2010-01-12
Hi everybody

I am trying to record audio playback from an application and the microphone at the same time on recordmydesktop using pulse audio. I just can't figure out how to mix them both.  I have tried a lot already and can only get either the mic or the audio playback to be recorded, not both. Can this be done using pavucontroll?

I have been search now for hours to find a solution (also here on the forum) for this and getting really frustrated now. Maybe i'm just missing something really obvious, so sorry if this is a stupid question.

---

### Post by Leo Damascus on 2010-01-12
Start by following the instructions here: 
[http://www.youtube.com/watch?v=AwKyJRPlsxw](http://www.youtube.com/watch?v=AwKyJRPlsxw)

Make sure you have VLC.  Then press ALT-F2 (or whatever you've set Run Application to) and run "vlc alsa://plughw:0,0" (without quotes).  Minimize the VLC popup, and it'll be recording the audio passed through your sound card while simultaneously passing your microphone through your sound card.

Kind of a workaround, but it should accomplish what you're trying to do.

---

### Post by thlh on 2010-01-12
thanks for the answer. i tried that, but VLC gives me errors 

```

$ vlc pulse://plughw:0,0
VLC media player 1.0.2 Goldeneye
[0x2363418] main interface error: no interface module matched "globalhotkeys,none"
[0x2363418] main interface error: no suitable interface module
[0x2226888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x2226888] main libvlc: vlc wird mit dem Standard-Interface ausgeführt. Benutzen Sie 'cvlc', um vlc ohne Interface zu verwenden.
[0x26e1d88] main access error: no access module matched "pulse"
[0x7f31a4001b78] main input error: open of `pulse://plughw:0,0' failed: no access module matched "pulse"

```also tried the same kind of trick with audacity, but that crashed when i switch on software passthrough of the recording. can't even get my mic to be played through the speakers, that used to work on jaunty. isn't there a possibility to mix two sources with pulse audio?

i want to record a skype video call, thats why i am going through all this fuss.

does anybody have any other suggestions?

---

### Post by Leo Damascus on 2010-01-12
Yeah.  VLC doesn't accept pulse for and MRL.  So instead of using the command-line prompt "vlc pulse://plughw:0,0" you would have to use "vlc alsa://pulse" to get pulse input, because VLC treats pulse as an audio-device in ALSA rather than its own architecture.  But you don't want to use pulse after following the instructions in the YouTube video, because pulse is recording straight from your soundcard.
Copy and paste the command "vlc alsa://plughw:0,0", which passes your mic through alsa, which the pulse recording in gtk-recordmydesktop will pick up.
The trick here is that your using both alsa and pulse to record from two places at once.

---

### Post by thlh on 2010-01-12
ops, my mistake, i posted the wrong lines. tried it with pulse too although i knew i would not work. it actually started working after a reboot. but now i have the problem that i only get the sound from my internal mic (laptop) and not from the headset. can i change that somewhere, alsamixer doesn't show me all the options it used to do under jaunty.

---

### Post by Leo Damascus on 2010-01-12
The YouTube video teaches you how to do that.  I linked to it because I thought it'd be easier for you to follow a video than written instructions.  But if you prefer written:
Go to the Ubuntu Software Center.  Type padevchooser into the search field.  Then install PulseAudio Device Chooser.
With that, it will install a program called PulseAudio Volume Control.  So select Applications > Sound & Video > PulseAudio Volume Control, and on the window that pops up, click the Input Devices tab.
On the bottom of the window, there will be a menu that says, "Show:  All Except Monitors."  Switch that so it says, "Show:  Monitors."  Then click the check-mark next to the first device that shows up.  Now pulse will record your sound card instead of your mic.

---

