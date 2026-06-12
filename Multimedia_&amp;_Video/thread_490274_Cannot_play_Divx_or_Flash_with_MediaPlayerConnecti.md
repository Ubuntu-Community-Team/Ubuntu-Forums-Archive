---
title: "Cannot play Divx or Flash with MediaPlayerConnectivity"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by eekfonky on 2007-07-02
Hello

I'm having trouble with my MediaPlayerConnectivity when I install it I'd like to use VLC for most embedded video but get no option for the Divx or Flash files. In fact I only get options for: Real Media, Windows Media, Quicktime, Playlist and MP3/AAC.
Any suggestions as I've seen screenshots of other setups and they have a lot more options

Cheers

---

### Post by eekfonky on 2007-07-03
.....anyone....please.....

---

### Post by Gremlinzzz on 2007-07-03
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/Re...t=%28codecs%29](https://help.ubuntu.com/community/Re...t=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

---

### Post by Gremlinzzz on 2007-07-03
Forgot flashplayer
sudo apt-get install flashplugin-nonfree
Use the guide Luke
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by eekfonky on 2007-07-03
I'll try that and let you know

Cheers

---

### Post by eekfonky on 2007-07-03
seems to work- except when I go to fullscreen the video runs slower than the audio - any ideas why?

---

### Post by Gremlinzzz on 2007-07-03
no don;t have any idea about that doesnt happen to me.i have watched movies online where the video and voice timing was off.but not because of full screen mode.

---

### Post by ntlam on 2007-08-19
> **Gremlinzzz said:**
> What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/Re...t=%28codecs%29](https://help.ubuntu.com/community/Re...t=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

Do I have to remove Mplayer before installing SMplayer?

---

### Post by ntlam on 2007-08-19
> **Gremlinzzz said:**
> 
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/Re...t=%28codecs%29](https://help.ubuntu.com/community/Re...t=%28codecs%29)
.

here the result for this command:
bash: [https://help.ubuntu.com/community/Re...t=%28codecs%29:](https://help.ubuntu.com/community/Re...t=%28codecs%29:) No such file or directory

---

### Post by ntlam on 2007-08-19
Yes, I had to remove Mplayer b'cos it was set as default. Now Smplayer works fine. Thanks for instruction.

---

### Post by Gremlinzzz on 2007-09-04
> **ntlam said:**
> here the result for this command:
bash: [https://help.ubuntu.com/community/Re...t=%28codecs%29:](https://help.ubuntu.com/community/Re...t=%28codecs%29:) No such file or directory

[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

