---
title: "xine was unable to initialize any audio drivers"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by p_quarles on 2007-11-23
I'm getting the error message in the subject line every time I attempt to start Amarok. This started only yesterday, and prior to that I have been using this machine for the last seven months without sound driver problems of any kind. 

I found one relevant thread ([link]("http://ubuntuforums.org/showthread.php?t=351218")), and followed the suggestions that various posters said worked for them, including removing ~/.kde/share/config/amarokrc, editing it for optimal settings, and editing the xine config file. None of these made any difference. The one thing I did not try was removing ~/.asoundrc. This file does not seem to exist in Kubuntu 7.10.

Starting Amarok from the terminal gives me this:
```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x87c450 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x87c450 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QPainter::begin: Cannot paint null pixmap
```Finally, the only other clue I can find is the fact that the Amarok GUI config dialogue no longer gives me options for either OSS or ALSA: only "autodetect" and "esd." 

Like I said, I haven't had any sound problems with this machine before, and consequently have no experience debugging this kind of issue. Anything that you can think of to point me in the right direction is appreciated.

By the way, system sounds are working fine.

EDIT: I just ran a few more tests, and find that sound also works with the Flash browser plugin, as well as with games. Miro (which I have configured to use Xine) is giving me a "This file type is not supported" message with videos that previously played without problems. So, the problem would definitely seem to be with Xine, rather than with the audio drivers themselves.

---

### Post by John Jason Jordan on 2007-11-23
> **p_quarles said:**
> I'm getting the error message in the subject line every time I attempt to start Amarok. This started only yesterday, and prior to that I have been using this machine for the last seven months without sound driver problems of any kind. 

I found one relevant thread ([link]("http://ubuntuforums.org/showthread.php?t=351218")), and followed the suggestions that various posters said worked for them, including removing ~/.kde/share/config/amarokrc, editing it for optimal settings, and editing the xine config file. None of these made any difference. The one thing I did not try was removing ~/.asoundrc. This file does not seem to exist in Kubuntu 7.10.

Starting Amarok from the terminal gives me this:
```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x87c450 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x87c450 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QPainter::begin: Cannot paint null pixmap
```Finally, the only other clue I can find is the fact that the Amarok GUI config dialogue no longer gives me options for either OSS or ALSA: only "autodetect" and "esd." 

Like I said, I haven't had any sound problems with this machine before, and consequently have no experience debugging this kind of issue. Anything that you can think of to point me in the right direction is appreciated.

By the way, system sounds are working fine.

EDIT: I just ran a few more tests, and find that sound also works with the Flash browser plugin, as well as with games. Miro (which I have configured to use Xine) is giving me a "This file type is not supported" message with videos that previously played without problems. So, the problem would definitely seem to be with Xine, rather than with the audio drivers themselves.
I am having the same exact problem. 

First, the .asoundrc file did not exist on my Ubuntu Gutsy x85_64 computer either, until I created it. I did so after reading a how-to for getting bluetooth headphones working. The how-to said to add certain lines to the .asoundrc file but, since I did not have the file, I just created the file and put the lines in it. That got my bluetooth headphones working, however, at that time I had no problem with Amarok or anything else.

As for the xine error message, xine doesn't even appear in Synaptic. I've tried everything else I could think of - gxine, gxine-plugins, etc. Nothing has helped. Amarok still thinks it needs xine. Personally, I don't really care, as I don't like Amarok anyway. It is annoying that you cannot delete the preinstalled radio links, and the interface is not UTF-8 compliant, so my classical MP3s with non-English names appear all messed up. I was trying Amarok only because of bugs in Rhythmbox.

Hopefully someone else can shed some light on what is going on.

---

### Post by p_quarles on 2007-11-23
Xine appears in the repos under the name "libxine1." The first thing I did, actually, was reconfigure that using dpkg. That didn't work either, obviously. 

In any case, I "fixed" the problem by reinstalling. Frankly, I thought Kubuntu 7.10 was more bloated and buggy out of the box in a lot of ways, so instead of trying to fix a bunch of little things I decided to go for KDE-core. 

Thanks for confirming the problem, anyway. I was hesitant about filing a bug report without knowing whether or not I'd just done something strange to my system without realizing it. Now that I'm not the only one who can't find ".asoundrc" it sounds like a legitimate bug.

---

### Post by John Jason Jordan on 2007-11-23
> **p_quarles said:**
> Xine appears in the repos under the name "libxine1." The first thing I did, actually, was reconfigure that using dpkg. That didn't work either, obviously. 
In any case, I "fixed" the problem by reinstalling. Frankly, I thought Kubuntu 7.10 was more bloated and buggy out of the box in a lot of ways, so instead of trying to fix a bunch of little things I decided to go for KDE-core. 
Thanks for confirming the problem, anyway. I was hesitant about filing a bug report without knowing whether or not I'd just done something strange to my system without realizing it. Now that I'm not the only one who can't find ".asoundrc" it sounds like a legitimate bug.
Thanks for the reply. 

I already had libxine1 installed, but I reinstalled it anyway. Didn't make any difference. Amarok still says it was unable to initiate any audio drivers. I have also completely removed and reinstalled Amarok, but no joy. Rhythmbox just hangs trying to play an MP3. The only app that appears to be able to play MP3s for me is VLC. VLC also plays streaming radio. I may give up on all these other apps and just use VLC if I can scrute its interface.

I don't know what is wrong with Amarok. For me it's just academic, as I don't even like Amarok.

---

### Post by p_quarles on 2007-11-23
As far as I know, VLC does not allow you manage any kind of library (certainly not as easily as any of the dedicated music players). It's a fantastic video player, but just about my last choice for music. 

If you get it working, great, but you might want to check out Exaile, Banshee, Audacious, XMMS, Songbird, or Noatun. There's also MPD (music player daemon), which is a command line app. A lot of people are fond of the Sonata GUI front-end for managing it -- supposedly one of the lightest media players out there. 

Good luck in any case.

---

### Post by John Jason Jordan on 2007-11-24
> **p_quarles said:**
> As far as I know, VLC does not allow you manage any kind of library (certainly not as easily as any of the dedicated music players). It's a fantastic video player, but just about my last choice for music. 
If you get it working, great, but you might want to check out Exaile, Banshee, Audacious, XMMS, Songbird, or Noatun. There's also MPD (music player daemon), which is a command line app. A lot of people are fond of the Sonata GUI front-end for managing it -- supposedly one of the lightest media players out there. 
Thanks for the suggestions. I have some additional information:

Rhythmbox - When I try to play an MP3 it locks up for a while, then puts a red - in front of the file in the playlist. If I right click on this file and select properties I get "Internal GStreamer error: state change failed. Please file a bug report at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer." I did so.

Amarok - still can't find an audio driver "xine was unable to initialize any audio drivers." Also user configuration does not work - can't change font in playlist, for example. Plus it is annoying that the user cannot delete the preinstalled radio links. That is so Microsofty that I hate it.

Banshee - Starts playing an MP3, then "Banshee encountered a fatal error." I saved the text of the error in case anyone is interested.

Exaile - Plays MP3s. Won't play streaming radio, except it will play ABC in Melbourne for a few minutes, then stops. If I let it sit it will resume for a few moments, then stop again. I think it's a bandwidth issue, but other apps have no problem streaming the same station, plus I'm on cable.

Gimmix - Can't open the folder where my MP3s are stored. 

Noatun - Can't get it to launch.

Sonata - I get "Starting Sonata ..." then nothing.

Songbird - Looks nice, but can't actually install it. All I can do is untar the file, then click on the executable. To install it requires a .deb, but the only .deb available is i386. I suppose I could install it with dpkg --force-architecture, but I'd rather not bother. As it is it cannot play radio. Shows promise, though.

Gxine - This is the one I've got working the best so far. It plays MP3s and streaming radio just fine, and through my bluetooth headphones too, as long as I turn the headphones on before launching it. The only problem is that it plays .asx streams fine (which Rhythmbox never did back when I had it working), but it won't play .ogg, .pls, or .m3u streams (which all worked in Rhythmbox). If I try any of those streams I get "no demuxer found, stream format not recognized." Very strange that it plays the only format that Rhythmbox would not play, but won't play the formats that Rhythmbox would do. I'm hoping I can find a plugin or codec or lib file somewhere to enable other stream formats. 

If anyone knows how to get Gxine to play the .m3u, .pls or .ogg streams, please speak up!

---

### Post by Daveth on 2008-01-01
a brand new install of Gutsy gave me the amarok error of xine not finding any drivers and I deleted both ~/.asoundrc files I found, and now it works, though only stereo as I write this. So that fix does work.
Happy New Year.

---

### Post by wyth on 2008-04-10
For what it's worth, I just ran into this problem on Hardy, and here's what worked for me:[LIST]
[*] Re-installed every xine package that was already installed
[*]Installed libxine1-all-plugins (which also installed libxine1-gnome, I believe; I'm on gnome)[/LIST]Not sure if it was the re-installs or the all-plugins, but it worked immediately after that.

EDIT: Forget it, it's borked again.

---

