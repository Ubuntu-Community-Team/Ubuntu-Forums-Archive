---
title: "No sound in Rhythmbox/Exaile while playing mp3"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by psynyd on 2007-01-20
Hi,

I'm a Linux newbie and have been using Edgy Eft for a round a month now. I got the solutions to most of the initial transition problems I faced either on these forums or in the documentation but   I still cant play mp3 from either Rhythmbox or Exaile. The files seem to be playing but i hear no audio. The soundcard can't be a problem as I use skype everyday and can listen to mp3 on Amarok. From what I've gathered, Amarok runs using xine and Rhythmbox uses gstreamer so I'm suspecting the problem must be with gstreamer. I installed all the codecs specified in the documentation including the multiverse ones but to no avail.

 I really want to get Rhythmbox running because i'm used to the iTunes interface. I have dumped windows and moved to Linux and wanna stay a Linux user for good! So please Help!

Thanks!

---

### Post by Cobikegeek on 2007-01-20
Have you done all of these steps?

1. Install Lame codecs using synaptic

2. Open rhythmbox

Select edit-preferences and click on the edit profiles box at the bottom of the window.   Click on "New" and create a profile named MP3.  Paste this code into the Gstreamer Pipeline text box:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux

Enter mp3 for file extension.  Click on the Active box and close.  From the profiles list select MP3 and close.

You can use this profile in Soundjuicer too to rip mp3 files from an audio cd.

Good Luck

(if you want better sound quality enter a higher # for bitrate.  196 for example.  Tradeoff is bigger files.)

---

### Post by agorex on 2007-01-20
Use Synaptic and install "gstreamer0.10-fluendo-mp3". It has worked for me.

You can also check this out:
[http://www.fluendo.com/resources/fluendo_mp3.php](http://www.fluendo.com/resources/fluendo_mp3.php)

---

