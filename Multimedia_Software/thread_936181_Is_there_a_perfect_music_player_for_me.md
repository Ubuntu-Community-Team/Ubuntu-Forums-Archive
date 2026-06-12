---
title: "Is there a perfect music player for me?"
date: 2008-10-02
forum: Multimedia Software
---

### Post by nikosm on 2008-10-02
Dear community,

I used to be a windows user and very happy with winamp. Now that I switched to Ubuntu, the natural choice was xmms. However, the two are not identical.
Compared to winamp:
 1)[-] xmms does not support unicode tags
 2)[+] xmms has a "physically remove file" menu item
 3)[-] xmms cannot queue a song more than once consequently
 4)[-] in xmms you cannot select several files and drag them as a group
 5)[-] when minimizing xmms, the playlist remains visible (but if you press the desktop button, both go away)
 6)[-] you cannot drag xmms to a different workspace (I mean the compiz feature)

I turned to audacious.
 - it resolved 1) which is very important and also 5), but missed on 2), the only advantage I noticed xmms had over winamp. Also, it crashes from time to time [COLOR="DarkOrange"](but maybe that's my installation, there's something wrong with the multimedia - btw, does anybody know how I can cleanup and reinstall all codecs and other multimedia stuff? ...without reinstalling ubuntu? :). Or is a systematic search for the error inevitable?). [/COLOR]Furthermore, it lacks the extremely light feeling of xmms, e.g. if you press next, it takes about a second before it stops playing the current song (which is not a big deal, but your brain is even faster in starting to wonder if it missed the click).

So, I was wondering if anybody has used a music player that is closer to my imaginary ideal:
 + very lightweight
 + unicode support
 + easy way to physically delete files
 + no problems in window managing (dragging, minimizing)
 + extensible with plugins, skinnable, good keyboard control, like xmms

Thank you very much for any advice

Nikos

Disclaimer: I am not complaining about anything, I know some of the things I am looking for can be very subjective, and I think all 3, xmms, winamp and audacious are GREAT programs! :) Just trying to go from very good to excellent ;).

---

### Post by kostkon on 2008-10-02
Nevermind.

---

### Post by DrMega on 2008-10-02
If you select multiple files from a folder, you can drag them all in one go into the xmms playlist window.

---

### Post by nikosm on 2008-10-02
> **DrMega said:**
> If you select multiple files from a folder, you can drag them all in one go into the xmms playlist window.

Sorry, that was not what I meant. I wanted to say that if you have a playlist

[COLOR="Blue"]1
2[/COLOR]
[COLOR="Red"]3
4
5[/COLOR]

and you want to have

[COLOR="Red"]3
4
5[/COLOR]
[COLOR="Blue"]1
2[/COLOR]

in winamp you could mark 1 and 2 and drag them to the bottom together. In xmms and audacious you have to first drag 1 to the bottom and afterwards drag 2 to the bottom.

---

### Post by uvdevnull on 2008-10-09
+1

I'm also in search of a Winamp replacement.  I haven't been able to find a Media Library manager quite as good as Winamp or iTunes, hence my search continues.  Have you tried Songbird?

---

### Post by Asgar on 2008-10-09
Where can i get xmms from?

---

### Post by nikosm on 2008-10-09
> **Asgar said:**
> Where can i get xmms from?
It's in the repositories, you can install it with sudo apt-get install xmms

---

### Post by nikosm on 2008-10-09
> **uvdevnull said:**
> +1

I'm also in search of a Winamp replacement.  I haven't been able to find a Media Library manager quite as good as Winamp or iTunes, hence my search continues.  Have you tried Songbird?

No, I haven't tried songbird, it doesn't seem to be as light-weight a music player as I am looking for. I must say that I never used the media library manager of winamp, so I don't miss it. I miss some of the other features of it, though I can say that audacious is quite good too.

---

### Post by WWSmith36 on 2008-10-09
There is no such thing as the perfect music player.

I used to be a big Winamp fan in my windows days.  Currently I feel the best player out there is Amarok.  It is located in the universe repository.  I believe it has all the features you are looking for.  I´m not sure a the the skins part, because I use the funky-monkey theme for it.

It is actually a kde application but it also compatible with gnome and runs fine.  Occasionally you might find a plugin that needs a library which isn´t installed, it will tell you what its looking for so you can go get it.

Music brainz file tagging requires
sudo apt-get install libtunepimp5-mp3

So definately install this if you plan of tagging file with Amarok.

Good Luck

---

### Post by SuperSonic4 on 2008-10-09
I agree with amarok. But I'd go with 1.4.x rather than 2 beta 2

---

### Post by forger on 2008-10-09
um... [audacious]("http://audacious-media-player.org")?
```
sudo apt-get install audacious audacious-plugins-extra audacious-plugins
```

---

### Post by nikosm on 2008-10-09
Thanks everybody for the suggestions. I tried amarok but I really missed the key (not key-combination) control that winamp is offering. 

I tried audacious, I am actually currently using it, but it's a bit slow responsive compared to winamp or xmms, making it feel a bit heavy, and you can not physically delete a file (am I the only one that thinks this feature is vital?).

For the moment I am sticking audacious, but if there were unicode support for xmms, I'd be using that.

Thanks again for sharing your experiences,

Nikos

---

### Post by forger on 2008-10-10
Have you installed all the plugins for xmms?
```
sudo apt-get install xmms2-plugin-all
```

e.g. > apt-cache show xmms2-plugin-pls
Description: XMMS2 - PLS playlist plugin
 This package enables xmms2 to read pls playlists.

> xmms2-plugin-all
  Depends: xmms2-plugin-curl
  Depends: xmms2-plugin-smb
  Depends: xmms2-plugin-mms
  Depends: xmms2-plugin-vorbis
  Depends: xmms2-plugin-flac
  Depends: xmms2-plugin-faad
  Depends: xmms2-plugin-modplug
  Depends: xmms2-plugin-mad
  Depends: xmms2-plugin-musepack
  Depends: xmms2-plugin-avcodec
  Depends: xmms2-plugin-wma
  Depends: xmms2-plugin-sid
  Depends: xmms2-plugin-oss
  Depends: xmms2-plugin-alsa
  Depends: xmms2-plugin-jack
  Depends: xmms2-plugin-id3v2
  Depends: xmms2-plugin-icymetaint
  Depends: xmms2-plugin-daap
  Depends: xmms2-plugin-ices
  Depends: xmms2-plugin-lastfm
  Depends: xmms2-plugin-vocoder
  Depends: xmms2-plugin-ao
  Depends: xmms2-plugin-mp4
  Depends: xmms2-plugin-xml
  Depends: xmms2-plugin-xspf
  Depends: xmms2-plugin-cdda
  Depends: xmms2-plugin-cue
  Depends: xmms2-plugin-pls
  Depends: xmms2-plugin-asx
  Depends: xmms2-plugin-rss
  Depends: xmms2-plugin-m3u
  Depends: xmms2-plugin-ofa
  Depends: xmms2-plugin-asf
  Depends: xmms2-plugin-normalize
  Depends: xmms2-plugin-pulse
  Depends: xmms2-plugin-karaoke
  Depends: xmms2-plugin-airplay
  Depends: xmms2-plugin-speex
  Depends: xmms2-plugin-gme
  Depends: xmms2-plugin-gvfs

---

### Post by nikosm on 2008-10-10
hi forger,

> **forger said:**
> Have you installed all the plugins for xmms?
```
sudo apt-get install xmms2-plugin-all
```


I just did, still no unicode support. By the way, are xmms2 and xmms different programs? Because I installed the xmms2 plugins like you told me and then started xmms to see if there is any difference. Was that wrong?

Thanks,
Nikos

---

### Post by forger on 2008-10-11
Ah my bad, I thought you wanted to open .pls playlist files, misread one of your previous posts :)

---

### Post by RandyNose on 2008-10-17
Install Amarok from the repository. I run Gnome, And use WinAmp with Windows, if I happen to be on that machine (only boot that machine up for a few hours every couple of months)...   There are some other great Audio Players in the repositories, so I'd suggest trying a few more.. Banshee, BMP... etc... Heck Try MPlayer with Audio files and see how you like it....

---

### Post by JeppeM on 2008-10-18
I just downloaded and installed songbird. Being a mozilla project, I have confidence in the quality of the program, as well as the active development. It's actually rather nice, nothing like winamp though, which I used back on windows. I do like it a lot though, and will keep exploring it I think :) If you don't find anything else, give it a try ;) I also heard that it's great with ipods, which will benefit me personally in a few weeks when I get my own (and first) ipod

I did try amarok as well, but it just didn't feel right, and i also had some problems with it not behaving all that nicely..

---

### Post by Zack McCool on 2008-10-18
I am a big fan of Amarok, but this thread inspired me to try Songbird and it looks pretty nice.  Certainly worth giving it a few days of getting used to to see if it suits you...

---

### Post by JeppeM on 2008-10-18
It looks like there's going to be a major release of songbird within a month - At least thats what the blogs on the songbird site says. Once the version 1.o has been released, i think that songbird could really gather a good userbase, and be a great mediaplayer.

It just needs a good video players as well, and i'll uninstall all the other stuff i have on my system :P

---

### Post by nikosm on 2008-10-19
Thanks everybody for the suggestions.

Songbird is definitely a nice and feature-rich media player, it would be without doubt great to play music during a party, but I am rather looking for something different, I want an as light-weight as possible music player that is able to run discretely in the background while I am using the computer to work. XMMS is so efficient (e.g.: press the right-arrow key to see how fast it scans through a file while playing, or the "b" key to see how fast it skips through the playlist) that it impresses me to see what can be done with my unspectacular hardware when it is used properly :). As I said, XMMS would be a dream if it didn't have these couple of "bugs" (especially unicode support and the playlist escaping the minimization). For the time I use xmms mostly and audacious for unicode tagged mp3 files.

XMMS is a player I am definitely very happy with :)

Thanks again for all the suggestions,
Nikos

---

### Post by ratmandall on 2008-10-19
Rhythmbox works great.

---

