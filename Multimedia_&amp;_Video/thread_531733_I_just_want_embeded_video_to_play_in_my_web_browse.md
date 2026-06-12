---
title: "I just want embeded video to play in my web browser."
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by RockTonic3 on 2007-08-21
Is it so much to ask?  I feel like i've tried anything, and still no video will play in my web browser!  I've spent a few days trying to get it to work in firefox, and eventually thought i'd try opera to see if it would be any easier and it wasn't.  video's do different things depending on what they are, but typically the application just hangs up and i have to force quit.  I have a dual boot and hate having to boot to xp just to see videos online...   can somebody please help?!  i'm not even sure what details to include because i feel like i've been all over the place, so please feel free to ask anything that you think is relevant!

---

### Post by Parms on 2007-08-21
> **RockTonic3 said:**
> Is it so much to ask?  I feel like i've tried anything, and still no video will play in my web browser!  I've spent a few days trying to get it to work in firefox, and eventually thought i'd try opera to see if it would be any easier and it wasn't.  video's do different things depending on what they are, but typically the application just hangs up and i have to force quit.  I have a dual boot and hate having to boot to xp just to see videos online...   can somebody please help?!  i'm not even sure what details to include because i feel like i've been all over the place, so please feel free to ask anything that you think is relevant!

I'm a n00b.. but what I did was installed 32 bit version of firefox and loaded flash player.. I guess the 64bit version will not play videos or you have to do a lot of manually work.

This one didn't work for me (didn't do anything).. but might for you..
[http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+player](http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+player)

This one did work for me... (installed a second 32 bit browser and videos worked and everything)
[http://ubuntuforums.org/showthread.php?t=202537&highlight=flashplayer](http://ubuntuforums.org/showthread.php?t=202537&highlight=flashplayer)

I'm also using 7.04 ubuntu 64bit AMD if that makes a difference.

If those don't work, sorry I just started using linux a couple days ago. On the second link, you can only watch videos from the 32 bit browser. 

Hope that helps.

---

### Post by Gremlinzzz on 2007-08-21
What i have too do to setup mplayer first i uninstall totem  plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

---

### Post by RockTonic3 on 2007-08-22
> 1 Hour Ago 11:30 PM
Gremlinzzz 	
Re: I just want embeded video to play in my web browser.
What i have too do to setup mplayer first i uninstall totem plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/Re...t=%28codecs%29](https://help.ubuntu.com/community/Re...t=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

Okay tried that...  everything went well but still no video.  In an attempt to be more specific...  i'm using a dell xps m170, and it's a 32 bit processor so thanks anyway parms but i don't think that stuff is what i need...  I'm also running beryl but the problem also exists when that isn't running.  

Has anybody had an easier time getting video to work on other browsers?  

thanks for the help so far

---

### Post by RockTonic3 on 2007-08-22
Update:

okay i just discovered that SOME websites will initiate the mplayer plugin before firefox quits on me.  it says it's loading then right before it starts to play, the browser hangs up and in a few seconds offers to force quit...

video's from youtube still do nothing but go black and make the browser hang up, eventually offering to force quit.

the following files are in my /usr/lib/mozilla-firefox/plugins folder

flashplayer.xpt
libflashplayer.so
libunixprintplugin.so
mplayerplug-in.so
playerplug-in.xpt
mplayerplug-in-rm.so
mplayerplug-in-rm.xpt
mplayerplug-in-wmp.so
mplayerplug-in-wmp.xpt
nphelix.so
nphelix.xpt

---

### Post by notoriousdbp on 2007-08-22
right you've got a clash there with the files that start mplayerplug-in-rm which will try to play the same videos as nphelix.so and nphelix.xpt (they are real player plug ins) so firefox, opera etc won't know which ones to use.  it's a case of one or the other.  open a terminal, navigate to your plugin folder and either ```
sudo rm nphelix*
``` to remove the real player versions or ```
sudo rm mplayerplug-in-rm*
``` for the mplayer real video plugins, depending on your preference

---

### Post by notoriousdbp on 2007-08-22
one more thing, have you installed w32codecs?

---

### Post by RockTonic3 on 2007-08-22
alright those files are gone but it's still not working...  i'm pretty sure i have the w32codecs, how can i make sure i did it right?  

:confused:

---

### Post by RockTonic3 on 2007-08-23
okay i'm pretty sure i definitely have the w32codecs installed, because if i do sudo apt-get install w32codecs it tells me i already have the latest version...

but, when i try to play .mpg in mplayer, it fails just like the embeded video in firefox (after a few seconds it hangs up).  is it possible that i have to tell mplayer to use the w32codecs?  if so, how do i do it?

---

### Post by sdowney717 on 2007-08-23
[http://www.cs.cornell.edu/~djm/ubuntu/](http://www.cs.cornell.edu/~djm/ubuntu/)

look thru here for win32 codecs install

w32codecs_20061022-0.0_i386.deb was the file I used to get codecs installed.

---

### Post by RockTonic3 on 2007-08-23
okay tried it all with totem instead of mplayer, still isn't working.  another thing i noticed, though...  depending on where i read, people say to put plugins in either /usr/lib/mozilla/plugins or /usr/lib/mozilla-firefox/plugins.  does it matter if both of these directories exist?  which one should the plugins be in, and if they do both exist should the plugins be in both folders?

one more thing, in firefox > Edit > Preferences > Content, under file types > Manage, it only shows flash stuff (extensions SWF and SPL).  For those guys who embeded video works, do you have more stuff in there?  seems like there should be an action for different types of media here?

---

### Post by kissg1988 on 2007-08-23
> **RockTonic3 said:**
> okay tried it all with totem instead of mplayer, still isn't working.  another thing i noticed, though...  depending on where i read, people say to put plugins in either /usr/lib/mozilla/plugins or /usr/lib/mozilla-firefox/plugins.  does it matter if both of these directories exist?  which one should the plugins be in, and if they do both exist should the plugins be in both folders?

one more thing, in firefox > Edit > Preferences > Content, under file types > Manage, it only shows flash stuff (extensions SWF and SPL).  For those guys who embeded video works, do you have more stuff in there?  seems like there should be an action for different types of media here?

Okay, it seems, you have something messed up with firefox, it's best to reinstall it.

Open a console window and type:
```

sudo apt-get remove firefox

```

Also, remove the mplayer plugin, use totem, instead. It works for me (and it's the default video player in Feisty, as far as I know.)

```

sudo apt-get remove mozilla-mplayer
sudo apt-get install firefox totem-mozilla flashplugin-nonfree

```

Now you have everything to play movies and flash animations in Firefox.

I hope, this will help some!

---

### Post by kissg1988 on 2007-08-23
To answer your questions... the directory /usr/lib/mozilla/plugins/ has only symbolic links to the plugin files, I think, this was left in firefox for compatibility with older applications. So, the plugin files have to be placed into the /usr/lib/mozilla-firefox/plugins/ or /usr/lib/firefox/ directory. It's because the directory /usr/lib/mozilla-firefox/ is a just symlink, that points to /usr/lib/firefox/. So, you can use both of them for putting plugins into it, it doesn't matter which one you choose.

---

### Post by RockTonic3 on 2007-08-24
okay i tried that...  still doesn't work!  this is getting more and more frustrating!  i even went through the firefox/mozilla-firefox directories and deleted all the plugins, thinking i would try to start with as clean of a slate as i could.  

i'm starting to lose hope!  somebody out there must have an answer...

---

### Post by sdowney717 on 2007-08-24
usr/lib/mozilla/plugins is where the true plugins are found.
If an arrow is on the icon, then it is a link to the library.

Type in about:plugins in the web browser and what does it say?

---

### Post by sdowney717 on 2007-08-24
about "colon" plugins, the emoticon gets in the way
here is my list

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.31

    File name: mplayerplug-in.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
audio/x-scpls 	Shoutcast Playlist 	pls 	Yes
Java(TM) Plug-in 1.6.0-b105

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6 	Java 		Yes

---

### Post by sdowney717 on 2007-08-24
if you have real player browser plugin  installed, remove it as mplayer will play real player streams in the browser.
the Browser gets confused.

[http://plugindoc.mozdev.org/linux.html](http://plugindoc.mozdev.org/linux.html)
[http://plugindoc.mozdev.org/linux.html#mplayer](http://plugindoc.mozdev.org/linux.html#mplayer)

you can follow these guidelines. you dont need to compile from source, just use synaptic package manager, uninstall and then reinstall. make sure the plugins are in the right folder.

You can also do a file search (places - search for files) and look for the mplayer plugins, not the arrowed links to see if they are in more than one spot. But I do believe, that the firefox browser self discovers the plugins when they are located in the mozilla directory and writes the links. so you dont have to worry about that. I dont remember creating any links.

---

### Post by sdowney717 on 2007-08-24
here is the genuine flash plugin location
Since these are not in the mozilla directory, it could be the installer writes the links into the firefox directory. Or it self discovers them.
it was just click and play, I did not notice any difficulty using these.

---

### Post by RockTonic3 on 2007-08-24
here is what doing about "colon" plugins gives me:

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Totem Web Browser Plugin 2.18.1

    File name: libtotem-basic-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.1.3

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
Java(TM) Plug-in 1.6.0-b105

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6 	Java 		Yes

```

i will have to try the other stuff later...  time for work!

---

### Post by sdowney717 on 2007-08-24
you need to get rid of lib totem. It cant play any of the proprietary web content. It needs to say mplayer.
So go into synaptic and remove totem - mozilla plugin completely, and install mplayer-plugin. 

Also you should remove totem -gstreamer and install totem xine.

See, the problem is ubuntu is totally setup with free codecs. So to make it function for web content, you have to install closed nonfree 'ugly' codecs.
But at least now, I see why it is not doing anything.

---

### Post by RockTonic3 on 2007-08-24
i hate to say it but that seems to have made things worse!  now when i go to youtube, it freezes before i have the chance to even click on a video to test it out.  it looks like the little flash thing at the top (video's currently being watched) starts to play and firefox freezes before it's done.  

just as an update...  this is what i get now from about : plugins

```

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.31

    File name: mplayerplug-in.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
Java(TM) Plug-in 1.6.0-b105

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6 	Java 		Yes
mplayerplug-in 3.31

    File name: mplayerplug-in.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File
```

and the following is the contents of my /usr/lib/mozilla/plugins folder:

libjavaplugin.so
mplayerplug-in-dvx.so
mplayerplug-in-dvx.xpt
mplayerplug-in-qt.so
mplayerplug-in-qt.xpt
mplayerplug-in-rm.so
mplayerplug-in-rm.xpt
mplayerplug-in.so
mplayerplug-in-wmp.so
mplayerplug-in-wmp.xpt
mplayerplug-in.xpt

only one of which, libjavaplugin.so, is a symlink.  

in usr/lib/firefox/plugins, the same files are found, but all of them are simlinks (linking to /usr/lib/mozilla/plugins) except for flashplayer.xpt and libflashplayer.so.  these files aren't symlinks and are only found in the firefox folder, not the mozilla folder...  when i tried to move them to the mozilla folder, i went to youtube and found that firefox thought flash was no longer installed (the 'plugin required' icon showed up instead of flash stuff), so i moved the files back to the firefox directory.  

how complicated!  sorry!

---

### Post by sdowney717 on 2007-08-24
curious to know if you can goto cbsnews.com and watch the online video content. I can.

Also, If you get it working and full screen news clips in mplayer loose a/v sync, you can edit this file

/etc/mplayer/mplayer.conf and set this to 'yes'

# Drop frames to preserve audio/video sync.
framedrop = yes


also, can you watch the cnn video? They use the flash plugin

also here are my files in that folder. 13 files, flash files are symbolic links

---

### Post by RockTonic3 on 2007-08-25
no and no.  cbsnews.com tells me i need to install windows media player, and cnn crashes firefox just like everything else.

---

### Post by RockTonic3 on 2007-08-25
here's a screen shot of my /usr/lib/mozilla/plugins directory

---

### Post by sdowney717 on 2007-08-25
the truth is it can be done and it does work even if it is not working for some reason for your situation.

Are you running feisty fawn ubuntu?
What version of firefox?
what are your software sources?, I uploaded a screen shot of mine.

When I first set this up in edgy, an older versions of ubuntu and firefox, you had to hand off mms streaming protocols by setting up certain criteria in about:config for mplayer to work.

seriously, perhaps this is what you need to do as well.
you right click and add these 2 user strings to firefox configuartion exactly as the picture shows they should be,.

rtsp://eyenet.rmod.llnwd.net/a134/o1/cbsnews/2007/08/20/video3185820.rm
this link is a realplayer file link. Actually for me it launches totem and I dont hear sound but do see the video


[http://www.cbsnews.com/stories/2007/08/20/storm/main3183764.shtml](http://www.cbsnews.com/stories/2007/08/20/storm/main3183764.shtml)
this is the link for mplayer using a real player stream at cbsnews

---

### Post by sdowney717 on 2007-08-25
[http://images.apple.com/movies/miramax/becoming_jane/becoming_jane-tlr1_h480.mov](http://images.apple.com/movies/miramax/becoming_jane/becoming_jane-tlr1_h480.mov)

here is a link which opens up mplayer in my browser

there is also a VLC player plugin that you can try out. I have not tried it myself, but this means I suppose uninstalling mplayer plugin befor you install vlc plugin.

you can also try here
[http://www.getautomatix.com/](http://www.getautomatix.com/)

from this thread
[http://ubuntuforums.org/showthread.php?t=246649&highlight=totem+rtsp](http://ubuntuforums.org/showthread.php?t=246649&highlight=totem+rtsp)

---

### Post by xoron on 2007-08-27
the easiest thing to do to get it to work is to

get easyubuntu (full of useful tools) ... from their website (google it)... it is a deb file and so you will find it easy to install.

then jus click on what you want and install it

easiest thing ever

and if you wanna have a player i just use vlc player it also plays steams like embedded divx media (but of course you can play the embedded file in the site itself)

to get VLC jus type

$ sudo apt-get-install vlc

enjoy

---

### Post by xoron on 2007-08-27
the easiest thing to do to get it to work is to

get easyubuntu (full of useful tools) ... from their website (google it)... it is a deb file and so you will find it easy to install.

then jus click on what you want and install it

easiest thing ever

and if you wanna have a player i just use vlc player it also plays steams like embedded divx media (but of course you can play the embedded file in the site itself)

to get VLC jus type

$ sudo apt-get-install vlc

enjoy

---

### Post by RockTonic3 on 2007-08-29
i'm running ubuntu 7.04, firefox version 2.0.0.6.  My software sources, .mms (about:config), and mplayer plugin options are identical to yours.  

thanks anyway xoron, but easyubuntu doesn't work and i haven't had luck with those kinds of programs in the past (automatix) so i don't think i'd like to try to get it to work.  

 i even went through and uninstalled every movie player/codec/internet browser package i could find in synaptic to try starting over...  didn't work obviously 

sorry this reply took a bit longer i'm back at college now and am getting busy!  thanks for the continued help.

---

### Post by kissg1988 on 2007-09-03
I don't know what kind of video adapter do you have, but maybe this workaround will help you:

[http://ubuntuforums.org/showthread.php?t=541362](http://ubuntuforums.org/showthread.php?t=541362)

In short, you have to disable the DRI module in xorg.conf (optionally, add an extra option to the Device section of your video card, to fully disable direct rendering.)

---

### Post by RockTonic3 on 2007-09-03
i have an nvidia GTX 7800 go 

the "load dri" wasn't included to disable

---

### Post by kissg1988 on 2007-09-06
I think, you should give it a try, anyway. Just to test if it works for you or not.

---

### Post by RockTonic3 on 2007-09-06
Sorry, I guess I wasn't very clear.

I did look through my xorg, and there was nothing about DRI in the document, so there was nothing for me to hash out.

---

### Post by RockTonic3 on 2007-09-14
well i reinstalled ubuntu and it works perfectly now, installation was point and click like it should have been in the first place!  i must have screwed something up at some point, thanks for the help though.

---

### Post by kkolev on 2007-09-16
For those that have a similar problem and don't want to reinstall ubuntu in order to fix it they could give [this]("https://addons.mozilla.org/en-US/firefox/addon/446") FireFox extension a try. It helps configuring all kinds of stuff.

I have both the vlc and the mplayer plugins and I can switch them without having to replace the current installed. \\:D/

NJY

---

