---
title: "quality player and equalizer"
date: 2009-02-22
forum: Multimedia Software
---

### Post by sowhat123456789a on 2009-02-22
I use Amarok on Ubuntu. But I can not listen the songs (mp3s...) like in Windows. I know that the sound card's drivers are installing just on Windows and not on ubuntu 100% but I want to ask you which player gives the best quality for sound formats (**especially for mp3s**). Also Amarok's equalizer is not effects the sound quality like Winamp's equalizer. There are ways (plugins...) to make the sound better?
Which player gives the best quality and which player has the best equalizer on Linux ( Ubuntu :) )  ?
Thanks...

---

### Post by mc4man on 2009-02-22
Players that I use with good equalizer control are audacious, mplayer (and smplayer) and vlc.

If you try audacious I'd suggest changing to skin from what it installs with to the 'default skin' (better visibility, black with blue lights
With focus on audacious go Ctrl+p to set preferences
To get a larger audacious when adjusting the equalizer go Ctrl+d
With some research you may be able to import winamp presets.

With the latest smplayer (and companion mplayer) you can make fine adjustments in the equalizer and save as default. (don't think there is any way to create 'presets'

info
[http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)
best way to install both
[https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa)

The newer vlc (0.9.x, 1.0) has some very nice sound controls though the equalizer is broken in 0.9.x (only stays set for 1 track), and won't be fixed. It has in the 1.0. (though many other things need 'fixing'.

You'd probably want to wait for the upcoming 1.0 release.
As far as it's equalizer vlc has a number of presets and there is a way to use those presets to store custom values. (The method is very unintuitive and somewhat a pita

What I'm going to do is work out some presets that suit me and edit them into the source so when vlc is built they are available as normal presets

---

### Post by sowhat123456789a on 2009-02-22
I try audacious .. I think it gives same quality with amarok but audacious's equalizer is more effective :)
Thnk you!

---

### Post by Shoeman on 2009-03-03
Amarok is the best player (interface and options) but with the worst sound. The equalizer does almost nothing. The bass is very weak. Audacious is a little better, but if you try to make large playlists or add many files at once it simply hangs, does not work for me. Banshee has a really good sound and equalizer does it's job very well, but I didn't find a way off adding files  that are not in the library to a playlist. In amarok or audacious I simply drag a folder to the playlist and it adds all files, including subfolders.

---

### Post by markbuntu on 2009-03-03
If you want quality sound you need quality speakers and good amplification. If you need to use the EQ then your speakers are crap.

I prefer amarok. The xine engine seems to be better than gstreamer for the quality of decoding. But, due to Intellectual Property Rights issues, patents etc,the owners of the MP3 patents are not willing to set them free. But that is a temporary problem. Their patent will run out soon and they will have no say in the matter, and neither will anyone else, forever.

---

### Post by Shoeman on 2009-03-03
> **markbuntu said:**
> If you want quality sound you need quality speakers and good amplification. If you need to use the EQ then your speakers are crap.

I prefer amarok. The xine engine seems to be better than gstreamer for the quality of decoding. But, due to Intellectual Property Rights issues, patents etc,the owners of the MP3 patents are not willing to set them free. But that is a temporary problem. Their patent will run out soon and they will have no say in the matter, and neither will anyone else, forever.

Quite not true. Amarok lacks a good equalizer because it's flat sound is poor, very weak bass. Banshee do a better job even with the EQ trurned of. If you have good speakers or phones with a bad source you will not get the best sound you could get. In fact audio in linux is not so good as in Windows XP, I think the manufacture's proprietary drivers do a better job than the generic ones. And it's also quite strange, but the best sound I can get in Ubuntu is running winamp under wine. There is no app as good a winamp made for linux. Unfortunatelly under wine some important features does not work, like global hot keys (something that banshee lacks too), notifier, auto-tag and modern skins and file manager integration. So in the sound quality criteria I would say:
winamp on wine>banshee>audacious>amarok

---

### Post by markbuntu on 2009-03-03
Windoze does a lot of behind the scene EQ to make it sound better on crappy speakers. That does not mean it is true sound, what it is suppoesd to sound like. I think Amarok is more true to the sound the makers are trying to get across.

I run my sound into a Onkyo reciever and Klipsch speakers. Each instrument/sound has a distinct place presence and depth regardless of the volume. Amarok seems best for that to me...just my opinion. Sound in windows always seemed to be over eq'd to me.
But what do I know? 
I haven't done any "professional" sound engineering for years.

---

### Post by diwas on 2009-03-03
I use Rythmbox for sound and yes, i know it doesnt have an equaliser but there is a way to have a system wide EQ(if u wish to use Pulse-audio) and tryst me the sound's great!

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

here's the link.

---

### Post by rojtheshadow on 2010-12-14
> **markbuntu said:**
> Windoze does a lot of behind the scene EQ to make it sound better on crappy speakers. That does not mean it is true sound, what it is suppoesd to sound like. I think Amarok is more true to the sound the makers are trying to get across.

I run my sound into a Onkyo reciever and Klipsch speakers. Each instrument/sound has a distinct place presence and depth regardless of the volume. Amarok seems best for that to me...just my opinion. Sound in windows always seemed to be over eq'd to me.
But what do I know? 
I haven't done any "professional" sound engineering for years.
OK, I'm new to Ununtu and am searching for a quality audio player but I know a thing or two about the Windows audio and you have a few misconceptions.

First of all, Windows doesn't do anything to make sound appear decent on crappy speakers.  In fact, the default Windows audio subsystem resamples in such a way that the audio quality is worse.  Kmixer in XP basically resampled and remixed all audio so that multiple sound sources could play simultaneously (I'm dummying this down a bit).  

The only way to get bit-perfect (and low latency) audio was to use ASIO which bypassed kmixer completely.  The unfortunate side effect of that was that if you had an audio app using ASIO, no other audio source was audible (the system was locked on the app).  Under Vista and 7, the audio API was redesigned (basically a virtual Envy24 chipset was constructed in memory to process audio) and WASAPI was implemented.  It essentially duplicated the functionality of ASIO at the OS level, again with the unfortunate side effect iterated above when used in exclusive mode.

Also, and as an aside, using an EQ does not automatically equal crappy  sound.  Anyone who has built a sound room (and I have - many times)  knows that EQ, sound pressure meters and sound alteration may be  necessary to optimize a room.

What I want to know is what gives bit-perect zero latency functionality (a la ASIO and WASAPI) under Ubuntu and what player supports that functionality as well as uses a quality mp3 decoder such as the mpg123 decoder used in Foobar2000.  Lossless takes care of itself from a decoder perspective.

Any suggestions?

---

### Post by Yellow Pasque on 2010-12-14
I use Foobar2000 through WINE and Exaile (a gstreamer app) ocassionally now that noise sharpening is implemented in gstreamer. You can enable the Canonical partner archive and install the Fluendo mp3 codec if you want it.

---

### Post by BenB1 on 2011-11-28
I understand thread is solved. TOMTOTDI ---> [http://www.mytechguide.org/8210/how-to-import-winamp-equalizer-preset-into-linux-audio-players-like-audacious-xmms-etc/](http://www.mytechguide.org/8210/how-to-import-winamp-equalizer-preset-into-linux-audio-players-like-audacious-xmms-etc/)

I had to follow the cli, then reload audacious. It did not want to intanta-magically load up the presets, had to refresh.

---

