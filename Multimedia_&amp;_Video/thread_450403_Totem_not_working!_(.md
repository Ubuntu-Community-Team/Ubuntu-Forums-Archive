---
title: "Totem not working! :("
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by Zdravko on 2007-05-21
I have an *.avi file and want to play it. I downloaded the required codec. Even after that, when I double click the file Totem appears for a second and then disappears. Why? How to fix this?

---

### Post by Malta paul on 2007-05-21
I don't know why totem disappears. I use the xine-lib version of Totem and it will play most formates. My favorite is VLC. down load using > application>Add/Remove, then search VLC.
Hope is is of some help :)

---

### Post by Zdravko on 2007-05-21
VLC does the same thing.

---

### Post by Reishka on 2007-07-09
I'm having this issue as well. Brand new install of Ubuntu, codecs downloaded, etc. 

Totem disappears, as well as VLC, whenever I'm attempting to view a movie file. I've been playing all my movies through Democracy TV as it's the only thing that won't disappear.

---

### Post by kelvin spratt on 2007-07-09
i use totem-zine i would suggest you try totem-zine, and also Kaffiene it does a self check on first startup and will tell you if you need to install more codecs  and the zines play virtually every format for me,

---

### Post by Gremlinzzz on 2007-07-09
Go to synaptic package manager and uninstall totem plugin
[http://smplayer.sourceforge.net/linux/index_en.php](http://smplayer.sourceforge.net/linux/index_en.php)
click download get the ubuntu deb package easy to install
go to synaptic again and install mplayer plugin.
get win32 codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
check mplayer plugin here
[http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
If screen gray but i dont think it will be right click on screen click configure choose x11 for video and a alsa audio.to play divx movies online add these commands to terminal
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

---

### Post by Bablefish on 2007-07-09
As often as this comes up someone (not me) should post this as a sticky. After going through this same problem and nearly giving up more than once, let me tell you there is a solution and the problem is not with Totem it's with the codecs you need. You will not get them through standard sources...but there is no need to panic it's simple.

1) install Medibuntu  (i reccomend going to there offical site and using the terminal installl, I found it was easier...all you need to do is copy and paste right into the Terminal.

2) Get Automatrix, you can find it here [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
Download, install it and run it. Make sure your connected to the internet. This will give you ALL your codecs.

3) Go to Add Remove and look for the Kaffiene Player and get it. I find it actually works better when you play DVDs

This should fix your prolem, just remember nearly everyone running Linux can't play Quicktime files

---

### Post by Reishka on 2007-07-09
As I stated -- my problem is not with codecs. I've already downloaded all the codecs, already run Automatrix. I've tried totem-xine, I've tried Kaffiene. I have Medibuntu. I'm still getting the issue of every program disappearing except for Democracy. I know it's not a problem just with totem alone. 

I've made *some* headway. I've gotten MPlayer to run video files after fiddling with the drivers (Right Click > Prefrences > Video). But that's the only thing I've gotten to work. Still don't know what's up.

---

