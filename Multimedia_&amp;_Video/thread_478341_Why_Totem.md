---
title: "Why Totem"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by Gremlinzzz on 2007-06-19
Why is Totem the default player for ubuntu. I always have to remove it and its plugin.Then install Mplayer.Just wondering who decided totem was better than mplayer and why?Would be nice to have mplayer configured by default.

---

### Post by flossgeek on 2007-06-19
Because Totem is the main Video Player for the GNOME Desktop. Also its a nice simple intuitive player, that works well if you have codecs installed. Theres nothing wrong with having more than one media player though, as you say just install MPlayer as you prefer it.

---

### Post by Gremlinzzz on 2007-06-19
My point is it shoud not be the main Video Player for the GNOME Desktop.I take it your using totem.well do this test of its web plugin. google' bar cam and click hogs breath bar checkout there live streaming video chances are you will get a black screen with totem.I get the video and choice of full screen with mplayers plugin.plus thanks to this forum i can watch divxs movies with mplayer plugin.:D

---

### Post by justin whitaker on 2007-06-19
> **Gremlinzzz said:**
> My point is it shoud not be the main Video Player for the GNOME Desktop.I take it your using totem.well do this test of its web plugin. google' bar cam and click hogs breath bar checkout there live streaming video chances are you will get a black screen with totem.I get the video and choice of full screen with mplayers plugin.plus thanks to this forum i can watch divxs movies with mplayer plugin.:D

That doesn't negate the prior comment. Totem is the official media player of the Gnome environment, and Ubuntu has always shipped with it by default. With all the codecs installed, it works well, and for what you are talking about, Live Video Streaming, most people would use something else anyway. Totem is more designed for the "I have this file I want to play" user.

So, add Mplayer, the Firefox plugin, and go to it. In terms of getting the broadest media bang for the buck, the combination of Totem and Rhythmbox is pretty good. 

Although I prefer Amarok and Mplayer. ;)

---

### Post by Gremlinzzz on 2007-06-19
For the "I have this file I want to play" you should give smplayer a try.Go ahead try it.chances are you will remove totem i did.
[http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

---

### Post by flossgeek on 2007-06-20
Another point of call is MPlayer lacks the GNOME HIG(Human Interface Guidelines), I am not putting Mplayer down it is a good application too. Totem by default is also based on gstreamer plugins by default, which hasn't quite got the full support yet, but its certainly better than it ever was. However you can use the library XINE as a backend to totem which means totem will play more codecs.

If you like VLC install it, if you like Mplayer install it, you are free to do as you choose ;)

---

### Post by timcredible on 2007-06-20
> **justin whitaker said:**
> . With all the codecs installed, it works well

no, it doesn't.  videos that play smoothly with mplayer play choppy in totem or don't play at all.

---

### Post by RomeReactor on 2007-06-20
> **timcredible said:**
> no, it doesn't.  videos that play smoothly with mplayer play choppy in totem or don't play at all.

Hi. Maybe you're missing some codecs; do you have totem-xine or totem-gstreamer? If you have xine:
```
sudo apt-get install libxine1 libxine1-ffmpeg libxine-extracodecs
```

---

### Post by Gremlinzzz on 2007-06-20
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer  [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)  plays my dvd movies.
Then i install mplayer plugin  using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose  X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

---

### Post by Bablefish on 2007-06-20
I would also install Automatrix to get even more codecs

---

### Post by Gremlinzzz on 2007-06-20
I never tried automatrix but i do use the ubuntu guide to get and add stuff
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
the other thing about mplayer is it has skins but none of them have any effect on the mplayer plugin.
Does anyone know if theres seperate skins for the mplayer plugin.or how to create and install one?

---

### Post by Gremlinzzz on 2007-07-05
Still wondering how many of you use totem and is it limited.i found it to be it's plugin doesn]t work on some sites that mplayer plugin does.on example would be 
[http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
try totem on this site. bet it don.t work.so who uses totem and why.

---

### Post by stchman on 2007-07-05
> **Gremlinzzz said:**
> Why is Totem the default player for ubuntu. I always have to remove it and its plugin.Then install Mplayer.Just wondering who decided totem was better than mplayer and why?Would be nice to have mplayer configured by default.

Totem is installed on my system.  I personally use VLC as I feel it has more functionality.

---

### Post by Gremlinzzz on 2007-07-10
Yeah totems on your system but you use VLC does anyone use totem ?
:guitar:

---

### Post by Gremlinzzz on 2007-07-14
Nobody uses totem so write your ubuntu representative and demand it be replaced with mplayer.
:lolflag:

---

### Post by Major_Kong on 2007-07-14
> **Gremlinzzz said:**
> Yeah totems on your system but you use VLC does anyone use totem ?
:guitar:

I use totem... at least when it's something "simple". Other than that it's mplayer. I would use mplayer all the time if it had a better gui. (SMPlayer isn't quite there yet)

---

### Post by dxdemetriou on 2007-07-14
Let's tell a story about the problem did totem for me:
The problem started from [http://elisa.fluendo.com/](http://elisa.fluendo.com/), when I tried to play the ogg theora video.
After a lot of troubles described [http://sourceforge.net/forum/forum.php?thread_id=1774739&forum_id=692299](http://sourceforge.net/forum/forum.php?thread_id=1774739&forum_id=692299) , I don't know really if it's totem's problem, but it crash my whole pc when I try to play any ogg theora. It don't work the ctrl-alt-backspace, neither ctrl-alt-f1, but if I press the power button it makes shutdown correctly. Maybe is not from totem the problem, but why mplayer and vlc works correctly with ogg theora?
I have wrote them somehow mixed, sorry but I tired from all that crashes.

edit: It crashes also with gmplayer if it uses the xv but not with gl2

---

### Post by justinjstark on 2007-07-14
Totem uses the gstreamer backend by default.  Gstreamer is a fairly recent framework for multimedia and does have some bugs and unsupported codecs.  Nonetheless, it is the future of multimedia in the gnome desktop environment.  Eventually, all of your encoding, transcoding, playing, and recording will be handled by gstreamer.  For instance, sound juicer rips and encodes using the gstreamer framework.  Also, newer applications like kungfu rip and encode dvds using gstreamer.

On the bright side, most of the bugs that I have filed and subscribed to in launchpad regarding gstreamer codec support have recently been fixed.  Expect great things come gutsy.

Why is totem default?
1) As stated, totem is the default media player in gnome.
2) Totem fits nicely with the gnome interface guidelines.
3) Totem uses gstreamer while mplayer and vlc do not.
4) The totem UI is gtk2.
...

---

### Post by lsutiger on 2007-07-15
I will just say this...mplayer works better for internet play. I use VLC for local play, as it will play anything you throw at it, but the internet plugin not so good. The great thing about Linux is that you have choices! And that in itself is freedom!!! God bless Linus torvald!
JOIN THE FREE SOFTWARE REVOLUTION!!!! :)
PS - GNU rocks!

---

### Post by Dead_$partan on 2007-07-16
Isnt there one application that can be installed and has all the codecs installed for audio and video?

I aint too fussed about having 2 or 3 different media players, I just wanna open a single multimedia application and be able to listen to audio or watch an xvid,divx,avi,mp4,wmi,mp3 or whatever file.

Thats one reason I like Windows Media Player, always works fine for me in widnows and i just install the codecs i need, double click on the multimedia file, WMP opens up and I watch or listen to it, easy.

I looked at Elisa but it looks like you gotta pay for the codecs.

---

### Post by justinjstark on 2007-07-16
> **Dead_$partan said:**
> Isnt there one application that can be installed and has all the codecs installed for audio and video?

I aint too fussed about having 2 or 3 different media players, I just wanna open a single multimedia application and be able to listen to audio or watch an xvid,divx,avi,mp4,wmi,mp3 or whatever file.

Thats one reason I like Windows Media Player, always works fine for me in widnows and i just install the codecs i need, double click on the multimedia file, WMP opens up and I watch or listen to it, easy.

I looked at Elisa but it looks like you gotta pay for the codecs.

Totem-xine will play pretty much anything as long as you install the xine codecs.

---

### Post by Gremlinzzz on 2007-07-16
> **Gremlinzzz said:**
> What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer  [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)  plays my dvd movies.
Then i install mplayer plugin  using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose  X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

I believe that smplayer and the mplayer plugin is about the best there is for linux systems
:guitar:

---

### Post by Gremlinzzz on 2007-08-03
:lolflag:

---

### Post by shirilover on 2007-08-03
> **Major_Kong said:**
> I would use mplayer all the time if it had a better gui. (SMPlayer isn't quite there yet)

If you don't like the GUI for MPlayer, why not create your own.
It's only a few png images and skin file that details the placement of the images.

---

### Post by Gremlinzzz on 2007-08-08
:guitar:

---

### Post by Major_Kong on 2007-08-08
> **shirilover said:**
> If you don't like the GUI for MPlayer, why not create your own.
It's only a few png images and skin file that details the placement of the images.

I'm trying to create one for mencoder first, or at least as soon as i find the time and will power.

I find the lack of a somewhat complete gui for video encoding (using mencoder) more disturbing...

---

### Post by AnRa on 2007-08-08
> **Major_Kong said:**
> I would use mplayer all the time if it had a better gui.You may try [GNOME MPlayer](http://www.getdeb.net/release.php?id=1171). ;)

---

### Post by Gremlinzzz on 2007-08-10
Ya cant please everyone but smplayer works plays my dvd s and gives me no problems.Think ill stay with what works.:guitar:

---

### Post by arthell on 2007-09-26
I went with the media player that offered the easiest answer to what I needed, which is Totem so far.

I started with mplayer, and after a few minutes wasn't able to get a networked server to show up as a valid source to play media off of. Started up Totem which detected the server and played the media fine.

Still haven't run into an issue with Totem yet, but then again I don't use online stations, etc.

---

