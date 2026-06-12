---
title: "smplayer won't play streaming .asx files"
date: 2010-12-24
forum: Multimedia Software
---

### Post by Paco62 on 2010-12-24
smplayer won't play any of my online radio stations in .asx format.  vlc and totem will play them so it is not a big deal, but I would like smplayer to work. anyone know how?

---

### Post by Paco62 on 2010-12-24
I should mention I am using 10.04

---

### Post by andrew.46 on 2010-12-24
Hi paco,

Can you give the link to the asx stream?

Andrew

---

### Post by Paco62 on 2010-12-24
attached are my .asx files.  Smplayer won't play any of them, whereas vlc and totem will.

---

### Post by andrew.46 on 2010-12-25
Hi Paco,

The problem seems to be that SMPlayer does not recognise these files as *playlists* and on my version of SMPlayer (0.6.8 ) there seemed to be no easy way to convince it otherwise from the 'Open File' dialogue. Try playing your files with MPlayer itself using the playlist option and you will achieve success with most of them:

```

andrew@skamandros~/Desktop/asx files$ **[COLOR="Red"]mplayer -playlist KDFCFM.asx[/COLOR]** 
MPlayer SVN-r32733-4.3.3 (C) 2000-2010 MPlayer Team

Playing http://208.80.54.16:80/KDFCFMCMP3.
Resolving 208.80.54.16 for AF_INET6...

Couldn't resolve name for AF_INET6: 208.80.54.16
Connecting to server 208.80.54.16[208.80.54.16]: 80...

Website: http://www.kdfc.com
Bitrate: 129kbit/s
Cache size set to 320 KBytes
Cache fill:  2.50% (8192 bytes)   
ICY Info: StreamTitle='M. DAVIS - BELLS OF CHRISTMAS MEDLEY';
Cache fill: 17.50% (57344 bytes)   

Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
mpg123: Can't rewind stream by 974 bits!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   9.1 (09.0) of 0.0 (unknown)  0.8% 51% 

```

So I am afraid that I can see the problem but not the solution, hopefully an SMPlayer guru will comment here or even the developer himself who frequents these forums...

Andrew

**Edit:** To better demonstrate this problem try running SMPlayer from the commandline:

```
smplayer -playlist KDFCFM.asx
```

and the stream will play in SMPlayer :).

---

### Post by mc4man on 2010-12-26
If you can't adjust smplayer to suit then just create a custom .desktop for asx playlist playback.
Simplest way -
right click on any .asx file - Open with - Other Application - Use a custom command
For the command use as mentioned
smplayer -playlist

Without any other work you'll then see that .desktop in your r. click context menus as smplayer with a small diamond icon.
To give a unique name and or icon of your choice then open the .desktop in a text editor and change the display name (Name=), and if desired give an icon. (Icon=
You'll find the .desktop in ~/.local/share/applications as userapp-smplayer-XXXXXX.desktop

there are several ways to open a .desktop in a text editor, probably easest for you would be to open gedit - click on open. Then r. click in the browse area - enable 'show hidden files' and browse to the .desktop
Ex below - gave it the smplayer icon and a name of asxplayer
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=smplayer -playlist %f
Name=asxplayer
Comment=Custom definition for smplayer
NoDisplay=true
Icon=smplayer

```

( When going to the open with - other application menu if the Remember this... box is enabled (default in maverick), then your 'new' smplayer will be set as the new left d. click default.

Or just use gnome-mplayer which automatically adjusts for playlists

---

### Post by coffeecat on 2011-06-20
Sorry to bump a 6-month old thread, but I have found an answer, even though the OP has not been back  since the day they started the thread. The solution might be of use to someone finding this thread through a search, as I did.

The answer was buried in the comments in this link:

[http://yuenhoe.co.cc/blog/2010/01/playing-asx-streaming-radiomedia-on-linux/](http://yuenhoe.co.cc/blog/2010/01/playing-asx-streaming-radiomedia-on-linux/)

Put simply: wget the playlist, open it with a text editor, extract the URL of the actual stream and use that in smplayer's Open > Radio > Edit. For example, for Classic FM:

```
wget http://media-ice.musicradio.com/ClassicFMMP3.m3u
```Opening that reveals a single line:

> [noparse]http://media-ice.musicradio.com:80/ClassicFMMP3[/noparse]... which works perfectly in smplayer.

Formats of playlists are new to me, but I had equal success with BBC Radio 3's r3_aaclca.pls playlist where the streaming URLs were under "File1=" and "File2=".

A *asx file from a Danish classical music station gave me working URLs under "<Ref href".

And now I can enjoy streaming music with smplayer. Unfortunately, I was experiencing the crackling sounds that others are getting with Natty's version of VLC, so using VLC for streaming radio was getting to be tedious.

---

