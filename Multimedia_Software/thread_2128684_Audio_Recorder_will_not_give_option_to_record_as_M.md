---
title: "Audio Recorder will not give option to record as MP3"
date: 2013-03-23
forum: Multimedia Software
---

### Post by Joshatlas on 2013-03-23
Just like the title says. I have tried everything that I know of to try and get Audio Recorder to give me the option to record as an MP3. I had it working while running 12.10 64 bit, but after formatting my computer and reinstalling 12.10 32 bit, I just can't seem to get it to work for me. I have installed all of the restricted ubuntu-restricted-extras, and also installed the third party extra option during the OS install with included Fluendo MP3 plugin. Sound Converter gives me an option to convert to mp3 if that info helps. Any help would be much appreciated because it has me stumped. Thanks

PS - I know mp3 is a crappy format but I need it for what I am trying to accomplish.

---

### Post by ron999 on 2013-03-23
> **Joshatlas said:**
> 
... try and get Audio Recorder to give me the option to record as an MP3...
... but after formatting my computer and reinstalling 12.10 32 bit, I just can't seem to get it to work for me.

Hi
You need to install the gstreamer0.10 plugins.

There's a whole set of them:-
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly

Install them all, if you like... but I think it is the "**ugly**" plugins that are used for mp3.

---

### Post by Joshatlas on 2013-03-23
I tried using the following -

[FONT=Arial][FONT=monospace]**sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse**

and this is what I got



[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-plugins-ugly-multiverse is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package gstreamer0.10-pitfdll
E: Couldn't find any package by regex 'gstreamer0.10-pitfdll'
E: Package 'gstreamer0.10-plugins-ugly-multiverse' has no installation candidate


[/B][/FONT][COLOR=#FF0000][FONT=monospace][/FONT][/COLOR][FONT=monospace]Any ideas?[/FONT][COLOR=#FF0000][FONT=monospace]
[/FONT][/COLOR][/FONT]

---

### Post by Joshatlas on 2013-03-24
Well I also just tried

**sudo apt-get install gstreamer0.10-plugins-ugly**

and got

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-ugly is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/B]

---

### Post by robert shearer on 2013-03-24
Do you mean the default audio recorder that comes with Ubuntu....?


If all else fails then use the most excellent audio recorder here....
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

> This program supports several audio (output) formats such as OGG audio, Flac, **MP3** and WAV.

> The installation is very easy. Run these commands on the command line:

```
sudo apt-add-repository ppa:osmoma/audio-recorder
```
```
sudo apt-get update
```
```
sudo apt-get install audio-recorder
```

You will also need to install one or more of these packages to add support for various audio-formats.
gstreamer1.0-plugins-base (OGG format)
gstreamer1.0-plugins-good (WAV and Flac formats)

gstreamer1.0-plugins-ugly (MP3 format)

gstreamer1.0-plugins-bad (AAC, m4a format)

Notice: The recorder now requires Gstreamer 1.0.

[B]Notice also:
Fluendo's gstreamer0.10-fluendo-mp3 package provides MP3-playback, but it has no recording capabilities. Playback only.[/B]
---
Start the program from Applications -> Sound & Video menu or search for it in the Dash (audio....).
Or start it from the command line:
audio-recorder

Mabe try 
```
sudo apt-get purge gstreamer0.10-fluendo-mp3
```

reboot and see if that fixes it....

---

### Post by Joshatlas on 2013-03-24
Thanks Robert Shearer! The information to wrote helped me figure it out. The program I am using is actually the same audio recorder that you are talking about. I noticed at towards the bottom of your post it said 

**Notice: The recorder now requires Gstreamer 1.0.**

So I purged the old gstreamer version

**sudo apt-get purge gstreamer0.10-plugins-ugly**

and installed the new copy of 1.0

**sudo apt-get install  gstreamer1.0-plugins-ugly**

and it works perfectly now.

Thank you so much because I would have never thought to look for the updated version 1.0

---

