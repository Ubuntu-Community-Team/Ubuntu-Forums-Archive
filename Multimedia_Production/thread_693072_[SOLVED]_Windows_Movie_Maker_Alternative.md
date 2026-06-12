---
title: "[SOLVED] Windows Movie Maker Alternative"
date: 2008-02-10
forum: Multimedia Production
---

### Post by stooshbunutu on 2008-02-10
Hiya, I guess I am another on of these people searching for a windows movie maker alternative.

I have tried avidmux and it is ok and have not been able to use properly cinelerra and LiVES. Kino is only for Kubuntu where as I use Ubuntu. Also have tried PiViTi but it wont read hardly any formates I want to use.

For sound I use Audacity and realy like it, is there an Audacity similar Video editor?

I will greatly appreciate any help :)

---

### Post by eye208 on 2008-02-10
> **stooshbunutu said:**
> Kino is only for Kubuntu
Nope. Despite the "K" in the name, Kino is GTK-based.

Besides, you can use any editor with both Gnome and KDE.

---

### Post by philc on 2008-02-10
> **stooshbunutu said:**
> I guess I am another on of these people searching for a windows movie maker alternative.


My personal preference is [Open Movie Editor]("http://openmovieeditor.sourceforge.net/HomePage").

There's an older version in Ubuntu's repositories, that will be missing some of the latest updates, but is the easiest installation option for you.

Or you can try building from the latest source, downloadable at the above link.

---

### Post by UbuWu on 2008-02-10
Kdenlive is great. The version in gutsy is very buggy though, the one in hardy is much better.

---

### Post by stooshbunutu on 2008-02-11
> **philc said:**
> My personal preference is [Open Movie Editor]("http://openmovieeditor.sourceforge.net/HomePage").

There's an older version in Ubuntu's repositories, that will be missing some of the latest updates, but is the easiest installation option for you.

Or you can try building from the latest source, downloadable at the above link.

Thanks philc, I am downloading as I type this and will try it out, will thankyou properly if it works.

---

### Post by stooshbunutu on 2008-02-11
Well I tried it but it wont load any videos,

Do you know any others or a way of getting it working properly?

---

### Post by stooshbunutu on 2008-02-11
> **eye208 said:**
> Nope. Despite the "K" in the name, Kino is GTK-based.

Besides, you can use any editor with both Gnome and KDE.

You were right it installed well and loods very promising - However importing video doesn't finish.... ever, and the sound is just a large fuzz.

Any ideas how I can get this working.

Thanks again in advance

---

### Post by philc on 2008-02-11
> **stooshbunutu said:**
> Well I tried it but it wont load any videos,

Do you know any others or a way of getting it working properly?

Which way did you install it? If using the version in the Ubuntu repositories, I think one of the missing features is the ability to use NTSC based footage.

Do you know how to install from source?

Otherwise, maybe try a Debian package instead:

[http://packages.debian.org/openmovieeditor](http://packages.debian.org/openmovieeditor)

That's got the Jan 2008 release.

---

### Post by stooshbunutu on 2008-02-12
> **philc said:**
> Which way did you install it? If using the version in the Ubuntu repositories, I think one of the missing features is the ability to use NTSC based footage.

Do you know how to install from source?

Otherwise, maybe try a Debian package instead:

[http://packages.debian.org/openmovieeditor](http://packages.debian.org/openmovieeditor)

That's got the Jan 2008 release.

I did install it from the Add/Remove section of the Applications Menu

I then tried the version from debain.org but no luck because some of the dependencies conflicted with others I already have installed and need.

Not sure what you mean by dowloading from source so the answer is probable no, How would I go about this?

Cheerz for your onging help

---

### Post by philc on 2008-02-13
> **stooshbunutu said:**
> 
Not sure what you mean by dowloading from source so the answer is probable no, How would I go about this?


When software is written there are a set of "raw" files, called the source, that need to be compiled before the application will work. So far you have been installing binary files, that have already been pre-compiled and packaged for your system.

If you have little Linux experience, and just want to easily install software, then installing from source may not be something you want to get into. However, if you're technically knowledgeable, looking for a challenge, a sense of achievement and some good knowledge about how Linux works then you should really learn how to install from source.

As a starting point, maybe try installing FFmpeg from source. It's a good foundation piece of software for a lot of Linux video editing tools. FFmpeg already exists in Ubuntu repositories - meaning you can install it through Synaptic package manager - but it is an older version. Best to get the latest version......

1. Ensure that FFmpeg is not installed via Synaptic. search for it and uninstall if needed.

2. Start a Terminal window via Applications > Accessories > Terminal

3. Follow the How-To for installing  FFmpeg on Gutsy from here:

[http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html](http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html)

The stuff in italics is what you need to type on the command line.

4. If you get stuck and or want to know more about what you're doing, try reading the How-To for FFmpeg on Debian Etch:

[http://stream0.org/2008/01/install-ffmpeg-on-debian-etch.html](http://stream0.org/2008/01/install-ffmpeg-on-debian-etch.html)

This gives you more background about what's happening and is very similar to the Ubuntu process.

If you get this far and are happy to continue, post here and I'll continue with instructions.

---

### Post by stooshbunutu on 2008-02-13
Really appreciating your help but I believe that this is a bit above me as I am still a bit of a newbie.

Thanks for trying

---

### Post by stooshbunutu on 2008-02-19
Does anyone know of any others?

---

### Post by imon9 on 2008-02-19
kdenlive..closest in functionalyty and maturity... check the synaptic for it... i use this one just because of that!

---

### Post by stooshbunutu on 2008-02-19
cheers will try it

---

### Post by !bilay on 2008-02-20
I've been struggling for a week to find a decent video editor in Gutsy and Kino is the only one that "almost" works.  Kdenlive is slow and buggy, openmovieeditor is a pain to compile the correct version, and blender sequence editor is not user friendly.  Also, Kino is the only one that's capable of writing back to my camcorder via firewire, something everyone with miniDV needs.  Just remember, start kino using "gksudo kino" to get firewire working.  Now my biggest problem is getting FLV to export properly, right now there's no sound and the maximum size is 320x240.

How can it be so bad, I'm going back to using Pinnacle in my Windows virtualbox, at the very least I can export a proper FLV file for the net.

---

### Post by stooshbunutu on 2008-02-20
for all those wondering, windows movie maker doesn't work with WINE

---

### Post by stooshbunutu on 2008-02-23
Nah Kdenlive dont integrate properly onto Ubuntu desktop, just Kubuntu

Any other help?

---

### Post by FakeOutdoorsman on 2008-02-24
I believe Kino only can import raw .dv and DV .avi files (I might be wrong).  Follow philc's instructions earlier in this thread on installing ffmpeg or look at the resourceful Ubuntu Wiki on [encoding videos for iPod]("https://wiki.ubuntu.com/iPodVideoEncoding") (there is a good ffmpeg installtion section there).  Then to convert a file to editable format for Kino try (depending on your video source or country):
```
ffmpeg -i filetobeconverted -target ntsc-dv outputfile.dv
```
or
```
ffmpeg -i filetobeconverted -target pal-dv outputfile.dv
```

---

### Post by srikar on 2008-02-24
[http://lives.sourceforge.net/](http://lives.sourceforge.net/)

---

### Post by stooshbunutu on 2008-02-24
After much careful consideration, trials, and research, I have found that the best solution was infact the one I tried first.

Avidemux

It is simplest, least buggy, opens quicker, is move versatile, and actually works all the time. Although the slight limitations on working with avi it converts nicely and can easily handly the mp4 format that other file conversion programs seem to tip up on.

Others may probably disagree with me but this is what I have found from trial and error (mainly error). Cinelerra is supposedly good but didn't even come close to working.

I have included a poll as to which is best

---

### Post by srikar on 2008-02-25
Hey why dont you checkout lives???

---

### Post by stooshbunutu on 2008-02-25
I already checked out lives, sorry forgot to add it to the poll,

For me lives didn't work properly and I just couldn't get it doing what I wanted to do.

Cheers anyway

---

### Post by stooshbunutu on 2008-02-25
> **!bilay said:**
> I've been struggling for a week to find a decent video editor in Gutsy and Kino is the only one that "almost" works.  Kdenlive is slow and buggy, openmovieeditor is a pain to compile the correct version, and blender sequence editor is not user friendly.  Also, Kino is the only one that's capable of writing back to my camcorder via firewire, something everyone with miniDV needs.  Just remember, start kino using "gksudo kino" to get firewire working.  Now my biggest problem is getting FLV to export properly, right now there's no sound and the maximum size is 320x240.

How can it be so bad, I'm going back to using Pinnacle in my Windows virtualbox, at the very least I can export a proper FLV file for the net.

Late respons I know but try exporting to whatever it handles best and then use WinFF to convert to .flv

---

### Post by j_baer on 2008-03-01
> **philc said:**
> My personal preference is [Open Movie Editor]("http://openmovieeditor.sourceforge.net/HomePage").

There's an older version in Ubuntu's repositories, that will be missing some of the latest updates, but is the easiest installation option for you.

Or you can try building from the latest source, downloadable at the above link.

Just installed from the repro's and it looks nice.  Any way to get the current release?

John

---

### Post by Creative2 on 2008-03-02
i have just installed open movie editor it seems it will included on ubuntu studio ,  but i am NOT sure.

well i have had some trouble because debian package on repository is a bit old and so..it has not effects and other thing, you can do this with that great piece of software..

[http://www.youtube.com/watch?v=9ljEb1PdEdM](http://www.youtube.com/watch?v=9ljEb1PdEdM)

---

### Post by hodenkat on 2008-06-02
I solved the problem!


Plugged my camcorder into the port running Hardy, nothing happened.

Launched Kino and got an error on the IEEE1394 control tab saying something about raw1394 not loaded or no read write access.

Rebooted into Windows, plugged camcorder in, dialog box came up asking if I wanted to capture video using Windows Movie Maker...
so I did!

The End:popcorn:

---

### Post by decoherence on 2008-06-27
> **hodenkat said:**
> I solved the problem!


Plugged my camcorder into the port running Hardy, nothing happened.

Launched Kino and got an error on the IEEE1394 control tab saying something about raw1394 not loaded or no read write access.



Lots of people have had that issue. The fix is generally adding the user to a group or perhaps loading a kernel module. I forget the specifics, but the info is Out There.

In any case, shouldn't this be automatically handled by debconf? It's bad form when you install from a repo and it just dunt work. Especially when it's got the little Ubuntu sticker beside it.

---

### Post by Nom de plume on 2008-06-27
I've been searching for the Kino fix, but haven't found it.

I got Kino, used it and loved it. It worked for about a day, then all of a sudden, it stopped importing files (the same .avi files that it had happily imported the day before). It doesn't give me any error messages or anything like that, it just starts importing a file and says 'Importing - this may take a while' then it stops and I find that it hasn't really done anything.

I tried opening it with gksudo kino, and the terminal says that it is skipping files. I wish I weren't so green, then maybe I would know what that meant.

Anyone else had the same problem? Or is it only me?

---

