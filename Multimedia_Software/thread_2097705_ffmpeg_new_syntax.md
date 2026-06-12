---
title: "ffmpeg new syntax"
date: 2012-12-24
forum: Multimedia Software
---

### Post by shantiq on 2012-12-24
ffmpeg seem to have a new syntax/glossary these days


things like -acodec and -vcodec have been replaced by -c:a  and the like


where can one find a "translating manual"  or a chart to show equivalences ?

and how much has changed?    thanx for all clear explanations

---

### Post by Merrattic on 2012-12-24
From what I can gather the main ones are:

acodec  >  c:a
vcodec  >  c:v

audio bitrate   >  b:a
video bitrate   >  b:v

Don't think much else has changed in this area, though I am sure "FOM" will be along with help. ffmpeg documentation is, as usual, terse and sparse with such details. it would be useful to gather all the recent changes and get them into the [http://ubuntuforums.org/showthread.php?t=2096866](http://ubuntuforums.org/showthread.php?t=2096866) thread

---

### Post by shantiq on 2012-12-24
thank you Merratic for this


yes i simply wonder how extensive it all is...   maybe just those


we need to have it all in those guides there for easy universal access


i have seen it written in the "new way"   here and there   and my question was triggered by FOM   giving me this

[CENTER]>  ffmpeg -i input -c:a libfdk_aac -profile:a aac_he_v2 -vbr 1 -afterburner 1 output[/CENTER]


which I at first thought was in sanskrit:KS:KS  [but works very well]

---

### Post by andrew.46 on 2012-12-24
The man page holds some treasures as well as some basics. This one for instance:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -h encoder=libopus 2>/dev/null[/COLOR]**
Encoder libopus [libopus Opus]:
    Supported sample rates: 48000 24000 16000 12000 8000
    Supported sample formats: s16 flt
    Supported channel layouts: mono stereo 3.0 quad 5.0 5.1 6.1 7.1
libopus AVOptions:
-application       <int>        E...A. Intended application type (from 2048 to 2051)
   voip                         E...A. Favor improved speech intelligibility
   audio                        E...A. Favor faithfulness to the input
   lowdelay                     E...A. Restrict to only the lowest delay modes
-frame_duration    <float>      E...A. Duration of a frame in milliseconds (from 2.5 to 60)
-packet_loss       <int>        E...A. Expected packet loss percentage (from 0 to 100)
-vbr               <int>        E...A. Variable bit rate mode (from 0 to 2)
   off                          E...A. Use constant bit rate
   on                           E...A. Use variable bit rate
   constrained                  E...A. Use constrained VBR


```

wll worth a look for the basic syntax as well :)

---

### Post by evilsoup on 2012-12-24
Generally, things that used to be prefaced with a* or v* have changed to *:a or *:v. So There's the examples Merrattic has given, then things like absf have been changed to bsf:a (though the old way of doing it still works, I assume they'll take that out eventually).

BTW, you can specify individual output streams by using their stream number. Let's say you're converting something with one video (stream 0) and two audio (1 and 2) streams. -c:v will target all vidoe streams, -c:a will target all audio streams, -c:0 will target the first stream (video in this case), and -c:a:0 will target the first audio stream. This can be generally used for all the options that use the -option:stream syntax.

---

### Post by shantiq on 2012-12-24
> you can specify individual output streams by using their stream number. Let's say you're converting something with one video (stream 0) and two audio (1 and 2) streams. -c:v will target all vidoe streams, -c:a will target all audio streams, -c:0 will target the first stream (video in this case), and -c:a:0 will target the first audio stream. This can be generally used for all the options that use the -option:stream syntax.



nice!:KS

---

### Post by FakeOutdoorsman on 2012-12-25
> **shantiq said:**
> ffmpeg seem to have a new syntax/glossary these days

things like -acodec and -vcodec have been replaced by -c:a  and the like

how much has changed?
ffmpeg will give suggestions for many of the new aliases (in a brown color in my console), and some of the old options should still work as expected for now. Some newish stuff:

[list]
[*]Option placement is more strict and consistent, so it is important to know the difference between input and output options since all options will be applies to the following input or output:
```
ffmpeg [global options] [input options] -i input [output options] output
```
Global options include "-y", "-n", "-stats", etc. See "man ffmpeg" command to see what options show "(global)" next to the option name.
[/list]

[list]
[*]"-sameq" is gone, thankfully: [Why was the ffmpeg &#8216;-sameq&#8217; option removed? What to use instead?](http://ffmpeg.org/faq.html#Why-was-the-ffmpeg-_002dsameq-option-removed_003f-What-to-use-instead_003f)
[/list]

[list]
[*]The "[-map](http://ffmpeg.org/ffmpeg.html#Advanced-options)" option is much more powerful and useful allowing for the use of [stream specifiers](http://ffmpeg.org/ffmpeg.html#Stream-specifiers-1) (make sure to read that link) as evilsoup has mentioned, and can also accept "negative mapping" to exclude specific streams. The new functionality has made the crappy, old -newvideo/-newaudio/-newsubtitle options obsolete and depreciated.
[/list]

[list]
[*]"-filter_complex" is used instead of "-vf" when you want to use filter(s) with multiple inputs, such as with *overlay*, to create a [complex filtergraph](http://ffmpeg.org/ffmpeg.html#Complex-filtergraphs), as opposed to a [simple filtergraph](http://ffmpeg.org/ffmpeg.html#Simple-filtergraphs) which involves one input and one output.
[/list]

Other stuff:
[list]
[*]-vcodec, -acodec, -scodec = -codec/-c (uses stream specifiers as in -codec:v or -c:v)
[*]-vf = -filter (uses stream specifiers as in -filter:v)
[*]-vframes, -aframes = -frames (uses stream specifiers)
[*]-vtag, -atag = -tag (uses stream specifiers)
[*]-qscale = -qscale:v/-q:v, -qscale:a/-q:a (uses stream specifiers)
[*]-intra = -g 0
[*] My boiler quit working yesterday. It is now 47°F/8°C indoors.
[/list]

---

### Post by andrew.46 on 2012-12-25
> **FakeOutdoorsman said:**
> My boiler quit working yesterday. It is now 47°F/8°C indoors.

Mid-summer here 40°C the other day; my brand new AMD 8350 + FFmpeg conversions heat my little room up a little too much :(. Converting [Decay ]("http://www.decayfilm.com/pages/download.html")for tv playback atm: 'The greatest discovery in physics could be our last.....'.

---

### Post by shantiq on 2012-12-26
thank you ... so many changes really:KS

sorry about that
> My boiler quit working yesterday

---

### Post by two4two on 2013-01-08
Which ffmpeg version?  I have not upgraded since Ubuntu Studio Natty.  So I assume this won't apply to me?

---

### Post by evilsoup on 2013-01-08
If you're using the version from the natty repos, then no I don't think any of this stuff will apply to you. There have been a lot of bugfixes and improvements since then, though, so it may be a good idea to upgrade to a more recent version. You can either compile it yourself (for the very latest development version), or [this PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) (not as cutting edge, but 2+ years of extra development is nothing to be sneered at).

---

