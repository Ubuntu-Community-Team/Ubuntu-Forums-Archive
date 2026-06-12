---
title: "Gnome Sound Themes"
date: 2009-10-08
forum: Multimedia Software
---

### Post by komputes on 2009-10-08
This is a continuation of this thread (which was closed):
[http://ubuntuforums.org/showthread.php?t=955485](http://ubuntuforums.org/showthread.php?t=955485)

I was wondering:

1) Is there a way to make your own theme? Where is this documented?
2) Is there a way to put the folder with the index.theme file and the subfolder with the sound files into a subdirectory to your user instead of usr/share/sounds

---

### Post by shafin on 2009-10-09
1. I did not find any documentation, maybe its there somewhere. This is what I could recover from the official theme readme file:
>         The criteria for sound inclusion:
        . No licensing issues
        . Appropriate length
                . Shorter than 1 second for any sound that denotes a specific event
            . Shorter than 5 seconds for a background sound (basically, startup/shutdown)
        . Appropriate sound
                . Volume
                   . Normalized between samples
        . Spectral range
                . No extremes
        . Good taste
                . KISS
                . General common sense (hah!)
    </snip>

    Of course, in addition to this the Theming Spec not only requires
    normalized sounds, but those with with good perceived loudness as
    described in:

        [http://replaygain.hydrogenaudio.org/calculationg_rg.html](http://replaygain.hydrogenaudio.org/calculationg_rg.html)There are a lot of sound themes at gnome look, unfortunately, not one of the themes I downloaded conformed to Freedesktop.org specifications and hence required manual setting up of sounds for each effects. I think a better way would be to get the official sound theme from [here]("http://people.freedesktop.org/%7Emccann/dist/sound-theme-freedesktop-0.7.tar.bz2") and then get your preferred sounds, replace the official theme files and edit index.theme, rename it and release/use. One handy tool for this is nautilus mouseover sound preview. 

2. just experimented with a ~/.sounds folder, it does not work. Maybe there is no support in the code, but it should be a trivial matter to fix. File a bug?

**Edit:** found the spec page:
[http://www.freedesktop.org/wiki/Specifications/sound-theme-spec](http://www.freedesktop.org/wiki/Specifications/sound-theme-spec)

---

### Post by AHD on 2010-08-16
Hi there,

I'm trying to customise this gnome thing but either i did not find any documentation or the changes are reverted after certain updates. (Presumably those related to these changes; this is standard behaviour.)

I assume that after this time no one will read my post, but I could not resist. 

What I think is, that all development is going into gnome3. I've tried several ubuntu releases. (...have been converted from SUSE) incl. 10.10. (imho the most stable one, if you take care what to update and what not. After several 10.4 bugdates I'm happy with 10.10)

If it wasn't for this huge repository I would stick with SUSE. Ubuntu (esp. 10.4) is chaos³, but that I can manage. (chmod +something I don't remember right now even let me save some files from the chaos manager (this f**** network thingy).

Regards,
Alex.

---

### Post by AHD on 2010-08-16
The most important thing I forgot. I tried KDE 4.5 and I'm impressed. There you can specify the sounds even for hard drive power saving ;)

Alex.

---

