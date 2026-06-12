---
title: "What is a .mkv file"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by basilwatson on 2007-04-01
hey all 

Has anyone else come across a codec / file   , mkv     I downloaded a great program on the wrc rally champ and its in a mkv file.

I looked in the repositories and a web search ound a couple of files mkvdev but they dont seem to work,,or Ive done something wrong 

Any ideas any one

---

### Post by Jojo12a on 2007-04-01
That's the matroska container format, the file should be playable by itself on ubuntu. I think (I'm not sure) gstreamer, xine, vlc and mplayer all support it.

---

### Post by Ambimom on 2007-04-01
Some arcane Russian media format....It has its own codecs that you can download enabling it to play in VLC player.  It's quite high definition, but it won't play in standalone divx player and you can't encode it to DVD.   I hate it.  Just google it or consult  Videohelp.com to find the codecs.  I'm not sure the codecs are available to Linux, however.

---

### Post by Rhubarb on 2007-04-01
mkv is not a codec, nor is it arcane, and it is not associated with High Definition either.
mkv is a container.  That's it.

You can find divx's in lot's of different containers, like: .divx, .avi, and .ogm.
Well you can also put divx into .mkv
In fact you can put pretty much whatever audio / video / subtitles you like, and with as many languages as you like too.

To play mkv / mka media files, use mplayer or vlc.

[http://www.matroska.org/](http://www.matroska.org/)

> First, it is essential to clarify exactly "What an Audio/Video container is", to avoid any misunderstandings:

    * It is NOT a video or audio compression format (video codec)
    * It is an envelope for which there can be many audio, video and subtitles streams, allowing the user to store a complete movie or CD in a single file.

Matroska is designed with the future in mind. It incorporates features you would expect from a modern container format, like:

    * Fast seeking in the file
    * High error recovery
    * Chapter entries
    * Selectable subtitle streams
    * Selectable audio streams
    * Modularly Extendable
    * Streamable over internet (HTTP and RTP audio & video streams)
    * Menus (like DVDs have)


---

### Post by Ambimom on 2007-04-01
:oops: I stand corrected -- brutually so -- mkv is [cough] not a codec; it is a container, like xvid or divx, except unlike those,  mkv is arcane [as in *ar·cane  (är-kn) adj. Known or understood by only a few*.  It is hardly mainstream.

Feel better? codec, container, I don't know the difference.  Frankly, I don't care.  I want to know if I can view the contents with a minimum of hassle.  In my experience mkv is a hassle.

---

### Post by balance07 on 2007-04-03
also, to correct further false information about matroska in this thread, you can of course encode from MKV to DVD, as you can from any readable A/V source. mplayer/mencoder is probably your best bet for this. if mplayer can play it, mencoder can encode it.

matroska is an important part of having a system for A/V media that is based on open standards and such. personally, i use MPEG-4 AVC (h.264) video with Vorbis audio in a matroska container. it has rich tagging support as well as multiple audio streams, multiple subtitles and chapter support.

i suggest you try it. and if you like it, spread the knowledge.

---

### Post by Rhubarb on 2007-04-04
Indeed, Matroska is a very nice and flexible container.

A somewhat less flexible but still open media container is OGM.
I do know that OGM (Ogg Media) container is somewhat flexible (not nearly as much as Matroska is).  OGM supports Theora or Mpeg4 video (xvid / divx), multiple Vorbis streams, subtitles (in srt text-format), and chapters.

Matroska is an excellent container, and I dare say that it's better than Ogg Media (OGM).

---

### Post by Azakus on 2007-04-06
> **balance07 said:**
> also, to correct further false information about matroska in this thread, you can of course encode from MKV to DVD, as you can from any readable A/V source. mplayer/mencoder is probably your best bet for this. if mplayer can play it, mencoder can encode it.

matroska is an important part of having a system for A/V media that is based on open standards and such. personally, i use MPEG-4 AVC (h.264) video with Vorbis audio in a matroska container. it has rich tagging support as well as multiple audio streams, multiple subtitles and chapter support.

i suggest you try it. and if you like it, spread the knowledge.

At the moment, mencoder cannot create matroska files.
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#Multimedia_Containers](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#Multimedia_Containers)

---

### Post by balance07 on 2007-04-06
> **Azakus said:**
> At the moment, mencoder cannot create matroska files.


that is true, but:
- mplayer CAN PLAY matroska files (assuming the codecs for the streams are supported, etc)
- mencoder CAN CREATE .264 files (MPEG-4 AVC), which can be converted EASILY to .mp4 files with mp4box, and then muxed into matroska with mkvmerge. or just use mkvmerge to convert xvid/mp3 in .avi to .mkv.

my point remains, matroska is completely usable right now and, in my opinion, the only video container anyone should need. (i still use ogg for audio).

---

### Post by juxtaposed on 2007-05-04
>  it is a container, like xvid or divx,

Xvid and Divx are codecs.

Explanation: A codec (Xvid, AVC, etc) is how the information is encoded. A container (AVI, MKV, etc) is something that contains things.

> Known or understood by only a few. It is hardly mainstream.

Well, you don't understand Xvid and Divx - are they archane?

> and it is not associated with High Definition either.

Except that scene groups put their high definition x264 files into matroska, while using AVI for Xvid.

---

### Post by RawMustard on 2007-05-11
I dunno, so many blind people.

Matroska is the best container there is, no if's, no buts, end of story!  Arcane sheesh!

Name me a container that can hold any video, audio type you want plus can hold chapter information, subtitles and attachments.  Yes Attachments.  I'd love to see nautilus have more support for Matroska. Instead of seeing some silly thumbnail that nautilus extracts from some arbitrary frame from a matroska file, it could display the album/DVD cover, wouldn't that be cool? I'd love to see all gnome apps support it better, they're sorely lacking in support at the moment :(

Matroska is the way forward for Linux IMHO, it's fully open source and does everything you need from a container.  It's better supported under windows, but it could be heaps better under Linux!

---

### Post by Azakus on 2007-05-11
> **RawMustard said:**
> I dunno, so many blind people.

Matroska is the best container there is, no if's, no buts, end of story!  Arcane sheesh!

Name me a container that can hold any video, audio type you want plus can hold chapter information, subtitles and attachments.  Yes Attachments.  I'd love to see nautilus have more support for Matroska. Instead of seeing some silly thumbnail that nautilus extracts from some arbitrary frame from a matroska file, it could display the album/DVD cover, wouldn't that be cool? I'd love to see all gnome apps support it better, they're sorely lacking in support at the moment :(

Matroska is the way forward for Linux IMHO, it's fully open source and does everything you need from a container.  It's better supported under windows, but it could be heaps better under Linux!

I totally agree. I always rip my dvd's to mkv's just because it is the only container I know of that can handle an H.264 video and Ogg Vorbis audio with chapters.

---

### Post by Judo on 2007-05-11
> Explanation: A codec (Xvid, AVC, etc) is how the information is encoded. A container (AVI, MKV, etc) is something that contains things.
I would like to make a correction to that statement.  AVC is not a codec, it is a standard.  (MPEG-4 part 10, technically identical to h.264)

> Some arcane Russian media format....
I know that it is named after the Russian dolls, which I cannot spell, but I do not think it is actually Russian.  If I remember correctly, "matroska" is the German pronunciation of the Russian word, which makes me think it's German.  Then again, it may not even have an origin, considering today's developers are all around the world.

I use Matroska for nearly everything.  Like others here, I use AVC (x264) and Vorbis (whatever encoder is available, they all sound the same at 128 kbps).

---

### Post by juxtaposed on 2007-05-18
> I would like to make a correction to that statement. AVC is not a codec, it is a standard. (MPEG-4 part 10, technically identical to h.264)

I stand corrected :)

---

### Post by stevoo on 2008-04-10
lovely .... right know i understood that it can play it ... 

but i believe when it is encoded in HD mplayer cannot play it ( as well as VLC and i think Xine ) 

I believe to be missing codecs .... who can help with that  ?

---

### Post by rggavubt on 2008-04-29
Since I upgraded to 8.04 the volume is very very low on mkv files.  I set the volume to the max on everything and I can barely hear the sound.  Anyone had this problem with Hardy Heron?

---

### Post by krekon on 2008-05-25
Well I have the same problem. I also have noticed that it happens in very large files like 1GB, and in smaller files until you use any subtitle within the movie and starts playing normally.

Any suggestions?

---

### Post by kabboomm on 2008-06-19
i have downloaded an .mkv file, bit wasn't able to play it, once i played it on my ogm player it would start for only 5 seconds then it would stop, but i tried to burn it on my convertXtodvd software, once it's been transferred to the dvd, i can already watch the movie.

---

### Post by kabboomm on 2008-06-19
> **RawMustard said:**
> I dunno, so many blind people.

Matroska is the best container there is, no if's, no buts, end of story!  Arcane sheesh!

Name me a container that can hold any video, audio type you want plus can hold chapter information, subtitles and attachments.  Yes Attachments.  I'd love to see nautilus have more support for Matroska. Instead of seeing some silly thumbnail that nautilus extracts from some arbitrary frame from a matroska file, it could display the album/DVD cover, wouldn't that be cool? I'd love to see all gnome apps support it better, they're sorely lacking in support at the moment :(

Matroska is the way forward for Linux IMHO, it's fully open source and does everything you need from a container.  It's better supported under windows, but it could be heaps better under Linux!

try burning the .mkv file to a dvd, i used convertXtodvd, once it's done burning, you can now watch your movie.

---

### Post by waspbr on 2008-06-19
you should be able to play .mkv files in mplayer

if you wanna know what a file format is, a good and fast option is to check out wikipedia, for instance
[COLOR="Red"][http://en.wikipedia.org/wiki/.mkv]("http://en.wikipedia.org/wiki/.mkv")[/COLOR]

---

