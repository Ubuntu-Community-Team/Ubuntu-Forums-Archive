---
title: "I can't watch asf video streams or recordings through firefox"
date: 2010-01-13
forum: Multimedia Software
---

### Post by maramot on 2010-01-13
I open [http://www.europarltv.europa.eu/](http://www.europarltv.europa.eu/) and try to watch some of the recordings there. The window that's supposed to display the video says "Click here to download the plugin". I click there and a window pops up saying " no suitable plugins were found/ (Unknown plugin "x-ms-wmp") ". Isn't there a way to watch these recordings?

---

### Post by fancypiper on 2010-01-13
Follow this guide:

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by maramot on 2010-01-13
I began the first chapter of that howto and ran:
[B]
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar[/B]

But I get:

"E: Couldn't find package non-free-codecs".

I have added the lines:

"deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free"

to my sources.lst and replaced "karmic" with "hardy" because I'm running 8.04

I also checked out the "Software Sources" applet. There, in the first tab, I have selected the options: "Canonical-supported Open Source software (main)", "Community-maintained Open Source software (universe)", "Proprietary drivers for devices (restricted)", "Software restricted by copyright or legal issues (multiverse)". 

In the "Updates" tab of the same applet, I have selected everything except for "Pre-released updates (hardy-proposed)".

Do I need to enable any other repositories?

---

### Post by mc4man on 2010-01-13
On a virtually new install of lucid, which shouldn't matter, can play back from there by just installing these plugins
( the only things installed prior where vlc and mplayer, again shouldn't matter

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

Note that the site does offer flash playback, I used the default wmp (haven't installed flash yet) and the default totem-browser-plugin for firefox

What was also required was a restart after installing the plugins

there are several other ways to playback from there, in vlc works very well
(get the address of a video from the page source
Ex. - first video  (EN is for english
vlc mms://twofour.wmod.llnwd.net/a2238/d1/u/EuroParlTV/video/N001-100113-EN.wmv

---

### Post by fancypiper on 2010-01-13
I followed that guide, but I didn't convert to Ubuntu until Hardy Heron, and when it couldn't find a package, I would eliminate that package after updating to make sure it wasn't available. I only add repositories if I need programs not in the ones I have.

Note down which ones you enabled and be ready to uninstall programs and remove that repository if things go wonky.

Have you installed VLC? It's dependencies should have the codecs you need.

---

### Post by maramot on 2010-01-13
@ mac4man: I already have the newest versions of those packages, although I haven't restarted yet. I know I could just paste the link. The thing is that I want it to work normally, not through using such methods.

@fancypiper, I'll need some more detailed explanation of that first part :) As for VLC, I have it installed and I've had it for a long time.

---

### Post by fancypiper on 2010-01-13
> **maramot said:**
> @fancypiper, I'll need some more detailed explanation of that first part :) As for VLC, I have it installed and I've had it for a long time.

After adding repositories, command:
sudo apt-get update

You got this error:
E: Couldn't find package non-free-codecs, so change this:
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree
gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 **non-free-codecs** sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

to this:
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

Is that clear? I assume you know how to keep notes :D

Have you tried playing the files on that site with VLC?

---

### Post by maramot on 2010-01-13
Oh, now I catch what you meant the first time with "I would eliminate that package after updating to make sure it wasn't available".  :)

How would I play these files with VLC?

I've just reached the following result:
I have installed a MediaPlayerConnectivity firefox addon. It's an addon which lists all the media on a page and allows you to click a link, which appears in a sidebar inside firefox and play the embedded media file from the page through clicking the link.

I have ran it's "wizard" which configures which file type is played by which player, choosing the default mplayer everywhere. Now, when I click the name of the wmv file, I get an mplayer window opening, which immediately launches an ("fatal") error message: "invalid header size, giving up".

I click "OK" there, which leads to more error messages (like "Bits overconsumption: 594 > 8" for example) but nevertheless, the video starts. Only the video quality is horrendous, much worse than what I get under windows.

My guess: I need codecs. Where can I get them from though?

---

### Post by fancypiper on 2010-01-13
I think you may need the mozilla-plugin-vlc to play from a browser, but I usually just make a playlist by launching VLC and clicking Media>Open Network Stream, then paste the url of the stream.

---

### Post by maramot on 2010-01-13
I have just installed the mozilla-plugin-vlc package. Result: After configuring MediaPlayerConnectivity plugin to play wmv and flash (just in case, since I don't know which I should change) with vlc, I get a black rectangle when I open the page [http://www.europarltv.europa.eu/](http://www.europarltv.europa.eu/) and I can click on it. Clicking launches VLC which doesn't play anything. Just sits there, not bufferring, no nothing, just stays there, open.

If I click on any of the recorded sessions though, I still get the "Click here to dowload plugin" sign in the same area where the video should be. This time though, when I click on that place, it doesn't send me to a new page and it doesn't look for a plugin, it just stays like this.

Edit:
After restarting, I am once again sent to the window which looks for plugins and says No suitable plugins were found / Unknown Plugin (application/x-ms-wmp) and I have a button "Manual install" which sends me to microsoft's site.

---

### Post by maramot on 2010-01-13
After reinstalling mediaplayerconnectivity from firefox's site, I am able to watch the tecorded videos (wmv) from the europarltv site. The first video though (the flash-integrated one) that shows up immediately after you open the site, can't be played. I suppose this will be fixed if I tell mediaplayerconnectivity which flash player it should use. I don't know what address to give mediaplayerconnectivity though? How do I adress ubuntu's flash player, where is it installed?

---

