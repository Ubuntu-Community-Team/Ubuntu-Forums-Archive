---
title: "Cannot get microphone to work in Intrepid"
date: 2009-04-16
forum: Multimedia Software
---

### Post by lynx6855 on 2009-04-16
I have been trying off and on for the past three months to get my headset microphone to record.  It is driving me around the bend.  I have read through the numerous posts on the topic but have failed to find any working solution.  I have Intrepid on an HP desktop with Realtec ALC888 sound card installed. 

I am very happy with Linux and would love to largely ditch Windows, but as I am a regular user of Skype, without a working microphone in Ubuntu, I've got to boot to Windows to make any call.  (Microphone works fine in Windows.)  

Any help would be most appreciated.

---

### Post by freemath on 2009-04-19
Hello there,

I'm no expert at this, but I want to tell you what works for me. My computer is a Thinkpad X61 running Intrepid with an internal microphone. I installed Skype but could not record sound. Gnome Sound Recorder could not record sound either. So I understood that the problem was microphone recording.

I tried many advices on the web, including removing pulseaudio and installing esound, but to no effect.

Finally one advice was succesful for me. 

1. Keep the default pulseaudio sound system, or reinstall it if you have removed it. There is no need to tinker with pulseaudio.

2. On System > Preferences > Sound: Set "Sound Capture" to "HDA Intel AD 198x Analog (ALSA)". 

3. On System > Preferences > Volume Control: Device is "DHA Intel (Alsa mixer)". Click the Preferences button, put checks on "Internal Mic", "Capture". You might need to put checks on some other options too, especially those that are classified as "Recording". I do not understand precisely the working yet. But the key is, I guess, to [COLOR="Red"]put checks on two "Input Sources", which are classified as "Options"[/COLOR].

4. Again, on System > Preferences > Volume Control: On the tab "Options", for the two "Input Sources" choose "Internal Mic".

5. Now try recording with Gnome Sound Recorder. You may need to adjust the levels on Volume Control. 

6. Once Gnome Sound Recorder works, you can try Skype. In Skype's options, "Sound Devices": Sound In "HDA Intel ("hw:Intel,0)", Sound Out "pulse", Ringing "pulse". Uncheck "Allow Skype to automatically adjust my mixer levels".

This procedure also works on an Acer Travelmate 6525 running Intrepid.

Hope this helps.

---

