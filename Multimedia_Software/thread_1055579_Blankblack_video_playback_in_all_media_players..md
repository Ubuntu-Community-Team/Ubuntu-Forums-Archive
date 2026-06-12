---
title: "Blank/black video playback in all media players."
date: 2009-01-30
forum: Multimedia Software
---

### Post by Slothie on 2009-01-30
I've just upgraded my Compaq Evo NC810 Laptop from Ubuntu Dapper to Xubuntu Ibex. All is going well until I tried playing video...

It matters not which media player I try, they all play the media (.mov, .wmv, .flv files...) with sound but with no video. Please don't just say "Totem is crap try xine/mplayer/vlc etc" because I have, and they all do the same thing. 

Strangely, Youtube videos play through firefox with no problem, after I installed flashplugin-nonfree.

What did I do? 
I backed up all the file in /home/... to a USB drive:
```
cd /
tar cvz home | split - /media/LaCie/archive/tuxtop/bu090130-
```
Then did a fresh install of xubuntu. Then I unarchived all the files over my new login directory:
```
cd /
cat /media/LaCie/archive/tuxtop/bu090130-* | tar xvz

```
I then mucked about getting Thunderbird to see my emails (renamed .thunderbird directory)
Then I installed the flash plugin and got that working
Then I noticed the media played didn't work!
After extensive googling I found these instructions, so I did:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```
That didn't fix it, so I tried installing mplayer (didn't work) totem-xine (ditto) vlc (ditto)... 
I feel I must have a more fundamental problem...

Never had any problems playing videos in totem under dapper, so it's not that the video adapter isn't supported!

Any ideas anyone?

---

### Post by mc4man on 2009-01-30
I don't know xubuntu very well, maybe try changing the video output.
For vlc, xine, ect. you'd do it in the players setting's/preferences. (try X11 or OpenGl

For totem there'd be a system setting.

Not sure what's the deal in that regard in xubuntu 

In *ubuntu* it's in System -> Preferences -> Multimedia Systems Selector
You could try 'X Window system (no Xv)'
Also in *ubuntu*, the Multimedia Systems Selector is not enabled in the preferences menu by default 

 Is there any restricted video driver available?

---

