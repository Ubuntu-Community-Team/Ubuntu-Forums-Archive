---
title: "USB Headset Not Working"
date: 2010-11-29
forum: Multimedia Software
---

### Post by Ellume on 2010-11-29
Yes, I am a newbie to ubuntu. So I'm trying to get my usb headset to work. Right now I can adjust the volume and mute using the buttons on the headset, but I can't get sound to play through it or the microphone to work.

When I go to System --> Preferences --> Sound I can see that there is a driver "USB PnP Sound Device" under the "Hardware" tab. When I go to the output tab and click on the "USB PnP Sound Device" then I just can't hear anything at all. I can adjust the volume with my headset regardless of whether I have "Internal Audio Analog Stereo" or "USB PnP Sound Device".

All help is greatly appreciated :D

---

### Post by Cotopaxi on 2010-12-25
Actually, I would also need some help on this one!

Thanks!

---

### Post by Cotopaxi on 2010-12-25
Anybody else has any experience with USB headsets, or are we two the only ones who don't get it working?

---

### Post by Cotopaxi on 2010-12-25
Ok, I managed to solve it:

I downloaded Gnome AlsaMixer “gnome-alsamixer” from the repositories. Once I opened it, it presented me two tabs:
1) “Realtek AL861-VD”, which I think is my sound card &
2) “USB Mixer”, with the sliders for “PCM (sound output volume) and “Mic” (Microphone sensitivity). Here all my problems got solved.

So now it works great, except for three minor problems:
1) When chatting over Skype the output volume on the headphone is still a little bit too high, although the volume slider is down at minimum.
2) When I modify the volume with the buttons of the built in control unit, I modify the volume that goes to the speakers, not the volume that goes to the headset! 
3) My music player “Amarok” is sending the sound to the USB headphone, the way I selected it in the system settings, but the video player “VLC” is still sending the sound to the loudspeakers of the laptop, although I selected in the system settings to have the sound sent to the USB headset. I just tried out the video player “Dragon Player” and this one does send the sound to the headset!

Now, two general observations:
1) When you plug in a USB headset, be prepared to have an extremely violent volume on your ears! So, minimize all volume sliders, the one for the headset and the volume slider of the application you are in.
2) The headset is a T-VISTO TVT-278USB (“[www.t-visto.com](www.t-visto.com)). For the twenty Dollars it cost me, the sound is very good. I mainly listen to instrumental music (acoustic instruments) and I like the sound very much.

One last thing: on another thread in this forum it is discussed to type “alsamixer” in the terminal window. It did solve the problem for some other people although not for me. Here goes the link:

[HTML]http://ubuntuforums.org/showthread.php?t=1469276&highlight=USB+headset[/HTML]

---

### Post by Cotopaxi on 2010-12-25
One last comment:

My system is Kubuntu 10.something (I don't know how to look that one up;))

The laptop is a lenovo (I also don't know how to look that one up :p).

The "VLC" media player is "vlc" in the repositories.

The "Dragon Player" is "dragonplayer" in the repositories

---

### Post by Cotopaxi on 2011-01-20
Ok, I really found a solution!

I installed "PulseAudio" and "PulseAudio Volume Control" <pavucontrol>.

They are both in the repositories.

I have written a (fairly long) HOWTO, which can be read at this link:

[HTML]http://ubuntuforums.org/showthread.php?t=1669659[/HTML]

Good Luck! ;)

---

### Post by Cotopaxi on 2011-01-20
Ok, I really found a solution!

I installed "PulseAudio" and "PulseAudio Volume Control" <pavucontrol>.

They are both in the repositories.

I have written a (fairly long) HOWTO, which can be read at this link:

[HTML]http://ubuntuforums.org/showthread.php?t=1669659[/HTML]

Good Luck! ;)

---

### Post by cxlxmx on 2011-02-09
I had similar problems and found that I needed to restart the computer with the USB dongle plugged in and the settings in sound preferences set up correctly.

---

