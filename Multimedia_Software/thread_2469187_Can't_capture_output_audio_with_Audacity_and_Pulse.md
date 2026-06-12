---
title: "Can't capture output audio with Audacity and PulseAudio"
date: 2021-11-22
forum: Multimedia Software
---

### Post by temporos on 2021-11-22
I'm trying to record a sound clip from my system, but I can't get Audacity to record from any device other than the built-in mic (ALSA/default). I have PulseAudio Volume Control installed, and all packages are up-to-date.

When I launch audacity, it'll happily record audio from the mic, but it throws errors if I choose anything other than "default" for the input device. When I change the input device back to the mic, it will then refuse to record again from the mic until I quit and relaunch.

In PulseAudio Volume Control, no entries ever appear in the Recording tab, even when Audacity is recording. Also, if I launch the PulseAudio control before I hit record on Audacity, Audacity will throw errors about the input device, even if it was recording from the mic ten seconds prior.

---

### Post by tea for one on 2021-11-22
Try this little test:-

Play a track from your music collection
Open Audacity and press record
Open Pulse Audio > Recording > Select [COLOR="#0000FF"]Monitor of Built-in Audio[/COLOR]
Check if Audacity is recording

Any joy?

---

### Post by temporos on 2021-11-22
No joy. The audio file played fine, and it looked like Audacity was recording, but the Recording tab of PulseAudio was still blank while the audio played.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289518&stc=1[/IMG]

Also, once I stopped the recording, Audacity refused to play back the recording. I'm pretty sure it just recorded the audio via the mic, instead of the audio out, but I can't play it back to tell.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289519&stc=1[/IMG]

---

### Post by tea for one on 2021-11-22
Your image  tells us [COLOR="#0000FF"]No application is currently recording[/COLOR]

Have a look at Audacity > Edit > Preferences > Recording > Device > Choose Default

Nearly there.........?

Edit - In post 2, when I wrote [COLOR="#0000FF"]Play a track[/COLOR], you have to use another application to play the track i.e. Rhythmbox.
I do not think that Audacity can play and record simultaneously (unless [COLOR="#0000FF"]Overdubbing[/COLOR], where I do not have sufficient knowledge to offer advice)

---

### Post by temporos on 2021-12-20
> **tea for one said:**
> Have a look at Audacity > Edit > Preferences > Recording > Device > Choose Default

There are two results to this. The first is when I start recording on Audacity, and then open Pulse Audio. The second is when I open Pulse Audio first, and then start recording in Audacity...

1. Start recording in Audacity, then start Pulse Audio. Audacity looks like it's recording from the mic just fine, but when I start Pulse Audio, the recording tab still says no applications are recording audio. Also, when I try to play back what Audacity recorded from the mic, it throws an error.

2. Start Pulse Audio, then start recording in Audacity. Audacity doesn't record anything, and Edit > Preferences > Recording > Device says no devices found.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289650&stc=1[/IMG]

---

### Post by tea for one on 2021-12-21
After successfully recording sound playing on my PC, my Audacity > Preferences: Devices show:-

Playback device:  default
Recording device : default

---

### Post by temporos on 2021-12-21
Yes, I can record *from the mic* with default/default. I want to record the audio being played by the computer, not the mic input. While Audacity is recording from the mic, PulseAudio still says no apps are recording.

---

### Post by tea for one on 2021-12-21
Perhaps temporarily remove, disable, de-activate your microphone so that the default source is a different device.

You may have a checkbox in your UEFI set up to turn on/off the microphone.

Alternatively, have a browse through the Audacity help pages

[https://manual.audacityteam.org/man/tutorial_selecting_your_recording_device.html](https://manual.audacityteam.org/man/tutorial_selecting_your_recording_device.html)

---

### Post by temporos on 2021-12-21
I think (at least part of) the problem is PulseAudio. When I'm recording in Audacity, nothing appears in the Recording tab of PulseAudio (screenshot).

Also, after I open PulseAudio, Audacity throws an error (screenshot) whenever trying to access *any* sound device to play or record, even if it was happily recording seconds earlier.

Is this something that might be fixed by uninstalling and reinstalling PulseAudio, or will that just break other things? Is that as simple as below...?

```
sudo apt purge pulseaudio
sudo apt install pulseaudio
```

**Edit: **@tea for one: I've been through the Audacity manuals several times, and I can't find anything about a situation quite like this. I've also searched and read many articles about recording system sounds using Audacity and PulseAudio, but again, no matches. It always just assumes something appears in the Recording tab of PulseAudio.

---

### Post by temporos on 2022-01-21
Just checking in to see if anyone can help further. I purged PulseAudio from my system, and then reinstalled it. Unfortunately, I still get the same issue: no streams are listed in the "Recording tab of the PulseAudio volume control. Also, Audacity sometimes throws an error saying it can't access the recording device, and other times it'll say it's recording, but will actually record silence.

Any help would be appreciated.

---

### Post by rogerk03 on 2022-03-19
I have exactly the same problem, I also installed via snap.  Funny thing is, I have 2 instances installed, one via APT installed and working fine, other one via snap and doesnt work.  I added all the permissions in the snap store, connected the pulseaudio to audacity in snap, still no joy.

---

### Post by bitrat2 on 2022-11-13
Hi,

I have a similar issue to yours, where I can't record system audio.  Also another issue, where I get intermittent high frequency distortion.

I can fix both with [FONT=courier new]**pulseaudio --kill**[/FONT]

Presumably this just restarts and reinitialises pulse. 

Cheers,
bitrat

---

### Post by joealen-023 on 2023-06-15
My problem is fixed by enabling the audio [device]("https://thegeekpage.com/fix-audacity-recording-device-error-or-while-opening-sound-device-issue/").

---

### Post by send2 on 2023-06-17
If you are trying to record from your sound card, here is a step by step guide from Audacity's page on Linux, you might have to click on the Linux tab as it also has instructions for Windows and macOS:

[URL="https://support.audacityteam.org/basics/recording-desktop-audio"]https://support.audacityteam.org/basics/recording-desktop-audio

[/URL]You have to install Pulse Audio Volume Control too if you don't have it. 

Hope this helps...

---

