---
title: "GMediaServer : Need help compiling 0.13.0 on Gutsy"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by tcrroadie on 2008-01-07
I am trying to compile the latest version of GMediaServer (0.13.0) on my Gutsy server since the version that ships with Gutsy does not have support for the Sony Playstation 3.  

I am receiving an error during ./configure

```
checking magic.h usability... yes
checking magic.h presence... yes
checking for magic.h... yes
checking for magic_open in -lmagic... no
configure: error: libmagic library or magic_open function not found
```

I have libmagic1 and libmagic-dev installed so I am a little stumped.  

Any help would be greatly appreciated.

---

### Post by windyweather on 2008-03-22
Sure would be nice if someone would do the build as an update.

--profile=ps3 doesn't work in 0.12.0 and
I'm getting 2103 protocol errors for music with 0.12.0 when talking to my PS3.

Nobody solve the build problem?

UPDATE: I found the 0.13.0 version built for Hardy and it installs just fine on Gutsy.

[http://packages.ubuntu.com/hardy/i386/gmediaserver/download](http://packages.ubuntu.com/hardy/i386/gmediaserver/download)

I'm trying it now to see if solves my problem. It does understand the --profile=ps3 option, so I am hopeful.

Update: I'm still getting the 2103 protocol error with 0.13.0 and no ability to server MP3s, although photos work fine with PS3 running 2.17.
I'll report this problem to the gMediaServer folks.

Thanks- 
windy

---

### Post by Gul Macet on 2008-03-29
Oh, I got 0.13.0 to build all right. Once I'd satisfied myself that my recent version of libmagic did in fact have magic_open in it, I decided the magic_open test in **configure** must be busted, so I removed it, and replaced it with the line:

LIB="-lmagic $LIBS"

Now it configures and builds just fine.

That's the good news, along with the fact that 0.13.0 gmediaserver now recognizes --profile=ps3.

The bad news is that it doesn't work any better than 0.12.0. I still get all kinds of protocol errors from my PS3, and it still tells me my .mp3 files are all "Unsupported".

So, no joy. Couldn't get Elisa to run, either. Guess I'm stuck with WMP11 on my Windows machine.

---

### Post by windyweather on 2008-03-29
I'm using Twonky Media 4.4.4 for Linux on my little Linux Via 7 box and it works fine for photos and MP3s. It's only $29 for a license.

It tosses an occasional protocol error, but other than that it works fine.

fwiw,
ww

---

### Post by Gul Macet on 2008-03-29
I'm starting to think you might be right going the Twonky route.

I just built and configured Fuppes ([http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/)) and while it's a pleasure to install, it still has issues. Songs stop after a minute or two, or even repeat (that is, it will jump back a minute or so in the past and keep playing forever), and this is on a stock Dell laptop w/Gutsy.

I'll go to great lengths to avoid using Windows for this, even pay money if I have to.

---

