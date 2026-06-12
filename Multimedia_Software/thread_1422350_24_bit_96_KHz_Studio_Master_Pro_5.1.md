---
title: "24 bit 96 KHz Studio Master Pro 5.1"
date: 2010-03-05
forum: Multimedia Software
---

### Post by raymondvillain on 2010-03-05
Running Karmic on a 64 bit AMD processor, using Amarok and Rythmbox to play music that I have ripped from CD's.

I just became aware that 16 bit 44.1 KHz CD music files (in FLAC format) are not the only option.  I can (and so can anybody else) download 24 bit, 96 kHz in "Pro" and "Studio Master" 5.1 files (in FLAC) formats.

My installation of Amarok doesn't play either of these formats.  VLC and Totem movie player play them with no hassles.

I do not have a surround sound audio card (at least I don't think so) installed in my machine.

What are all you really heavy music heads using to play these 24 bit 96 kHz files?

---

### Post by AdrianVeidt on 2010-03-05
I guess the flip answer would be "anything but Xine". But that's really the case, since Gstreamer, Mplayer, VLC and whatnot all play them fine. Even the Xine 1.2, which is unstable, has not implemented reliable support for these files (just tested it).

I'd recommend Banshee, which uses Gstreamer as the backend.

---

### Post by mc4man on 2010-03-05
Overall I find xine based players ( amarok,pana in particular) to be more capable than any gstreamer player except for these type files  - it's something that occurred in xine-libs 1.16 and hasn't  been fixed as of yet or ever ...?
(xine-lib 1.15 plays them fine

---

### Post by AdrianVeidt on 2010-03-05
My mistake. Xine 1.2 can play 24-bit flac files, but it still has trouble with 24-bit 96 khz 5.1 flac files.

---

### Post by mc4man on 2010-03-05
I just noticed this ( so it was somewhat  fixed, too bad lucid will probably stay at 1.17 
2010-02-23:
	> Release
 xine-lib 1.1.18
 A new version of xine-lib is available. This release adds support for
       WMA Pro and basic support for Quicktime media links (much better support
       is present in the 1.2 branch) and has various fixes for 24-bit FLAC and
       LPCM, TTA, and AAC in Flash video; there's also one important fix for
       DXR3 users, allowing xine-lib to work with recent versions of the em8300
       driver. It also has enhanced support for metadata (currently Ogg-only).

  Building with internal ffmpeg works again. This is a deprecated option;
       we strongly recommend against using this for reasons of codec and
       security support. Don't use it; use external ffmpeg libraries instead.
 

Edit:
went ahead and packaged the 1.18 for karmic and now 96 & 192 flac play fine - 5.1 though is still not right. An added advantage to 64 bit would be wmap thru ffmpeg. ( had to remove the  DXR3  plugins, don't need here and the karmic ver. of em8300 is too old, lucid has dropped it altogether

Tested wmap on my 32 bit by.removing w32codecs - both pana (amarok1.4) and a redone totem-xine play wmap fine, totem-xine also plays wmv with wma3 audio.
1.18 released 3 days after the lucid upgrade to 1.17 - too bad..

---

### Post by The Bright Side on 2012-05-14
Hey guys,

couple questions regarding 5.1 FLAC playback under Ubuntu... Since Anathema's new album "Weather Systems" is now available as FLAC 5.1, I'd love to play it from my machine and ideally also burn it to DVD.

Haven't bought the file yet, but I do remember that I once had some .dts files mixed in 5.1 Surround and when I attempted to play them back through VLC, all I got was silence...

Are you using any special settings to get FLAC 5.1 files to play in VLC? I am using the Sound Blaster 5.1 Surround Pro card (USB) and the sound output is 5.1 analog.

Also, do you know how to burn FLAC 5.1 files to DVD? I don't think Brasero will do it just like that - one would have to author it first, right?

---

### Post by shantiq on 2012-05-14
hi bright side  the repo Vlc   for precise plays those files straight off


see     [ATTACH]217931[/ATTACH]



as does [**Deadbeef**]("http://sourceforge.net/apps/mediawiki/deadbeef/index.php?title=Installing:Ubuntu")
  in precise you might need this [**info**]("http://ubuntuforums.org/showpost.php?p=11907746&postcount=73")

[ATTACH]217932[/ATTACH]




also here a great [**howto**]("http://ubuntuforums.org/showthread.php?t=1849260") for ripping to 5.1

---

