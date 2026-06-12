---
title: "BBC iplayer radio &quot;listen again&quot; on 10.04"
date: 2010-05-26
forum: Multimedia Software
---

### Post by Janeleaper on 2010-05-26
I live outside the UK so can only use the BBC iplayer for BBC radio stations (video is blocked for people outside the UK).  

Previously I could play both "live" radio and "listen again" programmes.  This was in 7.10, 8.04, 8.10 and 9.04.  However, after I upgraded to 9.10 the "listen again" programmes would not play.  

9.10 was very glitchy and unstable for me on both the machines I upgraded  (both are Dell Inspiron 530). One of the machines has no sound at all. The other machine eventually failed to boot.  So, I thought maybe the BBC "listen again" facility would work on 10.04.

On one machine, I've just reinstalled 9.10 from disc and then upgraded to 10.04.  The installation looks good, with no glitches, except that I still can't get BBC "listen again" programmes to play. I've just tried the multimedia comprehensive troubleshooting sticky advice, but it had no effect.

---

### Post by gandaran on 2010-05-26
> **Janeleaper said:**
> I live outside the UK so can only use the BBC iplayer for BBC radio stations (video is blocked for people outside the UK).  

Previously I could play both "live" radio and "listen again" programmes.  This was in 7.10, 8.04, 8.10 and 9.04.  However, after I upgraded to 9.10 the "listen again" programmes would not play.  

9.10 was very glitchy and unstable for me on both the machines I upgraded  (both are Dell Inspiron 530). One of the machines has no sound at all. The other machine eventually failed to boot.  So, I thought maybe the BBC "listen again" facility would work on 10.04.

On one machine, I've just reinstalled 9.10 from disc and then upgraded to 10.04.  The installation looks good, with no glitches, except that I still can't get BBC "listen again" programmes to play. I've just tried the multimedia comprehensive troubleshooting sticky advice, but it had no effect.

which media player plugin you have installed? the default totem plugin?
well totem doesn't work well with the bbc site, try installing another player plugin or install realplayer.

---

### Post by ron999 on 2010-05-26
@Janeleaper
It's just the Adobe flash player addon for Firefox that's needed.

---

### Post by Janeleaper on 2010-05-26
Gandaran: Gnome Player (plus Gecko).  

Ron 999: Can you be more specific?  There is no Adobe Flash Add On listed on the Mozilla page.

---

### Post by Janeleaper on 2010-05-26
To be clear: I do have Adobe Flash Plug-in version 10.0.45.2-1 Lucid installed. This is not the problem.

---

### Post by ron999 on 2010-05-26
> **Janeleaper said:**
> To be clear: I do have Adobe Flash Plug-in version 10.0.45.2-1 Lucid installed.

That's the one.
So you have a different problem.

---

### Post by gandaran on 2010-05-26
> **Janeleaper said:**
> Gandaran: Gnome Player (plus Gecko).  

Ron 999: Can you be more specific?  There is no Adobe Flash Add On listed on the Mozilla page.
gecko-mediaplayer? you have this package installed? this is the plugin for firefox and should work quite well with bbc? if it doesn't try disabling or even removing the totem plugin.

just tried the BBC radio service and it works both ways, either you choose the flash player or listen in a pop out player, works perfectly either with flash or gecko player!

---

### Post by Janeleaper on 2010-05-26
Yes I have gecko-mediaplayer.  

Following your suggestion I completely removed Totem and restarted the computer.  That did not help. 

I'm going to reinstall Totem because I can use it to listen to the Beebotron service.  I find the quality of beebotron variable -- sometimes there is uneven streaming, but it is better than nothing.

I went through all these possible solutions when I had the same problem with 9.10, with the same lack of success.  It is baffling.

---

### Post by gandaran on 2010-05-26
the w32codecs package from the medibuntu repository you have them installed?

---

### Post by Janeleaper on 2010-05-26
Yes

---

### Post by gandaran on 2010-05-26
then all I can think is something must be wrong with your firefox settings
type this code in the firefox url bar and post the full results
```
about:plugins
```

---

### Post by Janeleaper on 2010-05-26
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File: nphelix.so
    Version: 
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.5174 built with gcc 4.1.2 on Oct 6 2009

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
DivX Browser Plug-In

    File: gecko-mediaplayer-dvx.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
QuickTime Plug-in 7.6.4

    File: gecko-mediaplayer-qt.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
RealPlayer 9

    File: gecko-mediaplayer-rm.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plug-in

    File: gecko-mediaplayer-wmp.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-asx 	Media Files 	asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
application/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in is now gecko-mediaplayer 0.9.9.2

    File: gecko-mediaplayer.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
audio/x-mpegurl 	MPEG Playlist 	m3u 	Yes
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mp4 	MPEG 4 audio 	mp4 	Yes
audio/x-mp4 	MPEG 4 audio 	mp4 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
video/x-m4v 	MPEG 4 Video 	m4v 	Yes
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg,oga,ogm 	Yes
application/ogg 	Ogg Vorbis Media 	ogg,oga,ogm 	Yes
audio/x-ogg 	Ogg Vorbis Audio 	ogg,oga 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg,oga 	Yes
video/x-ogg 	Ogg Vorbis Video 	ogg,ogm 	Yes
video/ogg 	Ogg Vorbis Video 	ogg,ogm 	Yes
application/x-vlc-plugin 	VLC plug-in 	vlc 	Yes
application/x-google-vlc-plugin 	Google VLC plug-in 		Yes
audio/flac 	FLAC Audio 	flac 	Yes
audio/x-flac 	FLAC Audio 	flac 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/x-flv 	Flash Video 	flv 	Yes
video/flv 	Flash Video 	flv 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
audio/x-matroska 	Matroska Audio 	mka 	Yes
video/x-matroska 	Matroska Video 	mkv 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/x-aiff 	AIFF Audio 	aif 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
audio/midi 	MIDI Audio 	mid,midi,kar 	Yes
audio/x-scpls 	Shoutcast Playlist 	pls 	Yes
video/x-mng 	Multiple-Image Network Graphics 	mng 	Yes
IcedTea NPR Web Browser Plugin (using IcedTea6 1.8 (6b18-1.8-0ubuntu1))

    File: IcedTeaPlugin.so
    Version: 
    The IcedTea NPR Web Browser Plugin (using IcedTea6 1.8 (6b18-1.8-0ubuntu1)) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_18 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_18 	IcedTea 	class,jar 	Yes
Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
iTunes Application Detector

    File: librhythmbox-itms-detection-plugin.so
    Version: 
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes

---

### Post by gandaran on 2010-05-26
everything looks okay! 
do you connect to internet using a proxy server?
how about firefox addons like flashblock, do you have it installed?

well I'm sorry cant help you.

---

### Post by Janeleaper on 2010-05-26
That's OK.  Thanks for trying.

Like I said, I had this problem with 9.10 and went through all the possible solutions then.  Because my 9.10 installation was unstable I hoped that a fresh install by cd and then updating to 10.04 would solve the problem, but it hasn't done so.

It seemed worth posting the problem again, just in case someone came up with something new.

---

### Post by Rumpty on 2010-05-26
I'm in NZ. Just tried the BBC iplayer on the World Service and Radio3, and it goes like a charm. In Firefox. Can I help?

I don't have w32 codecs installed, and generally keep the installed "extras", codecs, players etc to a minimum.

---

### Post by Janeleaper on 2010-05-26
I don't know if you can help or not.  Are you listening to listen again programmes or live radio?

---

### Post by Rumpty on 2010-05-26
Live radio. I didn't try Listen again

---

### Post by Janeleaper on 2010-05-26
Well, it is only listen again that I have a problem with.

---

### Post by Rumpty on 2010-05-26
Only Listen Again - I may have missed that point. Can you give me a link to try? There are many formats used.

---

### Post by Janeleaper on 2010-05-26
It is a bit difficult to give you a link to it -- listen again is any programme which has already been played live.  The programmes remain available for 7 days.  Go to the schedule for one of the BBC radio stations and choose a programme that has already been played.

---

### Post by Janeleaper on 2010-05-26
For example: [http://www.bbc.co.uk/programmes/b00sf94r](http://www.bbc.co.uk/programmes/b00sf94r)

---

### Post by Rumpty on 2010-05-27
Yes, that one plays fine.

Make sure that, in Pulse Audio Volume Control, the faders in the Output Devices and the Playback tabs are turned up.

If it still doesn't work, install gstreamer0.10-plugins-bad, plus all the libs etc that will install with it, using Synaptic Package manager.

---

### Post by Janeleaper on 2010-05-27
How do I get into Pulse audio volume control?

---

### Post by Janeleaper on 2010-05-27
And why would a volume control setting only affect listen again programmes and produce the error message "content does not seem to be working", but not live radio? I don't have any sound problems apart from listen again programmes not playing.  I can play music, live radio, etc etc.

---

### Post by Janeleaper on 2010-05-27
I've checked and gstreamer 0.10 is already installed.

---

### Post by mc4man on 2010-05-27
Other than the flashplayer plugin, (which you have), this has nothing to do with any add. plugins, codecs, ect.

You could try setting up a new user, logging in and seeing if 'listen again' works there, if so then it's something in your user settings

Try  going to ~/.macromedia/Flash_Player/#SharedObjects/XXXXXXXX/www.bbc.co.uk/emp, delete the .sol's inside and try again.

(you mentioned w32codecs which are irrelevant here but just to confirm this is a 32 bit install?

---

### Post by Janeleaper on 2010-05-27
Mc4man you are some kind of genius.  I logged on as guest and low and behold listen again works.

But - I'm not sure what you are telling me to do next. I'm a noob.  When you say go to, do you mean in terminal?

---

### Post by mc4man on 2010-05-27
> Try going to ~/.macromedia/Flash_Player/#SharedObjects/XXXXXXXX/www.bbc.co.uk/emp, delete the .sol's inside and try again.

Open up your home folder -> View -> click on "Show Hidden Files"
Then scroll down and find the .macromedia folder and follow the path shown above 
(XXXXXXXX is a series of letters/numbers 

If no go then  just delete (move to trash) the whole .macromedia folder itself

~/ = home folder
.<folder or file name> = hidden file or folder

---

### Post by Janeleaper on 2010-05-27
No this does not work.  I tried all the permutations, finally deleted macromedia file, deleted browser history, restarted computer, but I still get "the content does not appear to be working..." message.

---

### Post by mc4man on 2010-05-27
Well it's something in your user setting's, ect. (your guest user is using the same plugin
I'd probably try a different browser and see 
Chromium browser would be a good choice, either from ubuntu repo or the [daily build ppa]("https://launchpad.net/~chromium-daily/+archive/ppa")

If so I'd initially decline to import settings from other browser (firefox) when first running.

(if inclined at some point for another 'fresh install' then don't go the upgrade route - if you want 10.04 then install 10.04

---

### Post by Janeleaper on 2010-05-27
I tried Chrome - no effect, and weirdly, I tried logging in as Guest again,but it now won't play listen again now, even though it would the first time.  

I give up. I've sent off for the 10.04 cd and when it arrives I'll try a fresh install on our other computer which is running a rather unstable 9.10.  It will be interesting to see if that will play BBC listen again.

But thanks anyway.

---

### Post by Rumpty on 2010-05-27
When all else fails, you should find that if you enter that web address that you gave as a test into the address bar in Firefox, it should work. That is probably the most direct way of getting it going.

---

