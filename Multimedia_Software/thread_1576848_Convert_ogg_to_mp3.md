---
title: "Convert ogg to mp3"
date: 2010-09-17
forum: Multimedia Software
---

### Post by solomonson on 2010-09-17
I have a few ogg files that I want to put on my phone.  My phone doesn't play oggs, so I need to convert.  It's just an audiobook so I really don't care about quality.  Oddly, nothing I try seems to be up to the task.  Here's what I tried so far:
[U]
sox my.ogg my.mp3:[/U] 
"sox FAIL formats: can't open output file `x.mp3': SoX was compiled without MP3 encoding support"

_mencoder:_
wants video too??  Wha??

_vlc (from GUI):_
"p, li { white-space: pre-wrap[COLOR=#ff0000]Streaming / Transcoding failed:[/COLOR] [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG Audio layer 1/2/3.[/COLOR]
 [COLOR=#000000]If you don't know how to fix this, ask for support from your distribution.[/COLOR]
 
 [COLOR=#000000]This is not an error inside VLC media player.[/COLOR]
 [COLOR=#000000]Do not contact the VideoLAN project about this issue."[/COLOR]

_lame my.ogg my.mp3:_
"sorry, vorbis support in LAME is deprecated."

_audicity (via GUI):_
success..but I'm now going to have to somehow script it.

This is very annoying.  It makes me want to rip directly into mp3 from now on. Is there an easy way to convert an ogg file to an mp3 from the command-line?

---

### Post by PhilGil on 2010-09-17
Although mainly a GUI tool, sound converter (package: soundconverter) has a basic command-line interface.  The GUI is also pretty slick - just set up your conversion options and drag in the files or folders you'd like to convert.

I use it all the time to convert ogg to mp3.

---

### Post by VastOne on 2010-09-18
> **PhilGil said:**
> Although mainly a GUI tool, sound converter (package: soundconverter) has a basic command-line interface.  The GUI is also pretty slick - just set up your conversion options and drag in the files or folders you'd like to convert.

I use it all the time to convert ogg to mp3.

Same here but if you overclock like I do, watch out when doing mass conversions because it will heat that processor up.

---

### Post by dirghrabadia on 2010-09-18
Shouldn't FFmpeg work? [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by bcschmerker on 2010-09-18
> **PhilGil said:**
> Although mainly a GUI tool, sound converter (package: soundconverter) has a basic command-line interface.  The GUI is also pretty slick - just set up your conversion options and drag in the files or folders you'd like to convert....Thanks for the tip; I may be using this package in the near future.  In 10.04, as of 17 September 2010, GNOME Sound Recorder cannot generate MP3 direct from analog, but it *will* do Ogg Vorbis object files.  I presume that Sound Converter has a Manual page for it?  It would definitely help, in terms of completing the metadata for the MPEG-1 Level 3 audio files that I need to synthesize.

---

### Post by Yellow Pasque on 2010-09-18
How about building your own sox with mp3 support?

---

### Post by cascade9 on 2010-09-18
> **PhilGil said:**
> Although mainly a GUI tool, sound converter (package: soundconverter) has a basic command-line interface.  The GUI is also pretty slick - just set up your conversion options and drag in the files or folders you'd like to convert.

Soundkonvter (KDE, as if that kwasnt kobvious LOL) works well too. 

I onyl use it for .flac-> MP3 conversions for my probtable media player. It will play .flac, but with 6GB of memory I just cant fit enough .flacs on it. Also MP3 album art actually works, flac album art doesnt work on my player.

---

### Post by andrew.46 on 2010-09-18
The problem of SoX being unable to transcode to mp3 is one that is often raised on these forums, perhaps you would be interested in enabling *full* mp3 support? The following works under the 32 bit Lucid Lynx, it may work under the 64 bit version but I have not tested this. You will need to have the Universe Repository enabled as well as the 'Source Code' option.

First install some build tools:

```

sudo apt-get install build-essential fakeroot dpkg-dev devscripts

```

Next install the build dependencies for SoX as well as the new one of libmp3lame-dev:

```

sudo apt-get build-dep sox
sudo apt-get install libmp3lame-dev

```

Then pick up the source:

```

cd $HOME/Desktop && mkdir build && cd build
apt-get source sox
cd sox-14.3.0

```

Now remove the option that blocks mp3 encoding, add libmp3lame-dev to the build depends, remove the warning about mp3 writing, rebuild the packages, install them and finally clean the source:

```

sed -i 's/--without-lame //' debian/rules
sed -i 's/libmagic-dev, /libmagic-dev, libmp3lame-dev, /' debian/control
sed -i 's/Write support not available yet.//' debian/control
fakeroot debian/rules binary
sudo dpkg -i ../*.deb
fakeroot debian/rules clean

```

Now you can encode to mp3 with Sox :).

Andrew

---

### Post by Yellow Pasque on 2010-09-18
Get the uncrippled version of sox from: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)

---

### Post by Mike922 on 2011-01-30
So having installed SOX as per above and being in a directory with an ogg file with the filename of **SOS.ogg** here is my command line.

```
sox SOS.ogg SOS.mp3
```

and I get the following

> sox FAIL formats: can't open input file `SOS.ogg': No such file or directory

If I try

```
sox ./SOS.ogg SOS.mp3
```

I get

> sox FAIL formats: can't open input file `./SOS.ogg': No such file or directory

What am I doing wrong?

Thanks,
Mike

---

### Post by andrew.46 on 2011-01-31
> **Mike922 said:**
> What am I doing wrong?

Hmmm..... can you check that the file is definitely there by running:

```
ls -l
```

in the directory where you are issuing your command? Also just check that you now have only *one* version of SoX installed, something like the following command might be useful:

```
sudo find /usr -iname 'sox'
```

---

### Post by komputes on 2012-02-14
[CENTER][B][IMG]http://imgbin.org/images/6799.jpg[/IMG]

Good news everyone![/B]


[/CENTER]
From what I can tell, this is no longer necessary since 10.10 (Maverick) thanks to [this bugfix]("https://bugs.launchpad.net/ubuntu/+source/sox/+bug/223783/comments/22")!

> 
sox (14.3.1-1ubuntu1) natty; urgency=low
   * Enable lame support (drop --without-lame and add libmp3lame-dev to
    build dependencies) (LP: [#223783]("https://bugs.launchpad.net/bugs/223783")).*Now for my issue...*

"sox file.wav file.mp3" gives me MP3/128k/44.1

However the quality is horrible. I can't get a conversion to MP3/192k/44.1 as commands fail with this:

```
$ sox startup.wav -r192k startup.mp3
sox FAIL formats: can't open output file `startup.mp3': LAME initialization failed
```I  have sox, lame, libsox-fmt-all, libmp3lame0, libmp3lame-dev. Do you  guys have this issue with the self-compiled versions. Any solution on  how to fix that?

Also, related thread:
**How to record all audio output from sound card in Ubuntu 9.10 Karmic Koala**
[http://ubuntuforums.org/showthread.php?t=1330728](http://ubuntuforums.org/showthread.php?t=1330728)

---

### Post by andrew.46 on 2012-02-15
Perhaps try:

```

sox startup.wav -C 192 startup.mp3

```

or perhaps go for VBR with:

```

sox startup.wav -C -2 startup.mp3

```

Information about the options for mp3 and sox, and a host of other formats can be found in the *soxformat* man page.

---

### Post by komputes on 2012-02-16
:grin: andrew.46 thanks so much, that totally did it :D

It works when converting a file, but I'm trying to find an equivalent command for converting from stdout.

The command I had before produced a wav and now I am looking to produce an mp3:

```
#parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - ~/Taped_Recording_$TIME.wav
parec -d "$MONITOR" | sox -t mp3 -C 192 - ~/Taped_Recording_$TIME.mp3

```

Let me know if this is too much for this thread and we can move it to my other thread (still seems subject related). Cheers.

---

### Post by andrew.46 on 2012-02-17
Unfortunately I do not use pulse audio, which I presume is where parec comes from, so I am not any use on this one :(. Hopefully someone else has the answer...

---

