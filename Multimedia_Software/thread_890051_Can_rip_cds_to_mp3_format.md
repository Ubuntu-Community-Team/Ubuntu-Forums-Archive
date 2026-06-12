---
title: "Can rip cds to mp3 format"
date: 2008-08-14
forum: Multimedia Software
---

### Post by Antihero20 on 2008-08-14
I got rythmbox and it doesn let me switch to rip cds to mp3, instead it ripps them to .ogg

How do i change this? i tried in the preferences, it appears it does support mp3 but just doesn&#347; seem to let me

---

### Post by ajgreeny on 2008-08-14
Perhaps you need the right codecs for mp3 playback and encoding.  Can you play mp3s?   Search for "lame"  in synaptic and you may find many apps that will help.

---

### Post by mc4man on 2008-08-14
> How do i change this?
I don't use rythmbox but probably you need to install lame. (maybe also liblame0. Look in synaptic.

rythmbox will default to a quality setting of 6 for mps's. (scale is 0-9, 0 the best, 9 the worst.

To change go to preferences -> music -> choose mp3 as preferred format and then click edit.
In the next box choose cd quality, mp3 and again choose edit. In the next box (see screen) maximize the window so you can see the whole comm.

> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=[COLOR="Red"]6[/COLOR] ! id3v2mux 
Change what's in red to alter quality if desired

---

### Post by kfhughes on 2008-08-19
I tried this morning to import a CD as MP3s.  RhythmBox, Sound Juicer and Banshee don't show "CD Quality, MP3" as an option.  If I edit the profiles, I can see this profile and it's set to Active.  I have lame installed as well as gstreamer0.10-fluendo-mp3.  I'm at a loss for what to do next.

---

### Post by pe7er on 2008-08-22
You could try: ```
sudo apt-get install ubuntu-restricted-extras
```
See: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

After I installed that, I was able to select MP3 in the Rythmbox configuration.

---

