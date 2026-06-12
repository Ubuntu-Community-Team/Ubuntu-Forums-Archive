---
title: "What's a good video converter?"
date: 2011-04-30
forum: Multimedia Software
---

### Post by mitk0o0o0 on 2011-04-30
You may all know about Total Video Converter, Any Video Converter and such used in Windows, where you chose codecs, like i want to convert to mp4 for my phone.

But.. there's one specific thing i'm looking for that most don't seem to have. Cutting.
I need for example, to cut from 24:00 to 30:00, that is the only part i want cut and converted to mp4 ready for my phone. 
EDIT: Forgot to mention here, custom bitrate, framerate, resolution (240x400), etc..

Anyone know such? I really don't feel like booting to Windows to do all that stuff. It's annoying.

---

### Post by estevez on 2011-04-30
Avidemux is a definitely first thing to try here. Its in repos.

---

### Post by andrew.46 on 2011-05-01
If you are comfortable with the commandline, or perhaps wish to learn how to use it, FFmpeg is the converter for you.

---

### Post by mitk0o0o0 on 2011-05-01
> **estevez said:**
> Avidemux is a definitely first thing to try  here. Its in repos.I've tried that out once and it didn't turn  out very well. :D Pretty difficult interface it has.

> **andrew.46 said:**
> If you are comfortable with the commandline, or perhaps wish to learn how to use it, FFmpeg is the converter for you.I've tried that FFmpeg program with interface and it couldn't do the work right, i'll try with the commandline. ;)

---

### Post by estevez on 2011-05-01
Avidemux may look little harsh for first time users, but its definitely capable and powerfull video editing tool. 

You can try Handbrake (handbrake.fr), you have to add ppa repository to install it - 

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

Handbrake is primary DVD converter, but has a pretty, simple interface, presets for standard outputs (like one ccd avi, iphone, youtube...) and "just works". It has limitations in filters, selecting parts of input you want to encode, but if you dont like avidemux, then handbrake is a tool for you (ffmpeg via CLI is a best solution.... for nerds among us :).

---

### Post by mitk0o0o0 on 2011-05-01
> **estevez said:**
> Avidemux may look little harsh for first time users, but its definitely capable and powerfull video editing tool. 

You can try Handbrake (handbrake.fr), you have to add ppa repository to install it - 

[https://launchpad.net/~stebbins/+archive/handbrake-releases]("https://launchpad.net/%7Estebbins/+archive/handbrake-releases")

Handbrake is primary DVD converter, but has a pretty, simple interface, presets for standard outputs (like one ccd avi, iphone, youtube...) and "just works". It has limitations in filters, selecting parts of input you want to encode, but if you dont like avidemux, then handbrake is a tool for you (ffmpeg via CLI is a best solution.... for nerds among us :).I really like handbrake for getting stuff out of a DVD but for now i only know till which second but **from the beginning**. Is it possible to have it start from some point and end to one (which i already know how), it's just idk how to make it start from 3:40 for example.

---

### Post by khelben1979 on 2011-05-01
[Avidemux - YouTube]("http://www.youtube.com/results?search_query=avidemux&search=Search&sa=X&oi=spell&resnum=0&spell=1"), try it! And I agree that the user interface is difficult, that's why I strugglig with using Mencoder and FFMpeg myself from the commandline whenever I'm doing things.

[Cinelerra]("http://en.wikipedia.org/wiki/Cinerella") is quite interesting though if you're looking for a GUI to do these things, I've experienced it to be a bit buggy though, but I haven't tried the latest versions for quite a while.

---

### Post by estevez on 2011-05-01
mitk0o0o0, at least version 0.9.5 has just below the source selection dropbox, where you can select chapters/seconds/frames and then input desired values from and to. So you can easily select 270 sec and encoding start from 4:30 of the source. Or i didnt got your point?

---

### Post by inobe on 2011-05-01
pitivi is already in ubuntu under sound and video, it's rendering features are out of this world with functions.

every aspect of a video can be edited, chopped, sliced, spliced and can be converted to any format known for almost all devices "assuming you already have these libs"

because all apps are useless without them.

you would want to check ubuntu docs on restricted formats.

---

### Post by Densdoor on 2011-05-01
I do not know how it rates to others but I have used WinFF to change the recordMyDesktop OGV files into mpgs to upload to YouTube and it worked well.

It converts other types also. It is easy to use.

-Dennis

---

### Post by wilee-nilee on 2011-05-01
> **estevez said:**
> Avidemux may look little harsh for first time users, but its definitely capable and powerfull video editing tool. 

You can try Handbrake (handbrake.fr), you have to add ppa repository to install it - 

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

Handbrake is primary DVD converter, but has a pretty, simple interface, presets for standard outputs (like one ccd avi, iphone, youtube...) and "just works". It has limitations in filters, selecting parts of input you want to encode, but if you dont like avidemux, then handbrake is a tool for you (ffmpeg via CLI is a best solution.... for nerds among us :).

Short of any codec problems I have seen that this is one of the best. I think it really matters what filters the phone has, as far as codecs.

---

### Post by inobe on 2011-05-01
in post #6 op states of editing?

---

### Post by mitk0o0o0 on 2011-05-02
^ Nevermind, i seem to get it now. Stupid me, the beginning thing seems to have been there all the time xD

Thanks for all the suggestions so far, i'll be sure to try out these programs. More are welcome. :D

---

