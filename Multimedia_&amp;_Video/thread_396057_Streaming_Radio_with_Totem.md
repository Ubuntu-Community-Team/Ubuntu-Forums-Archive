---
title: "Streaming Radio with Totem"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by manwe on 2007-03-29
Hey all, 
I keep getting an error in Totem while  trying to listen to a radio feed. When I open the url I get the following error:

Totem could not play 'mms://wm.cbc.ca/cbcr1-victoria'.
No URI handler implemented for "mms".

Looking through "about: plugins" in Firefox I don't see mms listed anywhere, is there another plugin that I need to load? The website states that mplayer should work but, totem keeps opening by default. Is there a way of setting a default plugin?

I'm a bit of a linux newb so please bear with me.

Cheers, 
Manwe

---

### Post by H.E. Pennypacker on 2007-03-29
I believe Rhythmbox or Listen Music Player are better suited for streaming online radio.  Try those, but start with Rhythmbox, because it is installed by default.  

Also, do a forum search on "cbc.ca" to see if anyone else has had a problem specific to this website.

---

### Post by manwe on 2007-03-29
I had the same issue in rythmbox. At which point I installed:

gstreamer0.8-mms

And still nothing. I uninstalled the totem plugin and lo and behold it worked fine using the mplayer plugin. So the radio is working fine.

Any ideas on getting rhythmbox to handle mms streams? It would be nice to listen to it through there.

Cheers,

manwe

---

### Post by H.E. Pennypacker on 2007-04-01
You may either use Totem, VLC, or MPlayer (or anything else that works).  I tried your URL using Totem, and VLC.  Both work just fine.  Copy and paste your URL (mms://wm.cbc.ca/cbcr1-victoria) into your address bar, and Firefox should ask you if you want to play Totem to play it.  Totem should start up, and play it just fine.  

If not Totem, start up VLC.  Go to File > Open Network Stream (or press CTRL-N).  Copy and paste the URL, and play.

That should be it.

---

### Post by toxickiwi on 2007-04-04
I have had the same problem with team1040 & cfax radio stations what I did is from the shell:

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 


then restarted firefox and it worked fine.

ref: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Codecs)

---

### Post by boes on 2007-04-06
I love to listen radio and have not been problem using win***s program
but have failed when using ubuntu version 6.06.

[http://www.rsi.sg/english_loadaudio.php?audio=http://NETtv.1-NET.com.sg/RadioRSI/Indonesian.asx](http://www.rsi.sg/english_loadaudio.php?audio=http://NETtv.1-NET.com.sg/RadioRSI/Indonesian.asx)

but its ok to these below stations

[http://abc.net.au/ra/indon](http://abc.net.au/ra/indon)
[http://wma.str3am.com/KSK](http://wma.str3am.com/KSK)

can anybody help me with the first one.
thank you
boes

---

