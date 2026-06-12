---
title: "a player called deadbeef"
date: 2010-06-07
forum: Multimedia Software
---

### Post by shantiq on 2010-06-07
[INDENT][INDENT][INDENT]**[COLOR=#000000]was just sent a link to this player called [/COLOR][[COLOR=#000000]deadbeef [/COLOR]]("http://deadbeef.sourceforge.net/")[COLOR=#000000]  and it is very good plays cuefiles  and all sorts of formats[/COLOR]**[COLOR=#000000]


* mp3, ogg vorbis, flac, ape, wv, wav, m4a, alac, mpc,shn,aac/mp4, cd audio (and many more)


* sid, nsf and lots of other popular chiptune formats
* ID3v1, ID3v2.2, ID3v2.3, ID3v2.4, APEv2, xing/info tags support
* character set detection for non-unicode id3 tags - supports cp1251 and iso8859-1
* unicode tags are fully supported as well (both utf8 and ucs2)
* cuesheet (.cue files) support, with charset detection (utf8/cp1251/iso8859-1)
* tracker modules like mod, s3m, it, xm, etc
* HVSC song length database support for sid
* gtk2 interface with efficient custom widgets
* no GNOME or KDE dependencies
* minimize to tray, with scrollwheel volume control
* drag and drop, both inside of playlist, and from filemanagers and such
* control playback from command line
* global hotkeys
* multiple playlists
* album artwork display
* 18-band graphical equalizer
* metadata editor
* user-customizable groups in playlists
* user-customizable columns with flexible title formatting
* radio and podcast support for ogg vorbis, mp3 and aac streams
* gapless playback
* plugin support; bundled with lots of plugins, such as global hotkeys and last.fm scrobbler; sdk is included
* duration calculation is as precise as possible for vbr mp3 files (with and without xing/info tags)
* was tested and works on x86, x86_64 and ppc64 architectures. should work on most modern platforms
* plays from zip files



[/COLOR][[COLOR=#000000]**official site downloads/deb  etc **[/COLOR]]("http://deadbeef.sourceforge.net/download.html")[COLOR=#000000]

**or**
[/COLOR][/INDENT]
[/INDENT]
[/INDENT]
[COLOR=#000000][SIZE=3]**_install=_**[/SIZE]  3 steps one at a time     installs the latest version 
```

sudo add-apt-repository ppa:alexey-smirnov/deadbeef

``````

sudo apt-get update

``````
sudo apt-get install deadbeef
```

&#10020;**Personally **favour the[/COLOR]**[[COLOR=#000000] portable version[/COLOR]]("http://deadbeef.sourceforge.net/download.html")**[COLOR=#000000] these days as it simply sits in your home folder or wherever you wish to have it and works perfectly well


&#10020;**Alternative **icon lookin' like a** busted plectrum:**[ATTACH=CONFIG]252005[/ATTACH][ATTACH=CONFIG]252006[/ATTACH][ATTACH=CONFIG]252007[/ATTACH][/COLOR]

---

### Post by jmccrohan on 2010-06-07
I have only recently discovered this player. Previously I was running foobar2000 under WINE because I didn't like any of the native players.

---

### Post by shantiq on 2010-06-07
> **jmccrohan said:**
> I have only recently discovered this player. Previously I was running foobar2000 under WINE because I didn't like any of the native players.




**[COLOR="Blue"]there is also qmmp in your synaptic which is really really good and if you want the older stuff but really cool try xmms   not in your synaptic but much info [here]("http://ubuntuforums.org/showthread.php?t=833164&highlight=xmms") also aqualung in your synaptic   [/COLOR]**

---

### Post by panos_thes on 2010-06-22
I cannot make it work in Lucid 10.04 LTS, no sound. Anyone can help me setting up the preferences?

---

### Post by shantiq on 2010-06-22
[B][COLOR="Blue"]yes had the same


simple answer

go to Edit/Preferences/sound then pick   output device  default audio device


see in the picture attached


[/COLOR][/B]

---

### Post by panos_thes on 2010-06-22
yeah, works like that! thanks :)
Also, i can play songs only when i marked them, right click open with deadbeef, drag and drop to playlist doesn't do anything.

---

### Post by phillw on 2010-06-26
[COLOR="Blue"][B]AFAIK deadbeef cannot yet import playlists from other systems, but it is certainly a nice player.

Regards,

Phill.[/B][/COLOR]

---

### Post by d3v1150m471c on 2010-06-26
just use vlc

---

### Post by phillw on 2010-06-26
> **d3v1150m471c said:**
> just use vlc

[COLOR="Blue"][B]I have both installed, but as a lubuntu user I have found deadbeef to be far less resource hungry for music, yet being able to handle large collections of music. Every byte of RAM and cycle of CPU is important. VLC is IMHO a very good DVD player

Regards,

Phill.[/B][/COLOR]

---

### Post by d3v1150m471c on 2010-06-26
ffplay or cvlc

---

### Post by phillw on 2010-06-26
[COLOR="Blue"][B]> **d3v1150m471c said:**
> ffplay or cvlc
If you'd like to join in on discussions about low resource hungry audio and video players, then do have a look at lubuntu in my sig.

To shantiq : I am interested in AT, and as I learn more I am hoping to get AT embedded into lubuntu, or further push the project vinux [http://ubuntuforums.org/showthread.php?t=1499511](http://ubuntuforums.org/showthread.php?t=1499511) can I suggest that you also keep up to date with the mailing list for ubuntu-accessibilty over at [https://wiki.ubuntu.com/Accessibility](https://wiki.ubuntu.com/Accessibility) 

Regards,

Phill.[/B][/COLOR]

---

### Post by ssri on 2010-06-26
Yeah, deadbeef reminds me of plain vanilla foobar2000.  It has been able to play everything I've thrown at it (APE, chip tunes (s3m, it, mod, mtm)).  Very impressive and I am looking forward to its continued development.

---

### Post by shantiq on 2010-06-27
> **phillw said:**
> [COLOR="Blue"][B]AFAIK deadbeef cannot yet import playlists from other systems, but it is certainly a nice player.

Regards,

Phill.[/B][/COLOR]

[B][COLOR="Blue"]oh yes it can Phil (thanx for the links)   


[COLOR="Magenta"]Simply save your other player playlist in the .m3u format. It will open in deadbeef

When you save your playlist in Deadbeef also save as .m3u   then you can export to other players too:p
[/COLOR]

i also agree that vlc is better used as a dvd player ( also like gxine) than a music player as i use cuefiles and vlc does not support that or my favourite old-time format shorten.


as regards others players the latest versions of [qmmp 0.4.1]("https://launchpad.net/~stiff.ru/+archive/qmmp-releases") is also definitely worth having a look at but for me the KING is still [xmms]("http://ubuntuforums.org/showthread.php?t=1312757&highlight=shn&page=2")with the external cuefile monitor


[CENTER][[IMG]http://img153.imageshack.us/img153/1366/screenshotkir.th.png[/IMG]](http://img153.imageshack.us/img153/1366/screenshotkir.png)[/CENTER]



[/COLOR][/B]

---

### Post by phillw on 2010-06-27
[COLOR="Blue"][B]export is ......

import is ......
[/B][/COLOR]
:lolflag:
[COLOR="blue"][B]
As I previously said, with a bit of encouragement I'm sure the author would be interested in doing it, and hopefully people will help with the translations.

Regards,

Phill.[/B][/COLOR]

---

### Post by shantiq on 2010-06-27
> **ssri said:**
> Yeah, deadbeef reminds me of plain vanilla foobar2000.  It has been able to play everything I've throw it (APE, chip tunes (.  Very impressive and I am looking forward to its continued development.


[B][COLOR=Blue]thanx for ALBUM ART  man i had not seen it was there:p


[U]steps to install are
[/U]
** 1. ** Edit/preferences/plugins/album Artwork/configure/tick them all
[B]
2.[/B] then   right-click on columns at the top of player (where is says artist/album  tracks all that ) and add column
**3.**  then right-click go to group by and pick artist/date album



then widen your album image

[CENTER][[IMG]http://img842.imageshack.us/img842/4681/deadbeef041004.th.png[/IMG]](http://img842.imageshack.us/img842/4681/deadbeef041004.png)[/CENTER]




[/COLOR][/B]

---

### Post by cascade9 on 2010-06-27
@ ssri- what, deadbeef does album art? From the look of it, it does album art from local folders as well....I'll have to look into this, se how configurable the player is. If it can have the layout changed (like columns UI in foobar) it could be enough to get me off foobar2000 in WINE.

---

### Post by ssri on 2010-06-27
> **cascade9 said:**
> @ ssri- what, deadbeef does album art? From the look of it, it does album art from local folders as well....I'll have to look into this, se how configurable the player is. If it can have the layout changed (like columns UI in foobar) it could be enough to get me off foobar2000 in WINE.

Yeah, I have album art stored local folders, which deadbeef automatically detects.  So far, I haven't seen any configurability options a la foobar2000, or something as accessible as fb2k, which can probably be explained by how relatively new the program is.  For the most part, the configurability for deadbeef comes from its plugins, which hopefully some new one in the not-so-distant future can replicate the columnsUI component from fb2k.  I guess one has to follow the devlist to see if anything like that is in the offing.

---

### Post by CrimsonBizarre on 2010-07-05
This is awesome. Finally a decent linux media player.

---

### Post by samigina on 2010-08-12
Where is the gapless option? I want crossfade too...

---

### Post by phillw on 2010-08-12
Yeah, there are a few who also love it.

The project page is at [http://sourceforge.net/apps/mediawiki/deadbeef/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/deadbeef/index.php?title=Main_Page)

We've not come across bad things, but you would be installing something that is not 'pure' ubuntu (I have a strong feeling that if it messed up, there would be comments. So, I think it is safe, but that is just my honest opinion).

I can only say that myself and others like it and it has not 'killed' our systems.

[http://sourceforge.net/tracker/?group_id=272657](http://sourceforge.net/tracker/?group_id=272657) would be to put your comments / requests.

[http://sourceforge.net/projects/deadbeef/](http://sourceforge.net/projects/deadbeef/)

Regards,

Phill.

---

### Post by shantiq on 2010-08-17
TO INSTALL FROM SOURCE OR GIT VERSION




**SOURCE**


> sudo apt-get install intltool automake gettext libtool \
autotools-dev  libasound2-dev libcddb2-dev libcdio-dev libcurl4-gnutls-dev libflac-dev libgtk2.0-dev libmad0-dev libogg-dev \
libsamplerate0-dev libsndfile1-dev libvorbis-dev libwavpack-dev libavformat-dev libavcodec-dev libavutil-dev libpulse-dev \
 libdbus-1-dev libpango1.0-dev libx11-dev   automake libtool  libgtk2.0-dev  libcurl4-gnutls-dev libdbus-1-dev libfaad-dev \
   intltool libimlib2-dev libzip-dev yasm[COLOR=#000000][FONT=Times New Roman][COLOR=#0000ff][FONT=verdana]



[/FONT][/COLOR][/FONT][/COLOR]> [COLOR=#000000]./configure && make && sudo make install [/COLOR]
[COLOR=#000000][FONT=Times New Roman][COLOR=#0000ff][FONT=verdana] 

[B]GIT
[/B] 
[/FONT][/COLOR][/FONT][/COLOR]     
     ```

git clone git://deadbeef.git.sourceforge.net/gitroot/deadbeef/deadbeef 


``````
cd ./deadbeef

``````
git checkout -b devel origin/devel

```[COLOR=#000000][FONT=Times New Roman][COLOR=#0000ff][FONT=verdana]

[/FONT][/COLOR][/FONT][/COLOR] 
```
       ./autogen.sh && ./configure 
```[COLOR=#000000][FONT=Times New Roman][COLOR=#0000ff][FONT=verdana]



[/FONT][/COLOR][/FONT][/COLOR]   
```
       make 
```[COLOR=#000000][FONT=Times New Roman][COLOR=#0000ff][FONT=verdana]

[/FONT][/COLOR][/FONT][/COLOR] 
```
       sudo make install 
```[COLOR=#000000][FONT=Times New Roman][COLOR=#0000ff][FONT=verdana]


[COLOR=Black]alternative icons attached  :KS:KS  right click on existing icon/properties/double click on image and change for new[/COLOR]



[/FONT][/COLOR][/FONT][/COLOR]                                                                                                                            Attached Images                                          [IMG]http://ubuntuforums.org/attachment.php?attachmentid=166737&stc=1&d=1282072829[/IMG] [IMG]http://ubuntuforums.org/attachment.php?attachmentid=166738&stc=1&d=1282072829[/IMG]

---

### Post by MetalMusicAddict on 2010-11-07
I'm sure I'm missing something. Can DeadBeef use .PNGs for cover art? /artist/album/cover.png?

---

### Post by the torgo fondle on 2010-11-07
I would like to see a plugin for this player that automatically sends the now playing information to the clipboard. If I have the time I might try to write one. It seems like it wouldn't be that hard.

---

### Post by ivanovnegro on 2010-11-15
I came across this player now and I have to say its great, its fantastic.
Never used minimalistic players like this one, but I really like it, the sound quality is amazing.
In the last days I had problems with my large music library and decided to go for something that does not need one, as I think at the moment there is nothing that can handle without ANY glitches my library of >200 gb. And I have my library very good sorted manually, so just drag and drop without to use the whole system cpu.
This player convinced me to the minimalistic style.
One question, if somebody could help me. How can I use the streaming function or where I cand find it? Did not figured it out yet.
Thanks.

---

### Post by shantiq on 2010-11-15
hi ivanovnegro


edit/preferences/plugins     choose what you need there


if that is what you mean/are looking for    lastfm is there

---

### Post by ivanovnegro on 2010-11-15
> **shantiq said:**
> hi ivanovnegro


edit/preferences/plugins     choose what you need there


if that is what you mean/are looking for    lastfm is there

Thank you for your reply. I meant the radio function not Last.FM. I was in the preferences section but could not find how to setup Shoutcast or similar. There are some streaming configurations but I cannot access them, they are not highlighted when I click on "Configure".
I read Deadbeef can stream Shoutcast stations.
So, like I have you here to answer some things, I dont want to bother you... Have some more questions, is deadbeef suppose to scrobble to Libre.FM also? I read it somewhere but in the preferences I can only find Last.FM.
I noticed that sometimes I have a little scratch in the sound when the next song comes. 
What means samplerate, there are some things like sinc_fastest and so on, what can I manipulate?
Im new to this player and its an amzing one, I hope I did not have ask you too much. :)

---

### Post by shantiq on 2010-11-15
sorry do not know any of the answers for this :::)))))    i do not use those stations      ask alexei who designed the program  maybe

---

### Post by ivanovnegro on 2010-11-15
> **shantiq said:**
> sorry do not know any of the answers for this :::)))))    i do not use those stations      ask alexei who designed the program  maybe

No problem. Anyway thank you.

---

### Post by faucon50 on 2010-11-16
Hello,

Take a look at this: [https://bbs.archlinux.org/viewtopic.php?id=96968&p=1](https://bbs.archlinux.org/viewtopic.php?id=96968&p=1) and: [http://ubuntuforums.org/showthread.php?t=1503749](http://ubuntuforums.org/showthread.php?t=1503749)

For urls: File>add a place>ok then, add how many you want on the tab and File>save as playlist. So let 1 tab for radios where you can load your urls from /home/user/Musik and an another one for your ripps. You will just need to switch from one tab to the other for radios or ripp. Once the urls playlist loaded deadbeef will load it everytime.

P.S. Sorry my english is not perfect.

---

### Post by ivanovnegro on 2010-11-16
> **faucon50 said:**
> Hello,

Take a look at this: [https://bbs.archlinux.org/viewtopic.php?id=96968&p=1](https://bbs.archlinux.org/viewtopic.php?id=96968&p=1) and: [http://ubuntuforums.org/showthread.php?t=1503749](http://ubuntuforums.org/showthread.php?t=1503749)

For urls: File>add a place>ok then, add how many you want on the tab and File>save as playlist. So let 1 tab for radios where you can load your urls from /home/user/Musik and an another one for your ripps. You will just need to switch from one tab to the other for radios or ripp. Once the urls playlist loaded deadbeef will load it everytime.

P.S. Sorry my english is not perfect.

Thank you for your advice but I have to be dumb, its not very intuitive, I dont understand it. I added to places the URL and then clicked OK and then I opened a new tab made by me but there is nothing, the only thing I was able to do is to add the URL in my tab where I already listen to music and it looks strange.

---

### Post by shantiq on 2010-11-16
---------------------

---

### Post by ivanovnegro on 2010-11-16
> **shantiq said:**
> ok ivanovnegro made a video to show how to get shoutcast going    it is really easy

if you want the same in spanish i can do that for you    but i am sure you can understand it as it is



   [ **===>here**]("http://www.youtube.com/watch?v=Rp-5P9NQseA")



if you want to see it without bandwidth fluctuation


download it 720p    ```
youtube-dl -t http://www.youtube.com/watch?v=Rp-5P9NQseA
```

or 480p    ```
youtube-dl -f 35 -t http://www.youtube.com/watch?v=Rp-5P9NQseA
```

Shantiq, fantastic!! Thank you very much, you was a great help. Its so simple and amazing, like this way to add Shoutcast, not had this idea, I wanted to do another way, that was the problem.
Thank you again!!

---

### Post by ivanovnegro on 2010-11-17
After some testing, I think I cannot live too long with this player.
Its a fantastic mini player with a fantastic sound and very easy to use but with my collection that is so large I noticed I cannot search for my stuff because it has not a library.
I can do it via Nautilus but that way I do not prefer. I can load all my files but this takes an amount of time even it is very fast doing this faster as other players, but everytime to load again is too bothering as my music collection would grow. And when I have it open I have to go through an amount of data and its not yet very functional. It cannot do a better view of compilations and the tagging system is not really good, no mass tagging. I dont want to use an external tagger as my player, Guayadeque already do the job very good, so I could use this one to tagg but then it would be again another app, I prefer to do it with one thing.
I will observe the development of Deadbeef as it is a good application and for a minimalistic style it serves very good but I need more functionality to say it could be like foobar, at the moment it only looks like it.

---

### Post by shantiq on 2010-12-05
nice new portable version on alexei's site so easy to install that [**way**]("http://deadbeef.sourceforge.net/download.html")


choose the second one of course where it says portable

---

### Post by u-neeks on 2010-12-19
> **MetalMusicAddict said:**
> I'm sure I'm missing something. Can DeadBeef use .PNGs for cover art? /artist/album/cover.png?

Sure, it can. 
For load both (jpg and png) go in:
[COLOR="RoyalBlue"]Preferences/Plugins/Album Artwork/Configure/Local cover file mask/[/COLOR]
and put '[COLOR="RoyalBlue"]cover.*g[/COLOR]' there.

---

### Post by Yellow Pasque on 2010-12-19
If it had something equivalent to the noise sharpening plugin for fb2k (recently ported to gstreamer), then I would use it. I guess I'm still stuck with fb2k because there is something about each player I try that I don't like (rbox, exaile, guayadeque, amarok, etc.)

My requirements for a music player are pretty modest IMO, but I can't find a program that does them all and looks how I want (or maybe I just don't know how to configure it to look how I want). It has to have noise sharpening (either a built-in plugin or any player that uses gstreamer), movable columns, and white text on black/dark background.

---

### Post by shantiq on 2010-12-19
temujin     edit/ preferences/ colour will fix the last request

view/equalizer   then go and find on the net the equalizer of your choice should do that   i attach all the .feq    which are foobar's own  install with import foobar's presets on the equalizer


is DSP the one [here]("http://www.foobar2000.org/components/view/foo_dsp_effect") probably could be adapted   turned into .feq



the columns not sure   :KS:KS:KS




enclosed sample image

---

### Post by Yellow Pasque on 2010-12-19
> temujin edit/ preferences/ colour will fix the last request
That's what makes deadbeef intriguing to me. Its look and layout is awesome, but it's missing the noise sharpening plugin I love so dearly. The DSP I'm looking for is not an equalizer. Noise sharpening adds noise in the inaudible range to increase clairty in the audible range. Foobar called this foo_dsp_delta, Audacious calls it Crystalizer, and the link in my sig calls it gstreamer-delta. Thanks anyway.

---

### Post by shantiq on 2010-12-19
wow temujin it is good  just tried it with audacious

it is like a really high quality sharpener

crystal-clear     there has to be a way to move it to deadbeef for sure:KS

---

### Post by nenolod on 2011-01-08
> **Temüjin said:**
> If it had something equivalent to the noise sharpening plugin for fb2k (recently ported to gstreamer), then I would use it. I guess I'm still stuck with fb2k because there is something about each player I try that I don't like (rbox, exaile, guayadeque, amarok, etc.)

My requirements for a music player are pretty modest IMO, but I can't find a program that does them all and looks how I want (or maybe I just don't know how to configure it to look how I want). It has to have noise sharpening (either a built-in plugin or any player that uses gstreamer), movable columns, and white text on black/dark background.

Audacious 2.5 has all of this except for colour themeing as of latest hg.

I wrote audacious's Crystalizer plugin... the reason why I called it that was mostly to make a statement about CreativeLabs' BS marketing of this feature.

The actual mechanism is more correctly called "Nyquist's dealiasing."  It works by introducing additional noise to raise the floor which causes the aliasing to be less perceived... the first use of this formula comes from the 1950s for improving telephone call clarity.  The way that it introduces the noise is by altering the vibration amplitude based on the last sample, yielding a signal with the resolution of roughly 1.5x the Nyquist aliasing limit.

I was thinking about renaming the plugin to 'Nyquist de-alias', but that might be confusing.

If you can wait a few days, I will try to get colour theming into 2.5's gtkui plugin.

---

### Post by cascade9 on 2011-01-08
> **u-neeks said:**
> Sure, it can. 
For load both (jpg and png) go in:
[COLOR=RoyalBlue]Preferences/Plugins/Album Artwork/Configure/Local cover file mask/[/COLOR]
and put '[COLOR=RoyalBlue]cover.*g[/COLOR]' there.

Heh, I didnt think it supported .png either, but this works...well, it works if I change it to *.*g (I dont use 'cover' for artwork, it seems silly to have lots of files with the same name). 

I seem to have some .jpegs not show up with that settings, I'm going to have to play with settings and see if I can get it 100% right.

> **Temüjin said:**
> If it had something equivalent to the noise sharpening plugin for fb2k (recently ported to gstreamer), then I would use it. I guess I'm still stuck with fb2k because there is something about each player I try that I don't like (rbox, exaile, guayadeque, amarok, etc.)

My requirements for a music player are pretty modest IMO, but I can't find a program that does them all and looks how I want (or maybe I just don't know how to configure it to look how I want). It has to have noise sharpening (either a built-in plugin or any player that uses gstreamer), movable columns, and white text on black/dark background.

+1 on ' can't find a program that does them all and looks how I want'. 

I tried noise sharpening with FB2K, but IIRC it did some funny things to some of my music.

---

### Post by Yellow Pasque on 2011-01-08
nenolod, that would be nice if it was more easily configurable independent of gtk color-theming, but it's not a top priority for me now that I figured out how to tweak my gtk color theme, even if using xfce, so that Audacious looks nice. I'm going to try the hg version now to see if it's finally suitable to replace fb2k.
Thank you for your development effort. If I really end up using Audacious, I will try to drink less beer and donate a few $'s to show my gratitude. <3

---

### Post by mc4man on 2011-01-08
> Audacious 2.5 has all of this except for colour themeing as of latest hg.
Didn't notice the 2.5 was avail. (hadn't looked in awhile). Very nice job and as a side point works quite well in 11.04. Additionally easily takes care of a possible segfault scenario in natty when using aud from the context menu.
Well done..

---

### Post by ivanovnegro on 2011-02-22
Im still using Deadbeef sometimes for albums because of its superb sound, could not seperate me of this app even that it has not a library.
But one thing I noticed on the last version 0.4.4 is that I have always a 'click/gap' after the track goes to the next one, really annoying for an app with such a good sound quality.
Someone here experienced the same? And it seems to be a known issue as I reported it on the project's page on Sourceforge but my request was a duplicate of another one that I could not find to see what it really is. I need this fixed. :p
Another question I have, is there a possibilty to have the latest development build like SVN or something to not wait for a fix too long and to see how Deadbeef is evolving?

---

### Post by MetalMusicAddict on 2011-02-22
> **ivanovnegro said:**
> Another question I have, is there a possibilty to have the latest development build like SVN or something to not wait for a fix too long and to see how Deadbeef is evolving?

I'll add a little "how-to" later but [HERES]("http://sourceforge.net/apps/mediawiki/deadbeef/index.php?title=Installing:Ubuntu") the build deps and he hosts his code using GIT.

```
git clone git://deadbeef.git.sourceforge.net/gitroot/deadbeef/deadbeef
```

---

### Post by ivanovnegro on 2011-02-22
> **MetalMusicAddict said:**
> I'll add a little "how-to" later but [HERES]("http://sourceforge.net/apps/mediawiki/deadbeef/index.php?title=Installing:Ubuntu") the build deps and he hosts his code using GIT.

```
git clone git://deadbeef.git.sourceforge.net/gitroot/deadbeef/deadbeef
```

Thanks. Yes, right, I saw the Wiki but wasnt sure what to do exactly, a how to would not be bad. Normally Im compiling some things myself but not every time I have luck with such processes if I forget some command.

---

### Post by MetalMusicAddict on 2011-02-22
This bit of text pasted into a terminal *should* take care of you.

```
[SIZE="1"]sudo apt-get install libasound2-dev libpulse-dev libmad0-dev libwavpack-dev libsndfile1-dev libcdio-dev libcddb2-dev automake libtool libsamplerate0-dev libgtk2.0-dev libavformat-dev libcurl4-gnutls-dev libdbus-1-dev libfaad-dev intltool checkinstall git autotools-dev -y ; git clone git://deadbeef.git.sourceforge.net/gitroot/deadbeef/deadbeef DeaDBeef-GIT ; cd DeaDBeef-GIT ; ./autogen.sh ; ./configure --prefix=/usr ; make -j5 ; sudo checkinstall --pkgname=deadbeef --pkgversion "0.4.4+git`date +%Y%m%d`" --backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman=yes --default ; cd[/SIZE]
```

This will grab the build dependencies, build a basic package and skip any additional questions. If you want to be more interactive, take off the "--default" part at the end of the above text.

Side note: I'm using the "*--pkgversion "0.4.4+git`date +%Y%m%d`r`"*" part to keep what build it is strait but I'd rather do something like SVNs revision number.

Anyone know a way to grab what current GIT revision we've just grabbed?

---

### Post by ivanovnegro on 2011-02-22
> **MetalMusicAddict said:**
> This bit of text pasted into a terminal *should* take care of you.

```
[SIZE="1"]sudo apt-get install libasound2-dev libpulse-dev libmad0-dev libwavpack-dev libsndfile1-dev libcdio-dev libcddb2-dev automake libtool libsamplerate0-dev libgtk2.0-dev libavformat-dev libcurl4-gnutls-dev libdbus-1-dev libfaad-dev intltool checkinstall git autotools ; git clone git://deadbeef.git.sourceforge.net/gitroot/deadbeef/deadbeef DeaDBeef-GIT ; cd DeaDBeef-GIT ; ./autogen.sh ; ./configure --prefix=/usr ; make -j5 ; sudo checkinstall --pkgname=deadbeef --pkgversion "0.4.4+git`date +%Y%m%d`r`" --backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman=yes --default[/SIZE]
```

This will grab the build dependencies, build a basic package and skip any additional questions. If you want to be more interactive, take off the "--default" part at the end of the above text.

Side note: I'm using the "[SIZE="1"]*--pkgversion "0.4.4+git`date +%Y%m%d`r`"*[/SIZE]" part to keep what build it is strait but I'd rather do something like SVNs revision number.

Anyone know a way to grab what current GIT revision we've just grabbed?

Thank you, I did it manually and it worked, but it is a good question how to stay current with the versions.

---

### Post by ivanovnegro on 2011-02-22
Ok, I have now the latest I think, Deadbeef devel but I have no sound with it, in the settings I also cannot find the sound output like in the stable version, seems to be a bug/work in progress or something right now, Im not sure.

---

### Post by MetalMusicAddict on 2011-02-22
> **ivanovnegro said:**
> it is a good question how to stay current with the versions.
If you don't quite know what I mean, SVN (svnversion) and BZR (bzr revno) have ways to print the current revision. I don't *think* theres a GIT equivalent, so I just chose to print the date.

> **ivanovnegro said:**
> Ok, I have now the latest I think, Deadbeef devel but I have no sound with it, in the settings I also cannot find the sound output like in the stable version, seems to be a bug/work in progress or something right now, Im not sure.

Got a screenshot? I can choose from a couple of different output types here.

If something's weird, try to remove any deadbeef packages and make your source folder clean. ("make clean") There might be something hanging around from your old setup.

---

### Post by ivanovnegro on 2011-02-22
> **MetalMusicAddict said:**
> If you don't quite know what I mean, SVN (svnversion) and BZR (bzr revno) have ways to print the current revision. I don't *think* theres a GIT equivalent, so I just chose to print the date.



Got a screenshot? I can choose from a couple of different output types here.

If something's weird, try to remove any deadbeef packages and make your source folder clean. ("make clean") There might be something hanging around from your old setup.

You were right, I cleaned it and it works.
Now I will test if the bug is gone.
I think for the Git repos exist also git fetch like for SVN versions.
If you are also using the latest dev version of Deadbeef how do you update then?

---

### Post by ivanovnegro on 2011-02-22
And yes, so far, the annoying bug is gone, great!
Now I can enjoy the superb sound again.

---

### Post by MetalMusicAddict on 2011-02-22
> **ivanovnegro said:**
> If you are also using the latest dev version of Deadbeef how do you update then?

I was using the PPA until I figured out my little HOW-TO method above.

---

### Post by ivanovnegro on 2011-02-22
> **MetalMusicAddict said:**
> I was using the PPA until I figured out my little HOW-TO method above.

Yes, I understand but I wanted to know how we can update now to possible newer versions?

---

### Post by ivanovnegro on 2011-02-23
To be on the latest revision you have to do simply 'git fetch' and then  repeat 'make && sudo make install'. This is the procedure for Git.

---

### Post by shantiq on 2011-02-24
hi ivanov   thought about your requirements for a library type player

[COLOR="Blue"]**[[B]http://www.foobnix.com/**]([B]http://www.foobnix.com/**)
[/B][/COLOR]

```
sudo add-apt-repository ppa:foobnix-player/foobnix
sudo apt-get update
sudo apt-get install foobnix

```


not bad at all although the sound is nowhere near deadbeef quality
but

* it has a wicked library system
* you can load up your own image to decorate it
* and it will link your playing track to similar artists which is brilliant to discover new music  click on info for that (see screenshot2)


see attached screenshots

---

### Post by shantiq on 2011-02-24
also for guys who really want a good sound i have 2 alternative routes here both command line but really nice



1.   simple    using SoX   ```
sudo apt-get install sox
```

enter you music folder 

and run

```
play *flac 
```  or whatever it is you want to play


you can add effects   ```
play *flac bass +5
```   sounds good to me    see screenshot 1


2.   **and this is gold**


nvlc which is part of the vlc package


enter your music folder in your terminal

```
cd Music
```    or wherever your trax are


then **simply** enter ```
nvlc */./*
```    you will get a player in your terminal  where you can pause/fast forward (use arrows on keyboard)/see track info    and the sound is brilliant


see screenshot 2


**Both ways produce great sound!!**

---

### Post by ivanovnegro on 2011-02-24
> **shantiq said:**
> hi ivanov   thought about your requirements for a library type player

[COLOR="Blue"]**[[B]http://www.foobnix.com/**]([B]http://www.foobnix.com/**)
[/B][/COLOR]

```
sudo add-apt-repository ppa:foobnix-player/foobnix
sudo apt-get update
sudo apt-get install foobnix

```


not bad at all although the sound is nowhere near deadbeef quality
but

* it has a wicked library system
* you can load up your own image to decorate it
* and it will link your playing track to similar artists which is brilliant to discover new music  click on info for that (see screenshot2)


see attached screenshots

Thanks for some new ideas. I know Foobnix but it seems to me too strong centered on online music and this stuff. Are you sure it is fast for large libraries, I doubt it. I tested it yet and didnt like it so much. I have the feeling that all Python apps are slow, dont know why.
And yes, if the sound is not good as in Deadbeef, no way!
Im enjoying ultimateley more and more Deadbeef, as I said my music collection is perfectly in order. Yes, its a pity that Deadbeef doesnt have a library but maybe this thing could slow this app also down like the others. I repeat, the sound is SUPERB!!!
I found out for all players (I tested them all!), 30.000 tracks or something less is the limit to run without glitches or problems.
I have only to get used to it more and more to use my file browser and thats all.

---

### Post by MetalMusicAddict on 2011-03-17
Hmm... It worked once for me. Cover art. I've followed the directions on the PPA and self-compiled versions. I can't get art to show for the live of me. :(

Tips?

---

### Post by shantiq on 2011-03-18
hi MMA have you tried to follow [**this ?**]("http://ubuntuforums.org/showpost.php?p=9516552&postcount=15")


Not exactly intuitive but that is the way it is rigged up :KS

---

### Post by MetalMusicAddict on 2011-03-18
> **shantiq said:**
> hi MMA have you tried to follow [**this ?**]("http://ubuntuforums.org/showpost.php?p=9516552&postcount=15")


Not exactly intuitive but that is the way it is rigged up :KS

Yeah. I followed your post the 1st time. :) I absolutely only want local or embedded covers (i spent alot of time making perfect hi-res ones) so I dont use the lastfm or the other fetching options. My mask is: ****cover*.png;*front*.jpg;*cover*.jpg*** My in-folder and embedded covers are PNGs. (wanted to use free formats)

Really odd thing is, with the cfg I had working, I would try to use the same settings on another box and am in the same spot I'm in now. So weird.

[[IMG]http://img200.imageshack.us/img200/3724/screenshotlg.th.jpg[/IMG]](http://img200.imageshack.us/img200/3724/screenshotlg.jpg)

---

### Post by shantiq on 2011-03-18
hmmmmmmmmmmmmmm


do not know much more than i have already put there


this is what i have got for mine

```
*cover*.jpg;*front*.jpg;cover.*png;[COLOR="Red"]cover.*g[/COLOR]
```


maybe add the red bit?  cannot remember where it came from but supposed to cover other eventualities...
beyond that i simply do not know


ps    and by the by never realized you could make your image so small cool dude thanx for that :KS

[CENTER]
[[IMG]http://img834.imageshack.us/img834/1337/freedomination25.th.png[/IMG]](http://img834.imageshack.us/img834/1337/freedomination25.png)[/CENTER]

---

### Post by shantiq on 2011-03-26
save as an m3u and create a new playlist

```
http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls
http://91.121.92.167:8900
http://sverigesradio.se/topsy/direkt/1603-hi-mp3.pls
http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls
http://www.radiosuisseclassique.ch/live/mp3.m3u
http://radioclasica.rtve.stream.flumotion.com/rtve/radioclasica.mp3.m3u
http://www.dr.dk/netradio/Metafiler/ASX/DR_P2_128.asx
http://http-live.sr.se/p2musik-aac-192
http://bbc.co.uk/radio/listen/live/r3.asx
http://music.myradio.com.ua:8000/Classica128.ogg
mms://mms.rondofm.fi/RondoHF
http://www.tv-radio.com/station/france_musique_mp3/france_musique_mp3-128k.m3u
http://listen.radionomy.com/radio-mozart
http://myradio.com.ua/alias/Classica128.m3u
http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u
http://www.rozhlas.cz/audio/download/ddur_maxogg.m3u
http://mediau.yle.fi/liveklassinen
http://www.play.cz/radio/classic128.asx
http://broadcast.infomaniak.ch//radioclassique-high.mp3.m3u
http://avw.mdr.de/livestreams/mdr_figaro_live_128.m3u
http://avw.mdr.de/livestreams/mdr_klassik_live_128.m3u
http://ndrstream.ic.llnwd.net/stream/ndrstream_ndrkultur_hi_mp3.m3u
http://www.listenlive.eu/mr3.m3u
http://82.135.234.195/Klasika.asx
http://shoutcast.omroep.nl:8074/listen.pls
http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u
http://live.slovakradio.sk:8000/Devin_256.mp3.m3u
http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls

http://media-ice.musicradio.com/ClassicFMMP3.m3u
mms://live.rfn.ru/rcult









```


mostly from [here]("http://www.listenlive.eu/classical.html")

---

### Post by starws on 2011-05-13
[_DeaDBeeF 0.5.0 is available _]("http://deadbeef.sourceforge.net/posts/deadbeef_0.5.0_has_finally_arrived%21.html")

Key features:
support for output in 8,24,32,float32 bits per sample and samplerate up to 192kHz 
multichannel output support
new plugin for importing and exporting M3U and PLS formats
improved metadata editing, allowing modification of any text fields,  including custom fields; added support for editing metadata for multiple  selected tracks
new converter plugin for format transcoding
added album covers to OSD notifications

---

### Post by shantiq on 2011-05-27
[B]some important information from Alexei on site 2011/05/15
[/B]


> if you are building from tarball, and wondering where are the aosdk, DUMB, shn and some other plugins -- they are not there :) they were moved out of tarball to get the player into linux distributions with strict licensing policies, where they want clean tarballs, without any traces of code that's not GPL licensed.

but plugins are still in git, and they are in the static build archive. i will also prepare them as separate downloads a bit later.



Personally shn is a must and I use 64-bit so the only way i could see was to remain with
[0.4.4 ]("http://sourceforge.net/projects/deadbeef/files/deadbeef-0.4.4.tar.bz2/download")AND[** here**]("http://ubuntuforums.org/showpost.php?p=10913615&postcount=68")


 there is [a plugin]("http://deadbeef.sourceforge.net/plugins.html") but only for 32-bit



if anyone can think of a way to run 0.5.1 with 64-bit with shorten i will love to find out...

---

### Post by ivanovnegro on 2011-05-27
> **shantiq said:**
> [B]some important information from Alexei on site 2011/05/15
[/B]






Personally shn is a must and I use 64-bit so the only way i could see was to remain with
[0.4.4 ]("http://sourceforge.net/projects/deadbeef/files/deadbeef-0.4.4.tar.bz2/download")


 there is [a plugin]("http://deadbeef.sourceforge.net/plugins.html") but only for 32-bit



if anyone can think of a way to run 0.5.1 with 64-bit with shorten i will love to find out...

This wont solve your problem, but he also said that the 32 bit build should also run fine on 64 bit, the [last part]("http://deadbeef.sourceforge.net/portable.html"). Maybe until Alexey fix this.

Anyway, so far, DeaDBeeF gets better and better.

---

### Post by shantiq on 2011-05-27
ivanov the 0.4.4 has shorten on board by default and works on 64-bit straight off

:KS   that is why i hold back for the time being

---

### Post by shantiq on 2011-06-07
if you were to want to remain with 0.4.4 ( most of you will not )this will do it


[B]for 64-bit
[/B]
```
wget http://sourceforge.net/projects/deadbeef/files/debian/0.4.4/deadbeef_0.4.4-1_amd64.deb/download
cd Downloads
sudo dpkg -i download
```


[B]for 32-bit 
[/B]

```
wget http://sourceforge.net/projects/deadbeef/files/debian/0.4.4/deadbeef_0.4.4-1_i386.deb/download
cd Downloads
sudo dpkg -i download
```

---

### Post by DDZ on 2012-03-14
> **shantiq said:**
> Equalizer Presets DO NOT DELETE.zip (4.0 KB, 22 views)

I discovered DeaDBeef yesterday through a magazine. I just collected all equalizer presets I could find (from _[here]("http://www.hdvietnam.com/diendan/4-software-ky-thuat-phan-mem/76319-huong-dan-thao-luan-gioi-thieu-moi-van-de-ve-nghe-nhac-lossless-bang-foobar-110.html#post1583119")_, _[here]("http://alexander-gg.deviantart.com/art/foobar-Rock-104365845?q=boost%3Apopular%20in%3Acustomization%2Fskins%2Fmedia%2Ffoobar2000%20equalizer&qo=0")_ and _[here]("http://joekingdesign.deviantart.com/art/foobar2000-custom-equalizer-283023203?q=boost%3Apopular%20in%3Acustomization%2Fskins%2Fmedia%2Ffoobar2000%20equalizer&qo=1")_) and converted them from Foobar2000 to DeaDBeef format. There are 63.
If anyone has chillout-lounge-electro.feq, latino-salsa.feq, acid-nujazz.feq, indie-punk.feq... from _[this site]("http://maj-kompjuter.blogspot.com/2007/08/foobar-2000-equalizer-presetssettings.html")_ (the link is dead), it will be nice ! ;)

---

### Post by shantiq on 2012-03-14
excellent man the more the merrier  :KS:KS


only thing is i use 0.4.4 version and .ddbeq is a non-starter for me it has to be .feq  ;  maybe [with all respect] the Irish version  ::::]]]]]


**PS  easy to correct manually tho just changing it works** maybe people can use .ddbeq on later versions

or cd to folder and run


```
for FILE in *.ddbeq;do mv -v "${FILE}" "${FILE%.ddbeq}.feq";done

```


also converted and zipped as attachment if anyone cannot be bothered to do it themselves :]   And again DDZ many thanx for these

**PS2**  would be so cool to get the amazing crystaliser plugin from Audacious too to work on Deadbeef too

---

### Post by DDZ on 2012-03-15
> **shantiq said:**
> **PS2**  would be so cool to get the amazing crystaliser plugin from Audacious too to work on Deadbeef too
This was what I thought! ;)

---

### Post by shantiq on 2012-03-15
:KS:KS:KS  hi again DDZ   not sure it is all that easy tho  '' with crystalizer :KS

---

### Post by shantiq on 2012-05-05
in 12.04 Pangolin

It now has the ability to play from zip and shorten has been re-instated
**[0.5.2.is the version]("http://deadbeef.sourceforge.net/")**



To install from source   you will need these


> sudo apt-get install autotools-dev libasound2-dev libcddb2-dev libcdio-dev libcurl4-gnutls-dev libflac-dev libgtk2.0-dev \
libmad0-dev libogg-dev libsamplerate0-dev libsndfile1-dev libvorbis-dev libwavpack-dev libavformat-dev libavcodec-dev \
libavutil-dev libpulse-dev libdbus-1-dev libpango1.0-dev libx11-dev   libcddb2-dev \
   automake libtool  libgtk2.0-dev  libcurl4-gnutls-dev libdbus-1-dev libfaad-dev \
   intltool libimlib2-dev libzip-dev yasm libmad0   

** if any of the devs do not come up when you run ./configure go to synaptic and add the one the dev depends on or from command line**

**ie libwavpack-dev   requires libwavpack1 etc...   **         depends on what you have already simply enter the dev in synaptic then remove -dev
you will easily see what it depends on


then get[ **source code  **]("http://sourceforge.net/projects/deadbeef/files/deadbeef-0.5.2.tar.bz2/download")

untar then go into folder  ```
cd deadbeef-0.5.2
``````
./configure
```Should show this on plugins
```
Plugin Summary:

    stdio: yes - Standard IO plugin
    gme: yes - chiptune music player based on GME
    nullout: yes - NULL output
    alsa: yes - ALSA output
    sid: yes - SID player based on libsidplay2
    ffap: yes - Monkey's audio (APE) decoder
    lastfm: yes - last.fm scrobbler
    mpgmad: yes - mpeg player based on libmad
    vorbis: yes - ogg vorbis player
    flac: yes - flac player
    wavpack: yes - wavpack player
    sndfile: yes - PCM (wav,aiff,etc) player based on libsndfile
    vtx: yes - vtx file player (ay8910/12 emulation)
    adplug: yes - adplug player (OPL2/OPL3 emulation)
    vfs_curl: yes - http/ftp streaming support
    cdda: yes - cd audio player
    gtkui: yes - GTK user interface
    hotkeys: yes - Global hotkeys support
    ffmpeg: yes - ffmpeg codecs
    oss: yes - oss output plugin
    pulse: yes - PulseAudio output plugin
    artwork: yes - Cover art plugin
    supereq: yes - Equalizer based on Super EQ library by Naoki Shibata
    notify: yes - notification-daemon support plugin
    shellexec: yes - shell commands plugin
    musepack: yes - musepack player plugin
    wildmidi: yes - WildMidi player plugin
    tta: yes - TTA player plugin
    dca: yes - libdca (DTS Audio) player plugin
    aac: yes - AAC player (m4a, aac, mp4) based on FAAD2
    mms: yes - mms streaming support
    dsp_src: yes - High quality samplerate conversion using libsamplerate
    m3u: yes - M3U and PLS playlist support
    vfs_zip: yes - zip archive support
    converter: yes - plugin for converting files to any formats
    psf: yes - PSF format plugin, using AOSDK
    dumb: yes - DUMB module plugin, for MOD, S3M, etc
    shn: yes - SHN plugin based on xmms-shn
    mono2stereo: yes - mono2stereo DSP plugin

``````
make
``````
sudo  make install
```    takes a while that way but then you have the latest:KS version on latest Ubuntu

[B]
===============[/B]


a shorter route is [**Alexei's PPA**]("https://launchpad.net/%7Ealexey-smirnov/+archive/deadbeef?field.series_filter=oneiric") and simply change software sources to Oneiric as no version for Pangolin ready yet


**====================**

Looking like a busted plectrum:KS

---

### Post by faucon50 on 2012-05-08
Hello,

Seens my upgrade to Xubuntu Precise with deadbeef from PPA (oneiric) it doesn't load cdda and vfs_zip plugins but they are both in /usr/lib/deadbeef as before! I don't know what's wrong... Thank you for any suggestion.

---

### Post by shantiq on 2012-05-08
ok av you tried to add the lib files then reinstall  the PPA
first remove it


 try   ```
sudo apt-get install libzip-dev libcdio-cdda1  libcdio-cdda-dev
```  

then go for PPA again [ i think they should be picked up then i hope:KS]


should equip you for zip && cdda if not already installed


or take the long route in previous post and add those libs to it



see if that works   ...

---

### Post by faucon50 on 2012-05-08
Thanks for your fast reply :) I got the answer from the dev right now, here:

[http://deadbeef.sourceforge.net/posts/deadbeef_0.5.2_is_out.html](http://deadbeef.sourceforge.net/posts/deadbeef_0.5.2_is_out.html)

So if someone is in the same situation they are 3 ways, compile or wait for the PPA update for Precise or you can get statically-linked plugins from static build. I have no idee about how to do the statically linked plugins. :(

---

### Post by pepperjinks on 2012-05-19
I'm having trouble installing deadbeef.

Followed instructions for installing on Pangolin. Input the first command  (sudo) in terminal. After I input the second once the first was done, it said libmad0-dev: command not found.
What should I do?

---

### Post by shantiq on 2012-05-19
> **pepperjinks said:**
> I'm having trouble installing deadbeef.

Followed instructions for installing on Pangolin. Input the first command  (sudo) in terminal. After I input the second once the first was done, it said libmad0-dev: command not found.
What should I do?


```
sudo apt-get install libmad0
```   needs to be in there as well [will add it to list above]

if any of the devs do not come up go to synaptic and add the one the dev depends on or from command line



see how that goes

---

### Post by komputes on 2013-01-01
\\:D/ Great MP3 Player!

Got fed up with Banshee so I just tried deadbeef from the deb package on the project website and this is really nice. It freezes a bit in Raring alpha using Unity, but works better in gnome-session-fallback. It is the fastest program I have used for MP3 management. I really like that it shows you hidden comment that iTunes adds to MP3s.

A few things it lacks (or I don't know how to do):
-Immutable Library (dragging from one playlist to another moves songs instead of copying)
-Copy songs from search window to playlist (or live search)
-Ratings support (since I use different players embed ratings is better)
-Export support (to export songs so I can add it to another tool to transfer to iPod)
-Apple Device Support (this one is tricky, I know)

If anyone could give me help with  any these that would be nice.

---

### Post by starws on 2013-01-06
> **komputes said:**
>  
-Immutable Library (dragging from one playlist to another moves songs instead of copying)


just use ctrl+move for copy

> **komputes said:**
>  
-Copy songs from search window to playlist (or live search)
-Ratings support (since I use different players embed ratings is better)
-Apple Device Support (this one is tricky, I know)


already in feature requests

---

### Post by komputes on 2013-01-07
Thanks starws, that worked like a charm!

The biggest thing that is blocking me now is that I'd like to transfer over a selection of songs to my iPod. I don't expect deadbeef to do this but at least I need a way to copy songs in a playlist so that they can be imported in a program which supports this device.

First I need to export/copy files in the playlist to a folder. This is not working for me but could be the beginning of a workaround or solution. This is as far as I got:

1) Export pls file

2) Filter out the path of the files
```
cat playlist.pls | grep / | cut -d / -f "2-100" | sed -e 's/media/\/media/'| sed -e 's/\ /\\\ /g' > pls.tmp
```

3) for loop to copy every file to playlist dir
```
for i in `cat pls.tmp` ; do cp $i /home/komputes/Desktop/playlist/; done;
```

ATM the for loop is getting stuck on the delimiter so the copy won't work.

---

### Post by Hate on 2013-04-19
I'd rather post here than open a new topic for my problem.

I've enable the OSD notify, but, even if enabled from the options, it just shows the deadbeef symbol instead of the album art in the notification...anyone knows how to fix this ? (I'm on Ubuntu 12.10 )

---

### Post by starws on 2013-04-19
> **Hate said:**
> I'd rather post here than open a new topic for my problem.

I've enable the OSD notify, but, even if enabled from the options, it just shows the deadbeef symbol instead of the album art in the notification...anyone knows how to fix this ? (I'm on Ubuntu 12.10 )

Does it shows album art for this track in playlist window?

---

### Post by Hate on 2013-04-21
> **starws said:**
> Does it shows album art for this track in playlist window?

yes

---

### Post by starws on 2013-04-23
> **Hate said:**
> yes

Deadbeef version is 0.5.6 ?

How did you install deadbeef? From ppa:starws-box/deadbeef-player ? From [http://deadbeef.sourceforge.net/download.html](http://deadbeef.sourceforge.net/download.html) ?

Is "Show album art" option enabled in OSD Notify plug-in configuration?

---

### Post by Hate on 2013-04-23
> **starws said:**
> Deadbeef version is 0.5.6 ?

How did you install deadbeef? From ppa:starws-box/deadbeef-player ? From [http://deadbeef.sourceforge.net/download.html](http://deadbeef.sourceforge.net/download.html) ?

Is "Show album art" option enabled in OSD Notify plug-in configuration?

I'm running 0.5.5 from ubuntu repositories , and the plugin is correctly configured...should I install deadbeef from that repo ?

---

### Post by starws on 2013-04-24
> **Hate said:**
> I'm running 0.5.5 from ubuntu repositories 

There is no deadbeef in ubuntu repositories, see [https://bugs.launchpad.net/ubuntu/+bug/572977](https://bugs.launchpad.net/ubuntu/+bug/572977)

> **Hate said:**
> should I install deadbeef from that repo ?

Yes, these sources are tested and highly recommended.

---

### Post by Hate on 2013-04-24
thanks, installing from that repo worked. :)

---

### Post by syntaxerror74 on 2013-10-27
Yay, this thing rules. Alexey has done one of the greatest jobs ever with this software. And that's simply because years ago, the only one that could hold (half) a candle to deadbeef was rhythmbox...

There is only two features I'd like to have, but I prefer not to bother Alexey about them (yet):

(1) "Physical move support". That is, when you have a bigger playlist and suddenly spot a Death Metal album in Folk section, the only way to move it where it belongs is:
 -- Use Nautilus (or similar) to physically move the album
 -- Remove album file names from current playlist
 -- Manually readd moved album to current playlist

ddb's ever-unrivaled Win32/64 competitor foobar2000 still can do this in a more convenient fashion.

(2) A way to search for PATHS

This is bugging me most. As most "iTuners" have their music catalogued in a wagonload of folders, this may sometimes be the only way to find an album by name, since it doesn't happen too rarely that the tracks are simply generic: track01.mp3, track02.mp3...

So AFAICS currently the only way to find an album by name in a multi-album playlist is to remember a single track of the album, since not even a tiny part of the file path will be parsed in search. TRACK NAMES ONLY (and some of their usually irrelevant metadata)

---

### Post by shantiq on 2013-10-29
thing is [**[COLOR=#000000]syntaxerror74[/COLOR]**]("http://ubuntuforums.org/member.php?u=1867082") deadbeef is not really a library player is it?  not sure it was ever designed to be one of those    ...    more of a ad hoc player with the ability to store parallel playlists with the tabs
[clementine]("http://www.clementine-player.org/") would be a better choice for a library or even [atunes]("http://www.atunes.org/")

---

