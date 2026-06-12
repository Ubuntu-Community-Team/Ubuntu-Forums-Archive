---
title: "How To Record Sound Ubuntu 9.04"
date: 2009-08-02
forum: Multimedia Software
---

### Post by AlexanderDGreat on 2009-08-02
Hi, I did a fresh install of Ubuntu 9.04, updated it, but can't record a sound using Sound Recorder until I installed from Synaptic, padevchooser. Also, install ubuntu-restricted-extras, this is to play common multimedia in your computer. I'm using HP dv2000 laptop.

After installation, go to System>Preferences>Sound, make it ALL PulseAudio Sound Server, except Device, choose under Device, something with "Playback: (yoursoundcard)".

Then, choose Applications>Sound & Video>PulseAudio Device Chooser. It will show an icon in your applet, click Volume Control and configure from there. Now, you can record, mp3's, youtube videos, etc... From what I understand, some features of PulseAudio is not accessible until you install the applet.

I learned these tools from: [http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

---

### Post by igorzwx on 2009-08-03
You can record sound with Audacity

[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

### Post by AlexanderDGreat on 2009-08-03
Hi igorzwx, thank you for that info, I might also try that someday, I was just trying to Record Sound w/o installing additional software in Ubuntu 9.04 in my HP DV2000 Series Laptop. Thanks. =)

---

### Post by gigaferz on 2009-08-09
thank you,

I was stressing again, fortunately it did work!!

  when using with sound recorder try moving the stream to a diferent device you need to use volume control -> recording. Then youll see the current application there is a little arrow wich is a menu then in there move the stream to a different device if you dont succed at first.

---

