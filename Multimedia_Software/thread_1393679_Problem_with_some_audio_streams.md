---
title: "Problem with some audio streams"
date: 2010-01-29
forum: Multimedia Software
---

### Post by DavidS on 2010-01-29
I am running Ubuntu 9.10 and Firefox 3.5.7

BBC audio and video streams work fine, as do YouTube videos.  But I am having a problem with streams from [http://www.rfi.fr/lffr/statiques/accueil_apprendre.asp](http://www.rfi.fr/lffr/statiques/accueil_apprendre.asp)

The link with the text "Ecouter 10'" is [http://www.rfi.fr/lffr/statiques/accueil_apprendre.asp](http://www.rfi.fr/lffr/statiques/accueil_apprendre.asp)
This opens a window, but nothing can be heard.  When I click on the link labelled "Si vous ne parvenez pas à écouter, essayer en cliquant ici" gmplayer jams up completely.  So I installed RealPlayer Gold 11, but this refuses to play the stream too, because it doesn't have mms, it seems.  The URL of the relevant stream here is mms://wmod.streaming.rfi.fr.edgestreams.net/rfi/francais/audio/journaux/r001/journal_francais_facile_21h00_-_21h10_tu_20100129.mp3.wsx

I tried installing the package ubuntu-restricted-extras, but this hasn't helped.

Is there any way I can get this type of stream to work correctly?

David

---

### Post by mc4man on 2010-01-29
Maybe search totem in synaptic and make sure totem-mozilla is installed. Then search mplayer and if mozilla-mplayer is installed then uninstall it.
 (there is another plugin called gecko-mediaplayer that could also work (uses gnome-mplayer), don't have it and totem-mozilla installed at same time, choose one or the other

Pretty much every thing you pointed to works fine here - karmic, totem-mozilla plugin. ( though can't read french at all but...

> The link with the text "Ecouter 10
screen 1 - opens in site player

> 
When I click on the link labelled "Si vous ne parvenez pas à écouter, essayer en cliquant ici
screen 2 - opens in totem-mozilla player ( plus a r. click on that gives option to open in totem itself.

Also both vlc and mplayer can play using the mms 

> vlc mms://wmod.streaming.rfi.fr.edgestreams.net/rfi/francais/audio/journaux/r001/journal_francais_facile_21h00_-_21h10_tu_20100129.mp3.wsx
VLC media player 1.0.4 Goldeneye
[0xa009140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xa0b4eb8] access_mms access: selecting stream[0x1] audio (0 kb/s)
[0xa0b4eb8] access_mms access: connection successful
[0xa27b288] pulse audio output: No. of Audio Channels: 2

> mplayer mms://wmod.streaming.rfi.fr.edgestreams.net/rfi/francais/audio/journaux/r001/journal_francais_facile_21h00_-_21h10_tu_20100129.mp3.wsx


---

### Post by ajgreeny on 2010-01-29
I am running 9.04 with Firefox 3.0.17.  I use the gecko-mediaplayer plugin for audio, and that works perfectly with the "ecouter 10'" link you showed in your post.  I have all the codecs I can think of, w32codecs. all the gstreamer good, bad and ugly, many mpeg packages, but interestingly, not the ubuntu-restricted-extras.

I am listening in UK, so it is not that only those with a French IP address can do so.  There must just be something different about your setup that stops you hearing the stream.  The difficulty is knowing what it could be.

I case it might help I attach a txt file with all the apps I have added since I installed 9.04

---

