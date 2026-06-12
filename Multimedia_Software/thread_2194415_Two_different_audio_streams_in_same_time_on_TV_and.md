---
title: "Two different audio streams in same time on TV and computer"
date: 2013-12-18
forum: Multimedia Software
---

### Post by lin4sm on 2013-12-18
Hi, I have just recently installed ubuntu 12.04. Most of the time I have been using windows, so I am a bit new in here.

My situation: I have PC which have monitor (DVI) and TV (HDMI) connected on the same graphics card. On a TV my daughter is watching cartoons and movies. I am working with the same computer just using monitor.
I need to have two different audio streams at the same time. One I need for TV with movie or cartoon sounds and second I need to my headphones with the audio from web browser or music player in general all other computer sounds to headphones.
At the moment all sound goes to TV or only to headphones. For video I am using VLC media player. 
On Windows 7 I had all sound going to headphones, but when I open VLC player and press right click, I could chose different audio output/device only for VLC player and the video sound was only on TV.
On ubuntu VLC media player I don't see the same options. For the sound is just only few bits, I dont't see options to change audio output/device.

Could you suggest any solutions without buying any hardware please? As I understand there should be solution within software side.

---

### Post by papibe on 2013-12-18
Hi lin4sm.

You could do that by installing 'Pulseaudio Volume Control' from the Software Center.

Open both audio programs, then open 'Pulseaudio Volume Control' and there you can set which device they should use as output.

Hope it helps. Let us know how it goes.
Regards.

P.S.: you may need to resize the 'Pulseaudio Volume Control' window to be able to access the settings of both applications.

---

### Post by lin4sm on 2013-12-18
> **papibe said:**
> Hi lin4sm.

You could do that by installing 'Pulseaudio Volume Control' from the Software Center.

Open both audio programs, then open 'Pulseaudio Volume Control' and there you can set which device they should use as output.

Hope it helps. Let us know how it goes.
Regards.

P.S.: you may need to resize the 'Pulseaudio Volume Control' window to be able to access the settings of both applications.

I have installed [COLOR=#000000]'Pulseaudio Volume Control'[/COLOR] and everything works fine now after minute of small changes.

So I had to set default audio to my headphones through system settings->sound. Then I could change VLC media player audio output to HDMI on Pulseaudio Volume Control.

Than you papibe for your help.

---

