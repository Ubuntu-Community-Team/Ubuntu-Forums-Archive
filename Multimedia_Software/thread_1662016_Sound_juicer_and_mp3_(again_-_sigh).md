---
title: "Sound juicer and mp3 (again - sigh)"
date: 2011-01-07
forum: Multimedia Software
---

### Post by WileyGaia on 2011-01-07
I know this has been posted before, I have searched but am not winning here... so, once again:

My Sound Juicer will not give me mp3 as an option for output format.

It is there in Preferences as a "Profile": "CD Quality, MP3", with Gstreamer pipeline:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

I have followed the sticky called "Comprehensive Multimedia & Video Howto" and done all the installations step for step...

Please can anyone assist?

---

### Post by WileyGaia on 2011-01-07
Apologies- running 10.04

---

### Post by Yellow Pasque on 2011-01-07
You need to get gstreamer0.10-lame package. If you can't figure out how to find/install/build that (there are some minor patent issues, which is why it isn't distributed by default), then rip to flac and convert to mp3 using lame.

---

### Post by Yellow Pasque on 2011-01-07
> **Temüjin said:**
> You need to get gstreamer0.10-lame package. If you can't figure out how to find/install/build that (there are some minor patent issues, which is why it isn't distributed by default), then rip to flac and convert to mp3 using lame.
Sorry, I keep forgetting that Ubuntu calls the package 'gstreamer0.10-plugins-ugly-multiverse'

---

### Post by WileyGaia on 2011-01-07
> **Temüjin said:**
> You need to get gstreamer0.10-lame package. If you can't figure out how to find/install/build that (there are some minor patent issues, which is why it isn't distributed by default), then rip to flac and convert to mp3 using lame.

I tried got this msg:
Note, selecting gstreamer0.10-plugins-ugly-multiverse instead of gstreamer0.10-lame
gstreamer0.10-plugins-ugly-multiverse is already the newest version.

REALLY don't want to go through double the effort to get to mp3

---

### Post by Yellow Pasque on 2011-01-07
Unfortunately, with GNOME, you have to dig into the registry (Windows style, yay!). So fire up gconf-editor (install it if you don't have it) and:
```
gconf-editor
```
Now, make sure that the mp3 profile is offered by navigating to:
/system/gstreamer/0.10/audio/global/profile_list

---

### Post by WileyGaia on 2011-01-08
> **Temüjin said:**
> Unfortunately, with GNOME, you have to dig into the registry (Windows style, yay!). So fire up gconf-editor (install it if you don't have it) and:

Now, make sure that the mp3 profile is offered by navigating to:
/system/gstreamer/0.10/audio/global/profile_list

Yep, the profile "MP3" is already there...

---

### Post by WileyGaia on 2011-01-10
surely there must be a solution for this?

I used to have GRIP when I ran 8.10 and that worked well, I was recommended on this forum to upgrade to 10.04 in order to get better support (with another issue), which I dutily did, now I see grip is not supported anymore, and I can't rip to MP3 anymore.... somewhat puzzled and confounded!?

---

### Post by samfuzz on 2011-01-10
replace the gstreamer pipeline (mp3 profile) with this one :

audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc quality=2 ! xingmux ! id3v2mux

---

### Post by WileyGaia on 2011-01-10
> **samfuzz said:**
> replace the gstreamer pipeline (mp3 profile) with this one :

audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc quality=2 ! xingmux ! id3v2mux

at work now, will try when i get home and let u know...
what does it all mean?

---

### Post by samfuzz on 2011-01-10
gstreamer-lame is obsolete :
[https://bugzilla.gnome.org/show_bug.cgi?id=494528](https://bugzilla.gnome.org/show_bug.cgi?id=494528)

it's preferable to use gstreamer-lamemp3enc

but old gstreamer-lame should work, i'm using lucid and the old pipeline is ok with soundjuicer.
i've read on a french forum that it was no ok with maverick+soundjuicer ( but i'm not sure, i'haven't tested it) in anycase the new gstreamer-lamemp3enc is recommended


ps :hope that you have understand my ugly english, it's not my native language

---

### Post by WileyGaia on 2011-01-10
> **samfuzz said:**
> gstreamer-lame is obsolete :
[https://bugzilla.gnome.org/show_bug.cgi?id=494528](https://bugzilla.gnome.org/show_bug.cgi?id=494528)

it's preferable to use gstreamer-lamemp3enc

but old gstreamer-lame should worked, i'm using lucid and the old pipeline is ok with soundjuicer.
i've read on a french forum that it was no ok with maverick+soundjuicer ( but i'm not sure, i'haven't tested it) in anycase the new gstreamer-lamemp3enc is recommended


ps :hope that you have understand my ugly english, it's not my native language

much appreciated - no probs with the english, i really apreciate that you are helping me out! 
dumb question: does this mean i should be installing gstreamer-lamemp3enc first?

---

### Post by samfuzz on 2011-01-10
enable multiverse and universe repositories
and install ubuntu-restricted-extras
sudo apt-get install ubuntu-restricted-extras
(lame i think is included in gstreamer0.10-plugins-ugly-multiverse package)
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

and replace the pipeline in the mp3 profile

---

### Post by WileyGaia on 2011-01-10
> **samfuzz said:**
> enable multiverse and universe repositories


apologies, I am a beginner - what does this mean?

---

### Post by samfuzz on 2011-01-10
looks here

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by WileyGaia on 2011-01-10
holy crap!!!

samfuzz: it worked!!!

thankyou x 1million

i was getting worried there for a minute...

i tried it step by step:
installed the restricted extras, that didn't work

amended the profile to your profile above, and now the option is in the menu, tested it and it ripped a disc beautifully!

once again, THANKYOU!

---

### Post by WileyGaia on 2011-01-10
as a matter of interest i did not install those repositories you advised me about...

must say, now that it is working, i am reluctant to do that...

---

### Post by samfuzz on 2011-01-10
cool
it seems there is a bug with soundjuicer and default gstreamer audio profile for mp3 encoding in maverick

not sure and canno't tested because i'm on lucid

edit :
i'm wrong , i haven't seen that you were on lucid, so it might be not a bug, because defaut profile works on lucid with soundjuicer

---

### Post by WileyGaia on 2011-01-10
> **samfuzz said:**
> cool
it seems there is a bug with soundjuicer and default gstreamer audio profile for mp3 encoding in maverick

not sure and canno't tested because i'm on lucid

i am on lucid as well

---

### Post by mdlueck on 2012-03-30
> **Temüjin said:**
> Sorry, I keep forgetting that Ubuntu calls the package 'gstreamer0.10-plugins-ugly-multiverse'

Worked perfectly on Ubuntu 10.04... successfully achieved enabling MP3 format in Sound Juicer. Thanks!

---

### Post by sparklyprgs on 2012-04-18
If you like **CBR MP3** files instead (they seem to work better in car MP3 players) you need something like this. Took me ages to work this out so hope it helps others:

audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc target=bitrate cbr=true bitrate=256 ! xingmux ! id3v2mux

The values for bitrate can be:
8, 16, 24, 32, 40, 48, 56, 64, 80, 96, 112, 128, 160, 192, 224, 256 or 320

Slightly confusing info is here:
[http://stuff.mit.edu/afs/athena/system/amd64_deb50/os/usr/share/gtk-doc/html/gst-plugins-ugly-plugins-0.10/gst-plugins-ugly-plugins-lamemp3enc.html](http://stuff.mit.edu/afs/athena/system/amd64_deb50/os/usr/share/gtk-doc/html/gst-plugins-ugly-plugins-0.10/gst-plugins-ugly-plugins-lamemp3enc.html)

---

