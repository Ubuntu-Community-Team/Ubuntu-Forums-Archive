---
title: "Can't play videos .avi and .mp4"
date: 2008-04-29
forum: Multimedia Software
---

### Post by arashiko28 on 2008-04-29
I have been trying to open a few .avi videos and get and error from VLC about being unable to open file, so I passed it to a USB memory and tried it on a DVD player with USB port and the video plays, so that makes me sure about the video being fine and being .avi. On totem it keeps looking for unexistent codecs to play the video. But I can play other .avi videos on the computer, I have tested others.

On the other hand, I have .mp4 videos and installed on synaptic what I saw as mp4 codecs, and yet haven't been able to get a nice video rendering, it freezes tough sound goes smoothly.
Please help!!!

---

### Post by arashiko28 on 2008-04-29
bump! Please, anybody? Ideas? I have tried almost everything!

---

### Post by duckgoesoink on 2008-04-29
Maybe a dumb question, but have you already installed Ubuntu Restricted Extras and enabled the Medibuntu source? If you install all the gstreamer plugins you should be able to play nearly anything (I think the one for .avi might be gstreamer0.10-ffmpeg).

---

### Post by arashiko28 on 2008-04-29
If that was dumb, this is the mother: I have no idea about what you're talking about. I mean, I have watched videos and edited videos and all of that, with no further than installing what I need and click. So please, explain yourself... I know I have all of gstreamer codecs installed, but i'll check again, I also installed the ones I saw on synaptic for mp4, but no success so far...

---

### Post by duckgoesoink on 2008-04-29
Ok, go to Add/Remove programs and search for Ubuntu Restricted Extras. Install it and see if that makes the files play. If it doesn't, enable the Medibuntu Repository and see if that works: paste this command into the terminal (Applications>Acessories>Terminal)

[INDENT]**sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list**[/INDENT]

then this one

[INDENT]**wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update**[/INDENT]

Then put this in the terminal to install all the codecs you might possibly need (assuming you are using Hardy 32 bit): 

[INDENT][B]sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libflashsupport liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs
[/B][/INDENT]



You actually don't have to use the terminal to do all this, you can use Synaptic Package Manager, which is in System>Administration, but this is faster.

BTW, there is a useful [sticky]("http://ubuntuforums.org/showthread.php?t=766683") dealing with all this at the top of the Multimedia & Video section - that's where I learnt. :-)

---

### Post by arashiko28 on 2008-04-29
haha, i'm not that newbie and I love terminal.

Anyway, no good at all. The mp4 still looks choppy and freezes and some avi files won't open.:(

---

### Post by duckgoesoink on 2008-04-29
> **arashiko28 said:**
> haha, i'm not that newbie and I love terminal.

Hehe, that's what I was trying to avoid before, with my "maybe this is dumb" question. ;-)


> **arashiko28 said:**
> Anyway, no good at all. The mp4 still looks choppy and freezes and some avi files won't open.:(

So it's strange that you've done all that and it still doesn't work. Mine all worked after that, including the little icon previews of the .avi files...

Anyone else have ideas?

---

### Post by arashiko28 on 2008-04-29
that's the weird thing, I mean, I have the preview of all chapters that CAN'T be played! How ever, chapters that CAN be played, has no icons! and I know that they're good, because I tested them on a non computer device, on a TV DVD and it recognized the .avi file and played it.:( I really want to fix this, specially because I deleted my windows partition.:), so Linux is all I rely on and as when I was blind and all I knew was windows and twitched everything until it worked, now it's Ubuntu time to get twitched and retorted!:lolflag:

---

### Post by duckgoesoink on 2008-04-29
I tried looking for more information, but didn't find much yet unfortunately. I found [this thread]("http://ubuntuforums.org/showthread.php?t=672552"), which had suggestions, but doesn't look resolved?


Come on all you experts, throw a few ideas in the ring for this guy here...

---

### Post by arashiko28 on 2008-04-29
:lolflag:GIRL!!!
Anyway, I have all that done already. I'll try to convert it to avi again. I know they're not corrupted, I can see them out of my computer. But I want them on the computer, because I watch my series when I'm not home. and the mp4. i'll try to convert it to .avi, the weird thing is that i can play other avi files, but these one in special, not. In properties it says on type: avi video, but on MIME type: video/x-msvideo, on codecs: XVID/MPEG-4.

---

### Post by Gunman1982 on 2008-04-29
Maybe this can help you:
[http://www.lockergnome.com/linux/2007/07/02/ubuntu-wont-play-avi-files/](http://www.lockergnome.com/linux/2007/07/02/ubuntu-wont-play-avi-files/)

Another option would be to use mplayer.

---

### Post by duckgoesoink on 2008-04-30
Bah, that's just weird huh? Good luck fixing it!

---

### Post by arashiko28 on 2008-04-30
mplayer? it just spends the whole day looking for codecs, besides it's not all of the .avi files, I have the codecs, it's just these files from this particular serie that gives me the headache, all the others can be played. And mp4 videos, they can be played, but lagging and eats up my processor.

---

### Post by KillaW0lf04 on 2008-07-20
hey guys im having the exact same problem with mp4 files. Most of them wont play in totem and when i run them in VLC they are very stuttery

---

### Post by dantakeoff on 2010-08-18
open synaptic package manager, install libmpeg4ip-0 and libmpeg4-dev and mencoder, and hey presto....dunno what the hell they do, but it worked for me....

---

