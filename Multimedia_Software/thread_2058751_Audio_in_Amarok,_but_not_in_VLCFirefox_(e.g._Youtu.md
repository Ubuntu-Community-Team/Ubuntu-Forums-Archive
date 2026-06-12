---
title: "Audio in Amarok, but not in VLC/Firefox (e.g. Youtube)"
date: 2012-09-16
forum: Multimedia Software
---

### Post by Ctulhu on 2012-09-16
Hi all

I used to have Windows 7 and then Mint 12 KDE on a Dell XPS 8300, but now I just upgraded to Kubuntu 12.04. However, audio/sound is extremely volatile. Here's some info:

1) On Windows 7, everything was working fine. According to the Device Manager, I had Creative SB X-Fi, driver 6.0.1.1348

2) On Mint 12 KDE, everything was working right after installation.

3) On Kubuntu, Phonon (in the Device Preference tab) shows 3 sound devices:
- X-Fi Titanium series [EMU20k2] Analog Stereo
- Built-in Audio Analog Stereo
- GF 110 High definition Audio Controller Digital Surround 5.1 (HDMI)

Two questions:

1) I now seem to have reliable audio in Amarok and videos in VLC (when the master channel is set to "X-Fi Titanium series [EMU20k2] Analog Stereo", but I don't get sound in Firefox, no videos (tried .avi and .mp4 in VLC and SMPlayer), nothing. When I go to Phonon>Audio Playback device and I test the X-Fi Titanium series [EMU20k2] Analog Stereo with Music and Video, I get the test sound.

2) When I go to Phonon>Audio HardwareSetup, then it shows 
- GF 110 High definition Audio Controller under Hardware>Sound Card
- Playback (GF 110 High definition Audio Controller Digital Stereo (HMDI)) under Device Configuration>Sound Device
EVEN WHEN I CHANGED BOTH to X-Fi Titanium series [EMU20k2] five seconds ago and clicked Apply and OK. When I make the changes, the speaker test (Front Left and Front Right) work, but the changes don't stick!

I don't get it - how can the audio be fine for music in Amarok but not for different kinds of videos! Any ideas plz?

---

### Post by whatthefunk on 2012-09-16
What backend are you using?  Go to System Settings > Multimedia > Phonon and then to the backend tab.  Default is GStreamer, but that one has given me problems similar to yours so I now use vlc.  Youll need to install the package phonon-backend-vlc and restart x after choosing it from the Phonon menu.

---

### Post by Ctulhu on 2012-09-16
The only backend listed there is GStreamer so I am installing phonon-backend-vlc now and will then reboot. will report in a minute ;-)

---

### Post by Ctulhu on 2012-09-16
Ok, I

- did what you said and installed the VLC backend
- also chose the X-Fi Titanium series as the audio device in VLC
- also chose the alsa (0.0 - Creative X-Fi) as the output driver in SMPlayer

... and now I have sound in videos in VLC and SMPlayer, YEY! Thanks a lot!!

What still does not work is sound in online vids AND phonon still does not retain my choice of X-Fi as a standard. When I reboot, I always even get a message that Kubuntu reverts back to Built-in audio (and offers me to revert to X-Fi).

---

### Post by whatthefunk on 2012-09-16
Hmmm....
Have you tried installing drivers for it?
[http://support.creative.com/downloads/welcome.aspx](http://support.creative.com/downloads/welcome.aspx)

This might be of use:
[http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi)

Also, is pulseaudio installed on your system?

---

### Post by Ctulhu on 2012-09-16
> Have you tried installing drivers for it?
Well, I thought those are installed because

- Phonon recognizes the sound card and, **more importantly**,
- audio works everywhere else now, just not in browsers (Firefox and Opera): I can even go to Youtube and have no sound, then I download the video, and then I have sound!!

> [http://support.creative.com/downloads/welcome.aspx](http://support.creative.com/downloads/welcome.aspx)
> [http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi)
Ok, will check those out.

> Also, is pulseaudio installed on your system? 
Yes, it is.

Thanks a lot!

---

