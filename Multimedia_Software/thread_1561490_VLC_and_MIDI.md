---
title: "VLC and MIDI"
date: 2010-08-26
forum: Multimedia Software
---

### Post by revnedleinadcm on 2010-08-26
Hi, I'm new to Linux, and using Ubuntu 10.04. I have a Soundblaster Live 5.1 card that is working properly, and have installed the awesfx package, but I can't get MIDIs to play properly. when I scroll over a MIDI file, there is a &quot;preview&quot; which plays in the background. But when I try to open the file in GNOMEplayer, nothing happens, and when I use VLC player, I get the message:   No suitable decoder module: VLC does not support the audio or video format &quot;MIDI&quot;. Unfortunately there is no way for you to fix this.  Now, I know that VLC does support MIDI, because it says so on their website, and they play MIDIs in Windows.  Any ideas?  THanks.  FYI, I have searched the forums and this seems to be a common enough problem, and I have followed some of the posts but to no avail yet.

---

### Post by andrew.46 on 2010-08-26
Hi revnedleinadcm,

Indeed vlc will play midi files well if it has been compiled against libfluidsynth and it has access to some soundfonts. Details of this can be [seen here]("http://www.remlab.net/op/vlc-midi.shtml") while the soundfonts I personally use can be [seen here]("http://www.personalcopy.com/linuxfiles.htm").

Unfortunately I don't believe there are any packages around that have been compiled in this way, although I am prepared to be proven wrong. I build my own and always against libfluidsynth...

All the best,

Andrew

---

### Post by falkTX on 2010-08-26
> **andrew.46 said:**
> Hi revnedleinadcm,

Indeed vlc will play midi files well if it has been compiled against libfluidsynth and it has access to some soundfonts. Details of this can be [seen here]("http://www.remlab.net/op/vlc-midi.shtml") while the soundfonts I personally use can be [seen here]("http://www.personalcopy.com/linuxfiles.htm").

Unfortunately I don't believe there are any packages around that have been compiled in this way, although I am prepared to be proven wrong. I build my own and always against libfluidsynth...

All the best,

Andrew

I have it on my (big) PPA:
[https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/)

I also have a new "vlc-110" package, which provides VLC 1.1.3 (default version in ubuntu is 1.0.6)

---

### Post by revnedleinadcm on 2010-08-26
Thanks. I have downloaded several fluidsynth packages and soundfont packages. Is there something I need to do to "point" VLC to the proper codecs to get it running midi files? The Remlab website talks about "enabling" fluidsynth within VLC, but doesn't describe how you do that.

---

### Post by andrew.46 on 2010-08-26
Hi revnedleinadcm,

> **revnedleinadcm said:**
> The Remlab website talks about "enabling" fluidsynth within VLC, but doesn't describe how you do that.

He means that vlc must be *compiled* against libfluidsynth, and then the soundfonts sourced from within the preferences as he shows in the screenshot on the page. Thus unfortunately you cannot simply download the Ubuntu repository vlc (which is not compiled against libfluidsynth) and expect to enable midi playback with this vlc package.

I run a guide on these forums for building vlc-git with an addendum that describes the building of vlc 1.1.3 but unfortunately it is a pretty complex guide and might very well be more than you are after...

Andrew

---

### Post by revnedleinadcm on 2010-08-26
Again, please excuse my ignorance, but how do I "compile VLC against libfluidsynth"? I don't know what that means, and I keep following links from the Remlab site, to fluidsynth, to glib, to GTK+, it's like a neverending cycle with no instructions anywhere. When I open up VLC preferences, "Fluidsynth" is not listed in the "Audio codecs" section, even though I have tried to obtain everything under the sun containing the terms "fluidsynth" and "soundfont". I have installed repositories and updated them and extracted vlc 1.1 packages and all the rest.  Again, sorry for my complete ignorance; I'm new to this Linux business as of 11 days ago.

---

### Post by andrew.46 on 2010-08-26
Hi revnedleinadcm,

> **revnedleinadcm said:**
>  Again, sorry for my complete ignorance; I'm new to this Linux business as of 11 days ago.

No, forgive me for dropping in too much information without any decent explanation :). I had not realised that you are relatively new to Linux so perhaps a short and somewhat simplistic explanation of the problem you are facing might be in order:

vlc started as a university project about 13 years ago and is maintained by a group of programmers who work on the project for free in their own time. They write the 'source code' for the program and everybody is free to use it and also to improve the source code and pass these improvements back to the developers. This 'source' is not actually suitable to be used *as it is* on your computer as the programming language used by the developers must be converted to machine readable code. This process of conversion is commonly known as compiling.

The Ubuntu developers have taken the vlc source code and not only compiled it into machine readable code but also processed it with a special set of rules to produce an installable package that fits on well with the rest of the packages made available from the Ubuntu Repository. When making up this package they have made a number of choices about what to build and not to build with this copy of vlc and guess what: midi playback has not been included :(.

There are some alternatives here. Some enterprising individuals have set up their own small repositories with copies of vlc available, these small repositories are known as PPAs (Personal Package Archives) and can vary a little in quality and usefulness. This is what falkTX is offering in this thread. There are a handful of PPAs offering vlc but I do not know how many will have midi playback available but if they do you will still need to download a soundfont. 

Other individuals have published guides wherein you can compile the source code yourself and produce a copy of vlc tailored to your own needs. This is what I do but I freely acknowledge that [the guide I have produced for vlc]("http://ubuntuforums.org/showthread.php?t=1398119") is quite complex and a bit of an ask for somebody with only 11 days experience with Linux!

That is the short version of the problem and I have glossed over some reasonably complex areas in trying to show you where the fundamental problem with your copy of vlc lies. Is that a little clearer?

All the best,

Andrew

---

### Post by swaan on 2013-04-13
I just found out that there is now an alternative to compiling VLC against libfluidsynth: install the vlc-plugin-fluidsynth package.
You still need set the soundfont file for fluidsynth under audio codec settings in VLC.

---

### Post by overdrank on 2013-04-13
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

