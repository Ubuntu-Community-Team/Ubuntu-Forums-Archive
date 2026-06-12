---
title: "Crackling audio  -  Question"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by Bohlio on 2007-05-18
Hello all,
I'm using a Diamond multimedia soundcard with a C-Media chipset and I'm having some audio problems:confused:

Every other form of audio seems to work, except for when i play anything through VLC, I need to have the system volume low and amplify it with my receiver in order to avoid crackling noises. Pretty much anything above 20% volume starts crackling. Does anyone know what could be causing this? I can play MP3s through Rhythmbox and it works perfectly with the system volume up to 100% I dont know what could be causing VLC to have this problem.
Any help would be appreciated.

Oh, and the audio is passing into my receiver via a digital coaxial cable.

---

### Post by luctor on 2007-05-19
my quess is that vlc uses a different mixer channel then the other media players.

---

### Post by Bohlio on 2007-05-20
Does anyone know this for sure? or do you know how to check it? anyone else have this problem?

---

### Post by Raaben on 2007-05-21
I'm having the exact same VLC problem, and Amarok-xine plays my MP3's with crackling noises every so often. It only started today after I installed and started using KDE, and nothing I've changed in the control center fixed it. Both programs worked just fine under Gnome/XFCE...

I have an onboard Realtek ALC850

---

### Post by psyke83 on 2007-05-21
Hi,

It's a bug in VLC's ALSA driver. Go to Settings, Preferences, click Advanced Options, then navigate to Audio, Output modules and change "Audio output module" to OSS.

---

### Post by FrozenFOXX on 2007-05-22
Thank you VERY much, I'll try that out immediately.  I love VLC and was starting to get rather pissed off with the sound quality.

---

### Post by Raaben on 2007-05-22
Ah, that works. Seems that my Amarok problem was due to a few bad MP3's that I somehow didn't notice earlier. Dunno how I missed the VLC error until the other day, since I was watching a movie before that.

Is it really a bug in VLC or is it with Ubuntu's ALSA? I compiled the latest VLC from source and it's still behaving that way, and I haven't had that problem in other distros with the same version since I use VLC every day. (I just started with Feisty the other day)

---

### Post by Bohlio on 2007-05-23
thanks psyke 83, I dont have any more crackling now :-P

---

### Post by dzark on 2007-07-30
Found the solution in another thread: [http://ubuntuforums.org/showthread.php?p=2940695](http://ubuntuforums.org/showthread.php?p=2940695)

To quote tie_dyed_sox:
> 
I also had a problem with crackling sounds in VLC but was able to fix it by configuring the ALSA device name in the VLC settings.

Settings -> Preferences -> Audio -> Output modules -> ALSA -> ALSA Device Name

Click 'Refresh list' and select something other than the default.

Worked wonders for me.

Cheers,
wulf

---

