---
title: "[SOLVED] Problem with gxine"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by upthelum on 2007-07-23
Trying to view video streams from the web. When i click the video it opens gxine and displays a message about gxine plugin, and wont play the file. 
Synaptic says i have it installed and i have problems with other media players not playing cd's. Can anyone suggest where i might start trying to repair these problems?

---

### Post by benx009 on 2007-07-23
what type of video stream is it?  if it's flash, then you just need to install the flash plugin for your browser.  

i know that mplayer also plays some video streams for me.  installing the **mplayer** package as well as the **mozilla-mplayer** package (both available in the ubuntu repos) should help (xine never really worked for me)

---

### Post by Gremlinzzz on 2007-07-23
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer
:guitar:

---

### Post by upthelum on 2007-07-23
For some reason i got the mplayer plugins but the player came up as uninstallable. Still not working...

---

### Post by upthelum on 2007-08-04
Ok i've upgraded and now the video needs Flash which i have a thread going on elsewhere.

---

### Post by Gremlinzzz on 2007-08-04
your using kubuntu you need the package with kde support
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.

---

### Post by Gremlinzzz on 2007-08-04
> **Gremlinzzz said:**
> your using kubuntu you need the package with kde support
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.

if you have a 64amd processor this flash will not work.

---

