---
title: "How to hardsub a video?"
date: 2015-05-06
forum: Multimedia Software
---

### Post by remmas-sido on 2015-05-06
Hello guys 
Let us just say that I have a mkv video, and I would like to encode it to mp4 or avi hardsubbed video. How do I do that?

---

### Post by bfmetcalf on 2015-05-06
> **remmas-sido said:**
> Hello guys 
Let us just say that I have a mkv video, and I would like to encode it to mp4 or avi hardsubbed video. How do I do that?

Look into Handbrake.  It works well for converting mkv to mp4 for sure and has a lot of options to get the subtitles hardsubbed.

---

### Post by orionds on 2015-05-06
Make sure you install at least Handbrake 0.10. On previous versions hardsub, if I remember right, is only available for vobsubs, that is, subtitles on DVDs. If you want to hardsub srt (text) subtitle files, version 0.10 or the beta versions have this capability.

---

### Post by SeijiSensei on 2015-05-06
You can also do it directly from the command prompt with ffmpeg: [https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo](https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo).  You can change the container by using a different extension on the output file as in the example that creates an AVI file from Matroska input.

I presume the fork of ffmpeg that Ubuntu ships, called avconv, works the same way if you substitute "avconv" for "ffmpeg" in those commands.  If not, I recommend using Doug McMahon's build of ffmpeg at [this PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media).

---

### Post by remmas-sido on 2015-05-08
> **SeijiSensei said:**
> You can also do it directly from the command prompt with ffmpeg: [https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo](https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo).  You can change the container by using a different extension on the output file as in the example that creates an AVI file from Matroska input.
In order to do that you have to access the video directory through cd command?

---

### Post by remmas-sido on 2015-05-08
> **SeijiSensei said:**
> You can also do it directly from the command prompt with ffmpeg: [https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo](https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo).  You can change the container by using a different extension on the output file as in the example that creates an AVI file from Matroska input.

I presume the fork of ffmpeg that Ubuntu ships, called avconv, works the same way if you substitute "avconv" for "ffmpeg" in those commands.  If not, I recommend using Doug McMahon's build of ffmpeg at [this PPA]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media").
I'm trying to hardsub a mkv with ass subs embedded, but as soon as I type ffmpeg -i nameofthevideo.mkv I get this message displayed in the terminal: 
The ffmpeg program is only provided for script compatibility and will be removedin a future release. It has been deprecated in the Libav project to allow for
incompatible command line syntax improvements in its replacement called avconv
(see Changelog for details). Please use avconv instead.

---

### Post by SeijiSensei on 2015-05-08
deleted; see below

---

### Post by SeijiSensei on 2015-05-08
> **remmas-sido said:**
> In order to do that you have to access the video directory through cd command?

Yes, or use full paths:
```
ffmpeg -i /path/to/input.mkv [options] /path/to/output.mp4
```

As I said, if you use an Ubuntu version prior to 15.04, you need to substitute "avconv" for "ffmpeg" in the commands.  Otherwise you can install the current version of real ffmpeg by using the PPA repository I linked to above.  

(As for why this confusion exists, it's largely [political]("http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html").)

Authentic ffmpeg has [reappeared]("https://launchpad.net/ubuntu/vivid/+source/ffmpeg") in 15.04.  That's not a sufficient reason to upgrade; I just use the mc4man repository with 14.04.

---

### Post by remmas-sido on 2015-05-08
> **SeijiSensei said:**
> Yes, or use full paths:
```
ffmpeg -i /path/to/input.mkv [options] /path/to/output.mp4
```

As I said, if you use an Ubuntu version prior to 15.04, you need to substitute "avconv" for "ffmpeg" in the commands.  Otherwise you can install the current version of real ffmpeg by using the PPA repository I linked to above.  

(As for why this confusion exists, it's largely [political]("http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html").)

Authentic ffmpeg has [reappeared]("https://launchpad.net/ubuntu/vivid/+source/ffmpeg") in 15.04.  That's not a sufficient reason to upgrade; I just use the mc4man repository with 14.04.
Concerning the PPA you listed above I'm using Precise and the name Trusty is mentioned, in other words is it compatible with Precise the same way as Trusty?

---

### Post by SeijiSensei on 2015-05-08
No, it's only for Trusty.  I looked around a bit for a PPA that supports Precise and couldn't find one easily.  I'd just go with avconv if that's what you have available.  Does
```
avconv -i /path/to/file.mkv -vf "ass=/path/to/subtitle.ass" /path/to/file.mp4
```
do what you need?

I notice the mods fixed the site's content filter so you can type "ass" and not have it be censored. I asked for that a while back when trying to post about ASS subtitles :D.

There's always the option of [compiling your own version of ffmpeg from source]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu") if you want to have some "fun."

---

### Post by remmas-sido on 2015-05-08
> **SeijiSensei said:**
> No, it's only for Trusty.  I looked around a bit for a PPA that supports Precise and couldn't find one easily.  I'd just go with avconv if that's what you have available.  Does
```
avconv -i /path/to/file.mkv -vf "ass=/path/to/subtitle.ass" /path/to/file.mp4
```
do what you need?

I notice the mods fixed the site's content filter so you can type "ass" and not have it be censored. I asked for that a while back when trying to post about ASS subtitles :D.

There's always the option of [compiling your own version of ffmpeg from source]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu") if you want to have some fun.
-vf "ass=/path/to/subtitle.ass" I can't understand clearly, can you explain please?

---

### Post by FakeOutdoorsman on 2015-05-09
> **SeijiSensei said:**
> 2) ffmpeg will not extract the tracks from the Matroska container automatically.
Did you try the subtitles filter? It can reference the subtitles in the input file:
```
ffmpeg -i input.mkv -vf subtitles=input.mkv -c:a copy output
```
If your input has multiple subtitle streams and you want the second one (ffmpeg starts counting from 0):
```
ffmpeg -i input.mkv -vf subtitles=input.mkv:stream_index=1 -c:a copy output
```
See the [subtitles filter documentation](https://ffmpeg.org/ffmpeg-filters.html#subtitles) for more info 'n options. Note I [stream copied](https://ffmpeg.org/ffmpeg.html#Stream-copy) the audio just for the hell of it.
> **SeijiSensei said:**
> To use this you would first need to find a version of ffmpeg that runs on 12.04, or upgrade to 14.04 and use the mc4man PPA, or upgrade to 15.04 where ffmpeg is once again included with the distribution.
Or [download a static build of ffmpeg](https://ffmpeg.org/ffmpeg.html#Stream-copy). Probably the easiest method.

---

### Post by FakeOutdoorsman on 2015-05-09
> **SeijiSensei said:**
> Now use the nano editor to create a file called "hardsub" in /usr/local/bin like this

Alternatively you can just put your user scripts in ~/bin. It's in the $PATH by default in a normal Ubuntu (or it was last time I checked an Ubuntu ~/.profile/)...but only if ~/bin exists upon login. So once you make ~/bin and put your stuff in it you can either log in and log out, or  run:
```
source ~/.profile
```
or
```
. ~/profile
```

This method has the advantage of not needing sudo, or messing around with the "system" (although it is /local/), and you can turn it into a sloppy, lazy pigsty like mine. Disadvantage is that it won't be available to other users.

---

### Post by SeijiSensei on 2015-05-09
> **FakeOutdoorsman said:**
> Did you try the subtitles filter? It can reference the subtitles in the input file:
```
ffmpeg -i input.mkv -vf subtitles=input.mkv -c:a copy output
```
I was led astray by that [howto document]("https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo") I linked above.  It seems to distinguish ASS subtitles from other subtitles like SRT or SUB and suggests using the "-vf ass=" option.  However if you run that command pointing at the input file 
```
ffmpeg -i input.mkv -vf ass=input.mkv output
```
you get this error 
```
Parsed_ass_0 @ 0x244cfc0] Could not create a libass track when reading file 'test.mkv'
[AVFilterGraph @ 0x257eda0] Error initializing filter 'ass' with args 'test.mkv'
```
That led me to think that I needed to extract the subs and read them from a file if I wanted to use libass.

However if you run the command you suggested
```
ffmpeg -i input.mkv -vf subtitles=input.mkv output
```
then the subtitles are recognized and rendered with libass.  The documentation at ffmpeg.org made it seem the only way to invoke libass was with "-vf ass".  I made sure to remove the fonts I had in my .fonts directory first and ran fc-cache to clear them.  That way I could ensure the renderings on screen used the font attachments in the Matroska file and not the ones from fontconfig.

[s]I didn't include "-c:a copy" in my tests, but they worked fine without it.[/s] I missed your "just for the hell of it" comment my first time through.

[quote=FakeOutdoorsman]Disadvantage is that it won't be available to other users. [/quote]
I spend so much time on servers that I always assume a multi-user environment and use /usr/local for pretty much anything I add.  On a machine with just one user, then $HOME/bin is, of course, fine.

So, remmas-sido, the answer to your question is to use
```
ffmpeg -i /path/to/input.mkv -vf subtitles=/path/to/input.mkv output.mp4
```
or "output.avi" if that is what you'd prefer.

The link to the static builds brings me to an unrelated page.  The correct page is: [http://johnvansickle.com/ffmpeg/](http://johnvansickle.com/ffmpeg/).  I tested out [this one](http://johnvansickle.com/ffmpeg/builds/ffmpeg-git-64bit-static.tar.xz) on my 64-bit Kubuntu 14.04 machine.  It worked as expected. It's built on a old kernel so it should probably work well on your 12.04 machine.

---

### Post by remmas-sido on 2015-05-09
Hello guys 
so after a little but of research I finaly discovered how to hard-sub a video through Handbrake app. It's slow, but it gets the job done, and that's what matters,however, it only Import SRT files, and I want a hard-subbed video where I can see and enjoy the beautiful colors and fonts. In other word How to hard-sub a video with an ASS file,but at the same time the style of the subtitles does not changes as if you were playing an ASS subtitle with VLC. I hope you got the idea, and sorry for the long talk.

---

### Post by FakeOutdoorsman on 2015-05-09
> **SeijiSensei said:**
> I was led astray by that [howto document]("https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo") I linked above.  It seems to distinguish ASS subtitles from other subtitles like SRT or SUB and suggests using the "-vf ass=" option.
That wiki article could probably use some clarification (feel free to edit it if you like), and the existence of two different yet mostly similar filters adds to confusion.

> **SeijiSensei said:**
> That way I could ensure the renderings on screen used the font attachments in the Matroska file and not the ones from fontconfig.
Thanks for checking. I wasn't sure if it would use the fonts in the Matroska file or not.

> **SeijiSensei said:**
> I didn't include "-c:a copy" in my tests, but they worked fine without it.
I just added that as an example so other users can see that the audio doesn't have to be re-encoded.

> **SeijiSensei said:**
> I spend so much time on servers that I always assume a multi-user environment and use /usr/local for pretty much anything I add.
That's was I assumed...my comment was really for other potential users.

As a side note I'm also fan of Linode. Significantly less expensive per offering than previous services I've used and more usable/capable/flexible.

---

### Post by SeijiSensei on 2015-05-09
Please go back and read your other thread.  I and FakeOutdoorsman have presented an ffmpeg method that works very well.

Honestly it would have been better for you to have responded in the old thread..

---

### Post by remmas-sido on 2015-05-10
> **SeijiSensei said:**
> Please go back and read your other thread.  I and FakeOutdoorsman have presented an ffmpeg method that works very well.

Honestly it would have been better for you to have responded in the old thread..

Do you think my best option is to upgrade, or it's fine to stick with 12.04 release?

---

### Post by bapoumba on 2015-05-10
Threads merged.

---

### Post by Rob Sayer on 2015-05-10
Avidemux will handle ASS subs AFAIK.  Go into filters > subtitles.  However I always use mpeg-4 ASP (xvid) output when using the linux version of avidemux from the repos.

---

### Post by remmas-sido on 2015-05-10
> **Rob Sayer said:**
> Avidemux will handle ASS subs AFAIK.  Go into filters > subtitles.  However I always use mpeg-4 ASP (xvid) output when using the linux version of avidemux from the repos.

So Avidemux is my best bet?

---

### Post by SeijiSensei on 2015-05-11
> **remmas-sido said:**
> Do you think my best option is to upgrade, or it's fine to stick with 12.04 release?

You can stick with 12.04 if you install the static binary of ffmpeg I linked to above: [http://johnvansickle.com/ffmpeg/builds/ffmpeg-git-64bit-static.tar.xz](http://johnvansickle.com/ffmpeg/builds/ffmpeg-git-64bit-static.tar.xz). 
```

cd ~
mkdir -p bin
source .profile
cd bin
wget http://johnvansickle.com/ffmpeg/builds/ffmpeg-git-64bit-static.tar.xz
tar xf ffmpeg-git-64bit-static.tar.xz
cp ffmpeg-2.6.2-64bit-static/ff* .

```
Now your machine will use the copy of ffmpeg in ~/bin if you type the command:
```
ffmpeg -i input.mkv -vf subtitles=input.mkv out.mp4
```

---

