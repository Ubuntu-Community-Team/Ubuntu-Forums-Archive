---
title: "cd ripping - rythmbox"
date: 2008-09-08
forum: Multimedia Software
---

### Post by eric489 on 2008-09-08
Hi everybody !

First of all thanks for this amazing ubuntu forum.

As you may have read in the title I have a problem with cd ripping.
I enter my cd to be ripped, but the program which automatically opens and proposes me to rip the cd is rythmbox.

No problem so far, except that my cd gets ripped in .ogg vorbis format, and I'd rather have it in mp3 :(

I downloaded some other cd rippers ( like grip ), but none was as simple as rythmbox.

So my question is, how can i get the files in mp3 format ?


And another question : 
Totem movie player freezes the pc every time it reads a file,not only on the pc , but also when it reads one on the internet.
Any  idea how to fix this ?

---

### Post by mick222 on 2008-09-08
edit-preferences-> music and change preferred format
[http://ubuntuforums.org/showthread.php?t=766683&highlight=totem](http://ubuntuforums.org/showthread.php?t=766683&highlight=totem)
Try this link for help with multimedia
use mplayer for video from the internet . Flash still freezes firefox .

---

### Post by eric489 on 2008-09-08
> **mick222 said:**
> edit-preferences-> music and change proffered format

Sorry but mp3 isn't there, only ogg vorbis, wav and FLAC

Should i download something to get the .mp3 avaible ?

---

### Post by timcredible on 2008-09-08
yeah, lame, it's in synaptic.

---

### Post by eric489 on 2008-09-08
I've downoaded lame in synaptic.

But once back again in rythmbox, mp3 is avaible.

It's avaible when i click on the edit button, but it doesn't seem possible to mark it in the preferences and select it as ripping format...

---

### Post by eric489 on 2008-09-08
Any propositions ?:(

---

### Post by y6FgBn)~v on 2008-09-08
It sounds like you are missing certain codecs. Please refer to the link [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It's very easy to follow and just involves cutting and pasting commands. 

Another option would be to go to the Add/Remove menu and under the audio program section search for "restricted" and do installs from there for the codecs that you need.

Let us know if you need further assistance.

---

### Post by quack on 2008-09-09
Hey Eric, I had the same issue. Installed LAME and thought I had all the necessary codecs.

In Preferences, on the Music tab, the "Preferred format" listbox showed a selection of profiles I didn't want. When I clicked "Edit" it brought up the "Edit GNOME Audio Profiles" box & gave me a list of profiles - which included "CD Quality, MP3". But, even when I made the MP3 profile active the contents of the listbox don't change.

The trick for me was that I was missing the "gstreamer0.10-plugins-bad" package (I'd assumed that base, good & ugly would cover everything I needed). You might be missing a different one!

Adding the bad set & restarting Rhythmbox fixed it.

Note that the gstreamer pipeline is flawed... it thinks it's creating VBR MP3s but actually creates 128Mbps CDR ones.

After a lot of experimentation & websearching I built this pipeline which you can paste into the gstreamer pipeline field to fix things:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1 vbr-quality=4 vbr=4 ! xingmux ! id3v2mux

That'll make decent quality joint-stereo VBR MP3s.

I'm still not entirely convinced that it's perfect... there's some odd pops & crackles in my MP3s. Running grip (or cdparanoia & lame directly from the command line) seems to be better still but still shows the occasional glitch which isn't in the original ripped WAV file.

---

### Post by quack on 2008-09-11
OK... update.

My pops & clicks were weird cos they were partly reproduceable (replay same track, same clicks in same places => fault is surely in the encoder) and partly variable (moved around on every play => fault is surely in the playback).

Turns out they were entirely caused by trying to play things back in VLC. Now playing them in Rhythmbox, Totem, Banshee etc and they're fine.

---

