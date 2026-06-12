---
title: "chromium-codecs-ffmpeg packages (extra and normal)"
date: 2017-09-25
forum: Multimedia Software
---

### Post by kazakore on 2017-09-25
What is the difference between the [COLOR=#404040][FONT=&quot]chromium-codecs-ffmpeg and the [/FONT][/COLOR][FONT=Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#404040]chromium-codecs-ffmpeg-extra packages? They are mutually exclusive so you can#t have both installed![/COLOR][/FONT]

[FONT=Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#404040]Come across this as I can't get certain media playing in Opera. Youtube works but Bandcamp doesn't. I'm not certain but I think Youtube is using html5 and works and Bandcamp (mp3 playback) is attempting to use Flash. Googling and following a few guides (none of which helped) seemed to indicate using the libffmpeg.so from the Chromium plugins back into the Opera folder and that's how I came across these two similar seeming packages.[/COLOR][/FONT]

[FONT=Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#404040]Help with getting all media playing as well would be appreciated but I get the feeling I might just give up with Opera...[/COLOR][/FONT]

---

### Post by Frogs Hair on 2017-09-25
I run the extra package along with adobe-flash-plugin and ubuntu-restricted-extras   and am listening to Bandcamp on Opera [COLOR=#0A0A0A][FONT=Arial]47.0.2631.80[/FONT][/COLOR][COLOR=#0A0A0A][FONT=Arial] [/FONT][/COLOR] as I type.

---

### Post by mc4man on 2017-09-25
See screen for description

---

### Post by Frogs Hair on 2017-09-25
Using the package pictured above.

---

### Post by kazakore on 2017-09-25
> **mc4man said:**
> See screen for description

Not only Extra I guess as it removes the normal one, so just extra bits plus the one it calls Free (but ffmpeg is FOSS so all of it is free!)? But ffmpeg being a single framework/codec-package it seems weird to split it in any way!....

---

### Post by kazakore on 2017-09-25
> **Frogs Hair said:**
> I run the extra package along with adobe-flash-plugin and ubuntu-restricted-extras   and am listening to Bandcamp on Opera [COLOR=#0A0A0A][FONT=Arial]47.0.2631.80[/FONT][/COLOR] as I type.

I didn't have the ubuntu-restricted-extras installed (I don't really want all that extra gumph on my system) but already had the other two. Just installed that one my system and no change! Wonder what is different about yours....



I do also have the default Firefox installed and it works fine there.

---

### Post by mc4man on 2017-09-25
I'm sure there are threads about this, as far as opera iirc you have to (re)place the .so in one of it's folders. It's also liable to work with one .so & not with another.
Ultimately a real pita to keep going..

---

### Post by kazakore on 2017-09-26
> **mc4man said:**
> I'm sure there are threads about this, as far as opera iirc you have to (re)place the .so in one of it's folders. It's also liable to work with one .so & not with another.
Ultimately a real pita to keep going..

Yeah that's what the guides I read said (sorry thought I'd linked the latest one in first post but seems I forgot.) Either using the one from the Chromium plugins folder or downloading a specific version from the Abode website. Neither worked for me but as you say they seem to break often when Opera or the other programs are updated....

---

### Post by mc4man on 2017-09-26
Checking opera-stable (47.0) this libffmpeg.so would work
[https://github.com/iteufel/nwjs-ffmpeg-prebuilt/releases/tag/0.20.3](https://github.com/iteufel/nwjs-ffmpeg-prebuilt/releases/tag/0.20.3) (probably 2nd one down, the linux 64 bit one

There are likely other sources of the .so from other places that would also work...

---

### Post by kazakore on 2017-09-26
I do keep on thinking the Flash must be a red herring as I get this from Adobe's test page though...

> You have version 27,0,0,130 installed

[http://get.adobe.com/flashplayer/about/](http://get.adobe.com/flashplayer/about/)

---

### Post by mc4man on 2017-09-26
> **kazakore said:**
> I do keep on thinking the Flash must be a red herring as I get this from Adobe's test page though...



[http://get.adobe.com/flashplayer/about/](http://get.adobe.com/flashplayer/about/)
flash support seems part of opera, if it has anything to do with the libffmpeg.so then same in any libffmpeg.so , I see this - 
> $ strings  /home/doug/Downloads/libffmpeg.so   |grep flash
flashsv
flashsv2

$ strings  /home/doug/Downloads/opera-stable_47.0.2631.80_amd64/usr/lib/x86_64-linux-gnu/opera/libffmpeg.so   |grep flash
flashsv
flashsv2


---

### Post by monkeybrain20122 on 2017-09-29
There was an upgrade for chromium-codecs-ffmpeg-extra on Sept 21,  since then many Youtube videos no longer worked on Opera (47) since the html5 player lost h264 (and some other things too which I don't remember) support. Yesterday upgraded opera to 48 and it all works again.

---

