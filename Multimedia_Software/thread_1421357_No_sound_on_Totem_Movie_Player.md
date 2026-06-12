---
title: "No sound on Totem Movie Player"
date: 2010-03-04
forum: Multimedia Software
---

### Post by satimis on 2010-03-04
Hi folks,


Ubuntu 9.10 64bit
Totem Movie Player 2.28.2

No sound on playing .flv files, the volume control greyout. However vlc can play them without sound problem.  YouTube also works without problem on sound.  Please advise how to fix the problem.  TIA

B.R.
satimis

---

### Post by RedSingularity on 2010-03-06
Maybe totem cant play that format.  Does totem ask to install a .flv plugin?

---

### Post by satimis on 2010-03-06
> **RedSingularity said:**
> Maybe totem cant play that format.  Does totem ask to install a .flv plugin?

It can play .flv video file but without sound.  I tried mp3 files also without sound.

Edit:

Sound (Speaker icon) muted.  Pulseaudio removed and esound installed.  Pulseaudio causes movie on Totem jumping, frames moving rapidly.  Reinstall pulseaudio unmutes sound (speaker icon) but still no sound on 100% volume

S

B.R.
satimis

---

### Post by RedSingularity on 2010-03-07
Do you have the pulseaudio device chooser installed?

---

### Post by satimis on 2010-03-07
> **RedSingularity said:**
> Do you have the pulseaudio device chooser installed?

Hi RedSingularity,

Sorry, I don't follow.  What does it mean "pulseaudio device chooser"?

Pulseaudio was installed together with the installation of Ubuntu 9.10.  After the problem I removed it and installed esound.


Edit-1:

satimisu910@ubuntu910:~$ apt-cache policy "pulseaudio device chooser"
W: Unable to locate package pulseaudio device chooser
satimisu910@ubuntu910:~$ apt-cache policy 'pulseaudio device chooser'
W: Unable to locate package pulseaudio device chooser


Edit-2:

$ sudo apt-get install padevchooser
$ sudo apt-get remove esound
$ sudo apt-get install pulseaudio

reboot PC

Problem still remains.  No sound and movie jumps.  The worst thing is vlc without sound.  Movie is running.


B.R.
satimis

---

### Post by RedSingularity on 2010-03-07
In a terminal type 

pavucontrol

Look at the different sound levels.

---

### Post by satimis on 2010-03-08
> **RedSingularity said:**
> In a terminal type 

pavucontrol

Look at the different sound levels.

No hope.  Actually I can't run pulseaudio.  It causes Totem movie rushes to finish with a few frame (movie seems jumping)

$ pavucontrol

It seems frozen.

Playback
System Sounds
mono max

Output Device
RS780Azalia controller Digital Stereo (HDMI)
Front Left/Right max

Input Devices
Port: Microphone 1
Front Left/Right max

Configuration
RS780 Azalia controller
Profile: Digital Stereo (HDMI) Output
Internal Audio
Profile: Analog Stereo Input

Very slow response on clicking the tabs.  Waiting for long time.


B.R.
satimis

---

### Post by RedSingularity on 2010-03-08
Alright maybe pulseaudio is not going to work for you.  Take it off and we can try a few things from there.

---

### Post by satimis on 2010-03-09
> **RedSingularity said:**
> Alright maybe pulseaudio is not going to work for you.  Take it off and we can try a few things from there.

Yes, I'm now running vlc.  It works without problem

B.R.
satimis

---

### Post by Robodaddio on 2010-04-11
I had the same problem and was able to solve by right clicking the volume icon near the clock, left clicking 'choose preferences', left clicking the 'output' tab and changing from the currently selected 'HD48x0 audio Digital Stereo (HDMI) Stereo' to the 'Internal Audio Analog Stereo', slowed the fast playing Rythmbox and Totem players and restored sound.

Hope this helps.

> **satimis said:**
> Hi folks,


Ubuntu 9.10 64bit
Totem Movie Player 2.28.2

No sound on playing .flv files, the volume control greyout. However vlc can play them without sound problem.  YouTube also works without problem on sound.  Please advise how to fix the problem.  TIA

B.R.
satimis

---

### Post by satimis on 2010-04-11
> **Robodaddio said:**
> I had the same problem and was able to solve by right clicking the volume icon near the clock, left clicking 'choose preferences', left clicking the 'output' tab and changing from the currently selected 'HD48x0 audio Digital Stereo (HDMI) Stereo' to the 'Internal Audio Analog Stereo', slowed the fast playing Rythmbox and Totem players and restored sound.

Hope this helps.

Hi Robodaddio,

Thanks for your advice.

I don't have volume icon on top bar.  I'm running Gnome Alsa Mixer here.

Applications -> Gnome Alsa Mixer

VIA VT7108S
[check] IEC958 Default PCM

All controls unmuted (Not check)


B.R.
satimis

---

