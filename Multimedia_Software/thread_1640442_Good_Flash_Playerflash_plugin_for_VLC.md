---
title: "Good Flash Player/flash plugin for VLC?"
date: 2010-12-07
forum: Multimedia Software
---

### Post by Dragyrn1456 on 2010-12-07
hey, i use VLC for most of my media, but i also have some flash videos. on my old computer, i had Media Player Classic, and that could play Flash. but Vlc can't play flash, and Gnash has an audio lag. does anyone know a good, reliable flash animation player or have a flash plugin for VLC?

---

### Post by gshockxc on 2010-12-07
> **Dragyrn1456 said:**
> hey, i use VLC for most of my media, but i also have some flash videos. on my old computer, i had Media Player Classic, and that could play Flash. but Vlc can't play flash, and Gnash has an audio lag. does anyone know a good, reliable flash animation player or have a flash plugin for VLC?

I'm not sure why you're unable to play flash in VLC.  I have hundreds of flash videos that I play in VLC.  I'm running 10.04, just upgraded from 9.10.

---

### Post by Dragyrn1456 on 2010-12-10
for me, it opens for a spit second, then just resets VLC. I have 10.10, but i don't think that's the problem. Might you have a plugin you don't know is there?

---

### Post by Dragyrn1456 on 2010-12-18
i found a temporary solution: open in browser (w/ flash plugin). it will suffice for now, but my browser is a little slow, and i find opening something w/ my browser that isn't online a little redundant (note: i have OCD).

alert me if you find a codec/player.

---

### Post by VietCanada on 2010-12-18
You may need to add some codecs from medibuntu (PPA you add tour software sources) or the multiverse. I have no trouble playing anything I download from Youtube with VLC. I had a problem with video from the Discovery Channel site before I added the codecs.

Edit: I have to open videos often through VLC on Windows. In Linux I can right click the video and select play with VLC.

---

### Post by Dragyrn1456 on 2010-12-18
> **VietCanada said:**
> You may need to add some codecs from medibuntu (PPA you add tour software sources) or the multiverse. I have no trouble playing anything I download from Youtube with VLC. I had a problem with video from the Discovery Channel site before I added the codecs.


that may work, i have no clue as to what medibuntu is, though. and any video i download from youtube, i can download as a .mov, which i can play on VLC. a problem appears when i download SWF files from other sites, such as stickpage for my brother. i have them set to open in Firefox, but i find that to be a little, eh, redundant. gnash works, but there is an audio lag, and the dynamic camera just sits in one spot for the entire video, so you can't see anything.

---

### Post by markthekdeguy on 2010-12-21
VLC does play flash. there is a standalone flash player, but cant remember it,
sure it'll show up in Synaptic if u search for flash and standalone,
if its still being worked on.

Medibunti is a place that gives Ubuntu more plugins, codecs and goodies 
most of us want for video, music playing DVDs etc etc.
enable it by reading this

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

there is a nice graphical tool in there, called WinFF (GUI for FFMpeg)
(you'll need to search synaptic for- winff  ffmpeg  non-free-codecs w32codecs)
and it will simply convert any .flv to mpg avi or even just audio,
nice.
hth
Mark

---

### Post by Dragyrn1456 on 2010-12-21
for some reason, VLC won't play flash for me. if gnash is the other player you're thinking about, I've already ruled it out. 

i don't think i understand medibuntu, ill just stick with regular programs (im a noob when it comes to this). i have also already installed winFF, but i can't seem to convert my SWF or FLV files into anything. it sits there for 5 minutes, then tells me it failed. 

also, when i asked for a list of commands in terminal, medibuntu gave me a list of commands and options, allong with the words "this ATP has super cow powers" why?

---

### Post by efflandt on 2010-12-21
If you have gnash or any other flash plugin installed besides **flashplugin-installer** (or real 64-bit flash from adobe), multiple conflicting flash plugins might be your problem.

Note that if you upgraded Ubuntu version, instead of fresh install, flashplugin-installer might appear to be installed, but may not work until you reinstall it (I had that issue upgrading a system from 9.10 to 10.04).  But I do not think you have that problem if it works in Firefox, because when it was not working after the upgrade, it did not even show up in Firefox Add-ons.

Does Firefox Tools > Add-ons > Plugins show more than one Shockwave Flash?

---

### Post by Dragyrn1456 on 2010-12-24
i had gnash, but like i said, there is an audio lag, and the camera's screwed up. no, i have no other flash plugins besides Flashplugin-installer. 

I did upgrade to Ubuntu 10.10, but that was before i copied all my files over to that system. i will be fine for now with Firefox, but an offline, non-browser player would be nice.

<loading rest of reply...>

---

