---
title: "Is anyone able to get their plugins to play media on the web flawlessly in Firefox?"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by TWO on 2008-01-05
Playing media from the web flawlessly has been something I've been unable to do since my switch over to Ubuntu. 

I have the restricted repositories enabled and have downloaded every codec and every plugin possible. 

I am also in a constant juggle between VLC, Mplayer and Totem. 

Up until now, the plugins from Mozilla and VLC haven't worked one bit. 

As far as I remember, I use to have limited success with Mplayer but these days it just fails every time. If I use the MediaConnectivity plugin for Firefox and have Mplayer assigned as a program, on opening I am presented with an error message and the media doesn't play.

When VLC is assigned to the plugin, I end up with partially loaded streams and often poor sound quality.

Totem seems to be able handle streams that require Windows Media Player but it isn't without its faults. 

The annoying thing about this is that I have every codec and yet no single program seems to be able to handle streams properly. 

Does anyone experience the same problems and if not, how have you set things up so that everything works correctly?

Thanks in advance

TWO

---

### Post by liquid77 on 2008-01-05
Try swiftweasel and automatix to install the plugins usually used including those for playing media from the web...It works for me...

---

### Post by cor2y on 2008-01-05
use the mplayer mozilla plugin (found in synaptic) for all streaming media except flash, remove totem and vlc plugins and restart firefox if its opera be sure to create a symbolic  link to the mplayer mozilla plugin.
For flash you have the choice of either gnash or the adobe plugin but not both at once ,beware that gnash cannot handle newer flash objects/media and adobe's plugin has been known to freeze firefox on some websites since its not up to par with the windows version of the plugin.
I have found that both totem and vlc's plugins work on and off depending on the site (yahoo for instance doesn't seem to work with the totem plugin) however where the mplayer plugin shines is with its ability to be customized.From how much data to cache to whether or not you can save the media stream, something the totem plugin lacks.

---

### Post by ugm6hr on 2008-01-05
MediaPlayerConnectivity works quite well in Firefox to select the appropriate player.

I use realplayer for realmedia, since none of the other players copes properly:
[http://ubuntuforums.org/showpost.php?p=4036593&postcount=5](http://ubuntuforums.org/showpost.php?p=4036593&postcount=5)

Quicktime is not as well dealt with as in Windows / Macs, and I've found that I can only get them to play flawlessly in Mplayer.  However, unlike in Windows etc, you can't pause and rewind the stream.

Flash works just fine with the flash-plugin non-free.  Although it does occasionally cause Firefox to crash after playing the stream.

As for Windows Media streaming, DRM-loaded streams are a non-starter.  And there aren't many non-DRM sites that use .wmv that I use, except BBC (but they have realmedia option).  VLC plays with the best sound (and with no codecs), but seems to put a green bar across the top of the picture.  Mplayer has a clearer picture, but has crackly sound.

---

### Post by eye208 on 2008-01-05
> **TWO said:**
> Does anyone experience the same problems and if not, how have you set things up so that everything works correctly?
Totem works fine for almost everything here. I did not install all the GStreamer plugins at once but on demand. No problems so far. I can even play video streams in Second Life through GStreamer.

Can you point us to the URL of a stream that doesn't work for you?

---

### Post by rainwalker on 2008-01-05
I just installed the restricted extras, the gstreamer plugins, etc. and the totem-mozilla plugin, and it all works for me. 
The VLC plugin never worked very well for me either, and I've never tried the Mplayer plugin.

---

### Post by steveneddy on 2008-01-05
The key is to pick a multi-media player plugin and stick with it.

Firefox will complain if you install totem, VLC and mplayer at the same time.

I just install VLC plugin and be done with it.

---

### Post by rainwalker on 2008-01-05
> **steveneddy said:**
> The key is to pick a multi-media player plugin and stick with it.

Firefox will complain if you install totem, VLC and mplayer at the same time.

I just install VLC plugin and be done with it.

The VLC plugin doesn't actually work that well, unfortunately. At least, not for me :?

---

### Post by steveneddy on 2008-01-05
> **rainwalker said:**
> The VLC plugin doesn't actually work that well, unfortunately. At least, not for me :?

Hey dude! You're from Richardson? I live in Ft. Worth!

You are the closest person that I know of that uses Ubuntu.

OK - I lied - here are my Firefox plugins:

**Shockwave Flash** - I think through gnash - 
file: npwrapper.libflashplayer.so

**Totem Web Browser Plugin 2.20.0**
file: libtotem-basic-plugin.so

**Windows Media Player Plug-in 10 (compatible; Totem)**
file: libtotem-gmp-plugin.so
[B]
DivX® Web Player[/B]
file: libtotem-mully-plugin.so
[B]
QuickTime Plug-in 7.2.0[/B]
file: libtotem-narrowspace-plugin.so


I think I got these when I installed w64-codecs.

I run 64 bit Gutsy.

:popcorn:

---

### Post by rainwalker on 2008-01-05
> **steveneddy said:**
> Hey dude! You're from Richardson? I live in Ft. Worth!

You are the closest person that I know of that uses Ubuntu.


Cool! I'm in the process of converting 2 people; one from OS X (at least to dual-boot) and one who uses Windows.

---

### Post by steveneddy on 2008-01-05
> **steveneddy said:**
> Hey dude! You're from Richardson? I live in Ft. Worth!

You are the closest person that I know of that uses Ubuntu.

OK - I lied - here are my Firefox plugins:

**Shockwave Flash** - I think through gnash - 
file: npwrapper.libflashplayer.so

**Totem Web Browser Plugin 2.20.0**
file: libtotem-basic-plugin.so

**Windows Media Player Plug-in 10 (compatible; Totem)**
file: libtotem-gmp-plugin.so
[B]
DivX® Web Player[/B]
file: libtotem-mully-plugin.so
[B]
QuickTime Plug-in 7.2.0[/B]
file: libtotem-narrowspace-plugin.so


I think I got these when I installed w64-codecs.

I run 64 bit Gutsy.

:popcorn:

I have used VLC plugins before and I liked them.

---

### Post by bliffle on 2008-01-05
Does VLC plugin play Flash videos? Flash 9?

---

### Post by rainwalker on 2008-01-05
> **bliffle said:**
> Does VLC plugin play Flash videos? Flash 9?

The only thing that can play Flash anything is the Flash player and Gnash. The problem is, Gnash isn't yet up to the level that Flash is, and there's no non-beta Flash 9 for Linux. They finally got around to updating us to Flash 8, but now the installer is broken and there's no official fix.

---

### Post by eye208 on 2008-01-06
> **bliffle said:**
> Does VLC plugin play Flash videos? Flash 9?
It plays Flash video (.flv) but not Flash applets (.swf).

> **rainwalker said:**
> The problem is, Gnash isn't yet up to the level that Flash is, and there's no non-beta Flash 9 for Linux.
I'm running Flash 9.0 r115 here. What makes you think it's beta?

---

### Post by rainwalker on 2008-01-06
> **eye208 said:**
> II'm running Flash 9.0 r115 here. What makes you think it's beta?

Really? Last time I checked the download page for Flash 9 for Linux, it was beta.
How well does it work? Is it any better than Flash 8 (or whatever version the flashplugin-nonfree package installed before it broke)?

---

### Post by TWO on 2008-01-06
> **eye208 said:**
> Can you point us to the URL of a stream that doesn't work for you?

eye208, I think somebody mentioned the BBC website. That's a good place to start as the sound quality is poor for me on the wmv stream and I don't think I've ever had success with real player. The last time I had it installed on here, the program wouldn't start.

---

### Post by TWO on 2008-01-06
> **rainwalker said:**
> The VLC plugin doesn't actually work that well, unfortunately. At least, not for me :?

I have to agree with rainwalker here, VLC plugin hasn't done the job for me either. I'll be honest with you, I'm quite disappointed with VLC in Ubuntu. It was a breath of fresh air back in windows, but it just doesn't seem to be able to handle things well on the internet for me...:(

---

### Post by TWO on 2008-01-06
> **ugm6hr said:**
> MediaPlayerConnectivity works quite well in Firefox to select the appropriate player.

I use realplayer for realmedia, since none of the other players copes properly:
[http://ubuntuforums.org/showpost.php?p=4036593&postcount=5](http://ubuntuforums.org/showpost.php?p=4036593&postcount=5)

Quicktime is not as well dealt with as in Windows / Macs, and I've found that I can only get them to play flawlessly in Mplayer.  However, unlike in Windows etc, you can't pause and rewind the stream.

Flash works just fine with the flash-plugin non-free.  Although it does occasionally cause Firefox to crash after playing the stream.

As for Windows Media streaming, DRM-loaded streams are a non-starter.  And there aren't many non-DRM sites that use .wmv that I use, except BBC (but they have realmedia option).  VLC plays with the best sound (and with no codecs), but seems to put a green bar across the top of the picture.  Mplayer has a clearer picture, but has crackly sound.

ugm6hr, do you use Totem at all? 

I'm just trying to get an idea what programs people have success with...

---

### Post by TWO on 2008-01-06
For the first time, RealPlayer actually starts up when I open it which is a plus, but then the problems start when the MediaConnectivity plugin still wants to choose Mplayer over RealPlayer even though I assigned RealPlayer for Real format streams...grrr... :confused:

On uninstalling the Mplayer plugins, the BBC website now doesn't think that I have anything capable of playing Real format streams...:confused:

Wow, I remember web streams being the one persistent problem since I started using Ubuntu and it looks like 2008 is going to be another year of battling with it. It seriously can't be a good thing if one method of getting web streams to work varies from computer to computer? 

I reckon this is something that Firefox and Ubuntu need to resolve...and quickly! :?

---

### Post by ugm6hr on 2008-01-06
> **TWO said:**
> ugm6hr, do you use Totem at all? 


I have it installed (from default Ubuntu install), but have found that it always gives me an error whenever opening streaming files.  It doesn't stop the file from playing, but it is irritating to have to click OK on an error message before it plays.

I actually installed mplayer (the backports repo version 1.0rc2 rather than the main repo 1.0rc1) in order to use DeVeDe, but have found it doesn't suffer from the same problem, despite using the same gstreamer engine (I think).  Check out the quicktime trailers here to give them a try: [http://www.apple.com/trailers/](http://www.apple.com/trailers/)

If the BBC website is important - I would recommend just installing realplayer (follow my previous link if you have the i386 Gutsy Ubuntu) and using that in preference to WMP format.  It works flawlessly, as you would expect.

In fact, the media player I use most is VLC, but it seems to put a green bar across the top of all video streams, so I only use it to play DVDs etc.  It played everything (except realmedia) successfully in Feisty, but something has obviously gone wrong on my Gutsy install with it.  I do wonder whether it is Compiz that is doing it, but that doesn't explain why there is no problem when playing media files off my HD or DVD.  If you look at the VLC features list ([http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)), it should play everything (except realmedia), and it does - just with a green bar!  The good thing about it is that when you install it, it installs with all the streaming codecs in one file (sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2).

> 
For the first time, RealPlayer actually starts up when I open it which is a plus, but then the problems start when the MediaConnectivity plugin still wants to choose Mplayer over RealPlayer even though I assigned RealPlayer for Real format streams

Bizarre - it works just fine for me.  Maybe try setting it manually with *usr/bin/X11/realplay*, or disabling and re-installing MPC.  Just make sure that the BBC stream plays OK in realplayer (copy and paste the URL directly into Realplayer).

---

### Post by TWO on 2008-01-06
> **ugm6hr said:**
> 
I actually installed mplayer (the backports repo version 1.0rc2 rather than the main repo 1.0rc1) in order to use DeVeDe, but have found it doesn't suffer from the same problem, despite using the same gstreamer engine (I think).  Check out the quicktime trailers here to give them a try: [http://www.apple.com/trailers/](http://www.apple.com/trailers/)


Mplayer plays the trailers on the Apple link that you gave me but not without spitting a couple of errors out first then playing really jumpy. It is really annoying that you can't just pause streams as well and let it load.
 
Did you say that Mplayer was the only one that can play Quicktime?

---

### Post by ubuntu-freak on 2008-01-06
I posted a how-to you should find useful
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by gumpontheweb on 2008-01-09
> **eye208 said:**
> 

Can you point us to the URL of a stream that doesn't work for you?
I get no audio from here:  
[http://www.aei.org/events/eventID.1626](http://www.aei.org/events/eventID.1626)
I have had pretty good results.

---

### Post by TWO on 2008-01-13
> **gumpontheweb said:**
> I get no audio from here:  
[http://www.aei.org/events/eventID.1626](http://www.aei.org/events/eventID.1626)
I have had pretty good results.

gumpontheweb, I get a "page not found" error when trying to access that site.

---

### Post by TWO on 2008-01-13
Update.

ugm6hr, Mplayer is finally streaming WMV streams on the BBC website at a decent-ish capability on both low and high quality options on the site. Actually, I only get the picture for the high quality version if I click on full page view then back to normal view.

I have subsequently uninstalled real player as the BBC site doesn't seem to be able to recognise it. So, I'm about try Helix player as suggested by Nathan(reassuringlyoffensive) for Real Media streams.

---

### Post by ugm6hr on 2008-01-13
The mplayer config edits that Nathan has given in his thread ([http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)) are very good.  I have now edited my settings, and taken the step of removing MediaPlayer Connectivity.

It does mean I can't use Realplayer either (since there is no mozilla plugin), but mplayer does a reasonable job of .ram anyway.  It certainly works very well for Quicktime (with full forward/back/pause control).

My realplayer and wmv streams will only play in one direction in mplayer.  Altho the quality is fine.

---

### Post by TWO on 2008-01-13
> **reassuringlyoffensive said:**
> I posted a how-to you should find useful
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

Nathan, the BBC website recognises that I have a player capable of Real media streams however on waiting for the screen to load, Firefox says that I need the necessary plugins to play it.

I already have Mplayer and that is the only option to download that there is when it's asking to install the plugin. On clicking it, (as expected) it says that it is already installed...:confused:

---

### Post by ubuntu-freak on 2008-01-13
> **TWO said:**
> Nathan, the BBC website recognises that I have a player capable of Real media streams however on waiting for the screen to load, Firefox says that I need the necessary plugins to play it.

I already have Mplayer and that is the only option to download that there is when it's asking to install the plugin. On clicking it, (as expected) it says that it is already installed...:confused:

 
Where does it tell you that you need plugins? Do you have my settings and all plugins, codecs? 
 
Realplayer is now Helix. That's why you can't find it the repo. Helix plays my radio streams fine.
 
Can you reply in my how-to thread? Keeps it alive.
 
Nathan

---

### Post by alien53 on 2008-01-13
I had the same problems then SUCEEDED

this page

[   _**Adobe help for flash plugin**_  ](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

had simple instructions, and they worked; on the desktop click as follows -

**applications/accessories/terminal**  then enter the instructions as given by Adobe

This instantly worked for Epiphany browser too :)

---

### Post by kelvin spratt on 2008-01-13
Mplayer can be a bit picky and their has been problems with it a Gutsy some sort of bug, as with Adobe, I just completely uninstalled Mplayer then reinstalled and that was that BBC and their iplayer all working in full screen with Mplayer.

---

### Post by ubuntu-freak on 2008-01-13
Glad you got it workin. Firefox ignores changes you make sometimes.
 
Delete /home/.mozilla/firefox/pluginreg.dat
 
Nathan

---

### Post by TWO on 2008-01-14
> **reassuringlyoffensive said:**
> Where does it tell you that you need plugins? Do you have my settings and all plugins, codecs? 
 
Realplayer is now Helix. That's why you can't find it the repo. Helix plays my radio streams fine.
 
Nathan

When I click on a media link, be that radio or video and select the rm. stream option, the window appears where the stream should (eventually) play but what I get instead is a message at the top of the window in a yellow bar saying "additional plugins are required to display all the media on this page,"  with a grey button with "install missing plugins" to the right.

On the part of the page where the stream should be, all I get is a green jigsaw piece and below it, the message: "click here to download plugin." 

I have all the settings and plugins/ codecs that you suggested, including the modification of the configuration file of mplayer. The result is better .wmv streaming on the BBC website- albeit after clicking full screen and the back again- but as far as .rm streams are concerned, it's screaming that there are no plugins. 

Real media seems to be a real pain in the you know what on Ubuntu....

---

### Post by ubuntu-freak on 2008-01-14
Don't believe the hype! You DO NOT need RealPlayer. It's either that or I'm just special. I've never had RealPlayer installed and I've been watching rm streams today and listening to ram radio.

I've updated my how-to today. tidied it up and clarafied some things. I take it you followed my how-to fully but are having problems? Scroll down to the --IMPORTANT-- section and have a read. Take note of the Firefox comment.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Nathan

---

### Post by TWO on 2008-01-17
I seem to be having more luck with Mplayer at the moment, though not with it's ability to play Real Media streams! 
Changing the video output to the 'gl' option seems to have stopped the program from spitting out annoying video messages.

.rm stream remain elusive as ever though. I really can't see how you can play them without codecs for .rm.

As for the wmv streams on the BBC site that I keep going on about, the low quality version works much better than the high quality one, though I think that may be in part to the restrictive network I'm behind at the moment...

---

### Post by ubuntu-freak on 2008-01-17
> **TWO said:**
> I seem to be having more luck with Mplayer at the moment, though not with it's ability to play Real Media streams! 
Changing the video output to the 'gl' option seems to have stopped the program from spitting out annoying video messages.

.rm stream remain elusive as ever though. I really can't see how you can play them without codecs for .rm.

As for the wmv streams on the BBC site that I keep going on about, the low quality version works much better than the high quality one, though I think that may be in part to the restrictive network I'm behind at the moment...


I've totally updated my how-to today. It has instructions for removing helix now and install realplayer. Plus a fix for realplayer for some users. If you used my settings before you need to replace them with todays as mplayer is disabled from handling rm, heix, and smil now.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Real media should work fine after that. Does for me so it can for you also. I mean, we both have the same distro don't we? And I've shared everything I did to get it working:)

Nathan

---

### Post by Jored on 2008-01-18
Great advice, reassuringlyoffensive.

I can't find your updated post. :confused:

Could you post the link to it?

Many thanks

---

### Post by ugm6hr on 2008-01-18
> **Jored said:**
> I can't find your updated post. :confused:

Could you post the link to it?


Look at the link in the post above (number 35)!

Here it is again: [Updated link from reasurringlyexpensive]("http://ubuntuforums.org/showthread.php?t=661833")

---

### Post by ubuntu-freak on 2008-01-18
I was asleep :)

---

### Post by Jored on 2008-01-19
Thank you. Didn´t realize one could update earlier posts.

I have done everything indicated in the post and the system mostly does what it should. I had it freeze a couple of times as it was depackaging and installing stuff. The only thing I could do was to power off and restart.

Now the system freezes constantly and responds to nothing, with the HDD activity light stuck on. I have to power off and restart. The freezes are not triggered by any specific task or application. It is completely random. However, I discovered that I can trigger a freeze every time I try to play a YouTube video. It starts to open the file normally and 2/3 of the way along it totally freezes the system.

Any clues? I would hate to have to reinstall as I´m running a dual boot configuration and it´s a bit of a hassle.

I´m running fully updated Gutsy 7.10 from a fresh install on a Toshiba Portege 4000 with 640MB memory and 80GB HDD.

---

### Post by ubuntu-freak on 2008-01-19
> **Jored said:**
> Thank you. Didn´t realize one could update earlier posts.

I have done everything indicated in the post and the system mostly does what it should. I had it freeze a couple of times as it was depackaging and installing stuff. The only thing I could do was to power off and restart.

Now the system freezes constantly and responds to nothing, with the HDD activity light stuck on. I have to power off and restart. The freezes are not triggered by any specific task or application. It is completely random. However, I discovered that I can trigger a freeze every time I try to play a YouTube video. It starts to open the file normally and 2/3 of the way along it totally freezes the system.

Any clues? I would hate to have to reinstall as I´m running a dual boot configuration and it´s a bit of a hassle.

I´m running fully updated Gutsy 7.10 from a fresh install on a Toshiba Portege 4000 with 640MB memory and 80GB HDD.

 
You restarted as it was installing stuff? Ouch! Did you resume the installation?
 
Xorg update gave people grief, thought they fixed it though.
 
Nathan

---

### Post by TWO on 2008-01-20
> **reassuringlyoffensive said:**
> I've totally updated my how-to today. It has instructions for removing helix now and install realplayer. Plus a fix for realplayer for some users. If you used my settings before you need to replace them with todays as mplayer is disabled from handling rm, heix, and smil now.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Real media should work fine after that. Does for me so it can for you also. I mean, we both have the same distro don't we? And I've shared everything I did to get it working:)

Nathan

OK. I've followed all your instructions on your how-to and the problem that I have now is that Firefox keeps picking mplayer as the programme for playing real media streams in spite of me having not only followed your instructions down to a tee, but having made sure that real media is selected for playing real streams via Firefox's preferences menu...

---

### Post by bharadwaj on 2008-01-20
try the tottem plugin to firefox woks perfectly

---

### Post by ubuntu-freak on 2008-01-20
> **TWO said:**
> OK. I've followed all your instructions on your how-to and the problem that I have now is that Firefox keeps picking mplayer as the programme for playing real media streams in spite of me having not only followed your instructions down to a tee, but having made sure that real media is selected for playing real streams via Firefox's preferences menu...

 
Or you could copy my mplayer settings. Rm, helix and smil need to be set to 0 and then you need to 
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
Then Firefox will use RealPlayer
for rm, ra, rv, ram, helix, smil etc.
 
Nathan

---

### Post by Jored on 2008-01-20
> **reassuringlyoffensive said:**
> You restarted as it was installing stuff? Ouch! Did you resume the installation?
 
Xorg update gave people grief, thought they fixed it though.
 
Nathan

Unfortunately, yes. System completely froze.

Pls bear with me as I'm learning my way. Can I restart from scratch from your "How to.." or do I first need to unistall whatever did get installed? What I mean is, can I follow your "How to as if starting from a fresh Gutsy install?

Many thanks

---

### Post by ubuntu-freak on 2008-01-20
> **Jored said:**
> Unfortunately, yes. System completely froze.

Pls bear with me as I'm learning my way. Can I restart from scratch from your "How to.." or do I first need to unistall whatever did get installed? What I mean is, can I follow your "How to as if starting from a fresh Gutsy install?

Many thanks

 
Instead of sudo apt-get install, try sudo apt-get --reinstall install. Then the rest as normal. :) 
 
Nathan

---

### Post by TWO on 2008-01-21
> **reassuringlyoffensive said:**
> Or you could copy my mplayer settings. Rm, helix and smil need to be set to 0 and then you need to 
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
Then Firefox will use RealPlayer
for rm, ra, rv, ram, helix, smil etc.
 
Nathan

I did copy your settings, but I had to right click on the mplayer window during streaming to stop it from being assigned to Real Media streams...grrr:(

I'm still battling away with Real. It now appears embedded in the window but not without throwing this new error message out: 
 "Could not find an appropriate hxplay or realplay in the system path to use as an embedded player"

But there is, and it's installed and assigned! :confused:

Also, have you any idea why mplayer should continue to run and eat my CPU when I have closed it down after a stream? I so wish the BBC would use an open source stream, it would make life so much easier. It's not fair that we have to put up with second best...

---

### Post by TWO on 2008-01-21
Ok, this is definitely more of a problem with the BBC site -the only site I seem to go on about at the moment...I just tried [http://www.film.com](http://www.film.com) and some of the trailers work much better on this, though sometimes I don't get pictures....

---

### Post by ubuntu-freak on 2008-01-21
> **TWO said:**
> Ok, this is definitely more of a problem with the BBC site -the only site I seem to go on about at the moment...I just tried [http://www.film.com](http://www.film.com) and some of the trailers work much better on this, though sometimes I don't get pictures....

 
BBC wmv is a bit weird to be honest. Not sure how they implement it compared to other sites. Try adding this line to the top of the mplayerplug-in.conf
 
download=1
 
I removed it cos I thought it was pointless. Gonna do more tests wednesday. Don't have access til then.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-21
Don't forget to 
 
rm $HOME/.mozilla/firefox/plugins/pluginreg.dat
 
Nathan

---

