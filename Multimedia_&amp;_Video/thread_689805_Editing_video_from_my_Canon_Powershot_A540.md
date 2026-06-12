---
title: "Editing video from my Canon Powershot A540"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by Howlin' Hobbit on 2008-02-06
When my camera records videos it turns out AVI files that are Motion JPG for the video part and (IIRC) MPEG2 for the audio. I can't remember how to look that up right now so I'm not positive on the audio thing.

I'm running Dapper Drake (with the latest kernel) on an old Dell Inspiron 5000 laptop.

I simply want to make videos of me playing music (ukulele mostly... for any fellow uke-phreaks hanging out in here) and upload them to YouTube.

The initial problem was the AVI's that my camera turned out were *way* too large for YouTube.

After *4 freaking days* of trying all sorts of things, I finally got Mediacoder running under WINE so I could shrink them without screwing up the sync etc. That's a "shame on you, Linux." I shouldn't have to run a dang Windoze program to do something like that.

But, hey! It's working and in the process I learned more about Linux, (mostly) fixed the months-long problem with the update manager and got the AVI's playing on my Ubuntu box. These are big wins.

But now I'm depending on YouTube's online editor/remixer to clip off the parts that show me backing away from the camera after I turn it on, getting settled in the chair, etc. and finally reaching for the camera again to turn it off. This is not so good since their thing seems to be broken almost as much as it is working. If not more.

I want to be able to trim those bits off before I upload.

**Nothing** I've tried works to do that.

Kino wants a DV format file and Mediacoder won't transcode into that format for me. I may just be missing a setting on the latter. It wouldn't make me an MPEG4 until I stumbled across the "Muxer" tab on the program (it had been giving me "can't mux the audio and video together" errors). I took a S.W.A.G. at which setting to give in that tab and, lo!, I can get my vids squished down to the right size now.

None of the command line stuff that I tried for either mencoder or ffmpeg worked.

I even downloaded, burned to a CD, and installed the dyne:bolic thing. No joy.

Does anyone know *any* way that I can clip the ends of the videos off? I probably need a GUI version so I can be sure I'm clipping off the proper amount of seconds at either end. It needs to run on a trailing edge laptop.

I don't care if I have to swap it over to another format, clip the ends, swap it into yet another format, and then shrink it down into the MPEG4 w/MP3 audio that YouTube likes before uploading. I simply want to be able to do this all at my Ubuntu box.

Any help is appreciated. I've already had to leave my "big" machine with Windows (so I can do audio recording/mixing) and, believe it or not, the above rant is not because I want to switch away from Linux. In general I like Ubuntu **loads** better than Windows -- you can come up with lots of the reasons -- I just want to get this one operation working.

One final thing... Kino tells me that my AVI file isn't the DV they like, would I like to import it? I say "yes" and it seems to hang in the import function. If this is something that takes an hour or so and I'm simply not being patient enough, let me know that and I'll try the patience thing at least long enough to give Kino a chance.

Thanks in advance for any help.

---

### Post by philc on 2008-02-06
> **Howlin' Hobbit said:**
> 
None of the command line stuff that I tried for either mencoder or ffmpeg worked.


Can you elaborate some more regarding why or how this didn't work? Were you unable to install the applications? Unable to figure out the correct line commands (it is hard work with FFmpeg and Mencoder!)? Or was the output not what you expected?

The reason is that many Linux video editing tools rely on FFmpeg in some way for either decoding or encoding video. If you're having problems installing it, then you will likely have problems with Linux video editing software.

If FFmpeg is installed OK, then I would suggest Open Movie Editor. It's a pretty straightforward editing tool, with a traditional timeline and probably won't take too long to learn.
[http://openmovieeditor.sourceforge.net/HomePage](http://openmovieeditor.sourceforge.net/HomePage)

Also, perhaps worth trying Fuoco Tools or ConvertIT, which have busy threads on these boards.

---

### Post by Howlin' Hobbit on 2008-02-06
> **philc said:**
> Can you elaborate some more regarding why or how this didn't work? Were you unable to install the applications? Unable to figure out the correct line commands (it is hard work with FFmpeg and Mencoder!)? Or was the output not what you expected?
Apps installed fine. I didn't try to figure out the line commands, I went through a HUGE list of them that I found via one of the forum posts. Actually a couple lists. They either turned out 0 byte files (sometimes with error messages, sometimes not) or files that were horrendously out of sync, garbled or otherwise unusable.

> **philc said:**
> If FFmpeg is installed OK, then I would suggest Open Movie Editor. It's a pretty straightforward editing tool, with a traditional timeline and probably won't take too long to learn.
[http://openmovieeditor.sourceforge.net/HomePage](http://openmovieeditor.sourceforge.net/HomePage)

Open Movie Editor has distros for Gutsy Gibbon and Hardy whatever-it-is (Heron??). I'm running Dapper Drake LTS. I don't want to upgrade at least until such time as they have an LTS version of whichever. Should I just try to get the deb file for OME and install it?

> **philc said:**
> Also, perhaps worth trying Fuoco Tools or ConvertIT, which have busy threads on these boards.
Installed ConvertIT first and got no joy. No file written or garbled crap... mostly the former.

On looking up Fuoco I see that it's a converter. I have mediacoder working well enough to convert from what my camera churns out to something that YouTube likes (and is much smaller for ease of upload). What I need now is something to trim the ends off of the video so that the "getting ready to play" and "turning off the camera" parts don't get uploaded to YouTube.

Thanks for your time.

---

### Post by Creative2 on 2008-02-09
if your problem is dv format  fuoco can encode in that format:(it uses ffmpeg ...)[COLOR="Red"] JUST INSTALL FFMPEG AND MENCODER FROM MEDIBUNTU REPO
[/COLOR]
extra---->to kino---->ntsc(or pal) 

make sure you have ffmpeg from medibuntu repo to ensure it will support every formats

or use this on terminal 

ntsc  if doesn't work use the other command  line for ntsc

```
ffmpeg -i INPUT -target ntsc-dv  OUTPUT.dv

```

```
ffmpeg -i INPUT -sameq -target ntsc-dv  OUTPUT.dv 
```

pal if doesn't work use the last command  line

```
ffmpeg -i INPUT -sameq -target pal-dv  OUTPUT.dv
```

```
ffmpeg -i INPUT -target pal-dv  OUTPUT.dv
```


youtube ready to upload (fuoco has this you can set bitrare audio and video but resolution must be that...or will be encoded by youtube programs and ...so ..)
```

ffmpeg -i INPUT -b 500k -r 30 -ab 128k -ar 44100 -s 320x240 -ac 2 -y OUTPUT
```

time selection (fuoco has this but in command line...i have command line for ffmpeg but i don't remember now..)

```

mencoder INPUT -ovc copy -oac copy -ss  hh:mm:ss.ms  -endpos hh:mm:ss.ms  -o myfile.avi
```


final answer:

importing of kino ,as everybody can see running it from a terminal , is a conversion from any format to dv...it uses ffmpeg ....so your problem is ffmpeg not installed correctly...(learn about medibuntu repo then reinstall ffmpeg mencoder and you will see kino can import your stuff)

**all this stuff is on fuoco tools ....** and it works if you installed [COLOR="Red"]ffmpeg and mencoder correctly from medibuntu repo[/COLOR]

---

