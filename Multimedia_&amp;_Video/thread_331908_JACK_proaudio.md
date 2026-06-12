---
title: "JACK proaudio"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by ssavelan on 2007-01-05
First,

Audio should be separated from multimedia in both the applications dropdown and this forum.

WHY?

Because the proaudio capabilities on UBUNTU are so POTENT and deserve their own space.

Ubuntu as a dedicated proaudio station is worth thousands/USD!!!

JACK with amsynth, Ardour, freewhelin' and friends run great  -*together*-!!!  I have little proaudio suggestions, needs, help for other people that should not forever be mixed with discussions of nvidia and ATI.  JACK is the coolest thing I ever seen.  The debian audio suite is a gold mine.

Anyone know how to get hydrogen to make outputs on JACK connection?

My video stuff works great.... and worked great "out of the box"... so easy... why do people talk about video so much.... FLASH9 tutorial on Google video, chmod a+x RealPlayer10GOLD.bin, put your .so files in the /usr/lib/mozilla/plugins or whatever.... then I have mplayer/xine on mozilla and not firefox for when I need to see Quicktime content... yeah get the codecs, add the repositories... etc,etc

where are the proaudio threads?

---

### Post by Patrick K on 2007-01-05
Not a Pro-Audio guy but I do record myself and other. I doubt there are enough people on this site to support a Pro-Audio forum. Most users here are either computer hobbyist or seekers of help. But I think separating video and audio might be a good idea. Some message board software allows sub-forums, maybe put Pro-Audio there. For the vast majority of users, playing videos, DVDs, and MP3's, and the like, is much more important than recording live music. Those of use that record live music are a very tiny minority of user. 

Anyway, I've not hear of Jack before. Can you provide a link? I'm using Audacity primarily plus Ableton's Live 4 Lite (came with the M-Audio board) mostly for making drum tracks. I like being able to just hit the "R" key and start recording with Audacity. Very simple. Unfortunately, it doesn't support real time effects. 

Now, if I can just get my Audiophile 2496 card to work with Audacity and Edgy. Works great in Windows.

---

### Post by ssavelan on 2007-01-15
JACK is amazing... jack-rack is probably my favorite package in the world.  You can route one program to the next... real-time as it gets.  

qjackctl can be sudo apt-get installed...... as can jack-rack.

Are you running Ableton in Ubuntu?  That would be swell... I have a friend using Ableton in Windows and if I could get it to work in Ubuntu I could help him change more easily.

You can get your soundcard to work...

[URL="http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix"]
http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix[/URL]

I have an EchoLayla24 running pretty strongly....

you will have to download all of the [ALSA tarballs]("http://www.alsa-project.org/") (grab utils, firmware, etc.) and unpack them.

then, within the alsa-driver directory  you will do something like:

$ ./configure --with cards=ice1712 --with oss=yes --with sequencer=yes
$ make
$ sudo make install

***DO NOT USE THIS IMMEDIATELY, THE SYNTAX MAY BE APPROXIMATE, THERE ARE BETTER LINKS IN THE WIKI***

I used :[https://help.ubuntu.com/community/EchoMia]("https://help.ubuntu.com/community/EchoMia")


"./configure
make
sudo make install"

within all of the new alsa directories

let me see if I can get a better link for you....

no, but you can adapt the explanation for the echo to your soundcard.....
I think just replace * in   "--with-cards=*" to "ice1712" ... I think..  of course you will have to include your other soundcard if you are wanting the option to use it for lightweight apps...

hope that helps....

about jack... search ALSA audio JACK, etc.

---

