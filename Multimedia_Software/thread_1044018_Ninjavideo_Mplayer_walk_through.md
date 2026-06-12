---
title: "Ninjavideo/ Mplayer walk through"
date: 2009-01-19
forum: Multimedia Software
---

### Post by ivanbloodbane on 2009-01-19
I have had a lot of problems with ninjavideo.net and I have finally found the right solution. I started off with nothing coming up not even the applet starting correctly so hopefully this walk through will help anybody that is have trouble with the site. This is my first post and first walk through revised (coming from the original sticky on video player's located at the end) and any improvements/short cut's are welcome. I found most people are getting Mplayer installed right but not set up correctly So I decided re-iterate the guide in such a way just for Mplayer. 

the first line in the terminal (under Applications > Accessories > terminal) will get you every thing under the sun you need to play video's on Ubuntu 8.4 32-bit. 

**sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar  **

this is your java, flash and gsteramer's that will allow you to play embedded viedo's

the next line will delete any extra plug-in's that you installed

**sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-plugin-vlc totem-mozilla xine-plugin**

these plug-in's are good to have, but why install them when mplayer does it all for you?

and then in the Synaptic Package Manager (under System > Administration > Synaptic Package Manager) search for mplayer and install mozilla-mplayer and mplayer (medibuntu package) 

If you do not have the medibuntu a third-party source list install it by typing the following in the terminal.

**sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list**  

activate the medibuntu package by going to System > Administration > Software Sources in Software Sources go to third party software and check the two boxes for medibuntu.

Next open mplayer and right click and go to Preferences > Audio and click the Enable Software Mixer box.

Then type in the flowing in the terminal

[B]gedit $HOME/.mplayer/mplayerplug-in.conf
[/B]
and copy paste

[B]download=1
cachesize=1024
cache-percent=25
keep-download=0
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=1
black-background=1
rtsp-use-http=0
rtsp-use-tcp=0[/B]

this basically sets up the player. save the file and close it. 

Next go to Places > Home up top go to view and click on show hidden folders. Go to .mozilla and click the Firefox folder. My system shows a file name 9qeawped.default I do not know if it will be different the guide does not say this file but in the file there is a file name pluginreg.dat delete it and restart Firefox. 

This takes the the file you just saved and copies it to the mplayer plug in.

Now all that is left to do is to configure the mplayer plug in. Once you see the buffering take place right click on the mplayer and click configure check the box that says Enable Divx support and then at the top chose your viewing mode and audio mine is x11 for video and I use ALSA for audio. Enjoy. Personally I love ninjavideo because of there mad upping skills and very high quality videos. 

the original sticky on any video system's and other cool Multimedia and video can be found at 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)****

---

### Post by Baby Boy on 2009-01-29
I've followed this guide but I still can't play/download the videos. When I go right-click => Play on the video box, there is a brief message saying "Getting playlist..." then it changes to "Stopped". Clicking on download takes me to "Failed to connect" page. Still around to help me?

The possible problem might be that Mplayer can't really play videos, only sound (though I haven't fiddled around this much), which happen to be downloaded from ninjavideo.net (plays fine in Totem).

The applet doesn't show the blue "ONLINE" text either like it does in Windows.

EDIT: Actually, scratch that. I've found another guide on ninjavideo.net forum, now everything works. What I've done though:

-sudo apt-get autoremove (removed some things related to the totem mozilla plugin, could be that)
-downloaded sun java 6 plugin via Add/Remove (the one with "1 star popularity")

---

