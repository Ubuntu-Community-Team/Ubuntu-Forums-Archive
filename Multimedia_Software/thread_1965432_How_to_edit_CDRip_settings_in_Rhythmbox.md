---
title: "How to edit CDRip settings in Rhythmbox"
date: 2012-04-25
forum: Multimedia Software
---

### Post by Marcelo Ramone on 2012-04-25
Hello,

I'M trying to edit the mp3 rip settings in rhythmbox in order to increase the quality to 320 kbs, but the edit button is locked.

Any help please?

Thanks.-

[http://ubuntuone.com/2q57AjQi0btIs258sabCbe]("http://ubuntuone.com/2q57AjQi0btIs258sabCbe")

---

### Post by Marcelo Ramone on 2012-04-25
[http://ubuntuone.com/4QqbHZ20RmWWrRZynk2ctZ](http://ubuntuone.com/4QqbHZ20RmWWrRZynk2ctZ)

---

### Post by mc4man on 2012-04-25
wouldn't hurt to say what release of ubuntu you are using
(RB cd ripping is pretty crappy in 11.10, a bit better in 12.04 as far as retrieving track info

In both you would need to create a .psr & enable the preset in RB, written slightly different depending on which ubuntu

---

### Post by Marcelo Ramone on 2012-04-25
Hello,

I'M using 12.04

Can you please explain about how to "create a .psr & enable the preset in RB" ?

Thank you.-

---

### Post by mc4man on 2012-04-25
This will be appearing it a RB update next month, if it allows more than 1 at a time per profile I'm not sure - currently doesn't.

In this case I'm going to name the preset 'high', the update will use something else like '12:04-default'

```
sudo gedit /usr/share/rhythmbox/rhythmbox.gep
```
add the line I've marked in blue, save

> [GStreamer Encoding Target]
name = rhythmbox
category = muh
description = Common encoding profiles for Rhythmbox

[profile-mp3]
name = mp3
description = MPEG Layer 3 Audio
format = application/x-id3
type = container

[streamprofile-mp3-1]
parent = mp3
type = audio
format = audio/mpeg, mpegversion=1, layer=3
presence = 1
[COLOR="Blue"]preset=high[/COLOR]

.....clipped

```
mkdir -p ~/.gstreamer-0.10/presets
```
```
gedit ~/.gstreamer-0.10/presets/GstLameMP3Enc.prs

```
Example of VBR this is crafted to use VBR @ a quality of 1
```
[_presets_]
element-name=GstLameMP3Enc
version=0.10.36

[high]
name=lamemp3enc
perfect-timestamp=false
hard-resync=false
tolerance=40000000
target=Quality
cbr=false
quality=1
encoding-engine-quality=Standard
mono=false
```

If you want a different VBR then adjust the 
quality=1


Ex. of a CBR .prs, set to 320
```

[_presets_]
element-name=GstLameMP3Enc
version=0.10.36

[high]
name=lamemp3enc
perfect-timestamp=false
hard-resync=false
tolerance=40000000
target=Bitrate
bitrate=320
cbr=true
encoding-engine-quality=Standard
mono=false
```


Available options & parameters can be seen in this from terminal
```
gst-inspect lamemp3enc
```

ATM you can _only have 1 profile for mp3 & 1 preset_ (from what  I can figure out

If when opening music > preferences in RB it then says you need to install ... then you made a mistake

Bug I had on where you can get the .gep & .prs as currently planned, posted the above to show what I use Atm, (VBR @1 & to help get the deal

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/945987](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/945987)

---

### Post by Marcelo Ramone on 2012-04-25
Excellent!

I've been looking for something like this for a long time and could not find it!

Finally an effective solution!

I've tested and works 100%

Thank you!

[http://ubuntuone.com/1kWeAtNCFigB5CxSW7zalN](http://ubuntuone.com/1kWeAtNCFigB5CxSW7zalN)

---

### Post by mc4man on 2012-04-25
I've applied the same idea to vorbis, add the preset to the .gep

```
sudo gedit /usr/share/rhythmbox/rhythmbox.gep
```
Add blue
```
[profile-oggvorbis]
name = oggvorbis
description = Ogg Vorbis
format = application/ogg
type = container

[streamprofile-oggvorbis-1]
parent = oggvorbis
type = audio
format = audio/x-vorbis
presence = 1
[COLOR="Blue"]preset=Default[/COLOR]
```

 & then
```
gedit ~/.gstreamer-0.10/presets/GstVorbisEnc.prs
```
Vorbis in gnome/gstreamer now defaults to 0.3 - not good

Ex. of q = 0.8
```
[_presets_]
element-name=GstVorbisEnc
version=0.10.36

[Default]
name=vorbisenc
perfect-timestamp=true
hard-resync=false
tolerance=40000000
quality=0.8
managed=false
```

---

### Post by Gemnoc on 2012-10-08
Hello,

Thanks for this, but just to be clear: this does in no way gets back the "Settings" button (or Edit, not sure my locale is not English) in the Rhythmbox preferences, right? To change settings we need to modify the .prs file?

How could such a huge regression happen?!? And how can [those guys]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/945987") consider this bug fixed?!?

---

### Post by mc4man on 2012-10-08
> **Gemnoc said:**
> Hello,

Thanks for this, but just to be clear: this does in no way gets back the "Settings" button (or Edit, not sure my locale is not English) in the Rhythmbox preferences, right? To change settings we need to modify the .prs file?
In the RB version in 12.04, correct. The 'fix' was to create an override to the absolute crap new Gnome defaults for mp3 & vorbis. These 2 overrides would be the 'new' defaults, as in what you'd get without doing anything.
To change from the new ubuntu-default presets you'd need to create a .prs as described

> **Gemnoc said:**
> 
How could such a huge regression happen?!? And how can [those guys]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/945987") consider this bug fixed?!?
Ask the Gnome devs

In the 12.10 RB there now is a 'settings' option in RB that we'll create a custom preset, the setting allows one to alter the quality. 
(in 12.10 -
Default is crappy Gnome presets
ubuntu-default are the new override presets as seen in 12.04
Custom is whatever you wish

Seems a bit confusing I'm sure - that's one reason why that bug report (was my report), got a little 'out of hand' & probably requires reading a couple of times to seperate out 12.04 & 12.10 which have slightly differing fixes.
(plus other apps got involved to further muddle

Screen shows RB in 12.10

(note that banshee uses it's own settings now & may be a little better - third party ripper/encoders like rubyripper, asunder are superior, ect.

---

### Post by Gemnoc on 2012-10-08
Thanks for your explanations, mc4man. I hadn't realized you were the bug reporter.

You're right, that bug report ended up being a total mess - and I find unfathomable the Ubuntu dev consider the issue "fixed". It may be the Gnome devs' fault, but end result is, "fix" or not, the button still stays greyed out, and the only way to change the quality settings is to create a text file inside a hidden folder. How is the regular Ubuntu user to know about that if he does not make a search... And that's for an LTS to boot. This is a deep usability regression. Unfathomable I say. The real fix in Ubuntu 12.10 should be backported to 12.04.

I have tried Asunder and it can't even detect audio cds. Sound Juicer does not have any way to change settings. Your fix works, many thanks for that. I may try Banshee.

---

### Post by mc4man on 2012-10-08
Myself prefer rubyripper - not that hard to self install
RB-2.98 can be installed in 12.04, did so here to test.

Or I believe this ppa has 2.98 RB for 12.04
[https://launchpad.net/~webupd8team/+archive/rhythmbox](https://launchpad.net/~webupd8team/+archive/rhythmbox)

One thing to keep in mind concerning mp3 in RB (2.97 or 2.98
The preset method cannot use xingmux so track times are usually off for mp3's encoded thru the gstreamer preset. 
(I think the only player to get a preset encoded mp3's TT correct is ironically banshee
Pretty much a Gnome3 mess..

---

### Post by Gemnoc on 2012-10-08
Yes, the first song I encoded last night shows a 10:00 duration while it should be around 4:00. The other ones seem fine.

Mess indeed... I'll see about rubyripper, or maybe simply switch back to Banshee.

Again, many thanks for your great help.

---

### Post by mc4man on 2012-10-08
> **Gemnoc said:**
> 

Mess indeed... I'll see about rubyripper

If you get to RR & any issues maybe I'll do an updated how-to for 12.04 - have several post on for earlier ubuntu releases in the rubyripper thread in Tips & Tutorial section

---

### Post by brs5tettba on 2013-03-03
> **mc4man said:**
> 
ATM you can _only have 1 profile for mp3 & 1 preset_ (from what  I can figure out


Working with rhythmbox.gep in sound-juicer, the following allowed me to add multiple profiles.

First I added multiple profiles (high, medium, and low) as described by mc4man (thank you!!), then in rhythmbox.gep:
```

[profile-mp3-hi]
name = mp3-hi
description = MPEG Layer 3 Audio (hi qual)
format = application/x-id3
type = container

[streamprofile-mp3-1]
parent = mp3-hi
type = audio
format = audio/mpeg, mpegversion=1, layer=3
presence = 1
preset=high

[profile-mp3-med]
name = mp3-med
description = MPEG Layer 3 Audio (med)
format = application/x-id3
type = container

[streamprofile-mp3-2]
parent = mp3-med
type = audio
format = audio/mpeg, mpegversion=1, layer=3
presence = 1
preset=medium

[profile-mp3-low]
name = mp3-low
description = MPEG Layer 3 Audio (low)
format = application/x-id3
type = container

[streamprofile-mp3-3]
parent = mp3-low
type = audio
format = audio/mpeg, mpegversion=1, layer=3
presence = 1
preset=low

```

---

