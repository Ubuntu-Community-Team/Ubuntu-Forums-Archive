---
title: "sound-juicer: recommended gstreamer pipeline for mp3"
date: 2008-06-24
forum: Multimedia Software
---

### Post by Circus-Killer on 2008-06-24
Hey there,

I've been trying to figure this out for quite a long time now. I'm trying to find the best recommended settings to encode high quality mp3 files.

Obviously, this can be very opinionated, but what I am looking for is something like they have over at [HydrogenAudio]("http://wiki.hydrogenaudio.org/index.php?title=Lame"). Unfortunately, their settings dont work directly with gstreamer. I am trying to get the equivalent to "-V1 --vbr-new" for gstreamer.

this is what i got at the moment:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 vbr-quality=1 ! id3v2mux
```

if anybody has any clue if/where i am going wrong, please help.

---

### Post by Circus-Killer on 2008-06-24
*bump*

---

### Post by Circus-Killer on 2008-06-24
okay, ive changed the gstreamer pipeline to:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=1 ! id3v2mux
```

i still dont know if this is right.
i am trying to get it to be equivilant to -V1 --new-vbr.

any suggestions/comments?

---

### Post by Circus-Killer on 2008-06-25
> **Circus-Killer said:**
> okay, ive changed the gstreamer pipeline to:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=1 ! id3v2mux
```

i still dont know if this is right.
i am trying to get it to be equivilant to -V1 --new-vbr.

any suggestions/comments?

alright, in my quest to get this right, i managed to find some explanations behind the settings im using.

"mode=0" is for stereo (mode=1 for joint stereo)
"vbr=4" is the same as --new-vbr
"vbr-quality=1" is the same as -V1

so in conclusion, i have achieved what i was trying to do.
am i correct?
any comments?

---

### Post by sicofante on 2008-07-10
I'm in the same boat as you. No matter what I try, I always get the same file size and i can see (in file properties) I always get 128 Kbps (no clue about VBR, CBR, ABR, etc.)

Have you been succesful to get files with different bitrates?

Have you found a full correspondence table of gstreamer pipeline settings and the original LAME settings?

---

### Post by screaminj3sus on 2008-07-16
No matter hat I do I only get an average bitrate of 150-160 kb/s, and I'm trying to get v0. Is there anyway to fix this? I do have lame and the gstreamer multiverse installed. Thsi is way too much work just to rip a cd.

EDIT: at OP install Rubyripper, you have to compile it but it's the best ripper I've used in a while, rips v0 flawlessly for me. It's a lot like EAC for windows, very high quality rips.

---

### Post by Circus-Killer on 2008-07-24
well, the [wiki]("https://help.ubuntu.com/community/CDRipping") page gives this as the best pipeline to use:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1 vbr=4 quality=1 preset=1001 vbr-max-bitrate=320 ! xingmux ! id3v2mux
```

gonna give it a bash and see how the quality comes out.

---

### Post by Major_Kong on 2008-07-24
if you want to see all the options use this in the console:
> 
gst-inspect-0.10 lame

But overall i wouldn't use soundjuicer for two reasons mostly:

1. Gstreamer is full of mp3 encoding bugs. It's better to use the lame cli encoder to handle the encoding part.

2. Soundjuicer doesn't support secure ripping.


Try using rubyripper. And checkout this thread -> [http://wiki.hydrogenaudio.org/index.php?title=LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME)

---

### Post by Circus-Killer on 2008-07-25
okay, took your advice, switched to a ripper that uses lame.
switched to kaudiocreator.
not thrilled about using a kde application in gnome, but hey, go with what works, right? ;)

---

### Post by Sweet Spot on 2008-07-25
On a related note, I've been ripping and encoding to MP3 with K3b, and the LAME setting at default is :

lame -h --tt %t --ta %a --tl %m --ty %y --tc %c - %f

I honestly don't know what's what in that argument and would like to be encoding with good quality at around 192 kbps. What should I change in the line, and what does it mean in its current state ?

Doug

---

### Post by Yellow Pasque on 2008-07-25
Is there any reason why you can't encode to OGG/Vorbis instead?

Also, I don't normally recommend throwing money at problems, but hard disk storage is very cheap these days. Have you considered encoding to FLAC instead and buy another disk if you need more storage?

---

### Post by Major_Kong on 2008-07-25
> **Circus-Killer said:**
> okay, took your advice, switched to a ripper that uses lame.
switched to kaudiocreator.
not thrilled about using a kde application in gnome, but hey, go with what works, right? ;)

Try rubyripper, it's gtk - [http://getdeb.net/download/2015/0](http://getdeb.net/download/2015/0) - and it works fine.

> 
lame -h --tt %t --ta %a --tl %m --ty %y --tc %c - %f


The "-h" is for the noise shaping & psycho acoustic algorithm.
All the "--" switches are the encoder's id3 tag options,
>     --tt <title>    audio/song title (max 30 chars for version 1 tag)
    --ta <artist>   audio/song artist (max 30 chars for version 1 tag)
    --tl <album>    audio/song album (max 30 chars for version 1 tag)
    --ty <year>     audio/song year of issue (1 to 9999)
    --tc <comment>  user-defined text (max 30 chars for v1 tag, 28 for v1.1)
"%t", is k3b field for the track's title, "%a", for the track's artist, etc.

If you want to encode to ~192 kbps, try this:

lame -h _-V 2_ --tt %t --ta %a --tl %m --ty %y --tc %c - %f


PS: [http://wiki.hydrogenaudio.org/index.php?title=LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME) - You should have a look at this.

---

### Post by Sweet Spot on 2008-07-26
Thanks Kong. I'll try that, as well as look at HA forums for stuff, but I always find their musings a bit cryptic, and never get a good straight answer there. 

doug

---

### Post by e-nygma on 2008-07-27
Try this in the gstreamer pipeline.  You can change the min and max bitrate, as well as other parameters, to suit your taste.  These settings encode a variable bit rate file which average between 192 to 220, depending on the complexity of the music.  If you want a smaller file size, or a larger one, just change the min and max bit rate.  I hope this helps.  


audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 vbr-min-bitrate=128 vbr-max-bitrate=224 ! xingmux ! id3v2mux

---

### Post by Circus-Killer on 2008-07-28
> **Temüjin said:**
> Is there any reason why you can't encode to OGG/Vorbis instead?

Also, I don't normally recommend throwing money at problems, but hard disk storage is very cheap these days. Have you considered encoding to FLAC instead and buy another disk if you need more storage?

nope, car radio will only play mp3 :popcorn:

---

### Post by Circus-Killer on 2008-07-29
@ Major_Kong

you stated in previous post:
> The "-h" is for the noise shaping & psycho acoustic algorithm.

what exactly is this noise shaping and psycho acoustic? does it improve quality?

here is how my lame command is:
```
lame --vbr-new -V2 --tt %{title} --ta %{artist} --tl %{albumtitle} --ty %{year} --tn %{number} --tg %{genre} %f %o
```

from what i read, i still need to use --vbr-new because the lame encoder im using is at 3.97 and you can leave out that from 3.98 and up.

but as said, i didnt use the -h, and i was wondering how much different the output would be if i did use it, and what that difference would be?

---

