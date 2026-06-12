---
title: "Renovated abcde guide..."
date: 2014-12-21
forum: Multimedia Software
---

### Post by andrew.46 on 2014-12-21
I have renovated a guide for the commandline ripper abcde during the long task of renovating my entire website. I am very keen that abcde users on these Forums have a look and cast the blowtorch of criticism across its belly in the interests of making the guide more robust.

Major changes have been:

[LIST=1]
[*]Aimed the whole guide at abcde 2.6
[*]Added an Opus section as standalone and 'combo' menu
[*]Updated the Musepack section to cater for the newly added SV8
[*]Removed the long list of codec definitions that nobody ever read!
[*]Tested and slightly tweaked the options for each codec
[*]
[/LIST]

abcde: Command Line Music CD Ripping for Linux
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

I also fixed a few small but significant syntax errors. A disappointment has been remaining with faac for aac encoding. The NeroAacEnc addition really needs a little work in abcde so I was loath to use it and mc4man has not yet organised fdkaac to be included :).

**Edit**: As a final test I am using abcde magic to encode to six different codecs, it is almost magical the way it does that :). Screenshot.....

---

### Post by FakeOutdoorsman on 2014-12-22
I still use abcde and your configs. Most recently to move some weird stock music from CD to a file server in the work office. Titles such as "Manifest Destiny", "Force of Hobbit", and "Modern Gladiator".

As for the guide this sentence, from the MP3 section, is confusing:
> Encoding is done post-encoding so options can be added here for this as well.

A link to [Hydrogenaudio LAME](http://wiki.hydrogenaud.io/index.php?title=LAME) might be worth mentioning too.

Other than that looks good to me.

---

### Post by mc4man on 2014-12-22
I thought I worked that out. Am currently moving to a new ext. ssd & due to a small self - inflicted snafu with unetbottin can no longer boot to prev. install.

Any way at a min. this - (based on the diff in ppa for abcde - 2.5.5+git as of 07/05
Meant to be used with fdkaac-encoder binary
```
@@ -3952,6 +3952,12 @@
 		AACENCODEROPTS="${AACENCODEROPTSCLI:-$AACENCOPTS}"
 		AACENCODER="$AACENC"
 		;;
+esac
+case "$AACENCODERSYNTAX" in
+	fdkaac)
+		AACENCODEROPTS="${AACENCODEROPTSCLI:-$AACENCOPTS}"
+		AACENCODER="$AACENC"
+		;;
 esac
```

After I get set up ect. tonight will ck. out when I can

---

### Post by andrew.46 on 2014-12-22
> **mc4man said:**
> I thought I worked that out. [...] Any way at a min. this - (based on the diff in ppa for abcde - 2.5.5+git as of 07/05


I have something similar but I took the chance to renovate the ghastly mess of the other 2 aac encoders, patch attached.

---

### Post by andrew.46 on 2014-12-22
> **FakeOutdoorsman said:**
> 
As for the guide this sentence, from the MP3 section, is confusing:

> Encoding is done post-encoding so options can be added here for this as well. 

A link to [Hydrogenaudio LAME](http://wiki.hydrogenaud.io/index.php?title=LAME) might be worth mentioning too.

D'oh!! It should read '*[COLOR="#FF0000"]Tagging[/COLOR]* is done post-encoding.....'! Thanks for catching that, I have fixed it and added in the link as you suggested.

---

### Post by mc4man on 2014-12-22
> **andrew.46 said:**
> I have something similar but I took the chance to renovate the ghastly mess of the other 2 aac encoders, patch attached.
That looks ok & via your version I  notice there has been some activity in the git - thanks

---

### Post by andrew.46 on 2014-12-24
Mind you if you are adding 2.6 to a PPA just be aware there is an issue with tagging mp3s with older versions of eyeD3 which possibly should have been resolved before the release. Two posts have a fix:

[https://code.google.com/p/abcde/issues/detail?id=116](https://code.google.com/p/abcde/issues/detail?id=116)

[https://code.google.com/p/abcde/issues/detail?id=101](https://code.google.com/p/abcde/issues/detail?id=101)

The first post seems to have a well known name, could be the lead developer of Fetchmail, Leafnode 2 and others ? I relinquished my ability to contribute to abcde so I no longer have commit rights, probably just as well as the mp3 tagging issue is a little messy! (Mind you using eyeD3 0.7.5 means there are no issues).

---

### Post by mc4man on 2014-12-24
> **andrew.46 said:**
> Mind you if you are adding 2.6 to a PPA just be aware there is an issue with tagging mp3s with older versions of eyeD3 which possibly should have been resolved before the release. Two posts have a fix:

[https://code.google.com/p/abcde/issues/detail?id=116](https://code.google.com/p/abcde/issues/detail?id=116)

[https://code.google.com/p/abcde/issues/detail?id=101](https://code.google.com/p/abcde/issues/detail?id=101)

The first post seems to have a well known name, could be the lead developer of Fetchmail, Leafnode 2 and others ? I relinquished my ability to contribute to abcde so I no longer have commit rights, probably just as well as the mp3 tagging issue is a little messy! (Mind you using eyeD3 0.7.5 means there are no issues).
I'll look into forthwith, thanks.. (atm there aren't that many users of abcde via the ppa, currently 77

---

### Post by andrew.46 on 2014-12-24
Mind you in an extra bonus for my guide I have added in [the fdkaac patch]("http://www.andrews-corner.org/patches/aacfix_abcde2.6.diff") as well as the quite useful patch for [higher bitrates with faac]("http://www.andrews-corner.org/patches/A00-bitrates.patch"). I will work over the next little while to change encoding with fdkaac and NeroAacEnc to 'inline' tagging rather than use AtomicParsley for post encode tagging (which I have never warmed to). I gather inline tagging with faac would be problematic with Debian / Ubuntu license issues although I am not sure where that wrangle is currently up to :).

---

### Post by mc4man on 2014-12-24
Will have to do some mp3 encoding tests over the holiday. 
What is clear is if users want to use eyed3 0.7.x then they'll have to build it & make any needed adjustments. 
(- currently debian/ubuntu are using a 2.5 year old version of eyed3

---

### Post by andrew.46 on 2014-12-24
> **mc4man said:**
> currently debian/ubuntu are using a 2.5 year old version of eyed3

Very rare to see a current eyeD3 out there! I had trouble formally packaging the newest version so I downloaded the current source and installed with pip. pip is new to me but good to learn another tool...

---

### Post by mc4man on 2014-12-24
> **andrew.46 said:**
> Mind you in an extra bonus for my guide I have added in [the fdkaac patch]("http://www.andrews-corner.org/patches/aacfix_abcde2.6.diff") as well as the quite useful patch for [higher bitrates with faac]("http://www.andrews-corner.org/patches/A00-bitrates.patch"). I will work over the next little while to change encoding with fdkaac and NeroAacEnc to 'inline' tagging rather than use AtomicParsley for post encode tagging (which I have never warmed to). I gather inline tagging with faac would be problematic with Debian / Ubuntu license issues although I am not sure where that wrangle is currently up to :).

For amd64 users of nero it may be useful to nail down the min. i386 packages needed to run.
*Edit - libstdc++6:i386

(fdkaac is also 'problematic' for debian/ubuntu, at least to the extent that you never see it enabled in anything.. so not a concern guide-wise, ect.

---

### Post by andrew.46 on 2014-12-24
> **mc4man said:**
> fdkaac is also 'problematic' for debian/ubuntu, at least to the extent that you never see it enabled in anything.. so not a concern guide-wise, ect.

But of course it produces such great sound!

---

### Post by andrew.46 on 2014-12-25
I logged on to one of my Ubuntu vms today and I notice that out of the box (with faac and AtomicParsley installed) aac tagging is broken. I notice also on my main partition that if faac is not compiled against libmp4v2 AtomicParlsey will not tag the tracks at all. Alternative muxers are not in great supply unfortunately... life would be easier if debian / Ubuntu compiled faac with mp4 support...

**Edit: **Started [a new thread]("http://ubuntuforums.org/showthread.php?t=2258239&p=13194393") on this issue...

---

### Post by andrew.46 on 2014-12-26
> **andrew.46 said:**
> I will work over the next little while to change encoding with fdkaac and NeroAacEnc to 'inline' tagging rather than use AtomicParsley for post encode tagging (which I have never warmed to).

I am renegotiating with Steve M. to get back on the abcde team and the aac work will hopefully be my first push. I attach a patch against git that should:

[LIST=1]
[*]Allow fdkaac 'inline' tagging
[*]Allow neroAacTag to tag files produced with NeroAacEnc
[*]Do some version sniffing with faac and inline tagging: 'to tag or not to tag'.
[*]Remove AtomicParsley as is no longer needed
[*]
[/LIST]

I would love some testing with this one as it is a big change to abcde and I don't want to stuff it up :). If all goes well I will than push doc + man page changes and then look at the broken mp3 encoding issue. Even with eyeD3 0.7.5 the comment syntax is broken at the moment, needs the = sign removed as demonstrated in red:

```

			case "$ID3SYNTAX" in
				id3);;
				eyed3)
					# FIXME # track numbers in mp3 come with 1/10, so we cannot
					# happily substitute them with $TRACKNUM
					# FIXME as well! # Older versions of eyeD3 (< 0.7.0) expect
					# --set-encoding and --set-text-frame so perhaps some version
					# sniffing would be useful. Might also be better to simply cut
					# ties with the older eyeD3... Andrew.
					# eyeD3 --comment syntax is also different in < and >= 0.7.0
					run_command tagtrack-$OUTPUT-$1 nice $ENCNICE $TAGGER $TAGGEROPTS \
						**[COLOR="#FF0000"]--comment "$COMMENTOUTPUT" [/COLOR]**-A "$DALBUM" \
						-a "$TRACKARTIST" -t "$TRACKNAME" ${CDYEAR:+-Y "$CDYEAR"} \
						-G "$GENREID" -n "${TRACKNUM:-$1}" \
						${TRACKNUM:+-N "$TRACKS"} \
						${ENCODING:+--encoding="$ENCODING"} \
						${TPE2:+--text-frame=TPE2:"$TPE2"} \
						"$ABCDETEMPDIR/track$1.$OUTPUT"
					;;

```

which is an easy enough fix. So anybody who is bored over the Xmas / New Year period please test.....

---

### Post by mc4man on 2014-12-26
I'll check it out later or tomorrow,  what's the tagger for aac?

---

### Post by andrew.46 on 2014-12-26
> **mc4man said:**
> I'll check it out later or tomorrow,  what's the tagger for aac?

A choice of faac, neroAacEnc or fdkaac (set in AACENCODERSYNTAX & AACENC). Options for each of the three in AACENCOPTS.

---

### Post by mc4man on 2014-12-26
I guess what I meant is do you want to test with eyeD3? And if so what version.
(- seems very easy to install locally the 0.7.x version, though is there any expectation the 0.6.x in Debian/Ubuntu should also work?

---

### Post by andrew.46 on 2014-12-26
> **mc4man said:**
> I guess what I meant is do you want to test with eyeD3? And if so what version.
(- seems very easy to install locally the 0.7.x version, though is there any expectation the 0.6.x in Debian/Ubuntu should also work?

I am becoming a little thicker each day :). I have not addressed the mp3 tagging issue yet so that will be broken with older eyeD3. eyeD3 0.7.5 will work fine except for the problem with the COMMENT field. The only option I was looking at with that is the version switching suggested by Matthias, I was going to leave deeper issues to the developers who made the move to eyeD3...

The tagger for the aac files will be auto selected: either faac or nor none for files using faac, neroAacTag for files using neroAacEnc and fdkaac will tag its own files.

Sorry for being so obtuse and not reading closely :(

---

### Post by mc4man on 2014-12-26
gotcha, will give it a try..
(- just finished 'reacquainting' myself with abcde & seeing whether I wanted to use cdparanoia or cdda2wav, likely will use cdda2wav (real one) for 'just because' reasons more than anything else.

As far as faac - Debian/Ubuntu will never add back libmp4v2 to faac due to incompatible licenses so users will need to keep that in mind if using a faac that's not self-built.

Speaking of 'thick' or thereabouts I thought I saw you mention something about audacious & .m4a/aac, though where escapes me...? ( also for some reason I always forget what to do when there are multiple cddb results..

---

### Post by andrew.46 on 2014-12-27
> **mc4man said:**
> (- just finished 'reacquainting' myself with abcde & seeing whether I wanted to use cdparanoia or cdda2wav, likely will use cdda2wav (real one) for 'just because' reasons more than anything else.

You should come to the 'dark side' one day: both are installed in a full default installation of Slackware and the whole Debian vs Jörg Schilling debacle would become a fairy story to frighten the children :)

> As far as faac - Debian/Ubuntu will never add back libmp4v2 to faac due to incompatible licenses so users will need to keep that in mind if using a faac that's not self-built.

And faac is so low on the scale of aac sound quality it seems a pity to spend so much time sorting it all out...

> Speaking of 'thick' or thereabouts I thought I saw you mention something about audacious & .m4a/aac, though where escapes me...? ( also for some reason I always forget what to do when there are multiple cddb results..

In the middle of the patch I spent some time commenting on the eventual outcome of the 'abcde + Ubuntu + faac' situation where abcde places these files in a container labelled .mp4. (In another thread on these Forums Temujin pointed out the problem with this). Really should be in .aac but vlc and MPlayer don't mind while Audacious will not play. abcde needs a post_process function to politely mv all of the mp4s to aac.

The selection of the multiple cddb entries needs you to exit your system pager, usually with the 'q' key and then select the number of the option you are happiest with. I think that for most, more or less, 'q' is the default key :)

---

### Post by Yellow Pasque on 2014-12-27
Yes, Audacious makes assumptions based on the filename extension. It could probably be "smarter" and/or not care about the extension (which is the case for files with no extension or an unrecognized extension), but that would be slower, especially when adding a bunch of files. I use Audacious as my main player, but I'm not about to file a bug report. I have a feeling that the dev(s) would say they don't want to compromise on performance and that if you have misnamed files, that's your problem, and that Audacious makes you aware of it so you can correct it. Personally, I agree.

Note: It's not limited to aac/mp4 either. If you take an mp3 and give it a .flac extension, Audacious chokes on that too while mpv and vlc play it without complaint.

---

### Post by andrew.46 on 2014-12-27
> **Temüjin said:**
> Yes, Audacious makes assumptions based on the filename extension. 

I agree with you that this is the most correct way, although I am grateful that vlc and MPlayer are more forgiving :).

What frustrates me more than a little is the way in which decent software, and in its time faac was *the* aac encoder, is effectively neutered by packagers in the name of an ideal of 'free software'. Sigh...

---

### Post by mc4man on 2014-12-27
the current git patched fails here on inline tagging with fdkaac (error code 125
It does work with atomicparsely & also directly with fdkaac <options> <tags used in abcde> input file
(- if you have a chance to post a min. .abcde.conf that works for you & even possibly a fdkaac binary that you find works in Ubuntu.

(- I'll have another look at after deciding if I want to move to libfdk-aac1 (1.4 in current git

---

### Post by andrew.46 on 2014-12-27
In the temp folder that abcde uses there will be a file called errors which will give the failed command. Can you give that?

---

### Post by mc4man on 2014-12-27
running from the dl'ed to folder

> encodetrack-m4a-01: returned code 125: nice -n 10 --artist The Rolling Stones --album Beggars Banquet --title Sympathy For The Devil --track 01 --genre Rock & Roll --long-tag Year:1968 --comment  /home/doug/Desktop/abcde/git/abcde/abcde.8209820a/track01.wav -o /home/doug/Desktop/abcde/git/abcde/abcde.8209820a/track01.m4a

---

### Post by andrew.46 on 2014-12-27
Oops, I see the issue. Attached another diff, this is a full diff against current git...

```

# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#       m4a/aac using abcde version pre~2.6.1 
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Specify the encoder to use for m4a/aac. 
AACENCODERSYNTAX=fdkaac

# Specify the path to the selected encoder. 
AACENC=fdkaac

# Specify your required encoding options here. Multiple options can
# be selected as '--best --another-option' etc.
AACENCOPTS='--bitrate 128'

# Output type for m4a/aac.
OUTPUTTYPE="m4a"

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music"               

# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean
              
# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# What extra options?
MAXPROCS=2                                   # Run a few encoders simultaneously
PADTRACKS=y                                  # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=2                             # Useful for debugging
COMMENT='abcde version 2.6.1'             # Place a comment...
EJECTCD=y                                    # Please eject cd when finished :-)

```

---

### Post by mc4man on 2014-12-27
That's good now... (fdkaac 0.6.1, libfdk-aac 3.4.12
Am going to see now if any issues with newer  libfdk-aac

---

### Post by andrew.46 on 2014-12-27
> **mc4man said:**
> That's good now... (fdkaac 0.6.1, libfdk-aac 3.4.12

Yes, that was a clumsy transcription error on my part. See that AtomicParsley was removed?

---

### Post by mc4man on 2014-12-27
> **andrew.46 said:**
> Yes, that was a clumsy transcription error on my part. See that AtomicParsley was removed?
Yeah saw that.
OT and not important - 
For the life of me can't figure out why your patch won't apply to the 2.6 release abcde (works fine with current git
There is an offset of 3-4 lines per hunk but even after adjusting that (which really shouldn't matter) it still always fails on hunk 3

So as I said totally irrelevant, just makes me crazy I can't see the difference. There's something in the 2.6 release abcde file that causes it to fail
(- after adjusting your current diff to match a one I had quilt create that does work on 2.6-release & then running a diff on the 2 patches this is the only 'diff'
> ~/Desktop/abcde/git/test/abcde-2.6$ diff '/home/doug/Desktop/abcde/git/test/aacfix_git_again.patch' '/home/doug/Desktop/abcde/git/test/tag.patch'
57c57
< -
---
> -	
(is there something unseen on line 1200/1201 in 2.6-release?

edit: if I replace line 57 & 58 then your diff works on release source, way above my head...
```
-					
-				else
```

ex. - 
> :~/Desktop/abcde/git/test/abcde-2.6$ patch -Np1 -i ../aacfix_git_again.diff
patching file abcde
Hunk #1 succeeded at 791 (offset 3 lines).
Hunk #2 succeeded at 939 (offset 3 lines).
Hunk #4 succeeded at 3289 (offset 3 lines).
Hunk #5 succeeded at 3869 (offset 4 lines).
Hunk #6 succeeded at 3961 (offset 4 lines).
Hunk #7 succeeded at 4107 (offset 4 lines).
Hunk #8 succeeded at 4118 (offset 4 lines).

---

### Post by andrew.46 on 2014-12-27
I couldn't work it out either so I have made a fresh patch against 2.6 which should patch cleanly. This does not include all the doc / man pages changes that I will be making but I am waiting until I sort out push access with Steve M, I hesitate to disturb him too much over the holiday season :).

Patch attached....

---

### Post by mc4man on 2014-12-27
I think what it was (the issue in 2.6 & your current git master diff) revolved around what this commit fixed
[http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=blobdiff;f=abcde;h=44c08b76b0c100443a8ed6d10b7567fd80a0693b;hp=a4213012e8d0a6acc54df8b7f56fcadd87c7de32;hb=092d1e287c02857244bbd0ceb8b852d26ce87894;hpb=e4ffac817d866bc2d7c528afaf03a1eda48cd938](http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=blobdiff;f=abcde;h=44c08b76b0c100443a8ed6d10b7567fd80a0693b;hp=a4213012e8d0a6acc54df8b7f56fcadd87c7de32;hb=092d1e287c02857244bbd0ceb8b852d26ce87894;hpb=e4ffac817d866bc2d7c528afaf03a1eda48cd938)

---

### Post by andrew.46 on 2014-12-27
> **mc4man said:**
> I think what it was (the issue in 2.6 & your current git master diff) revolved around what this commit fixed
[http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=blobdiff;f=abcde;h=44c08b76b0c100443a8ed6d10b7567fd80a0693b;hp=a4213012e8d0a6acc54df8b7f56fcadd87c7de32;hb=092d1e287c02857244bbd0ceb8b852d26ce87894;hpb=e4ffac817d866bc2d7c528afaf03a1eda48cd938](http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=blobdiff;f=abcde;h=44c08b76b0c100443a8ed6d10b7567fd80a0693b;hp=a4213012e8d0a6acc54df8b7f56fcadd87c7de32;hb=092d1e287c02857244bbd0ceb8b852d26ce87894;hpb=e4ffac817d866bc2d7c528afaf03a1eda48cd938)

Hmmm... there is a patch option that may be relevant:

```

       -l  or  --ignore-whitespace
          Match patterns loosely, in case tabs or spaces have been  munged  in  your
          files.   Any  sequence of one or more blanks in the patch file matches any
          sequence in the original file, and sequences of  blanks  at  the  ends  of
          lines are ignored.  Normal characters must still match exactly.  Each line
          of the context must still match a line in the original file.

```

but as my wife is calling me to go out for lunch I dare not test it out :)

---

### Post by mc4man on 2014-12-27
It does seem the -l option would work in the case of 2.6 release & the patch on current git
(a bit of a moot point as they've been removed in git but still good to know & 'mystery' solved..

---

### Post by Yellow Pasque on 2014-12-28
> **andrew.46 said:**
> What frustrates me more than a little is the way in which decent software is effectively neutered by packagers in the name of an ideal of 'free software'. Sigh...

Imagine how frustrating it is for the people who know they have to neuter the packages because a media format meant for widespread usage is patented.
I understand why h.264 beats its competitors from a technical perspective, but IMO, there's no reason for Linux users to rip CD audio to anything other than FLAC, vorbis. or opus nowadays. If users needs to convert to a proprietary lossy format, then they should rip to FLAC and do the transcoding as an intermediate step (and maybe then they could realize that they need to be more careful when buying mobile devices and/or use Rockbox if they want to run Linux on their desktop).

---

### Post by andrew.46 on 2014-12-28
And perhaps also fdk-aac? I see some debian debate about the license here:

Debian Bug report logs - #694257
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694257](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694257)

The license itself is here:

Software License for The Fraunhofer FDK AAC Codec Library for Android
[https://android.googlesource.com/platform/external/aac/+/master/NOTICE](https://android.googlesource.com/platform/external/aac/+/master/NOTICE)

And we will have to cordially disagree here, I prefer to use the *best tools* to get the job done, not necessarily chosen because of the way a license has been written. For aac I would actually use qaac through wine (but this does not integrate with abcde) which of course is simply a clever front end for Apple Application Support. Similarly for mp3 I would use lame. But for lossless audio, as you have mentioned, there is of course flac and any speech cds I have I would use opus, both gloriously open source and both easily accessible through abcde.

My *only* personal 'rule' for Open Source is one that I have borrowed [from JED]("http://www.jedsoft.org/"), the developer of the usenet client slrn:

> 
I have no strong philosophical or religious feelings about open software; my view is purely pragmatic: Since I take from the open source community, I try to give back to it.


But soon we might have to adjourn to the Ubuntu Cafe, or even worse Recurring Discussions :)

---

### Post by mc4man on 2014-12-28
The latest git is using a new soname for shared lib, curious if anyone has noticed any issue if using the shared version.
referenced here - [https://github.com/mstorsjo/fdk-aac/commit/a0bfb7ee7c5372f846fe14a6eb7694294c35b062](https://github.com/mstorsjo/fdk-aac/commit/a0bfb7ee7c5372f846fe14a6eb7694294c35b062)

Re: abcde (patched) - are you comfortable with your current git diff?

Re: cd rips & encodes - I generally rip to flac & aac (.m4a), the .m4a's go onto my various nexus devices & an old ipod nano. 

Re: licenses/copyrights/patents  - have stopped caring about that convoluted mess except in area's where I think there may be a chance of enforcement/liability

---

### Post by andrew.46 on 2014-12-28
> **mc4man said:**
> Re: abcde (patched) - are you comfortable with your current git diff?

Well, the faac thing is a bit of a hack but this is as much as I plan on doing with it at the moment. A better plan would be to remove it completely and perhaps if the fdkaac encoder ever becomes mainstream this will be the case. With nero and fdkaac I am very happy though :).

If you plan on releasing this with one of your many ppas might be an idea to have a look at mp3 tagging with the old version of eyeD3, I have not looked closely but there appear to be problems...

> **mc4man said:**
> ]Re: cd rips & encodes - I generally rip to flac & aac (.m4a), the .m4a's go onto my various nexus devices & an old ipod nano. 

Can I ask what options you use for fdkaac? I have so far avoided vbr as it is marked 'experimental', left everything else to the reasonably sensible defaults and plucked a number out of the air for a bitrate...

---

### Post by FakeOutdoorsman on 2014-12-28
> **andrew.46 said:**
> Can I ask what options you use for fdkaac? I have so far avoided vbr as it is marked 'experimental', left everything else to the reasonably sensible defaults and plucked a number out of the air for a bitrate...

I've been using -vbr 5 for some time now. [Hydrogenaud.io fdk-aac](http://wiki.hydrogenaud.io/index.php?title=Fraunhofer_FDK_AAC#Issues) article mentions that most of the unsupported combinations have been fixed, but I've never experienced any issues.

---

### Post by mc4man on 2014-12-28
A bit 'undecided' so to speak. Definitely depends on the use case (speakers & storage concerns if any.
For ex. my ipod only gets used in a job site box so 64k is fine there (am going to experiment with some of the profiles.

For my tablets the nexus7's have some storage concerns, my galaxy pro doesn't really. In these cases may use on a half decent car stereo or upstairs with a HK bluetooth speaker. So 128k is min. though also use vbr. The android app used is also a factor..

(- from a ffmpeg side wonder about the -cutoff XXXXX option?

The gist is I currently don't have any great 'portable' sound system & ' so at some point not sure if higher br matters 

(- would love to get one of these but likely not in my cards - 
[http://en.devialet.com/phantom/](http://en.devialet.com/phantom/)

---

### Post by FakeOutdoorsman on 2014-12-28
> **mc4man said:**
> (- from a ffmpeg side wonder about the -cutoff XXXXX option?
-cutoff should be handled automatically by this library in both VBR and CBR, but I didn't actually confirm. See [bandwidth tables](http://wiki.hydrogenaud.io/index.php?title=Fraunhofer_FDK_AAC#Bandwidth).

No cutoff in -vbr 5.

> **mc4man said:**
> (- would love to get one of these but likely not in my cards - 
[http://en.devialet.com/phantom/](http://en.devialet.com/phantom/)
Is that the ball from the Dyson vacuum?

---

### Post by andrew.46 on 2014-12-29
> **mc4man said:**
> A bit 'undecided' so to speak. Definitely depends on the use case (speakers & storage concerns if any.
For ex. my ipod only gets used in a job site box so 64k is fine there (am going to experiment with some of the profiles.

After a bit of experimentation I simply used:

```

AACENCOPTS='--profile 2 --bitrate-mode 5 --afterburner 1'

```

I know --profile 2 is a default, but it is a placeholder so people can see how it is done. I put afterburner in (another default) simply because it sounds really cool :).

> The gist is I currently don't have any great 'portable' sound system & ' so at some point not sure if higher br matters 

(- would love to get one of these but likely not in my cards - 
[http://en.devialet.com/phantom/](http://en.devialet.com/phantom/)

I will not buy one of those simply because that is the slowest loading web page I seen for a very long time!

---

### Post by Yellow Pasque on 2014-12-29
> **andrew.46 said:**
> And we will have to cordially disagree here, I prefer to use the *best tools* to get the job done, not necessarily chosen because of the way a license has been written.

I feel the same way as you when it comes to my personal use of software. I run Debian sid with the debmultimedia repo, which doesn't exactly conform to dfsg or the more draconian copyright laws out there...
And yes, I too have felt the frustration of trying to help users within the Ubuntu when it would sometimes be easier if it was more like Arch Linux in its stance on licensing.

> But soon we might have to adjourn to the Ubuntu Cafe, or even worse Recurring Discussions
Yeah, I could say a lot more matter, but I don't want to distract from your mission. I will try and do some testing for you when I get some more motivation (not feeling it right now). I mainly use Audex to rip CD's, but the downside of it is the slew of KDE dependencies.

---

### Post by andrew.46 on 2014-12-29
> **mc4man said:**
> Re: abcde (patched) - are you comfortable with your current git diff?

Like a dog at a bone I cannot leave well enough alone and the faac thing was annoying me! So probably the final version is here before I go away for a few days. The sum total of this patch against the git abcde:

[LIST=1]
[*]AtomicParsley is removed as it is no longer needed for tagging.
[*]An aac $OUTPUTTYPE has been created to cater for Faac's problems. This was claimed to be already present in abcde (via the docs) but did not in fact exist!
[*]Faac encoding has been fixed as much as is possible:
[LIST]
[*]A cunning test differentiates between Faac with libmp4v2 support and Faac without
[*]Faac encoding *with* libmp4v2 support encodes to m4a with inline tagging
[*]Faac encoding *without* libmp4v2 support (creating ADTS files) still encodes to m4a but with 2 big warnings: 1. No tagging will be done 2. A better $OUTTPUTTYPE in ~/.abcde.conf would be aac.
[*]Faac *without* libmp4v2 support successfully encodes to .aac (set in ~/.abcde.conf as OUTPUTTYPE="aac") with a warning that there will be no tagging
[/LIST]
[*]neroAacEnc encoding is formalised in abcde and inline tagging with neroAacTag is created.
[*]fdkaac encoder is created in abcde with inline tagging, probably the easiest thing to do and potentially the most useful
[*]
[/LIST]

I have tested this extensively and I am almost sure that is the last effort, patch attached. Except perhaps for the documentation, and then the....

---

### Post by mc4man on 2014-12-29
Will ck. out later, thanks
(- got sidetracked checking out this 'app' *sylteditor* whose 'installer' I wouldn't wish on anybody. 
- basically caused root to own my ~/.Xauthority file which I didn't notice until a fresh start resulted in no ability to login.

Ot- -was also just reminded from this about audacious's  inability to play mpc V8 if the file has an .mpc extension. Works fine if one changes the ext. to .mp+ or really anything, could be .whocares

They semi blame ffmpeg for defining an ext for mpc V7 but not mpc V8. Personally I'm not sure, .. it's possible players that use ffmpeg successfully on mpc V8 use probed  file content to pick avformat 'type'  rather than extension
(which is what happens with aud when the ext isn't .mpc

---

### Post by andrew.46 on 2014-12-29
> **mc4man said:**
> Will ck. out later, thanks

No thank you for looking over it :). This patches against abcde 2.6 but requires *--ignore-whitespace* to fully patch as we discussed previously.

> Ot- -was also just reminded from this about audacious's  inability to play mpc V8 if the file has an .mpc extension. Works fine if one changes the ext. to .mp+ or really anything, could be .whocares

And just because this made my day I attach a screenshot showing audacious playing exactly that file :).

---

### Post by Yellow Pasque on 2014-12-30
I did some quick testing (no, it wasn't an extensive double-blind test) and I still prefer vorbis over AAC at similar bitrate (@about 224 kb/s, using oggenc -q 7 compared to using fdkaac -m5). 
Musepack SV8 seems interesting though, not to replace vorbis as a lossy format on my desktop, but to use on my old Sansa Clip that runs Rockbox. I'll have to see if SV8 gets noticeably better battery life than using vorbis.

Question about qaac: is the audio quality perceived as better or is it just better with tagging and such?

---

### Post by andrew.46 on 2014-12-30
> **Temüjin said:**
> Question about qaac: is the audio quality perceived as better or is it just better with tagging and such?

Better audio quality according to both the hydrogenaudio guys and my own testing with older ears and inferior sound equipment :)

---

### Post by mc4man on 2015-01-02
Here I went ahead & removed the extension info from libavformat, then aud works fine. Don't quite see why it's needed or a downside yet to removing
(- ffmpeg/libavformat/mpc.c  ln. #235, removed entirely

---

### Post by Yellow Pasque on 2015-01-02
> **mc4man said:**
> Don't quite see why it's needed or a downside yet to removing

My theory is that when adding files to a playlist, it's faster to look at the extension than attempt to figure out what kind of file it is based on the metadata. So when you're loading a lot of files to a playlist, using the extension is significantly faster. I could be way off though...

However, even if my theory's true, I wouldn't go that route with musepack, because of the ambiguity in the extension. The only people who would get a benefit from assuming .mpc implies an SV7 file are those folks with a lot of SV7 files in their library (and no SV8 files with a .mpc extension).

Reference bug: [http://redmine.audacious-media-player.org/issues/459](http://redmine.audacious-media-player.org/issues/459)

---

### Post by mc4man on 2015-01-02
> **Temüjin said:**
> My theory is that when adding files to a playlist, it's faster to look at the extension than attempt to figure out what kind of file it is based on the metadata. So when you're loading a lot of files to a playlist, using the extension is significantly faster. I could be way off though...

However, even if my theory's true, I wouldn't go that route with musepack, because of the ambiguity in the extension. The only people who would get a benefit from assuming .mpc implies an SV7 file are those folks with a lot of SV7 files in their library (and no SV8 files with a .mpc extension).

Reference bug: [http://redmine.audacious-media-player.org/issues/459](http://redmine.audacious-media-player.org/issues/459)
I guess then aud can fashion a fix if they're inclined..

The only players I can compare to that use avformat/codec for mpc are mpv & mplayer. It seems both just probe file content at  'play' time (per individual file)  to determine proper lavc decoder. So basically that's what aud will do if there is not a 'known to it' ext. or if the ext. info is removed from ffmpeg/libav. 
In that case it may be a ms or so difference per track.

---

### Post by andrew.46 on 2015-01-08
I altered my approach a little for faac and managed to get faac without libmp4v2 to output only aac. Final log at abcde is:

```

aac encoding renovations:

  * Faac encoding with & without libmp4v2 rectified
  * neroAacEnc 'formally' added to abcde, tagging with neoAacTag
  * FDK AAC encoding introduced using fdkaac, inline tagging used
  * AtomicParsley temporarily removed as not currently needed

Thanks to Doug Mcmahon for assistance with the above changes...

```

And all the details [here...]("http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=commit;h=7d70d0d1ed8496c6b3dcc242b13780ce0033b77b") Feel free to test and find any errors :)

---

### Post by Yellow Pasque on 2015-01-08
I tested it out with latest git, using your sample config and fdkaac for the aac encoder. I'm impressed enough that I'll probably use abcde instead of Audex the next time I need to rip.

- Do you or other abcde contributors plan to use ~/.config/ directory for XDG compliance?
- In your guide, you refer to mp**p**enc --longhelp, which I'm guessing you want to update to mp**c**enc since you've moved on to using SV8.

---

### Post by andrew.46 on 2015-01-09
> **Temüjin said:**
> I tested it out with latest git, using your sample config and fdkaac for the aac encoder. I'm impressed enough that I'll probably use abcde instead of Audex the next time I need to rip.

Good to hear that is is working well for you :). Actually I have you to thank for showing me the error of packing an ADTS stream into m4a, it took me a bit of thinking to come up with the eventual solution in abcde but it certainly works well here...

> **Temüjin said:**
> - Do you or other abcde contributors plan to use ~/.config/ directory for XDG compliance?

There are a couple of patches floating around on the [abcde issues page]("https://code.google.com/p/abcde/issues/list") but I confess it is not an area that has grabbed my attention. And I am not sure about the others (and there appears to only be myself, Steve and Ville at the moment...). Focus at the moment for me is fixing up the mp3 tagging issues, making sure WavPack is set properly and tidying up SV8 a little.

> **Temüjin said:**
> - In your guide, you refer to mp**p**enc --longhelp, which I'm guessing you want to update to mp**c**enc since you've moved on to using SV8.

You would be guessing right and I have corrected this in several places on the page, thanks for your sharp eyes :).

---

### Post by Yellow Pasque on 2015-01-09
Yeah, faac could be a bit smarter and refuse to write to files with m4a/mp4 (or give a more detailed warning) if it wasn't built with libmp4 support. That might be expecting a bit too much though, and then you probably get into a discussion about the meaning (or lack thereof) of filename extensions in UNIX-style OS's.

> Focus at the moment for me is fixing up the mp3 tagging issues, making sure WavPack is set properly and tidying up SV8 a little.
Sounds good. The ~/.config usage is a minor thing compared to those features. It's a shame Debian/Ubuntu is still stuck on eyed3 0.6.x [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=740457](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=740457)

---

### Post by andrew.46 on 2015-01-09
> **Temüjin said:**
> Sounds good. The ~/.config usage is a minor thing compared to those features. It's a shame Debian/Ubuntu is still stuck on eyed3 0.6.x [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=740457](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=740457)

The latest git abcde now has the ability to switch between old and new versions of eyeD3 and coming over the next week will be a more formalised manner of selecting mp3 tagging: id3v1, id3v2.3 or id3v2.4. These 2 commits should hopefully see an end to the current problems with mp3 tagging and might worth cherrypicking by distros having some issues with release version 2.6...

---

### Post by andrew.46 on 2015-01-10
> **andrew.46 said:**
> [..] coming over the next week will be a more formalised manner of selecting mp3 tagging: id3v1, id3v2.3 or id3v2.4. These 2 commits should hopefully see an end to the current problems with mp3 tagging and might worth cherrypicking by distros having some issues with release version 2.6...

In place now, from the commit log:

```

mp3 tagging: giving some more options

This update allows 3 different ways to tag mp3 files
using ID3TAGV:

  * id3v2.4 using eyeD3 (set in abcde as the default)
  * id3v2.3 using id3v2
  * id3v1 using id3

Thanks to Adriaan for this patch which fixes issue 101.

```

Hopefully this puts to rest a lot of mp3 tagging issues...

---

### Post by emk on 2015-01-25
Glad to read that it was not my fault that I couldn't use abcde to rip to aac - this should be mentioned in bold on the abcde wiki page in Ubuntu. I am fighting with it now for half a day. After the switch to flac, it was a matter of minutes. ](*,)

Now for the user who doesn't care about license issues, is ok with an occasional compile from github or elsewhere - what would be the recommended path of action?

Download abcde from git - OK, but it is a custom git version, not github. Which URI would I use? Any changes?
Installing the best codecs, maybe with patches - which ones should I use?

Or would it be better to stick with flac and convert everything else afterwards with ffmpeg? This way, the fdk-aac encoder could be used without too much hassle. Would this keep the tagging of the files intact? According to [this stackexchange answer]("http://unix.stackexchange.com/questions/77687/how-do-i-convert-flac-files-to-aac-preferrably-vbr-320k"), it should work. So a simple loop with ffmpeg in bash should be enough.

---

### Post by andrew.46 on 2015-01-25
Hi emk! If you download from the current git:

```
git clone http://git.einval.com/git/abcde.git
```

you will have a copy of abcde that will quite easily encode with either neroAacEnc or fdkaac. As you have found aac encoding with abcde is broken under ubuntu at the moment, there is a general explanation of the issue in the abcde [faqs]("http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=blobdiff;f=FAQ;h=e46ddc4a983825dabb76f23c1c444e495339a182;hp=e20b48789538f74ff974bbb79f02dc1e64ba4588;hb=7b07f87a896faffaf0dc928a93ae9064e3e83452;hpb=6481772b8515378a951535c19c68955b950e75a3"). (With an explanation of how current git behaves with the broken faac...).

mc4man has a PPA somewhere with a copy of fdkaac if you don't want to build your own...

---

### Post by emk on 2015-01-25
Thanks for the quick answer! I'll try the git later, for the moment, I used the workaround of encoding to flac with abcde and afterwards a quick

```
for i in *flac;do of="${i/.flac/.m4a}"; ffmpeg -i "${i}" -c:a libfdk_aac -vbr 3 -afterburner 1 -f mp4 -y "${of}";done

``` in the resulting directory.
Had do compile ffmpeg first, but this is easy since everything is on one page and the instructions are quite foolproof. Also, for ffmpeg in the current ubuntu vivid, only libvpx and fdk-aac are needed, everything else is available via a dev lib.

One thing I thought about: Would it make sense to get rid of all the other codecs and have abcde just rely on ffmpeg, since it is the swiss army knife anyway?

---

### Post by andrew.46 on 2015-01-25
> **emk said:**
> One thing I thought about: Would it make sense to get rid of all the other codecs and have abcde just rely on ffmpeg, since it is the swiss army knife anyway?

It could be done although some major difficulties would be:

[LIST=1]
[*]FFmpeg is a rapidly moving target in its development and options
[*]There are so many different versions of FFmpeg in the wild with a myriad of different compile options
[*]
[/LIST]

but certainly it could be done. It is a little against the spirit of abcde however which uses a fairly carefully selected groups of applications for each specific purpose. For instance with mp3 you could use:

[LIST=1]
[*]cdparanoia or cdda2wav for cd ripping
[*]a custom (abcde) perl script for musicbrainz query
[*]lame for encoding
[*]eyeD3 for tagging
[*]movement of the resulting files to the directory structure of your choice
[*]
[/LIST]

and each of these steps can have options of your choice added in. Bearing in mind that you can also automate the process to encode to aac, mp3, flac, ogg vorbis and wavpack *at the same time*, adding in your own selected options for each process. So FFmpeg, while a great tool, does not really fit in there. Nevertheless have a look at the script itself and see if you can see a method of adding it in, even if only for your own personal use...

---

### Post by mc4man on 2015-01-25
I see you got commits going again, good deal, thanks

---

### Post by andrew.46 on 2015-01-25
> **mc4man said:**
> I see you got commits going again, good deal, thanks

Indeed, I have used some of my own work but mostly the work of others to hopefully rectify the mp3 tagging / eyeD3 version issues, clarify and enhance aac tagging, add in wavpack encoding and add a few other small fixes. I have spoken to Steve M about releasing abcde 2.6.1 and he will hopefully get this going shortly :).

I am still coming to grips with abcde itself, not surprising when you think that is a 4,000 line shell script that has been developed by multiple authors since 1999!

---

### Post by emk on 2015-01-25
andrew.46, maybe you can help me with a problem I ran into - the second CD I tried to rip threw an error:
```
(== PROGRESS == [ !- !- V!!!! VV !!!!++>       | 076980 00 ] == :-)   ==)   /usr/bin/abcde: Zeile 3043:  6097 Speicherzugriffsfehler  (Speicherabzug geschrieben) nice $READNICE $CDROMREADER -$CDPARANOIACDROMBUS "$CDROM" ${READTRACKNUMS:-$UTRACKNUM} "$FILEARG"
[ERROR] abcde: The following commands failed to run:
readtrack-07: cdparanoia  returned code 139
Finished. Not cleaning /home/erik/abcde.d20bc910.

```I am clueless what to do. For what it's worth, the git version is now installed. The error is reproducible, also after a restart. Why does the segfault happen? It's clear that cdparanoia is the culprit. I checked the standalone cdparanoia - same problem. But this is the latest version, with no improvements in sight.

---

### Post by andrew.46 on 2015-01-25
Looks like a lot of read errors in the cdparanoia output:

```

**[COLOR="#FF0000"]+ [/COLOR]**  Unreported loss of streaming/other error in read
**[COLOR="#FF0000"]![/COLOR]**   Errors  found  after stage 1 correction; the drive is making the
    same error through multiple re-reads, and cdparanoia  is	having
    trouble detecting them.
**[COLOR="#FF0000"]V[/COLOR]**   Uncorrected error/skip

```

Is the cd itself in good condition? 

An alternative would be to use cdda2wav which has considerably more modern development (and can be set to use the 'paranoia' features of cdparanoia as well), also consider using:

```

EXTRAVERBOSE=2 

```

in your ~/.abcde.conf file to see any more hints. Have a look in the abcde temp file for the file marked 'errors' for logged errors...

---

### Post by mc4man on 2015-01-25
Gave the latest a try - 
At first yet again encode issues but have resolved & inline tagging with fdkaac is good.
Seems my .abcde.conf was using a profile for fdkaac (-p # option), switched to more direct parameters & all is ok. Could of sworn the -p # worked before..

---

### Post by andrew.46 on 2015-01-25
Was the profile error an fdkaac problem or an abcde problem? I am at work at the moment but I have memories of successfully using a profile option for fdkaac from within abcde before... Cannot test this on this horrible Windows XP desktop :(.

---

### Post by mc4man on 2015-01-25
False alarm, likely my error somewhere, working now with -p option
(will retest, maybe because I didn't have a -b also??
So for example  this now  works - 
-p 29 -b 64

---

### Post by andrew.46 on 2015-01-26
> **mc4man said:**
> False alarm, likely my error somewhere, working now with -p option
(will retest, maybe because I didn't have a -b also??
So for example  this now  works - 
-p 29 -b 64

Hopefully this was the case, I did not really want to dig through abcde looking for a mistake that I could only blame on myself :)

```

andrew@ilium~/media/luckynight/test$ **[COLOR="#FF0000"]fdkaac --profile 2 luckynight.wav [/COLOR]**
bitrate or bitrate-mode is mandatory

```

Was there supposed to be a new release of the library sometime soon?

---

### Post by mc4man on 2015-01-26
> **andrew.46 said:**
> 

Was there supposed to be a new release of the library sometime soon?
If you mean fdk-aac then they went to 0.1.4, the soname to libfdk-aac.so.[COLOR="#0000CD"]1[/COLOR]

---

### Post by andrew.46 on 2015-01-26
> **mc4man said:**
> If you mean fdk-aac then they went to 0.1.4, the soname to libfdk-aac.so.[COLOR="#0000CD"]1[/COLOR]

Hmmm... looks like [the new maintainer]("http://slackbuilds.org/repository/14.1/libraries/libfdk-aac/") of libfdk-aac has fallen down on the job, I can only see 0.1.3:

[https://github.com/mstorsjo/fdk-aac/releases](https://github.com/mstorsjo/fdk-aac/releases)

although I can see the change in [configure.ac]("https://github.com/mstorsjo/fdk-aac/commit/06ee7ef4e7d3486aa7c96a7ee10d3096d6f2e603"). Is their no 'official' tarball?

---

### Post by mc4man on 2015-01-26
Yeah - the current release is 1.3. May be better to stick with for awhile though haven't seen any [issues yet]("https://github.com/mstorsjo/fdk-aac/commit/a0bfb7ee7c5372f846fe14a6eb7694294c35b062") with 1.4 & the limited uses of here.

(- don't know about Slack - in Debian/Ubuntu the .so's can co-exist but there is only 1 dev package available at a time

---

### Post by emk on 2015-01-26
> **andrew.46 said:**
> An alternative would be to use cdda2wav which has considerably more modern development (and can be set to use the 'paranoia' features of cdparanoia as well), also consider using:

```

EXTRAVERBOSE=2 

```

in your ~/.abcde.conf file to see any more hints. Have a look in the abcde temp file for the file marked 'errors' for logged errors...

After switching from cdparanoia to cdda2wav, everything was smooth. I forgot that cdda2wav is by Jörg Schilling, or i would have used it right away. His whole cdrtools suite is exceptional. With the help of fdkaac, direct rips to aac also work. I am still a little suspicious because cdda2wav reads way faster and doesn't stop at all, even at the problematic track. I gave the options ```

-paranoia -paraopts=proof

```, but the result seems OK. Thanks for getting me back on track!

---

### Post by andrew.46 on 2015-01-26
> **emk said:**
>  With the help of fdkaac, direct rips to aac also work.

Good to hear that all is well, I will also be switching to cdda2wav in my personal setup after many years of using cdparanoia. There is also a *-max* setting that I was going to try, not sure is this would make any difference...

And the fdkaac encoding gave no trouble? I am hoping that this will be a big drawcard for abcde 2.6.1 although I know that fdkaac has not been packaged by a lot of distros yet.

---

### Post by mc4man on 2015-01-26
> **emk said:**
> I am still a little suspicious because cdda2wav reads way faster and doesn't stop at all, even at the problematic track. I gave the options ```

-paranoia -paraopts=proof

```, but the result seems OK. Thanks for getting me back on track!
That does seem 'odd', particularly with -paraopts=proof option. I've always used cdda2wav (real) in abcde & have found it to be a bit slower that cdparanoia  in general & noticeably slower with the proof option.
Are you using the real cdda2wav?, not the icedax Debian replacement..

---

### Post by emk on 2015-01-27
PEBKAC. I edited the options in the cdparanoia options line, not in the one below for cdda2wav. Now I can get cdda2wav to acknowledge the options. There are still issues remaining: with -paraopts=proof, I get into an endless reading loop with I/O errors, if I skip them and just use -paranoia, the disks get read, but always with an output like this:
```
recording 216.6133 seconds stereo with 16 bits @ 44100.0 Hz ->'/media/persistent/Hitachi300G/Temp/abcde.2b12e416/track03'...
using lib paranoia for reading.
percent_done:
 27%Tagging track 02 of 22: Moves Like Jagger...
100%  **track  3** 'We Found Love' **recorded with audible hard errors**
100%  **0 rderr, 0 skip, 0 atom, 0 edge, 0 drop, 0 dup, 0 drift**
100%  690 reads(211,7%) 77 overlap(0,5 .. 0,5)
```
I bolded the important parts. Seems like the whole rip doesn't even try to do some corrections, all statistics are 0. Always reported with audible hard errors. It makes no difference if I use another drive. One is a BD drive via USB, the other a DVD-rewriter via SATA, so it shouldn't be hardware-related.

If I replace the -paraopts=proof option with -paraopts=minoverlap=20,retries=200,readahead=600, *which is the same except for the omitted c2check,* the I/O errors are gone, and I get basically the same result, maybe slower. What gives?

---

### Post by mc4man on 2015-01-27
> **emk said:**
> 
 Always reported with audible hard errors. It makes no difference if I use another drive.  What gives?
That I can't say, seems to appear with the newer cdda2wav (3.01a26 tested here) but not with the stable release (3.00

Didn't try your parameters as I've no need for readahead here, my drive does not cache. But did do 2 rips with cdda2wav directly of the same track, same options, one with 3.01, one with 3.00. The 2 wav files are identical (md5 match, both sound the same, no errors, whatever.

The source is hosted on sourceforge which doesn't have any issue tracker, I guess if you wanted to pursue maybe try one of the cdrecord mailing lists & then don't hold your breath. 

The message is produced from this bit in cdda2wav.c, seems innocuous, myself would just ignore.
```
if (para_stat->readerrs || para_stat->c2badsecs) {
					fprintf(outfp,
						_(" with audible hard errors"));
```

---

### Post by andrew.46 on 2015-03-14
OK so a few more reasonably important updates to git including:

[LIST]
[*]a fix to allow cleaning after using wav as $OUTPUTFORMAT
[*]a fix to allow proper writing of $COMMENT when using multiple $OUTPUTFORMAT fields
[*]
[/LIST]

My own personal ~/.abcde.conf has always been a little different from my published offerings, although this will change with the upcoming release of 2.6.1. Here is my current day-to-day configuration which is based on the current git:

```

# -----------------$HOME/.abcde.conf----------------------- #
#                                                           #
# Andrew's personal ~/.abcde.conf file which converts       # 
# music cds to MP3, Ogg Vorbis, FLAC, Musepack, AAC,        #
# Opus, Wav & WavPack using abcde version 2.6.1-UNRELEASED  #
#                                                           #
#         http://andrews-corner.org/abcde.html              #
# --------------------------------------------------------- #

# Encode tracks immediately after reading. Saves disk space, gives
# better reading of 'scratchy' disks and better troubleshooting of
# encoding process but slows the operation of abcde quite a bit:
LOWDISK=y

# Specify the method to use to retrieve the track information,
# I give the default below but consider setting 'musicbrainz'
# instead, which is my own preferred option:
CDDBMETHOD=cddb

# Make a local cache of cddb entries and then volunteer to use 
# these entries when and if they match the cd:
CDDBCOPYLOCAL="y"
CDDBLOCALDIR="$HOME/.cddb"
CDDBLOCALRECURSIVE="y"
CDDBUSELOCAL="y"

OGGENCODERSYNTAX=oggenc                       # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                         # Specify encoder for MP3
FLACENCODERSYNTAX=flac                        # Specify encoder for FLAC
MPCENCODERSYNTAX=mpcenc                       # Specify encoder for Musepack
AACENCODERSYNTAX=fdkaac                       # Specify encoder for AAC
OPUSENCODERSYNTZX=opusenc                     # Specify encoder for Opus
WVENCODERSYNTAX=wavpack                       # Specify encoder for WavPack

OGGENC=oggenc                                 # Path to Ogg Vorbis encoder
LAME=lame                                     # Path to MP3 encoder
FLAC=flac                                     # Path to FLAC encoder
MPCENC=mpcenc                                 # Path to Musepack encoder
AACENC=fdkaac                                 # Path to AAC encoder
OPUSENC=opusenc                               # Path to Opus encoder
WVENC=wavpack                                 # Path to WavPack encoder

OGGENCOPTS='-q 6'                             # Options for Ogg Vorbis
LAMEOPTS='-V 2'                               # Options for MP3 
FLACOPTS='-s -e -V -8'                        # Options for FLAC
MPCENCOPTS='--extreme'                        # Options for Musepack
AACENCOPTS='-p 2 -m 5 -a 1'                   # Options for AAC
OPUSENCOPTS="--vbr --bitrate 128"             # Options for Opus
WVENCOPTS='-hx3'                              # Options for WavPack
 
OUTPUTTYPE="ogg,mp3,flac,mpc,m4a,opus,wav,wv" # Encode to 8 formats!

CDROMREADERSYNTAX=cdparanoia            
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
OUTPUTDIR="$HOME/Music"               
ACTIONS=cddb,playlist,read,encode,tag,move,clean
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

MAXPROCS=2                                    # Run a few encoders simultaneously
PADTRACKS=y                                   # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=2                                # Useful for debugging
COMMENT='abcde 2.6.1-UNRELEASED'              # Place a comment...
EJECTCD=y                                     # Please eject cd when finished :-)
EJECT=udisks                                  # 'eject' is broken in Slackware 14.1..
EJECTOPTS='--eject /dev/dvd'                  # Required udisks options.

```

Can I say I *love* working on abcde? It is a gloriously huge and messy script that does almost everything I want in a cd ripper :).

I attach a screenshot showing the latest 8 format encoding in place...

---

### Post by andrew.46 on 2015-03-19
And now with the addition of Monkey;s AUdio (ape):

```

# -----------------$HOME/.abcde.conf----------------------- #
#                                                           #
# Andrew's personal ~/.abcde.conf file which converts       # 
# music cds to MP3, Ogg Vorbis, FLAC, Musepack, AAC,        #
#    Opus, Wav, Monkey's Audio & WavPack using              #  
#         abcde version 2.6.1-UNRELEASED                    #
#                                                           #
#         http://andrews-corner.org/abcde.html              #
# --------------------------------------------------------- #

# Encode tracks immediately after reading. Saves disk space, gives
# better reading of 'scratchy' disks and better troubleshooting of
# encoding process but slows the operation of abcde quite a bit:
LOWDISK=y

# Specify the method to use to retrieve the track information,
# I give the default below but consider setting 'musicbrainz'
# instead, which is my own preferred option:
CDDBMETHOD=cddb

# Make a local cache of cddb entries and then volunteer to use 
# these entries when and if they match the cd:
CDDBCOPYLOCAL="y"
CDDBLOCALDIR="$HOME/.cddb"
CDDBLOCALRECURSIVE="y"
CDDBUSELOCAL="y"

OGGENCODERSYNTAX=oggenc                           # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                             # Specify encoder for MP3
FLACENCODERSYNTAX=flac                            # Specify encoder for FLAC
MPCENCODERSYNTAX=mpcenc                           # Specify encoder for Musepack
AACENCODERSYNTAX=fdkaac                           # Specify encoder for AAC
OPUSENCODERSYNTZX=opusenc                         # Specify encoder for Opus
WVENCODERSYNTAX=wavpack                           # Specify encoder for WavPack
APENCODERSYNTAX=mac                               # Specify encoder for Monkey's Audio

OGGENC=oggenc                                     # Path to Ogg Vorbis encoder
LAME=lame                                         # Path to MP3 encoder
FLAC=flac                                         # Path to FLAC encoder
MPCENC=mpcenc                                     # Path to Musepack encoder
AACENC=fdkaac                                     # Path to AAC encoder
OPUSENC=opusenc                                   # Path to Opus encoder
WVENC=wavpack                                     # Path to WavPack encoder
APENC=mac                                         # Path to Monkey's Audio encoder

OGGENCOPTS='-q 6'                                 # Options for Ogg Vorbis
LAMEOPTS='-V 2'                                   # Options for MP3 
FLACOPTS='-s -e -V -8'                            # Options for FLAC
MPCENCOPTS='--extreme'                            # Options for Musepack
AACENCOPTS='-p 2 -m 5 -a 1'                       # Options for AAC
OPUSENCOPTS="--vbr --bitrate 128"                 # Options for Opus
WVENCOPTS='-hx3'                                  # Options for WavPack
APENCOPTS='-c4000'                                # Options for Monkey's Audio
 
OUTPUTTYPE="ogg,mp3,flac,mpc,m4a,opus,wav,wv,ape" # Encode to 9 formats!

CDROMREADERSYNTAX=cdparanoia            
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
OUTPUTDIR="$HOME/Music"               
ACTIONS=cddb,playlist,read,encode,tag,move,clean
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

MAXPROCS=2                                    # Run a few encoders simultaneously
PADTRACKS=y                                   # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=2                                # Useful for debugging
COMMENT='abcde 2.6.1-UNRELEASED'              # Place a comment...
EJECTCD=y                                     # Please eject cd when finished :-)
EJECT=udisks                                  # 'eject' is broken in Slackware 14.1..
EJECTOPTS='--eject /dev/dvd'                  # Required udisks options.

```

---

### Post by shantiq on 2015-03-21
ok guys question for you

First Thanx to Andrew for new ape functionality


but my question is with fdkaac installed on my system

modified the .abcde.conf        file in my home folder  >>>   3 modifications as you will see below  [probably where the problem is?]

installed abcde to /usr/bin/   from latest version folder with ape   with command ```
sudo make install
```


and still I get pesky faac when i fire it up:      so what have not seen?        thanx

```
shantiq@shantiq-00000000000000000000000: abcde  -d /dev/sr1 -o aac   05
Grabbing tracks: 05
Retrieving 1 CDDB match...done.
---- Elissa / Baddy Doub ----
1: Baddy Doub
2: Dalolak
3: Hilm Al Ahlam
4: Waynak Habibi
5: Elissa
6: Chou Ma Sar
7: Zaalan
8: Ghali
9: Da Lolak (Original Mix)
10: Hilm Al Ahlam (French Mix)

Edit selected CDDB data [y/N]? n
Is the CD multi-artist [y/N]? n
Grabbing track 05: Elissa...
cdparanoia III release 10.2 (September 11, 2008)

Ripping from sector   79972 (track  5 [0:00.00])
      to sector  101139 (track  5 [4:42.17])

outputting to /home/shantiq/abcde.7409f50a/track05.wav

 (== PROGRESS == [                              | 101139 00 ] == :^D * ==)   

Done.


Encoding track 05 of 10: Elissa...
Freeware Advanced Audio Coder
FAAC 1.28

Quantization quality: 100
Bandwidth: 16000 Hz
Object type: Low Complexity(MPEG-2) + M/S




```




```
# System defaults for abcde version 2.2.x
# Nothing in this file is uncommented by default.
#
# If you wish to override these system-wide settings, create your own
# .abcde.conf file in your home directory.

# CDDB options
# Choose whether you want to use CDDB or Musicbrainz. Default is CDDB
#CDDBMETHOD=cddb

# If you wish to use a different CDDB server, edit this line.
# If you just wanted to use a proxy server, just set your http_proxy
# environment variable - wget will use it correctly.
#CDDBURL="http://freedb.freedb.org/~cddb/cddb.cgi"

# The CDDB protocol level.
# Right now 5 is latin1 output and 6 is UTF8 encoding.
#CDDBPROTO=6

# The CDDB protocol requires hello information, including a valid username
# and hostname. If you feel paranoid about giving away such info, edit this
# line - the format is username@hostname.
#HELLOINFO="`whoami`@`hostname`"

# This controls the email address CDDB changes are submitted to.
#CDDBSUBMIT=freedb-submit@freedb.org

# The following options control whether or not fetched CDDB entries
# are cached locally in $CDDBLOCALDIR
#CDDBCOPYLOCAL="n"
#CDDBLOCALDIR="$HOME/.cddb"
#CDDBLOCALRECURSIVE="y"

# If NOSUBMIT is set to y, then abcde will never prompt asking if you
# wish to submit your edited cddb file.
#NOSUBMIT=n

# If NOCDDBQUERY is set to y, then abcde will never even try to access
# the CDDB server; running abcde will automatically drop you into a
# blank cddb file to edit at your leisure.  This is the same as the
# -n option.  NOCDDBQUERY=y implies NOSUBMIT=y.
#NOCDDBQUERY=n

# Select here if you want to use the locally stored CDDB entries.
# This is useful if you do a lot of editing to those CDDB entries.
# Also, other tools like Grip store CDDB entries under $HOME/.cddb,
# so they can be reused when ripping CDs. (If this is set to "y" make
# sure that CDDBLOCALRECURSIVE is also set to "y".)
#CDDBUSELOCAL="n"

# List, separated with a comma, the fields we want the parsing function to
# output. Defaults to YEAR and GENRE, for a complete list of fields provided by
# CDDB.
# The fields are not case sensitive. Actually, "y,g" will work as fine as "Y,G"
# or "YEAR, GENRE"
#SHOWCDDBFIELDS=year,genre

# Specify the style of encoder to use here -
# oggenc, vorbize - for OGGENCODERSYNTAX
# lame, gogo, bladeenc, l3enc, xingmp3enc, mp3enc - for MP3ENCODERSYNTAX
# flac - the only supported for FLACENCODERSYNTAX at the moment
# speexenc - the only encoder for SPEEXENCODERSYNTAX
# mpcenc - encoder for MPCENCODERSYNTAX
# wavpack - encoder for WVENCODER
# mac - for APENCODER
# faac, neroAacEnc, fdkaac - for AACENCODER
# opusenc - for OPUSENCODER
# default is a valid option for oggenc, lame, flac, speexenc, mpcenc, wavpack, faac and opus.
# Currently this affects the default location of the binary, the variable
# to pick encoder command-line options from, and where the options are
# given.
#MP3ENCODERSYNTAX=default
#OGGENCODERSYNTAX=default
#FLACENCODERSYNTAX=default
#SPEEXENCODERSYNTAX=default
#MPCENCODERSYNTAX=default
#WVENCODERSYNTAX=default
#APENCODERSYNTAX=default
[COLOR=#800000]**#AAENCODERSYNTAX=fdkaac**[/COLOR]
#OPUSENCODERSYNTAX=default

# Specify the syntax of the normalize binary here - so far only 'normalize'
# is supported.
#NORMALIZERSYNTAX=default

# CD reader program to use - currently recognized options are 'cdparanoia',
# 'icedax', 'cdda2wav', 'dagrab', 'pird', 'cddafs' (Mac OS X only) and 'flac'.
#CDROMREADERSYNTAX=cdparanoia

# CUE reader syntax for the CUE reader program to use.
# abcde supports 2 CUE modes: 'mkcue' and 'abcde.mkcue' so you can set the
# MKCUE variable accordingly. The 'abcde.mkcue' uses an internal
# implementation, without the need of an external program.
#CUEREADERSYNTAX=default

# Specify the program to convert a CUE sheet back to a CD disc ID for CDDB queries.
# Select between '/path/to/cue2discid' (provided as an example) or
# 'abcde.cue2discid', implemented internaly.
#CUE2DISCID=abcde.cue2discid

# Keep the wav files after encoding. Set it to "y" and remove "clean" from
# the list of default actions, since we purge the temp directory as default.
#KEEPWAVS=n

# Track padding: force abcde to pad tracks using 0, so every song uses a two
# digit entry. If set to "y", even a single song encoding outputs a file like
# 01.my_song.ext
#PADTRACKS=n

# Define if you want abcde to be non-interactive.
# Keep in mind that there is no way to deactivate it right now in the command
# line, so setting this option makes abcde to be always non-interactive.
#INTERACTIVE=n

# Specify 'nice'ness of the encoder, the CD reader and the distmp3 proc.
# This is a relative 'nice'ness (that is, if the parent process is at a
# nice level of 12, and the ENCNICE is set to 3, then the encoder will
# run with an absolute nice value of 15. Note also, that setting these
# to be empty will result in some default niceness increase (4 in tcsh
# and 10 using the bsdutils' nice).
#ENCNICE=10
#READNICE=10
#DISTMP3NICE=10

# Paths of programs to use
#LAME=lame
#TOOLAME=toolame
#GOGO=gogo
#BLADEENC=bladeenc
#L3ENC=l3enc
#XINGMP3ENC=xingmp3enc
#MP3ENC=mp3enc
#VORBIZE=vorbize
#OGGENC=oggenc
#FLAC=flac
#SPEEXENC=speexenc
#MPCENC=mpcenc
#WVENC=wavpack
#APENC=mac
[COLOR=#800000]**#AACENC=fdkaac**[/COLOR]
#OPUSENC=opusenc

#ID3=id3
#ID3V2=id3v2
#EYED3=eyeD3
#CDPARANOIA=cdparanoia
#CDDA2WAV=icedax
#PIRD=pird
#CDDAFS=cp
#CDDISCID=cd-discid
#CDDBTOOL=cddb-tool
#EJECT=eject
#MD5SUM=md5sum
#DISTMP3=distmp3
#VORBISCOMMENT=vorbiscomment
#METAFLAC=metaflac
#NORMALIZE=normalize-audio
#CDSPEED=eject
#VORBISGAIN=vorbisgain
#MKCUE=mkcue
#MKTOC=cdrdao
#DIFF=diff

# Options to call programs with:

# If HTTPGET is modified, the HTTPGETOPTS options should also be defined
# accordingly. If HTTPGET is changed, the default options will be set,
# if HTTPGETOPTS is empty or not defined.
#HTTPGET=wget
# for fetch (FreeBSD): HTTPGETOPTS="-q -o -"
# for wget: HTTPGETOPTS="-q -nv -O -"
# for curl (MacOSX): HTTPGETOPTS="-f -s"
#HTTPGETOPTS="-q -O -"

# MP3:
# For the best LAME encoder options have a look at:
# <http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_encoder_settings>
# A good option is '-V 0' which gives Variable Bitrate Rate (VBR) recording
# with a target bitrate of ~245 Kbps and a bitrate range of 220...260 Kbps.
#LAMEOPTS=
#TOOLAMEOPTS=
#GOGOOPTS=
#BLADEENCOPTS=
#L3ENCOPTS=
#XINGMP3ENCOPTS=
#MP3ENCOPTS=

# Ogg:
#VORBIZEOPTS=
#OGGENCOPTS=

# FLAC:
# The flac option is a workaround for an error where flac fails
# to encode with error 'floating point exception'. This is flac 
# error in get_console_width(), corrected in flac 1.3.1
#FLACOPTS="--silent"

# Speex:
#SPEEXENCOPTS=

# MPP/MP+ (Musepack):
# For the encoder options look at 'mpcenc --longhelp', consider
# setting '--extreme' for a good quality encode.
#MPCENCOPTS=

# WavPack:
# Look at 'wavpack --help' for detailed options, consider using '-hx3' 
# for a good quality encode
#WVENCOPTS=

# Monkey's Audio (ape)
# Without this set mac chokes unfortunately. Choices
# are from 1000 to 5000.
#APENCOPTS='-c5000'
#APETAG=apetag

# M4A/AAC
# For faac options see 'faac --long-help' and consider
# using '-q 250' for a good quality encode.
# For neroAacEnc options see 'neroAacEnc -help' and
# consider using '-q 0.65' for a good quality encode.
# For fdkaac options see 'fdkaac --help' and consider using 
# '-profile:a aac_he_v2 -signaling explicit_sbr -b:a 38k -afterburner 1' for a

[COLOR=#800000]**#AACENCOPTS='--profile 156 -signaling explicit_sbr -b:a 38k -afterburner 1'**[/COLOR]

# OPUS
# For the encoder options look at: 'opusenc -h'
#OPUSENCOPTS=

# There are three ways to tag MP3 files: id3v1 (with id3), id3v2.3
# (with id3v2) and id3v2.4 (with eyeD3). Use ID3TAGV to select one of
# the older formats
#ID3TAGV=id3v2.4
#ID3OPTS=
#ID3V2OPTS=
#EYED3OPTS="--set-encoding=utf16-LE"
#CDPARANOIAOPTS=
#CDDA2WAVOPTS=
#PIRDOPTS="-p"
#CDDAFSOPTS="-f"
#CDDBTOOLOPTS=
#EJECTOPTS=
#DISTMP3OPTS=
#NORMALIZEOPTS=
#CDSPEEDOPTS="-x"
#CDSPEEDVALUE=""
#MKCUEOPTS=""
#MKTOCOPTS=""
#DIFFOPTS=""
#VORBISCOMMENTOPTS="-R"
#METAFLACOPTS="--no-utf8-convert"
#DIFFOPTS=""

# Actions to take
# Comma-separated list of one or more of the following:
#  cddb,cue,read,normalize,encode,tag,move,playlist,clean,default
#   encode implies read
#   normalize implies read
#   tag implies cddb,read,encode
#   move implies cddb,read,encode,tag
#   playlist implies cddb
# An action can be added to the "default" action by specifying it along with
# "default", without having to repeat the default ones:
#  ACTIONS=default,playlist
# The default action list (referenced as "default") is defined in the following
# comment:
#ACTIONS=cddb,read,encode,tag,move,clean

# CD device you want to read from
# It can be defined as a singletrack flac file, but since it might change from
# file to file it makes little sense to define it here.
#CDROM=/dev/cdrom
# If we are using the IDE bus, we need CDPARANOIACDROMBUS defined as "d"
# If we are using the ide-scsi emulation layer, we need to define a "g"
#CDPARANOIACDROMBUS="d"

# If you'd like to make a default location that overrides the current
# directory for putting mp3's, uncomment this.
#OUTPUTDIR=`pwd`

# Or if you'd just like to put the temporary .wav files somewhere else
# you can specify that here
#WAVOUTPUTDIR=`pwd`

# OUTPUTTYPE can be any of a number of formats, either a single format
# (e.g. "ogg") or a combination of them separated with ","
# (e.g. "flac,mp3"). Currently recognised and supported are:
# "flac", "m4a", "mp3, "mpc", "ogg", "opus", "spx", "vorbis", "wav", "wv", "ape"
#OUTPUTTYPE=ogg

# Output filename format - change this to reflect your inner desire to
# organize things differently than everyone else :)
# You have the following variables at your disposal:
# OUTPUT, GENRE, ALBUMFILE, ARTISTFILE, TRACKFILE, TRACKNUM and YEAR.
# Make sure to single-quote this variable. abcde will automatically create
# the directory portion of this filename.
# NOTICE: OUTPUTTYPE has been deprecated in the OUTPUTFORMAT string.
# Since multiple-output was integrated we always append the file type
# to the files. Remove it from your user defined string if you are getting
# files like ".ogg.ogg".
#OUTPUTFORMAT='${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'

# Like OUTPUTFORMAT but for Various Artists discs.
#VAOUTPUTFORMAT='Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Like OUTPUTFORMAT and VAOUTPUTFORMAT but for the ONEFILE rips.
#ONETRACKOUTPUTFORMAT=$OUTPUTFORMAT
#VAONETRACKOUTPUTFORMAT=$VAOUTPUTFORMAT

# Define how many encoders to run at once. This makes for huge speedups
# on SMP systems. Defaults to 1. Equivalent to -j.
#MAXPROCS=2

# Support for systems with low disk space:
# n:    Default parallelization (read entire CD in while encoding)
# y:    No parallelization (rip, encode, rip, encode...)
#LOWDISK=n

# If set to y, enables batch mode normalization, which preserves relative
# volume differences between tracks of an album.
#BATCHNORM=n

# Enables nogap encoding when using the 'lame' encoder.
#NOGAP=y

# Set the playlist file location format. Uses the same variables and format
# as OUTPUTFORMAT. If the playlist is specified to be in a subdirectory, it
# will be created for you and the playlist will reference files from that
# subdirectory.
#PLAYLISTFORMAT='${ARTISTFILE}-${ALBUMFILE}.${OUTPUT}.m3u'
# If you want to prefix every filename in a playlist with an arbitrary
# string (such as 'http://you/yourstuff/'), use this option
#PLAYLISTDATAPREFIX=''

#Like PLAYLIST{FORMAT,DATAPREFIX} but for Various Artists discs:
#VAPLAYLISTFORMAT='${ARTISTFILE}-${ALBUMFILE}.${OUTPUT}.m3u'
#VAPLAYLISTDATAPREFIX=''

#This will give the playlist CR-LF line-endings, if set to "y".
#(some hardware players insist on CR-LF line-endings)
#DOSPLAYLIST=n

# Custom filename munging:
# By default, abcde will do the following to CDDB data to get a useful
# filename:
# * Translate colons to a space and a dash for Windows compatibility
# * Eat control characters, single quotes, and question marks
# * Translate spaces and forward slashes to underscores
# To change that, redefine the mungefilename function.
# mungefilename receives the CDDB data (artist, track, title, whatever)
# as $1 and outputs it on stdout.
#mungefilename ()
#{
#    echo "$@" | sed s,:,\ -,g | tr \ / __ | tr -d \'\"\?\[:cntrl:\]
#}

# Custom genre munging:
# By default we just transform uppercase to lowercase. Not much of a fancy
# function, with not much use, but one can disable it or just turn the first
# Uppercase.
#mungegenre ()
#{
#    echo $CDGENRE | tr "[:upper:]" "[:lower:]"
#}


# Custom pre-read function
# By default it does nothing.
# You can set some things to get abcde function in better ways:
# * Close the CD tray using eject -t (if available in eject and supported by
#   your CD device.
# * Set the CD speed. You can also use the built-in options, but you can also
#   set it here. In Debian, eject -x and cdset -x do the job.
# KEEP IN MIND that executables included in pre_read must be in your $PATH or
# you have to define them with full /path/to/binary
# Uncomment and substitute the ":" with your commands.
#pre_read ()
#{
#:
#}

# Custom post-read function
# By default it does nothing.
# You can set some things to get abcde function in better ways:
# * Store a copy of the CD TOC.
# KEEP IN MIND that executables included in post_read must be in your $PATH or
# you have to define them with full /path/to/binary
# Uncomment and substitute the ":" with your commands.
#post_read ()
#{
#:
#}

# post_encode
# By default it does nothing.
# You can set some things to get abcde function in better ways:
# * Move the resulting directory over the network
# * Compare results with a previously made run, for tests
# KEEP IN MIND that executables included in post_encode must be in your $PATH or
# you have to define them with full /path/to/binary
# Uncomment and substitute the ":" with your commands.
#post_encode ()
#{
#:
#}

# If you'd like to have abcde eject the cdrom after all the tracks have been
# read, uncomment the following line.
#EJECTCD=y

# To encode on the remote machines foo, bar, baz, quux, and qiix, as well as
# on the local machine (requires distmp3 to be installed on local machine and
# distmp3host to be installed and running on all remote machines - see README)
#REMOTEHOSTS=foo,bar,baz,quux,qiix

# Set to 1,2, etc. to obtain some information about actions happening in the background
# Useful if you have a slow network or CDDB servers seem unresponsive.
#EXTRAVERBOSE=0


```

---

### Post by andrew.46 on 2015-03-21
Hey Shantiq!

Take the **[COLOR="#FF0000"]#[/COLOR]** mark away from your selections in the conf file and all should be well. BTW the output file type should be **[COLOR="#FF0000"]m4a[/COLOR]** not **[COLOR="#FF0000"]aac[/COLOR]**.

Are you using this file in ~/.abcde.conf? Perhaps an easier way is to use my own multi-format ~/.abcde.conf (above a few posts away) and then run it from the commandline simply as:

```

abcde -o m4a

```

And of course make your own modifications to the file, I suspect you would need to trim up the EJECT stuff at least.

This is my own pattern for testing abcde although now I also test against a bare commandline with no conf file. (This is how I missed my initial error with committing the Monkey's Audio changes.) Also how I do my own cd conversions...

---

### Post by shantiq on 2015-03-21
ha remove #     basic mistake ....    whoops    uncomment       [shows how much i do not know or quickly forget]


thanx Andrew


my line was wrong anyway:

3 changes are:

AAENCODERSYNTAX=fdkaac

AACENC=fdkaac

AACENCOPTS='--profile 29  -b 38000 -I'

in file .abcde.conf in home folder


for this type of file  HE-AACv2

```
mediainfo *
General
Complete name                            : 01.Baddy_Doub.aac
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 1.10 MiB
Duration                                 : 3mn 56s
Overall bit rate mode                    : Variable
Overall bit rate                         : 38.8 Kbps
Encoded date                             : UTC 2015-03-21 10:23:34
Tagged date                              : UTC 2015-03-21 10:23:34
Writing application                      : fdkaac 0.6.1, libfdk-aac 3.4.12, CBR 38kbps

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : HE-AACv2 / HE-AAC / LC
Codec ID                                 : 40
Duration                                 : 3mn 56s
Bit rate mode                            : Variable
Bit rate                                 : 38.0 Kbps
Maximum bit rate                         : 42.3 Kbps
Channel(s)                               : 2 channels / 1 channel / 1 channel
Channel positions                        : Front: L R / Front: C / Front: C
Sampling rate                            : 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 1.07 MiB (98%)
Encoded date                             : UTC 2015-03-21 10:23:34
Tagged date                              : UTC 2015-03-21 10:23:34
```

---

### Post by andrew.46 on 2015-03-21
Good to see it is all running :). Don't forget though that you will get a proper container and tagging as well if you also use:

```

OUTPUTTYPE="m4a"

```

aac is really only used in the newest abcde to catch copies of faac without m4a support...

---

### Post by shantiq on 2015-03-22
hmmmm   where do you place this Andrew ?   .   i put in in the conf

ok  in conf


> 
# OUTPUTTYPE can be any of a number of formats, either a single format
# (e.g. "ogg") or a combination of them separated with ","
# (e.g. "flac,mp3"). Currently recognised and supported are:
# "flac", "m4a", "mp3, "mpc", "ogg", "opus", "spx", "vorbis", "wav", "wv", "ape"
#OUTPUTTYPE=ogg
OUTPUTTYPE=m4a

  no speechmarks it seems  [i have tried with and without]

but this does not work with fdkaac 

if i enter

```
abcde  -d /dev/sr1 -o aac  -p 4


```   it gives me an untagged aac


if i enter m4a  it reverts to aac AND faac

```
abcde  -d /dev/sr1 -o m4a  -p 4

it gives:
WARNING: Your copy of Faac does not have mp4 support
WARNING: Encoding untagged files to aac...


```


to summarize using


AAENCODERSYNTAX=fdkaac

AACENC=fdkaac

AACENCOPTS='--profile 29  -b 38000 -I'

OUTPUTTYPE=m4a

---

### Post by andrew.46 on 2015-03-22
> **shantiq said:**
> 
to summarize using


```
AAENCODERSYNTAX=fdkaac

AACENC=fdkaac

AACENCOPTS='--profile 29  -b 38000 -I'

OUTPUTTYPE=m4a
```



I must apologise I thought you had made a simple transcription error on the Forum. With these settings I get the same result as you but you have made a small error here:

```

AAENCODERSYNTAX=fdkaac

```

This should actually be:

```

AA**[COLOR="#FF0000"]C[/COLOR]**ENCODERSYNTAX=fdkaac

```

And this should produce the desired files for you...

---

### Post by shantiq on 2015-03-22
eagle-eyed you are ::]]   do not think this mistake was mine on the conf ...  must have been there already in the default ...    do not see why or how i could have knocked off the "C"  ...   anyway no bother all good    thanx      a lot of options on abcde now :]


in the   .abcde.conf in home folder add


```
AACENCODERSYNTAX=fdkaac

AACENC=fdkaac

AACENCOPTS='--profile 29  -b 38000 -I'

OUTPUTTYPE=m4a
```



Love this format as it has GREAT sound and allows you to email an entire album in one attachment...

---

### Post by andrew.46 on 2015-03-23
> **shantiq said:**
> [...]   a lot of options on abcde now :][/CODE]

Indeed!! Choices are:

[LIST=1]
[*]mp3 encoded with lame, tagged with a choice of eyeD3, id3v2 or id3
[*]aac encoded with:
[LIST]
[*]faac with inline tagging
[*]neroAacEnc with tagging by NeroAacTag
[*]fdkaac with inline tagging
[/LIST]
[*]WavPack encoded with wavpack, inline tagging
[*]Opus encoded with opusenc, inline tagging
[*]Monkey's Audio encoded with Monkey's Audio Console (mac), tagged with Apetag.
[*]wav encoding, produced by cdparanoia or cdda2wav
[*]Flac encoding with flac, tagged by metaflac
[*]Vorbis encoded with oggenc, tagging by vorbiscomment
[*]Musepack encoded with mpcenc, inline tagging
[*]Speex encoding with speexenc, inline tagging
[/LIST]

You cannot ask for too much more than that :)

---

### Post by andrew.46 on 2015-03-28
I have been delving into the fascinating world of replaygain, hopefully abcde has benefited from my investigations:

```

commit dce5ef356c5860957317eb18013042b9d5db6862
Author: Andrew Strong <andrew.[...]@gmail.com>
Date:   Sun Mar 29 10:05:13 2015 +1100

    Replaygain for WavPack files
    
    The addition of wvgain allows replaygain for WavPack files. By
    default this allows 'track gain', we also use an option to add
    'album gain' tagging as well.

commit 9fb9b295883a3eef058e5a2c9113b800761f37fb
Author: Andrew Strong <andrew[...]@gmail.com>
Date:   Sun Mar 29 06:33:13 2015 +1100

    Replaygain fix for Musepack
    
    Replaygain for Musepack was still set for SV7's replaygain and
    thus broken under SV8. This commit changes support to SV8's mpcgain.


```

The original mistake with replaygain and MusePack was mine but I am mostly keeping that a little quiet :).

---

### Post by andrew.46 on 2015-04-02
I have done a little digging around and managed to get l3enc working with abcde, which can I say was very exciting!! A sample conf file is here:

```

# -----------------$HOME/.abcde.conf----------------------- #
#                                                           #
#    Andrew's personal ~/.abcde.conf file for mp3           # 
#   conversion with the ever slightly aged l3enc!!!         #
#            (Tagging will be with eyeD3)                   #
#         abcde version 2.6.1-UNRELEASED                    #
#                                                           #
#         http://andrews-corner.org/abcde.html              #
# --------------------------------------------------------- #

# Encode tracks immediately after reading. Saves disk space, gives
# better reading of 'scratchy' disks and better troubleshooting of
# encoding process but slows the operation of abcde quite a bit:
LOWDISK=y

# Specify the method to use to retrieve the track information,
# I give the default below but consider setting 'musicbrainz'
# instead, which is my own preferred option:
CDDBMETHOD=cddb

# Make a local cache of cddb entries and then volunteer to use 
# these entries when and if they match the cd:
CDDBCOPYLOCAL="y"
CDDBLOCALDIR="$HOME/.cddb"
CDDBLOCALRECURSIVE="y"
CDDBUSELOCAL="y"

MP3ENCODERSYNTAX=l3enc           # Specify encoder for MP3
L3ENC=l3enc                      # Path to the mp3 encoder
L3ENCOPTS='-br 256000 -hq -crc'  # Options for l3enc

OUTPUTTYPE="mp3" 

CDROMREADERSYNTAX=cdparanoia            
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
OUTPUTDIR="$HOME/Music"               
ACTIONS=cddb,read,encode,tag,move,playlist,clean

OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

MAXPROCS=2                           # Run a few encoders simultaneously
PADTRACKS=y                          # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=2                       # Useful for debugging
COMMENT='Encoded with l3enc!!!'      # Place a comment...
EJECTCD=y                            # Please eject cd when finished :-)

```

l3enc requires some older libraries, more information on the Slackware thread that showed me how to accomplish it:

[http://www.linuxquestions.org/questions/slackware-14/running-the-very-first-mp3-encoder-under-64bit-slackware-14-1-multilib-4175538527/](http://www.linuxquestions.org/questions/slackware-14/running-the-very-first-mp3-encoder-under-64bit-slackware-14-1-multilib-4175538527/)

---

### Post by andrew.46 on 2015-04-09
@mc4man: You may be interested to take [the latest abcde]("http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=commit;h=f30616026a2c1a52550c42088ed8b9b4419ad2d0") for a run as fdkaac will now run with abcde and the 'usepipes' option (no wav files generated, cdparanoia or cdda2wav output via stdout to fdkaac).

Once you have an abcde.conf file set for abcde just try:

```

abcde -o m4a -P

```

and check it out! Note that AACENCOPTS will not work for fdkaac, use FDKAACENCOPTS instead...

---

### Post by andrew.46 on 2015-04-22
And perhaps some will be interested to see [the first of 3 commits]("http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=commit;h=2cdd96e0c8e10e050523452ce5271f98f8b8f9d9") that will add automated or manual downloading of album cover art from within abcde. It functions fine with this commit, you will need to install glyr / glyrc and preferably set:

```

CDDBMETHOD=musicbrainz

```

The next couple of commits will add the ability to view the image before downloading, manually download another image of your choice from online or local source and automatically convert to jpg if necessary. Final commit will be some detailed documentation...

Very exciting times for abcde :).

---

### Post by andrew.46 on 2015-05-02
The album art commits are done and if anybody is interested in trying it all out here is a conf file for ripping with libcdio's cd-paranoia, encoding with lame, tagging with eyeD3 and also downloading and embedding album art:

```

# -----------------$HOME/.abcde.conf----------------- #
#                                                     #
# A sample configuration file to convert music cds to # 
#  MP3 format and also download and embed album art.  #
#         Using abcde version 2.6-UNRELEASED'         #
#                                                     #
#       http://andrews-corner.org/abcde.html          #  
# --------------------------------------------------- #

# Encode tracks immediately after reading. Saves disk space, gives
# better reading of 'scratchy' disks and better troubleshooting of
# encoding process but slows the operation of abcde quite a bit:
LOWDISK=y

# Specify the method to use to retrieve the track information,
# I give the default below but consider setting 'musicbrainz'
# instead, which is my own preferred option:
CDDBMETHOD=musicbrainz

# Make a local cache of cddb entries and then volunteer to use 
# these entries when and if they match the cd:
CDDBCOPYLOCAL="y"
CDDBLOCALDIR="$HOME/.cddb"
CDDBLOCALRECURSIVE="y"
CDDBUSELOCAL="y"

# Options for the new function getalbumart which will download
# the relevant album art image as cover.jpg:
GLYRC=glyrc
GLYRCOPTS= 
IDENTIFY=identify
IDENTIFYOPTS=   
CONVERT=convert
CONVERTOPTS="-strip -interlace Plane -gaussian-blur 0.05 -quality 85%"
ALBUMARTALWAYSCONVERT="y"   
DISPLAYCMD=display
DISPLAYCMDOPTS="-resize 512x512 -title abcde_album_art"
ALBUMARTFILE="cover.jpg"
ALBUMARTTYPE="JPEG"

# Specify the encoder to use for MP3. In this case
# the alternatives are gogo, bladeenc, l3enc, xingmp3enc, mp3enc:
MP3ENCODERSYNTAX=lame 

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/lame
LAME=lame

# Specify your required encoding options here. Multiple options can
# be selected as '--preset standard --another-option' etc.
# The '-V 2' option gives VBR encoding between 170-210 kbits/s.
LAMEOPTS='-V 2 --verbose' 

# Output type for MP3:
OUTPUTTYPE="mp3"

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only),flac and libcdio:
CDROMREADERSYNTAX=libcdio 

# Give the location of the ripping program and pass any extra options:      
CD_PARANOIA=cd-paranoia  
CDPARANOIAOPTS="--never-skip=40 --verbose"

# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files:
OUTPUTDIR="$HOME/Music"               

# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,getalbumart,encode,tag,move,clean
              
# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode:
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# Use the post_encode function to embed the album art and then
# backup the album art:
post_encode ()
{
 ARTISTFILE="$(mungefilename "$TRACKARTIST")"
 ALBUMFILE="$(mungefilename "$DALBUM")"
 
 if [ "$OUTPUTTYPE" = "mp3" ] && [ "$TAGGER" = "$EYED3" ] ; then
 vecho "Preparing to embed the album art..." >&2
 else
 vecho "Not embedding album art, you need mp3 output and eyeD3 tagging..." >&2
 return 1
 fi

 if [ "$VARIOUSARTISTS" = "y" ] ; then
  FINDPATH="$(eval echo "$VAOUTPUTFORMAT")"
 else
  FINDPATH="$(eval echo "$OUTPUTFORMAT")"
 fi

 TRIMPATH="$(dirname "$OUTPUTDIR/$FINDPATH")"
 cd "$TRIMPATH"

 if [ -e "cover.jpg" ] ; then
  for i in *.mp3
  do
   eyeD3 --add-image cover.jpg:FRONT_COVER "$i"
  done
  mkdir backup && mv cover.jpg backup
 vecho "Your files have had the album art embedded..." >&2
 else
 vecho "No album art found so no image embedded..." >&2
 fi
}

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=2                          # Useful for debugging
COMMENT='abcde version 2.6.1'           # Place a comment...
EJECTCD=y                               # Please eject cd when finished :-)

```

You will need the git abcde, glyrc and ImageMagick. Love to hear from some eager testers :)

---

### Post by mc4man on 2015-05-02
Am going to give a try later tonight (latest git, the conf you posted, ect.
(I'm considering adding an example or 2 conf to examples, (/usr/share/doc/abcde/examples/), got something(s) you think is appropriate? 

? - will the next release be shortly, ie. a new changelog..

---

### Post by andrew.46 on 2015-05-02
> **mc4man said:**
> Am going to give a try later tonight (latest git, the conf you posted, ect.
(I'm considering adding an example or 2 conf to examples, (/usr/share/doc/abcde/examples/), got something(s) you think is appropriate?

Feel free to modify any of the ones from my website :). The post_encode function I have included above is not necessary, without it the cover.jpg just sits with the files. Embedding was something I just played with and it was a bit of fun writing the function...

> ? - will the next release be shortly, ie. a new changelog..

Well, I think it would be a good time but I have not been able to contact Steve for quite some time and he, as the owner, is really the one to decide. I have cleared all of the bugs that I can, sorted out aac encoding, added in ape and wavpack encoding, added in album art downloading, added in ripping with libcdio's cd-paranoia = a solid changelog for at least a point upgrade :).

Anyway I shall chase Steve up...

---

### Post by mc4man on 2015-05-03
With the previous build I had (admittedly older - git 7311785) fdkaac encoding & tagging is fine. However with latest git now get a failure - 
```
encodetrack-m4a-01: returned code 1: nice -n 10 fdkaac 192k --artist The Rolling Stones --album Beggars Banquet --title Sympathy For The Devil --track 01 --genre Rock & Roll --date 1968 --comment abcde version 2.6.1 /home/doug/abcde.8209820a/track01.wav -o /home/doug/abcde.8209820a/track01.m4a
```
That is with my .abcde.conf & for also purposes of comparing with the one you posted in # 27
Does it work for you with .conf in #27?
( in mine the opts were - 
AACENCOPTS='-m 5 -a 1'
In #27 - 
AACENCOPTS='--bitrate 128'

Both .conf's produce same exact same error line  which  mentions - fdkaac 192k ??

Edit: I see - older .conf's will not work, aac/m4a needs specific, ie. - FDKAACENCOPTS ect.
I'll really need to
1. read the new abcde.conf
2. create specific ex.'s  for the various  aac... encoding choices
3. if packaged then warn in changelog

? - in the case of an older .conf does it not fallback  to the default (192k) because ..?

---

### Post by andrew.46 on 2015-05-03
> **mc4man said:**
> ? - in the case of an older .conf does it not fallback  to the default (192k) because ..?

Because I made a stupid mistake :). Sorry about that it is fixed now:

```

andrew@ilium~/development/abcde$**[COLOR="#FF0000"] git log -n 1[/COLOR]**
commit 37108bd410d736eed86b831e49c0fda1b2dfff4d
Author: Andrew Strong <andrew.-------------@gmail.com>
Date:   Mon May 4 04:52:07 2015 +1000

    Fix for 'fallback' fdkaac bitrate
    
    The previously set fallback bitrate for encoding with fdkaac was
    set incorrectly. Thanks to Doug Mcmahon for the report.
andrew@ilium~/development/abcde$ 

```

BTW you have probably noticed I have added a -G option to get album art via commandline... Sorry again for the stupid error on my part!

---

### Post by andrew.46 on 2015-05-03
> **mc4man said:**
> Edit: I see - older .conf's will not work, aac/m4a needs specific, ie. - FDKAACENCOPTS ect.


Well, the AACENCOPTS option should still work in the absence of the appropriate (new) aac option, but better to give the new options. The problem with the fdkaac options is that fdkaac itself has no default option when passed without bitrate or mode and of course my option for those who pass neither AACENCOPTS or FDKAACENCOPTS was incorrect :(.

---

### Post by mc4man on 2015-05-03
I'm going to try out the album art stuff tonight, otherwise looking good
It seems a bit more verbose in the console than what i remember, I like that..,  (the stuff about tags, mv ect.

---

### Post by andrew.46 on 2015-05-03
Of course post_encode function is just a little bit of froth which abcde does not really need. I confess that I use it to embed album art for my iPOD classic but almost everybody should be happy just with cover.jpg in the same directory as their encoded files.

Embedding looks a little problematic away from flac and mp3 anyway but perhaps one day there will be an option:

```
ALBUMARTEMBED=y
```

in abcde for those who want it, but this would require substantial work... Next for me is True Audio encoding with ttaenc :)

---

### Post by andrew.46 on 2015-05-23
I would be grateful for anybody who could test the new mungefilename function which I am about to commit. The default will be:

```

mungefilename ()
{
  echo "$@" | sed -e 's/^\.*//' -e 's/ /_/g' | tr -d ":><|*/\"'?[:cntrl:]"
}

```

This:

[LIST=1]
[*]Deletes any dots preceding the title (first sed command)
[*]Replaces all spaces with an underscore (second sed command)
[*]Deletes a grab bag of characters which variously Windows and Linux do not permit (final tr command)
[*]
[/LIST]

while a version that allows spaces in filenames is:

```


mungefilename ()
{
  echo "$@" | sed -e 's/^\.*//' | tr -d ":><|*/\"'?[:cntrl:]"
}

```

I have to confess to working on this for quite some time and I am hoping that it will perform well! Place this in your ~/.abcde.conf file and go for it :).

---

### Post by mc4man on 2015-05-23
> **andrew.46 said:**
> I would be grateful for anybody who could test the new mungefilename function which I am about to commit. 


Both work without issue here, I guess from past days of RR & dBpoweramp am used to spaces so I may go with that one locally..
Maybe tomorrow I'll see if I have any really odd named ones around though did just have to move most of my cd's elsewhere for the immediate future..

---

### Post by andrew.46 on 2015-05-23
Thanks for looking mc4man :). I have tested a lot without cd using something like:

```

echo "...Pink Floyd's Strange* New Album?" | 
sed -e 's/^\.*//' -e 's/ /_/g' | 
tr -d ":><|*/\"'?[:cntrl:]" ; echo

```

and variations...

---

### Post by mc4man on 2015-05-23
> **andrew.46 said:**
>  I have tested a lot without cd using something like:

```

echo "...Pink Floyd's Strange* New Album?" | 
sed -e 's/^\.*//' -e 's/ /_/g' | 
tr -d ":><|*/\"'?[:cntrl:]" ; echo

```

and variations...
well,  when you put it that way I inadvertently gain some sed  knowledge, part of your 'way', so thanks..

---

### Post by andrew.46 on 2015-05-23
sed can be a little addictive! Mind you the heart of these changes came from a very skilled gentleman on comp.unix.shell which is one of the few usenet newsgroups that still thrives and provides excellent advice.

---

### Post by andrew.46 on 2015-06-10
OK big rewrite ready for release 2.7 which will hopefully be moving along after this weekend sometime :).

abcde: Command Line Music CD Ripping for Linux
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

I have:

[LIST=1]
[*]Made musicbrainz the default CDDBMETHOD
[*]Added in an option to save and reuse cddb searches
[*]Changed the mungefilename function along with some better explanatory notes
[*]Left a link to the new [getalbumart page]("http://www.andrews-corner.org/getalbumart.html")
[*]Added in a conf file for WavPack
[*]Added in a conf file for Monkey's Audio (ape)
[*]Added in a conf file for fdkaac
[*]Added in a conf file for neroAacEnc
[*]Briefly (again) considered removing the Speex conf file...
[*]
[/LIST]

Should be a great release, thrashing out the details with Steve this Saturday...

---

### Post by andrew.46 on 2015-06-18
Finally:

```


andrew@ilium~/development/abcde$ git log 987890ea -n 1
commit 987890ea95fbb3d65401821ab322bca50ef31bf2
Author: Andrew Strong <andrew.xxxxxxxxxx@gmail.com>
Date:   Thu Jun 18 22:26:40 2015 +1000

    Release version 2.7
andrew@ilium~/development/abcde$ 

```

:)

---

### Post by mc4man on 2015-06-18
Is there a version restriction for eyed3? 
Also do either imagemagick or glyrc  have any current use?

---

### Post by andrew.46 on 2015-06-18
> **mc4man said:**
> Is there a version restriction for eyed3? 

There is a nice piece of scripting in abcde now that does a version sniff for eyeD3 and switches to the appropriate syntax. I have tested with both 0.6.14 and 0.7.5 (and now 0.7.8) and all work well.

> Also do either imagemagick or glyrc  have any current use?

Downloading album art is not the *default* but if it is specified glyrc is needed and ImageMagick is a great enhancement. The details have been published here:

abcde: Downloading Album Art...
[http://www.andrews-corner.org/getalbumart.html](http://www.andrews-corner.org/getalbumart.html)

And I hope this new function will bring new life to abcde. BTW #abcde is now available on freenode for any who want to chat about abcde.

---

### Post by mc4man on 2015-06-18
Excellent ( and your site is looking good as a resource - thanks.

---

### Post by andrew.46 on 2015-06-18
The whole release looks pretty solid but I guess eventual wide usage may reveal issues. I have enjoyed the whole process immensely though. Downloads in [the usual place]("http://abcde.einval.com/download/")...

---

### Post by andrew.46 on 2015-06-20
I have added in encoding with qaac + wine to the abcde git and it works well on my system:

```

andrew@ilium~/Music/m4a/Pink Floyd-Wish You Were Here$ mediainfo 04.Wish\ You\ Were\ Here.m4a 
General
Complete name                            : 04.Wish You Were Here.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 30.2 MiB
Duration                                 : 5mn 40s
Overall bit rate mode                    : Variable
Overall bit rate                         : 744 Kbps
Album                                    : Wish You Were Here
Track name                               : Wish You Were Here
Track name/Position                      : 4
Performer                                : Pink Floyd
Encoded date                             : UTC 2015-06-21 01:11:52
Tagged date                              : UTC 2015-06-21 01:11:55
Writing application                      : qaac 2.49, CoreAudioToolbox 7.9.9.6, Apple Lossless Encoder
Comment                                  : abcde 2.7.1-UNRELEASED

Audio
ID                                       : 1
Format                                   : ALAC
Codec ID                                 : alac
Codec ID/Info                            : Apple Lossless Audio Codec
Duration                                 : 5mn 40s
Duration_LastFrame                       : -71ms
Bit rate mode                            : Variable
Bit rate                                 : 744 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Stream size                              : 30.2 MiB (100%)
Encoded date                             : UTC 2015-06-21 01:11:52
Tagged date                              : UTC 2015-06-21 01:11:55


andrew@ilium~/Music/m4a/Pink Floyd-Wish You Were Here$ 

```

Note the alac encoding that is possible by using QAACENCOPTS="--alac". I would love to have this change tested by anybody with an interest...

---

### Post by shantiq on 2015-06-21
happy to do so Andrew but please you need to remind me how I update with git;   I have thoroughly forgotten
thanx   shan


Ha   ok   to click on snapshot on first line [here]("http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=summary")   and use that folder    will report

---

### Post by andrew.46 on 2015-06-21
There is a ready-made conf file here:

[http://www.andrews-corner.org/qaac.html#abcde](http://www.andrews-corner.org/qaac.html#abcde)

Be careful with the path to qaac: abcde will not tolerate spaces in the path. Something I cannot get to the bottom of...

---

### Post by shantiq on 2015-06-21
well Andrew with your [**excellent guide**]("http://www.andrews-corner.org/qaac.html#abcde") even a duffer like me :] can get there 
Great work!   

Proof of the pudding:::

```
shantiq@shantiq-00000000000000000000000:~/m4a/Lianne La Havas-Lost & Found EP$ mediainfo *m4a
General
Complete name                            : 04.Night School.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 14.5 MiB
Duration                                 : 2mn 40s
Overall bit rate mode                    : Variable
Overall bit rate                         : 755 Kbps
Album                                    : Lost & Found EP
Track name                               : Night School
Track name/Position                      : 4
Performer                                : Lianne La Havas
Genre                                    : Rock
Recorded date                            : 2011
Encoded date                             : UTC 2015-06-21 08:09:14
Tagged date                              : UTC 2015-06-21 08:09:18
Writing application                      : qaac 2.49, CoreAudioToolbox 7.9.9.6, Apple Lossless Encoder
Comment                                  : abcde version 2.7.1 UNRELEASED

Audio
ID                                       : 1
Format                                   : ALAC
Codec ID                                 : alac
Codec ID/Info                            : Apple Lossless Audio Codec
Duration                                 : 2mn 40s
Duration_LastFrame                       : -42ms
Bit rate mode                            : Variable
Bit rate                                 : 754 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Stream size                              : 14.5 MiB (100%)
Encoded date                             : UTC 2015-06-21 08:09:14
Tagged date                              : UTC 2015-06-21 08:09:18


```

---

### Post by andrew.46 on 2015-06-21
Woooo hooooo! ALAC has come to abcde :). Thanks for testing...

---

### Post by shantiq on 2015-06-21
Thanx for the brainwork Maestro :]

PS : personal embellishment for flexibility between alac and HE-AACv2 added to my .abcde.conf

```

# IF YOU WANT AN ALAC FILE CHANGE NEXT LINE  from fdkaac to qaac  IF YOU WANT A HE-AACv2 FILE 
[very small but still good sonically;  can zip a whole album in a normal email] CHANGE TO fdkaac >>

AACENCODERSYNTAX=[COLOR=#b22222]fdkaac[/COLOR]
FDKAAC=fdkaac
#   to set up qaac   see here >> http://www.andrews-corner.org/qaac.html#abcde
#   and place your qaac.exe the way it is below here [create folder if need be]

QAAC="$HOME/.wine/drive_c/qaac/qaac.exe"
QAACENCOPTS="--alac"   

# Output type for alac:
OUTPUTTYPE="m4a"

# For fdkaac options see 'fdkaac --help' THIS HERE BELOW WILL GIVE YOU A HE-AACv2 FILE
FDKAACENCOPTS='-p 29  -b 38000 -I' 


```

---

### Post by andrew.46 on 2015-06-21
qaac also encodes with HE-AAC, is there much difference between qaac and fdkaac output? I will have a closer look tonight but I suspect that you have already been deeper in this area than myself...

BTW abcde will ignore this:

```

**[COLOR="#FF0000"]AACENC[/COLOR]**=fdkaac

```

For the path statement you need:

```

**[COLOR="#FF0000"]FDKAAC[/COLOR]**=fdkaac

```

instead.

---

### Post by shantiq on 2015-06-22
yes Andrew qaac does not produce [HE-AACv2]("https://en.wikipedia.org/wiki/High-Efficiency_Advanced_Audio_Coding") [deeper sound]that I know of only HE-AAC
PS    thanx on correction
FDKAAC=fdkaac

used ```
qaac.exe --he -a 33
``` 

```
mediainfo 13\ GTO\'s\ -\ The\ Original\ GTO\'s.m4a 
General
Complete name                            : 13 GTO's - The Original GTO's.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 297 KiB
Duration                                 : 1mn 4s
Overall bit rate mode                    : Variable
Overall bit rate                         : 37.6 Kbps
Encoded date                             : UTC 2015-06-22 06:05:21
Tagged date                              : UTC 2015-06-22 06:05:28
Writing application                      : qaac 2.49, CoreAudioToolbox 7.9.9.6, AAC-HE Encoder, ABR 32kbps, Quality 96

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
[COLOR=#800000] Format profile                           : HE-AAC / LC[/COLOR]
Codec ID                                 : 40
Duration                                 : 1mn 4s
Bit rate mode                            : Variable
Bit rate                                 : 36.6 Kbps
Maximum bit rate                         : 46.7 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 289 KiB (97%)
Encoded date                             : UTC 2015-06-22 06:05:21
Tagged date                              : UTC 2015-06-22 06:05:28
```


same conversion with fdkaac


```
mediainfo 13\ GTO\'s\ -\ The\ Original\ GTO\'s.m4a 
General
Complete name                            : 13 GTO's - The Original GTO's.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 308 KiB
Duration                                 : 1mn 4s
Overall bit rate mode                    : Variable
Overall bit rate                         : 38.9 Kbps
Encoded date                             : UTC 2015-06-22 06:10:46
Tagged date                              : UTC 2015-06-22 06:10:46
Writing application                      : fdkaac 0.6.1, libfdk-aac 3.4.12, CBR 38kbps

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
[COLOR=#800000]Format profile                           : HE-AACv2 / HE-AAC / LC[/COLOR]
Codec ID                                 : 40
Duration                                 : 1mn 4s
Bit rate mode                            : Variable
Bit rate                                 : 38.0 Kbps
Maximum bit rate                         : 45.1 Kbps
Channel(s)                               : 2 channels / 1 channel / 1 channel
Channel positions                        : Front: L R / Front: C / Front: C
Sampling rate                            : 44.1 KHz / 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 301 KiB (98%)
Encoded date                             : UTC 2015-06-22 06:10:46
Tagged date                              : UTC 2015-06-22 06:10:46

```

---

### Post by andrew.46 on 2015-06-22
Thanks Shan for clearing that up...

---

### Post by andrew.46 on 2015-06-24
And a final alac question Shan: Have you experimented much with the implementation of the Apple Open Source encoder release included with qaac called refalac? I note that it does not even need all of the Apple detritus to run which is a big bonus! If you installed according to my web page you will have:

```

andrew@ilium~$**[COLOR="#FF0000"] refalac --check[/COLOR]**
refalac 1.49
libsoxconvolver 0.1.0
libsoxr-0.1.1
libsndfile-1.0.25
libFLAC 1.3.1
wavpackdll 4.75.0
tak_deco_lib 2.3.0 compatible

```

I am not sure if this has a place in abcde, perhaps on a cold rainy weekend I might have a look... But I am interested to hear if you have tested it at all?

---

### Post by shantiq on 2015-06-25
hmmm weird Andrew   used your sterling guide [here]("http://www.andrews-corner.org/qaac.html#abcde") and look what i get

```
shantiq@shantiq-00000000000000000000000:~$ qaac --check
qaac 2.49, CoreAudioToolbox 7.9.9.6
libsoxconvolver 0.1.0
libsoxr-0.1.1
shantiq@shantiq-00000000000000000000000:~$ refalac --check
refalac: command not found
shantiq@shantiq-00000000000000000000000:~$ 


```


OK   had to add this to my .bashrc

```
alias refalac='wine ~/.wine/drive_c/qaac/refalac.exe'
```
and run ```
. ~/.bashrc
```


now I am cooking

```
shantiq@shantiq-00000000000000000000000:~$ refalac  --check
refalac 1.49
libsoxconvolver 0.1.0
libsoxr-0.1.1


```


so shall see what it does and report :]


handy!   but no tags as from a wav only i understand

```
shantiq@shantiq-00000000000000000000000:~/Desktop$ refalac -A 13\ GTO\'s\ -\ The\ Original\ GTO\'s.wav 
refalac 1.49

13 GTO's - The Original GTO's.m4a
[100.0%] 1:04.640/1:04.640 (43.7x), ETA 0:00.000  
2850624/2850624 samples processed in 0:01.490
Overall bitrate: 667.758kbps
Optimizing...done


```

[IMG]http://s20.postimg.org/hk314v2qh/Foobar2000_Icon_pur_60_b.png[/IMG]

---

### Post by andrew.46 on 2015-06-25
Oops, I have a bunch of updates to that page sitting on my home computer and I had forgotten that I had not actually uploaded these! You have worked out the ~/.bashrc setting yourself, if you are interested in the extra import dlls for both refalac and qaac I have packaged these:

```

cd $HOME/qaac_build && \
wget http://www.andrews-corner.org/downloads/x32DLLs_20150620.zip && \
unzip -j x32DLLs_20150620.zip 'x32DLLs_20150620/*' -d ~/.wine/drive_c/qaac/

```

and then you will get the following:

```

andrew@ilium~$ **[COLOR="#FF0000"]refalac --check[/COLOR]**
refalac 1.49
libsoxconvolver 0.1.0
libsoxr-0.1.1
libsndfile-1.0.25
libFLAC 1.3.1
wavpackdll 4.75.0
tak_deco_lib 2.3.0 compatible
andrew@ilium~$ 

```

and:

```

andrew@ilium~$ **[COLOR="#FF0000"]qaac --check[/COLOR]**
qaac 2.49, CoreAudioToolbox 7.9.9.6
libsoxconvolver 0.1.0
libsoxr-0.1.1
libsndfile-1.0.25
libFLAC 1.3.1
wavpackdll 4.75.0
tak_deco_lib 2.3.0 compatible
andrew@ilium~$ 

```

I plan on finishing the page this weekend, it has been a lot of work and testing, more so than many of the guides I have written...

---

### Post by andrew.46 on 2015-06-25
> **shantiq said:**
> used ```
qaac.exe --he -a 33
``` 

I noted the effect of using '0' for an option:

```

-a, --abr <bitrate>    AAC ABR mode / bitrate
-V, --tvbr <n>         AAC True VBR mode / quality [0-127]
-v, --cvbr <bitrate>   AAC Constrained VBR mode / bitrate
-c, --cbr <bitrate>    AAC CBR mode / bitrate
                       [B][COLOR="#FF0000"]For -a, -v, -c, "0" as bitrate means "highest".
                       Highest bitrate available is automatically chosen.
                       For LC, default is -V90
                       For HE, default is -v0[/COLOR][/B]

```

Not much use for keeping bitrates low I guess but a good indicator of what qaac is capable of. Of course this gives the possibiliities:

```

qaac --formats

```

and manipulation of the *--rate* option allows the highest bitrates, perhaps not advisable but a bit of fun anyway :). I have been adding in the *--threading* option to test as well although this is only of any use if decoding *and* encoding are both hard at work, [see here]("http://www.hydrogenaud.io/forums/index.php?showtopic=85135&st=200&p=806178&#entry806178")...

---

### Post by shantiq on 2015-06-26
```
shantiq@shantiq-00000000000000000000000:~$ refalac  --check
refalac 1.49
libsoxconvolver 0.1.0
libsoxr-0.1.1
libsndfile-1.0.25
libFLAC 1.3.1
wavpackdll 4.75.0
tak_deco_lib 2.3.0 compatible
shantiq@shantiq-00000000000000000000000:~$
```


this way can convert from flac and other formats and keep tags  [then refalac is a hugely handy tool]


```
shantiq@shantiq-00000000000000000000000:/media/extradrive/home/shantiq/La.Musica/Tappa Zukie (FLAC)/(1978) Tapper Roots - FLAC$ refalac -A 05\ -\ Riding\ West.flac 
refalac 1.49

05 - Riding West.m4a
[100.0%] 3:34.000/3:34.000 (32.7x), ETA 0:00.000  
9437400/9437400 samples processed in 0:06.567
Overall bitrate: 911.788kbps
Optimizing...done
shantiq@shantiq-00000000000000000000000:/media/extradrive/home/shantiq/La.Musica/Tappa Zukie (FLAC)/(1978) Tapper Roots - FLAC$ mediainfo 05\ -\ Riding\ West.m4a 
General
Complete name                            : 05 - Riding West.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 23.3 MiB
Duration                                 : 3mn 34s
Overall bit rate mode                    : Variable
Overall bit rate                         : 912 Kbps
Album                                    : Tapper Roots
Track name                               : Riding West
Track name/Position                      : 5
Performer                                : Tapper Zukie
Genre                                    : Reggae
Recorded date                            : 1979
Encoded date                             : UTC 2015-06-26 05:11:24
Tagged date                              : UTC 2015-06-26 05:11:31
Writing application                      : refalac 1.49, Apple Lossless Encoder

Audio
ID                                       : 1
Format                                   : ALAC
Codec ID                                 : alac
Codec ID/Info                            : Apple Lossless Audio Codec
Duration                                 : 3mn 34s
Duration_LastFrame                       : -88ms
Bit rate mode                            : Variable
Bit rate                                 : 912 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Stream size                              : 23.3 MiB (100%)
Encoded date                             : UTC 2015-06-26 05:11:24
Tagged date                              : UTC 2015-06-26 05:11:31


shantiq@shantiq-00000000000000000000000:/media/extradrive/home/shantiq/La.Musica/Tappa Zukie (FLAC)/(1978) Tapper Roots - FLAC$
```

---

### Post by andrew.46 on 2015-06-26
> **shantiq said:**
> this way can convert from flac and other formats and keep tags  [then refalac is a hugely handy tool]

Perhaps one of the few useful tools that came from Apple's release of the reference encoder I suspect :). Good news is that your current abcde setup (2.7.1-UNRELEASED) can use refalac for encoding audio cds by this slightly hackish addition to the abcde.conf file (I have now adjusted online):

```

# The path for qaac can be problematic as abcde cannot cope
# with the 'standard' Wine location with spaces:
#   "$HOME/.wine/drive_c/Program\ Files/qaac/qaac.exe"
# However the following works well:             
QAAC="$HOME/.wine/drive_c/qaac/qaac.exe"

[B][COLOR="#FF0000"]# Or use the Open Source alac encoder with this small hack:
# QAAC="$HOME/.wine/drive_c/qaac/refalac.exe"[/COLOR][/B]

```

Very exciting times :)

---

### Post by Yellow Pasque on 2015-06-26
I'm personally not interested in using AAC for CD ripping (or music at all really). However, I'm curious in comparing the audio quality of qaac and fdk-aac to see if I can really hear a difference between them. Are there suggested settings for a good comparison between the two?

Edit: Okay, so -V (aka --tvbr) 100 looks like a good option for getting a high quality file without an insanely bloated bitrate. What would be the closest comparable setting with fdkaac?

---

### Post by andrew.46 on 2015-06-26
Mind you the qaac developer recommends starting at --tvbr 63 and working up until you find the sweet spot. The following creates vbr with overall bitrate 131 kbps:

```

qaac --tvbr 73 luckynight.wav

```

while the following creates a vbr file at about the same overall bitrate:

```

fdkaac --profile 2 --bitrate-mode 4 luckynight.wav

```

The sample file I have used is here:

```

wget http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.wav.bz2

```

There are several other modes and bitrates to test with both encoders but I guess this would give at least a *starting* point. This simple test put qaac / Apple ahead on my machine...

---

### Post by shantiq on 2015-06-27
ok if not bloated and good quality sound is what we are after T; let me once again sing the virtues of HE-AACvc : read specs [here]("https://en.wikipedia.org/wiki/High-Efficiency_Advanced_Audio_Coding")  and at 38k  it will astound you maybe as it always has me; also allows you to send an ENTIRE zipped album to a friend in a normal email

setting for this   [neroAacEnc also produces this format]

```
fdkaac -p 29  -b 38000 -I
```

---

### Post by andrew.46 on 2015-07-01
> **shantiq said:**
>  ```
qaac.exe --he -a 33
``` 

I am just writing up the qaac commandline on my site and I have been thinking about this commandline. I note the qaac default is actually cvbr, do you have a special reason for using abr? I realise that the wrangling of the experts over which mode should be used where are interminable but I was just a little curious as to *your* thinking, as I write up the page...

---

### Post by shantiq on 2015-07-02
...   that Andrew I just just trying to get a HE-AACv2   file    and this was the best way i saw to try that    but then understood there is no such format in qaac;   i know nothing about qaac    just the -A option really   ::]]    good luck with writing

---

### Post by andrew.46 on 2015-07-02
> **shantiq said:**
> good luck with writing

Page is pretty much done:

Using qaac under Linux...
[http://www.andrews-corner.org/qaac.html](http://www.andrews-corner.org/qaac.html)

:)

---

### Post by shantiq on 2015-07-02
really good and clear   Andrew  like all your guides :]

---

### Post by andrew.46 on 2015-07-02
> **shantiq said:**
> really good and clear   Andrew  like all your guides :]

Good to hear that this one has been useful :). With a bit of strategic work it rates fairly high in google so hopefully the word will get out there soon.

I am having a look at fhgaacenc at the moment (not for abcde I suspect) but looks like it produces HE-AAC v2 and with winamp just about gone it would be nice to have a look...

---

### Post by andrew.46 on 2015-07-02
OK a sample of fhgaacenc encoding to HE-AACv2:

```

wget http://www.andrews-corner.org/samples/luckynight_fhgaacenc_HE-AACv2.m4a

```

and for those installing fhgaacenc note that the standard wine installation (I am running 1.6.2) means you do not have to install VC2008 runtime, just extract the Winamp dlls...

**Edit**: And for those who are not sure:

**fhgaacenc:**

```

mkdir $HOME/fhgaacenc_build && \
cd $HOME/fghaacenc_build && \
wget http://tmkk.undo.jp/tools/fhgaacenc-20120624.zip && \
7z e fhgaacenc-20120624.zip \
     fhgaacenc.exe libsndfile-1.dll -r \
     -o$HOME/.wine/drive_c/fhgaacenc/

```

**winamp:**

```

cd $HOME/fghaacenc_build && \
wget http://winampplugins.co.uk/Winamp/winamp5666_full_en-us_redux.exe && \
7z e winamp5666_full_en-us_redux.exe \
     enc_fhgaac.dll libmp4v2.dll \
     nsutil.dll -r \
     -o$HOME/.wine/drive_c/fhgaacenc/

```

and for ~/.bashrc:

```

alias fhgaacenc='wine ~/.wine/drive_c/fhgaacenc/fhgaacenc.exe'

```

I admit I cannot warm to 7z but I guess it gets the job done here...

---

### Post by andrew.46 on 2015-07-09
Great news for AAC experimenters and abcde users:

```

commit 6801628438a6f204a10549d016725fae5ece600d
Author: Andrew Strong <andrewxxxxxxxxxxxxxxx@gmail.com>
Date:   Fri Jul 10 12:21:42 2015 +1000

    AAC encoding with fhgaacenc and wine
    
    Tagging is with AtomicParsley, welcome back into abcde :).


```

The bones of the fhgaacenc page are in place and will be complete by the end of the weekend for those who wish to experiment a little :)

Using fhgaacenc under Linux...
[http://www.andrews-corner.org/fhgaacenc.html](http://www.andrews-corner.org/fhgaacenc.html)

---

### Post by andrew.46 on 2015-08-29
I have added in True Audio support to abcde using tagging from mid3v2. I am not sure if *tta* is readily available to Ubuntu but it is the default while *ttaenc* can be specified from a conf file. Now to fix a few bugs and then roll out 2.7.1 :)

---

### Post by andrew.46 on 2015-10-06
New version of abcde has been released as abcde version 2.7.1. The changelog shows:

```

----------
  * Rebuild of the abcde Makefile. Thanks to Reuben Thomas and Steve
    McIntyre as well as ReaperX7, bobzilla, 55020, GazL and dugan from
    the Slackware Forums. This closes Issue 4:
    http://abcde.einval.com/bugzilla/show_bug.cgi?id=4 
  * Fix incorrect use of 'break'. Thanks to Reuben Thomas for the
    bug report and fix which closes Issue 6:
    http://abcde.einval.com/bugzilla/show_bug.cgi?id=6
  * Make older versions of id3 happy when 'Genre' field is empty.
    Thanks to Martin Husemann for the fix which closes Issue 8:
    http://abcde.einval.com/bugzilla/show_bug.cgi?id=8
  * Add YEAR and GENRE variables to do_getalbumart(). Thanks to
    Johannes Gernemann for this patch which closes issue 9:
    http://abcde.einval.com/bugzilla/show_bug.cgi?id=9
  * Support added for encoding to True Audio using tta while still
    supporting the older ttaenc. Tagging is with mid3v2.
  * Support added for encoding to MPEG-1 Audio Layer II (mp2)
    with either twolame or FFmpeg / avconv. Tagging with mid3v2.
  * Encoding to WavPack with FFmpeg. Some slight changes to WavPack
    syntax with backward compatibility built in for abcde 2.7. 
  * Encoding to m4a container with FFmpeg or avconv. This allows
    for alac encoding with FFmpeg's reverse engineered alac encoder.
  * AAC encoding with fhgaacenc via Wine. Tagging is provided
    by AtomicParsley which has been added back to abcde :). This
    allows encoding with HE-AAC v2, unavailable with qaac.
  * Support added for AAC encoding with qaac via Wine. This
    also allows for Apple Lossless Audio Coding (alac) using
    either qaac or refalac. This closes Issue 142, thanks to
    Bernd Fischer-Krellenberg for the enhancement request.
  * Grab year information too when using musicbrainz. Thanks to
    Marco Hoppstaedter for the patch. Closes issue 10:
    http://abcde.einval.com/bugzilla/show_bug.cgi?id=10
----------

```

Official tarball and signature here:

[http://abcde.einval.com/download/abcde-2.7.1.tar.gz](http://abcde.einval.com/download/abcde-2.7.1.tar.gz)
[http://abcde.einval.com/download/abcde-2.7.1.tar.gz.sign](http://abcde.einval.com/download/abcde-2.7.1.tar.gz.sign)

Enjoy :)

---

### Post by shantiq on 2015-10-06
:KS very thorough on the codec palette now


for example:

```
abcde   -o tta   4
Executing customizable pre-read function... done.
Getting CD track info... Grabbing tracks: 04
---- Soft Machine / Third ----
Year: 1970
Genre: Progressive Rock
1: Facelift [Live, at two venues in England! Fairfield Hall, Croydon, 4 Jan 1970 and at Mother's Club, Birmingham 11 Jan 1970]
2: Slightly All the Time
3: Moon in June
4: Out-Bloody-Rageous
Locally cached CDDB entry found, use it [Y/n]? y
Using cached CDDB match...
Edit selected CDDB data [y/N]? n
Is the CD multi-artist [y/N]? n
Creating playlist...
Grabbing track 04: Out-Bloody-Rageous...
cdparanoia III release 10.2 (September 11, 2008)


Ripping from sector  253095 (track  4 [0:00.00])
      to sector  339753 (track  4 [19:15.33])


outputting to /home/shantiq/abcde.2811b204/track04.wav


 (== PROGRESS == [                ++ +   +      | 339753 00 ] == :^D * ==)   


Done.




 echo Encoding track 04 of 4: Out-Bloody-Rageous...
Encoding track 04 of 4: Out-Bloody-Rageous...
encodetrack-tta-04 nice -n 10 ttaenc -e /home/shantiq/abcde.2811b204/track04.wav -o /home/shantiq/abcde.2811b204/track04.tta
TTA1 lossless audio encoder/decoder, release 3.4.1
Copyright (c) 2007 Aleksander Djuric. All rights reserved.
For more information see http://tta.sourceforge.net
------------------------------------------------------------
File:    [track04.wav]
Encode:    complete, wrote 104774627 bytes, ratio: 0.51, time: 11
------------------------------------------------------------
Total:    [1/1, 99.9/194.4 Mb], ratio: 0.514, time: 0'11
------------------------------------------------------------


encodetrack-04 true
 echo Tagging track 04 of 4: Out-Bloody-Rageous...
Tagging track 04 of 4: Out-Bloody-Rageous...
tagtrack-tta-04 nice -n 10 mid3v2 --verbose -A Third -a Soft Machine -t Out-Bloody-Rageous -y 1970 -g Progressive Rock -T 04/4 --comment=abcde version 2.7.1 UNRELEASED /home/shantiq/abcde.2811b204/track04.tta
Writing /home/shantiq/abcde.2811b204/track04.tta
No ID3 header found; creating a new tag
tagtrack-04 true
movetrack-04 mv /home/shantiq/abcde.2811b204/track04.tta /home/shantiq//tta/Soft Machine-Third/04.Out-Bloody-Rageous.tta
movetrack-output-tta true
Finished.



```

---

### Post by andrew.46 on 2015-10-06
> **shantiq said:**
> :KS very thorough on the codec palette now

Indeed, I cannot think of any more codecs that could be added :)

---

### Post by shantiq on 2015-10-06
well and many thanx to you since you are responsible for the high-end m4a and tta and no cannot think of any sensible ones to add :]

---

### Post by andrew.46 on 2015-10-06
I am enjoying ripping all of my cds to alac using qaac + abcde. I use an undocumented post_encode function to embed the album art:

```

post_encode ()
{
ARTISTFILE="$(mungefilename "$TRACKARTIST")"
ALBUMFILE="$(mungefilename "$DALBUM")"

if [ "$VARIOUSARTISTS" = "y" ] ; then
FINDPATH="$(eval echo "$VAOUTPUTFORMAT")"
else
FINDPATH="$(eval echo "$OUTPUTFORMAT")"
fi

FINALDIR="$(dirname "$OUTPUTDIR/$FINDPATH")"
cd "$FINALDIR"

if [ -e "cover.jpg" ] ; then
for i in *.m4a
do
AtomicParsley "$i" --artwork cover.jpg --overWrite 
done
 	
rm cover.jpg
vecho "Your files have had the album art embedded..." >&2
else
vecho "No album art found so no image embedded..." >&2
fi
}

```

which is a simple variation on the documented version in the abcde faqs. Quality on my ipod classic is fantastic!!

---

### Post by emk on 2015-11-01
I am using abcde now for a while with my raspberry pi and like the new functionality a lot. For me, embedded images are a necessity nowadays; even having  a cover.jpg in the folder doesn't cut it in several cases. So, my long-term target is to use abcde where it shines:

[LIST]
[*]automated process
[*]several formats in one go
[*]embedded image art in all formats
[*]
[/LIST]

For this to work, I wanted an extended post_encode which embeds album art in **all** relevant formats - flac, mp3, m4a, opus. At the moment, I am content with flac and mp3, but getting multiple steps working in the post_encode doesn't work out with my limited scripting knowledge.

This is my post_encode function:

```
post_encode ()
{
ARTISTFILE="$(mungefilename "$TRACKARTIST")"
ALBUMFILE="$(mungefilename "$DALBUM")"

if [ "$VARIOUSARTISTS" = "y" ] ; then
FINDPATH="$(eval echo "$VAOUTPUTFORMAT")"
else
FINDPATH="$(eval echo "$OUTPUTFORMAT")"
fi

FINALDIR="$(dirname "$OUTPUTDIR/$FINDPATH")"
cd "$FINALDIR"

if [[ "$OUTPUTTYPE" == *"mp3"* ]] && [ "$TAGGER" = "$EYED3" ] ; then
vecho "Preparing to embed the album art..." >&2
else
vecho "Not embedding album art, you need mp3 output and eyeD3 tagging..." >&2
return 1
fi

if [ -e "cover.jpg" ] ; then
for i in *.mp3
do
eyeD3 --add-image cover.jpg:FRONT_COVER "$i"
done

if [[ "$OUTPUTTYPE" == *"flac"* ]] ; then
vecho "Preparing to embed the album art..." >&2
else
vecho "Not embedding album art, you need flac output.." >&2
return 1
fi

if [ -e "cover.jpg" ] ; then
for i in *.flac
do
metaflac --import-picture-from=cover.jpg "$i"
done

mkdir backup
mv cover.jpg backup
vecho "Your files have had the album art embedded..." >&2
else
vecho "No album art found so no image embedded..." >&2
fi
}

```

And this are the complaints of abcde:
```
pi@EMK-RPi2B ~ $ abcde
/etc/abcde.conf: Zeile 512: Syntaxfehler beim unerwarteten Wort `}'
/etc/abcde.conf: Zeile 512: `}'
^[Grabbing entire CD - tracks01 02 03 04 05 06 07 08 09 10 11 12 13 14 15
```
What did I do wrong here? There is only a matching {} pair in there...

PS: If you have already found an easy way to embed art into opus, I am all ears.

---

### Post by andrew.46 on 2015-11-02
Hi emk :). This is an issue I have been picking away at for the last little while with no solution yet. I received an email recently with a similar issue, not you?

---

### Post by emk on 2015-11-02
Not me. I mailed you some time ago, but only for feedback that your NeroAACTag example is x86 only and on ARM one can use AtomicParsley to tag.

In the meantime, however, I have a **working** hack:

```
post_encode ()
{
ARTISTFILE="$(mungefilename "$TRACKARTIST")"
ALBUMFILE="$(mungefilename "$DALBUM")"

if [ "$VARIOUSARTISTS" = "y" ] ; then
FINDPATH="$(eval echo "$VAOUTPUTFORMAT")"
else
FINDPATH="$(eval echo "$OUTPUTFORMAT")"
fi

FINALDIR="$(dirname "$OUTPUTDIR/$FINDPATH")"
cd "$FINALDIR"

if [[ "$OUTPUTTYPE" == *"mp3"* ]] && [ "$TAGGER" = "$EYED3" ] ; then
vecho "Preparing to embed the album art..." >&2
else
vecho "Not embedding album art, you need mp3 output and eyeD3 tagging..." >&2
return 1
fi

if [ -e "cover.jpg" ] ; then
for i in *.mp3
do
eyeD3 --add-image cover.jpg:FRONT_COVER "$i"
done

if [[ "$OUTPUTTYPE" == *"flac"* ]] ; then
vecho "Preparing to embed the album art..." >&2
else
vecho "Not embedding album art, you need flac output.." >&2
return 1
fi

if [ -e "cover.jpg" ] ; then
for i in *.flac
do
metaflac --import-picture-from=cover.jpg "$i"
done

mkdir backup
mv cover.jpg backup
vecho "Your files have had the album art embedded..." >&2
else
vecho "No album art found so no image embedded..." >&2
fi
}
```

The only difference was a forgotten fi in the first version. Sometimes you are so close...

This is able to tag with album art for flac and mp3 in one go. I tried yesterday; apart from one complaint about the end about a missing FLAC file (not really), it worked. Now I only need to add the m4a tagging, and then maybe opus. You can tag opus with kid3-cli, but this looks like overkill to me. Do you know of any other tagger for opus?

---

### Post by emk on 2015-11-03
Also, one other thing: Having now done several discs, I noticed that cdparanoia is not up to par on borderline discs. I get a flood of annoying SCSI errors which can also bring the abcde script to a halt.

A freshly compiled [cdda2wav ]("http://sourceforge.net/projects/schilytools/")(the original, not the Debian icedax crap) is much better than cdparanoia.

The options I found for general use ```
CDDA2WAVOPTS="-vall cddb=0 speed=4 -paranoia paraopts=proof -B"
``` unfortunately break the script.

Any advice?

---

### Post by andrew.46 on 2015-11-04
I have not used cdda2wav with abcde all that much but I agree *completely *with your thoughts on cdparanoia! Which is why a while ago I added support to abcde for ripping with the GNU Compact Disc Input and Control library (libcdio). Works very nicely on my system and I am a little miffed that nobody but myself seems to be using it :).

I am not sure of the correct ubuntu package to download (I am between Ubuntu installations at the moment) but the conf file should contain:

```

CDROMREADERSYNTAX=libcdio       
CD_PARANOIA=cd-paranoia  
CDPARANOIAOPTS=""

```

CDPARANOIAOPTS are exactly the same as standard cdparanoia options.This requires abcde 2.7 and higher. I would be curious to know if this resolves your issue with your difficult discs...

**Edit:** I suspect this is the ubuntu package:

```

sudo apt-get install  libcdio-utils

```

---

### Post by speartip on 2015-11-04
Hi Andrew.
I appreciate your hard work with this. At present I am ripping some of my CD collection to opus vbr 192, using abcde & the .conf file you have provided in your link.
Just a quick question though.
Is there any advantage or quality gain by ripping this way, as opposed to using a gui app such as asunder?

---

### Post by andrew.46 on 2015-11-04
> **speartip said:**
> Is there any advantage or quality gain by ripping this way, as opposed to using a gui app such as asunder?

There is absolutely no quality gain in using abcde over asunder, they are both different methods to obtain the same result :). The advantage with abcde is that there is vastly more tinkering available to the end user, either through manipulating countless variable via commandline or conf file as well as directly editing the abcde script itself. It is simply a massive shell script so anybody can have a go!

---

### Post by andrew.46 on 2015-11-04
I have updated my website abcde guide for abcde 2.7.1 with a 'combo' file that now encodes to 10 different formats at the same time. How cool is that :)

---

### Post by emk on 2015-11-05
> **andrew.46 said:**
> I have not used cdda2wav with abcde all that much but I agree *completely *with your thoughts on cdparanoia! Which is why a while ago I added support to abcde for ripping with the GNU Compact Disc Input and Control library (libcdio). Works very nicely on my system and I am a little miffed that nobody but myself seems to be using it :).

I am not sure of the correct ubuntu package to download (I am between Ubuntu installations at the moment) but the conf file should contain:

```

CDROMREADERSYNTAX=libcdio       
CD_PARANOIA=cd-paranoia  
CDPARANOIAOPTS=""

```

CDPARANOIAOPTS are exactly the same as standard cdparanoia options.This requires abcde 2.7 and higher. I would be curious to know if this resolves your issue with your difficult discs...

**Edit:** I suspect this is the ubuntu package:

```

sudo apt-get install  libcdio-utils

```
You are right, libcdio is a complete unknown for me and probably all others. I'll give it a try. When you say that CDPARANOIAOPTS are the same, this means that your proposed
```
CDPARANOIAOPTS="--never-skip=40"
```just stays?


The 10 formats you encode in are impressive - which ones do you really use? I suspect that you could catch 99.9% of all use cases with flac, mp3, m4a and opus.

---

### Post by andrew.46 on 2015-11-05
Yes that option should work fine. My own usage is to:

[LIST=1]
[*]Use MusicBrainz for meta tags
[*]Rip with libcdio's cd-paranoia
[*]Encode to alac using qaac and wine
[*]Grab the album art using getalbumart 
[*]Embed the image with an AtomicParsley post_encode function
[*]Load to my iPOD classic with GTKPod
[*]Enjoy the music :)
[*]
[/LIST]

I have found better results using *cd-paranoia* rather than *cdparanoia*, I would be interested to see if you have the same experience?

---

### Post by emk on 2015-11-06
> **andrew.46 said:**
> Encode to alac using qaac and wine
Is there a reason for this combination? I would have leaned towards ffmpeg for this purpose.

---

### Post by andrew.46 on 2015-11-06
> **emk said:**
> Is there a reason for this combination? I would have leaned towards ffmpeg for this purpose.

The only reason really is that I added qaac + wine to abcde before I added FFmpeg and thus became accustomed to this workflow :). Sound is no doubt exactly the same...

---

### Post by andrew.46 on 2015-12-15
I have set myself a goal of a dozen fixes to abcde before the release of abcde 2.7.1 with [a few committed already]("http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=blob;f=changelog;h=6f074fa9703679ed1db185ca6b956cca56b3c47e;hb=c024365a846faae390f23c86f32235d6209e6edf") and some more underway. Are there any annoying bugs or wishlist items that can be added to this list?

I have run out of audio codecs to add which is a little disappointing :(

---

### Post by mc4man on 2015-12-15
Well I was just thinking about something, however it begs the question - 
Is there a cli for abcde that would say > rip the whole cd & use this specific .conf, ie. can abcde be pointed one .conf out of several

---

### Post by andrew.46 on 2015-12-16
> **mc4man said:**
> Well I was just thinking about something, however it begs the question - 
Is there a cli for abcde that would say > rip the whole cd & use this specific .conf, ie. can abcde be pointed one .conf out of several

In fact this is my model for testing abcde :). The option is *-c path_to_conf_file* and I have a plethora of conf files that I run through after major changes, usually also using the little known *-z* option which uses only a small fraction of each track...

---

### Post by FakeOutdoorsman on 2015-12-16
> **andrew.46 said:**
> I have run out of audio codecs to add which is a little disappointing :(

The native FFmpeg AAC encoder is now considered stable (at least for CBR) and no longer needs "-strict experimental"/"-strict -2". However, a few crashes have been found since, and if you find any bugs I'd be interested to hear about them.

---

### Post by andrew.46 on 2015-12-16
> **FakeOutdoorsman said:**
> The native FFmpeg AAC encoder is now considered stable (at least for CBR) and no longer needs "-strict experimental"/"-strict -2". However, a few crashes have been found since, and if you find any bugs I'd be interested to hear about them.

To tell the truth I have made the FFmpeg syntax pretty flexible so version 2.7.1 should already be able to use the FFmpeg native aac *without modification*. Something like the following:

```

AACENCODERSYNTAX=ffmpeg
FFMPEG=ffmpeg
FFMPEGENCOPTS="-c:a aac -b:a 160k"
OUTPUTTYPE="m4a"

```

I cannot test this at the moment as I am at work using Windows 8.1, sigh..... Great news that the FFmpeg aac encoder is almost there, if it works well enough with abcde I can certainly add it into the docs.

---

### Post by shantiq on 2015-12-16
good news Andrew


ok and tested ffmpeg aac


works ace
they ask you to add

FFMPEGENCOPTS="-c:a aac -b:a 320k [COLOR=#800000]-strict -2[/COLOR]"      to the line as experimental

otherwise smooth


PS:   maybe time you designed a new codec since ran out of them :]

---

### Post by mc4man on 2015-12-16
> **andrew.46 said:**
> In fact this is my model for testing abcde :). The option is *-c path_to_conf_file* and I have a plethora of conf files that I run through after major changes, usually also using the little known *-z* option which uses only a small fraction of each track...
Cool, I think I'll make myself a little .desktop for abcde with quicklist options for various conf's. 
If ever inclined to zip up & post a collection of conf's please do
(- wouldn't mind including a bunch in a 'Tools' folder or such.

---

### Post by andrew.46 on 2015-12-16
Thanks for the heads-up Fakeoutdoorsman, the aac encoder sounds pretty reasonable and certainly works in well enough with abcde 2.7.1. I encoded Pink Floyd's 'Meddle' and I am just now listening to Echoes......

I will experiment a little over the next week or so, it is very exciting that there is another contender in the now quite crowded aac encoder marketplace :)

---

### Post by andrew.46 on 2015-12-16
> **mc4man said:**
> Cool, I think I'll make myself a little .desktop for abcde with quicklist options for various conf's. 
If ever inclined to zip up & post a collection of conf's please do
(- wouldn't mind including a bunch in a 'Tools' folder or such.

Feel free to take the ones on my website, the ones I am using at home are substantially less tidy!

---

### Post by andrew.46 on 2015-12-24
> **FakeOutdoorsman said:**
> The native FFmpeg AAC encoder is now considered stable....

I was idly wondering what the status was of the native FFmpeg flac encoder? I guess in comparison with the flac encoder; not a lot of information out there... Certainly abcde uses the Xiph flac but it would be possible to use FFmpeg's encoder if it was at all worthwhile.

---

### Post by FakeOutdoorsman on 2015-12-24
[libavformat/flacenc.c gets some attention once in a while]("http://git.videolan.org/?p=ffmpeg.git;a=history;f=libavcodec/flacenc.c"), but I haven't heard any recent discussions about it. There may be some [flac related bug reports]("https://trac.ffmpeg.org/query?status=!closed&keywords=~flac") which may be worth looking at.

I guess you could compare encoding time between FFflacenc and Xiph flac. Perhaps they differ in default compression level. Either way, the resulting outputs should output the same data:
```
ffmpeg -i input ffout.flac
ffmpeg -loglevel error -i input -map 0:a -f md5 -
ffmpeg -loglevel error -i ffout.flac -map 0:a -f md5 -
ffmpeg -loglevel error -i xiphout.flac -map 0:a -f md5 -

```

---

### Post by andrew.46 on 2016-01-01
I have not implemented the FFmpeg native flac encoder yet but encoding to Matroska with abcde and FFmpeg is [now in place]("http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=commit;h=777e6fff499df63df9a65ac72eb1ce006b3f1905"):

```

andrew@ilium~/development/abcde$ git log -n 1
commit 777e6fff499df63df9a65ac72eb1ce006b3f1905
Author: Andrew Strong <andrew.xxxxxxxxxxxx@gmail.com>
Date:   Fri Jan 1 16:42:49 2016 +1100

    Support usage of Matroska container (mka)
    
    Support is added for output to the Matroska container (mka). The
    encoder/muxer is FFmpeg (or avconv). Typical ~/.abcde.conf file
    syntax would be:
    
     MKAENCODERSYNTAX=ffmpeg
     FFMPEG=ffmpeg
     FFMPEGENCOPTS="-c:a ac3 -b:a 448k"
     OUTPUTTYPE="mka"
    
    Thanks to Shantiq and Fakeoutdoorsman of the Ubuntu Forums
    for the idea!
andrew@ilium~/development/abcde$ 

```

Any testing would be gratefully received...

---

### Post by shantiq on 2016-01-01
yeaa and thank you


```
abcde -o mka 2
Executing customizable pre-read function... done.
Getting CD track info... Grabbing tracks: 02
Checking CDDB server status...
Querying the CDDB server...
Obtaining CDDB results...
Retrieving 1 CDDB match...done.
---- Robert Coyne with Jaki Liebezeit / The Obscure Department ----
1: Signature Song
2: Delicate Flower
3: Dove Of Peace
4: The Wonder Of Me
5: Why Would I Remeber You
6: Interlude
7: 21st Century Magic
8: White Residue
9: Masterclass
10: Laugh Now
11: Coda
12: The Obscure Department

Edit selected CDDB data [y/N]? n
Is the CD multi-artist [y/N]? n
Creating playlist...
Grabbing track 02: Delicate Flower...
cdparanoia III release 10.2 (September 11, 2008)

Ripping from sector   24712 (track  2 [0:00.00])
      to sector   37231 (track  2 [2:46.69])

outputting to /home/shantiq/abcde.9509430c/track02.wav

 (== PROGRESS == [                              | 037231 00 ] == :^D * ==)   

Done.


 echo Encoding track 02 of 12: Delicate Flower...
Encoding track 02 of 12: Delicate Flower...
encodetrack-mka-02 nice -n 10 ffmpeg -i /home/shantiq/abcde.9509430c/track02.wav -c:a ac3 -b:a 448k -metadata artist=Robert Coyne with Jaki Liebezeit -metadata album=The Obscure Department -metadata title=Delicate Flower -metadata track=02 -metadata date=2013 -metadata genre=Pop-Folk -metadata comment=abcde version 2.7.1 /home/shantiq/abcde.9509430c/track02.mka
ffmpeg version N-76944-g15206ff Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libdcadec --enable-libfreetype --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvo-aacenc --enable-libvidstab
  libavutil      55.  9.100 / 55.  9.100
  libavcodec     57. 16.101 / 57. 16.101
  libavformat    57. 19.100 / 57. 19.100
  libavdevice    57.  0.100 / 57.  0.100
  libavfilter     6. 17.100 /  6. 17.100
  libavresample   3.  0.  0 /  3.  0.  0
  libswscale      4.  0.100 /  4.  0.100
  libswresample   2.  0.101 /  2.  0.101
  libpostproc    54.  0.100 / 54.  0.100
Guessed Channel Layout for  Input Stream #0.0 : stereo
Input #0, wav, from '/home/shantiq/abcde.9509430c/track02.wav':
  Duration: 00:02:46.93, bitrate: 1411 kb/s
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 44100 Hz, 2 channels, s16, 1411 kb/s
Output #0, matroska, to '/home/shantiq/abcde.9509430c/track02.mka':
  Metadata:
    artist          : Robert Coyne with Jaki Liebezeit
    album           : The Obscure Department
    title           : Delicate Flower
    PART_NUMBER     : 02
    date            : 2013
    genre           : Pop-Folk
    comment         : abcde version 2.7.1
    encoder         : Lavf57.19.100
    Stream #0:0: Audio: ac3 ([0] [0][0] / 0x2000), 44100 Hz, stereo, fltp, 448 kb/s
    Metadata:
      encoder         : Lavc57.16.101 ac3
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le (native) -> ac3 (native))
Press [q] to stop, [?] for help
size=    9164kB time=00:02:46.93 bitrate= 449.7kbits/s    
video:0kB audio:9130kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.374279%
encodetrack-02 true
 echo Tagging track 02 of 12: Delicate Flower...
Tagging track 02 of 12: Delicate Flower...
tagtrack-mka-02 true
tagtrack-02 true
movetrack-02 mv /home/shantiq/abcde.9509430c/track02.mka /media/extradrive/home/shantiq/La.Musica/mka/Robert Coyne with Jaki Liebezeit-The Obscure Department/02.Delicate Flower.mka
movetrack-output-mka true
Finished.


```

---

### Post by andrew.46 on 2016-01-01
> **shantiq said:**
> yeaa and thank you

Pretty cool?!! Thanks for testing Shan :)

---

### Post by andrew.46 on 2016-01-01
I place my '11 format combo' ~/.abcde.conf file here:

```

# -----------------$HOME/.abcde.conf----------------- #
# 
#  A sample configuration file to convert music cds to 
#  MP3, Ogg Vorbis, FLAC, Musepack, AAC, WavPack, Opus,
#  Monkey's Audio (ape), True Audio, mp2 and ac3 at the
#  same time! Using abcde version 2.7.2-UNRELEASED...
#           
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Encode tracks immediately after reading. Saves disk space, gives
# better reading of 'scratchy' disks and better troubleshooting of
# encoding process but slows the operation of abcde quite a bit:
LOWDISK=y

# Specify the method to use to retrieve the track information,
# the alternative is to specify 'cddb':
CDDBMETHOD=musicbrainz

# Make a local cache of cddb entries and then volunteer to use 
# these entries when and if they match the cd:
CDDBCOPYLOCAL="y"
CDDBLOCALDIR="$HOME/.cddb"
CDDBLOCALRECURSIVE="y"
CDDBUSELOCAL="y"

OGGENCODERSYNTAX=oggenc                   # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                     # Specify encoder for MP3
FLACENCODERSYNTAX=flac                    # Specify encoder for FLAC
MPCENCODERSYNTAX=mpcenc                   # Specify encoder for Musepack
AACENCODERSYNTAX=fdkaac                   # Specify encoder for AAC
OPUSENCODERSYNTAX=opusenc                 # Specify encoder for Opus
WVENCODERSYNTAX=wavpack                   # Specify encoder for Wavpack
APENCODERSYNTAX=mac                       # Specify encoder for Monkey's Audio
TTAENCODERSYNTAX=tta                      # Specify encoder for True Audio
MP2ENCODERSYNTAX=twolame                  # Specify encoder for MP2
MKAENCODERSYNTAX=ffmpeg                   # Specify encoder for MKA/ac3

OGGENC=oggenc                             # Path to Ogg Vorbis encoder
LAME=lame                                 # Path to MP3 encoder
FLAC=flac                                 # Path to FLAC encoder
MPCENC=mpcenc                             # Path to Musepack encoder
FDKAAC=fdkaac                             # Path to the AAC encoder
OPUSENC=opusenc                           # Path to Opus encoder
WVENC=wavpack                             # Path to WavPack encoder
APENC=mac                                 # Path to Monkey's Audio encoder
TTA=tta                                   # Path to True Audio encoder
TWOLAME=twolame                           # Path to MP2 encoder
FFMPEG=ffmpeg                             # Path to FFmpeg encoder

OGGENCOPTS='-q 6'                         # Options for Ogg Vorbis
LAMEOPTS='-V 2'                           # Options for MP3 
FLACOPTS='-s -e -V -8'                    # Options for FLAC
MPCENCOPTS='--extreme'                    # Options for Musepack
FDKAACENCOPTS='-p 2 -m 5 -a 1'            # Options for fdkaac
OPUSENCOPTS="--vbr --bitrate 128"         # Options for Opus
WVENCOPTS="-hx3"                          # Options for WavPack
APENCOPTS="-c4000"                        # Options for Monkey's Audio
TTAENCOPTS=""                             # Options for True Audio
TWOLAMENCOPTS="--bitrate 320"             # Options for MP2
FFMPEGENCOPTS="-c:a ac3 -b:a 448k"        # Options for FFmpeg/ac3
 
OUTPUTTYPE="ogg,mp3,flac,mpc,m4a,opus,wv,ape,tta,mp2,mka"  # Encode to 11 formats!

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac. New to abcde 2.7 is 'libcdio'.
CDROMREADERSYNTAX=libcdio       
CD_PARANOIA=cd-paranoia  
CDPARANOIAOPTS="--never-skip=40 --verbose"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/Music"               

# The default actions that abcde will take.
ACTIONS=cddb,getalbumart,playlist,read,encode,tag,move,clean

# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# This function takes out dots preceding the album name, and removes a grab
# bag of illegal characters. It allows spaces, if you do not wish spaces add
# in -e 's/ /_/g' after the first sed command.
mungefilename ()
{
  echo "$@" | sed -e 's/^\.*//' | tr -d ":><|*/\"'?[:cntrl:]"
}

MAXPROCS=2                                # Run a few encoders simultaneously
PADTRACKS=y                               # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=2                            # Useful for debugging
COMMENT='abcde version 2.7.2-UNRELEASED'  # Place a comment...
EJECTCD=y                                 # Please eject cd when finished :-)

```

It uses libcdio which perhaps some are not all that familiar with but this is a better choice than the usual cdparanoia...

---

### Post by shantiq on 2016-01-02
Congratulations: you now have a ripping Swiss knife :]

---

### Post by speartip on 2016-02-06
After a fresh install, I am now getting the following error when running abcde:
```
 $ abcde
Executing customizable pre-read function... done.
Getting CD track info... Can't locate MusicBrainz/DiscID.pm in @INC (you may need to install the MusicBrainz::DiscID module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/bin/abcde-musicbrainz-tool line 18.
BEGIN failed--compilation aborted at /usr/bin/abcde-musicbrainz-tool line 18.
[ERROR] abcde: CD could not be read. Perhaps there's no CD in the drive?

```
I have libmusicbrainz-5.0 installed.
Any ideas?

---

### Post by shantiq on 2016-02-06
speartip does it absolutely for you has to be musicbrainz

maybe that is what you wish for


but what happens if you   go for CDDB instead in your .abcde.conf

```
# Specify the method to use to retrieve the track information,
# the alternative is to specify 'cddb':
**CDDBMETHOD=cddb**

# Make a local cache of cddb entries and then volunteer to use 
# these entries when and if they match the cd:
CDDBCOPYLOCAL="y"
CDDBLOCALDIR="$HOME/.cddb"
CDDBLOCALRECURSIVE="y"
CDDBUSELOCAL="y"
```

on musicbrainz if the disc has **not** been entered in the database it throws **all kinds of error messages**; used to use it with a different ripper [Morituri]and then stopped because of that


see if I run [B]CDDBMETHOD=musicbrainz
[/B]
i get the same as you

```
shantiq@shantiq-00000000000000000000000:~$ abcde -o mka 4
Executing customizable pre-read function... done.
Getting CD track info... Can't locate MusicBrainz/DiscID.pm in @INC (you may need to install the MusicBrainz::DiscID module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/bin/abcde-musicbrainz-tool line 18.
BEGIN failed--compilation aborted at /usr/bin/abcde-musicbrainz-tool line 18.
[ERROR] abcde: CD could not be read. Perhaps there's no CD in the drive?
shantiq@shantiq-00000000000000000000000:~$ abcde -o mka 4
Executing customizable pre-read function... done.
Getting CD track info... Grabbing tracks: 04
---- Jenny Lee / Right On! ----
Year: 2015
Genre: 
1: Blind
2: Boom Boom
3: Never
4: Long Lonely Winter
5: Bully
6: Riot
7: He Fresh
8: Offerings
9: White Devil
10: Real Life
Locally cached CDDB entry found, use it [Y/n]? 


```


but then i change it back to [B]CDDBMETHOD=cddb
[/B]and all good;  hey maybe you only want musicbrainz
and i am not helping ...

---

### Post by speartip on 2016-02-06
That's done the trick. Thanks Shantiq.

---

### Post by andrew.46 on 2016-02-06
Hmmm... I wonder if you are both missing the needed perl libraries? At the least you need *perl-MusicBrainz-DiscID *and *perl-WebService-MusicBrainz*, hopefully the Ubuntu repositories will drag the other needed perl libraries in when you install these 2...

---

### Post by shantiq on 2016-02-07
Thanx Andrew for info

```
 sudo apt-get install libmusicbrainz-discid-perl libwebservice-musicbrainz-perl
```


reestablishes musicbrainz albeit with a message about pragma but all good


```
shantiq@shantiq-00000000000000000000000:~$ abcde -o mka 4
Executing customizable pre-read function... done.
Getting CD track info... [COLOR=#800000]Use of the encoding pragma is deprecated at /usr/bin/abcde-musicbrainz-tool line 15[/COLOR].
Grabbing tracks: 04
abcde: attempting to resume from /home/shantiq/abcde.djqd6Qt3i76.jlHHbRGr67gs3P8-..
Selected: #1
---- 'right on!'    [from jennylee] ----
1: blind
2: boom boom
3: never
4: long lonely winter
5: bully
6: riot
7: he fresh
8: offerings
9: white devil
10: real life
Edit selected CDDB data [y/N]? n
Is the CD multi-artist [y/N]? n
Creating playlist...
Grabbing track 04: long lonely winter...
cdparanoia III release 10.2 (September 11, 2008)

Ripping from sector   48874 (track  4 [0:00.00])
      to sector   68179 (track  4 [4:17.30])

outputting to /home/shantiq/abcde.djqd6Qt3i76.jlHHbRGr67gs3P8-/track04.wav

 (== PROGRESS == [                              | 068179 00 ] == :^D * ==)   

Done.



```

---

### Post by speartip on 2016-02-07
> **andrew.46 said:**
> Hmmm... I wonder if you are both missing the needed perl libraries? At the least you need *perl-MusicBrainz-DiscID *and *perl-WebService-MusicBrainz*, hopefully the Ubuntu repositories will drag the other needed perl libraries in when you install these 2...

That was the issue. This is actually a Mint install, & unlike Ubuntu those 2 dependencies don't seem to be pulled in when abcde is installed.

Andrew... Seem to be getting great results with the fdkaac codec using your script. the only tweak I make is "FDKAACENCOPTS='-p 2 -b 320 -a 1'" . Might be a bit overkill, but sounds good. Keep up the good work. Much appreciated.

---

### Post by andrew.46 on 2016-02-07
Good to hear that abcde still has some keen users :). I confess that I now have abcde pretty much as I would want so the need to hack at it more has died away a little.

I am not sure what the 'pragma' message is about although a casual google seems to suggest that it is reasonable widespread. musicbrainz is Steve's baby so I will leave that one to him...

---

### Post by speartip on 2016-02-10
Was wondering if someone would be kind enough to help me here.
I was interested in trying out the aoTuV encoder mentioned on the abcde web page, from here:
[http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/)
I extracted the source code to a folder in my home directory.
Ran the commands ./configure, make, make install.
Seemed to install ok. Terminal never threw out any errors.
How do I now get Andrews abcde ogg script to use the new encoder? Or will it do it automatically?

---

### Post by mc4man on 2016-02-12
> **speartip said:**
> Was wondering if someone would be kind enough to help me here.
I was interested in trying out the aoTuV encoder mentioned on the abcde web page, from here:
[http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/)
I extracted the source code to a folder in my home directory.
Ran the commands ./configure, make, make install.
Seemed to install ok. Terminal never threw out any errors.
How do I now get Andrews abcde ogg script to use the new encoder? Or will it do it automatically?
Not sure that there is much advantage as aotuv changes have been added to libvorbis (though maybe not completely prior to 1.34, 14.04 uses 1.32, 16.04 will have 1.35 which can be used in 14.04 if desired.

Anyway abcde uses oggenc so check which libvorbisenc.so.2 oggenc is using with - 

```
ldd /usr/bin/oggenc
```

If not the .so you built & installed then run this & recheck
sudo ldconfig
(- in long run if on 14.04 better to replace the 3-5 libvorbis packages then using make install libs

---

### Post by speartip on 2016-02-12
Thanks mc4man.
The package installed on my system is libvorbisenc-1.3.4.
So I take it there is no advantage in using aoTuV codec then?
ldd /usr/bin/oggenc, returns:
```
linux-vdso.so.1 =>  (0x00007ffd333f1000)
    libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f189de4a000)
    libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f189dc1a000)
    libFLAC.so.8 => /usr/lib/x86_64-linux-gnu/libFLAC.so.8 (0x00007f189d9e8000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f189d6e2000)
    libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f189d4d9000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f189d113000)
    /lib64/ld-linux-x86-64.so.2 (0x0000558b40f95000)

```

---

### Post by mc4man on 2016-02-12
> **speartip said:**
> Thanks mc4man.
The package installed on my system is libvorbisenc-1.3.4.
So I take it there is no advantage in using aoTuV codec then?

I don't think so, if you read that aotuv page you linked you'll see that the  sound quality changes where put in libvorbis 1.3.2, since then just a few bug fixes thru last 2 betas that are in  vorbis 1.3.4 & 1.3.5 respectively 

In any event you're currently using the repo libvorbis from either 15.04 or 15.10 not anything you built.

---

### Post by mc4man on 2016-02-15
This could be a one off case but anyway - 
I wanted a sample of gapless so decided to use abcde to rip Dark side of the Moon. Musicbrainz would have track 1 @ 
1: Speak to Me / Breathe
Seeing as though / aren't allowed in filenames abcde names it (ex. opus
```
01.Speak to Me  Breathe.opus
```
The .m3u list it as - 
```
01.Speak to Me Breathe.opus
```
So the filename has a double space but the m3u only a single

(rubyripper used to do this as - 01.Speak to Me (Breathe In The Air).ext ..? (edit - this is what cddb would use, ie. #2 option

---

### Post by andrew.46 on 2016-03-05
Any Ubuntu users still using faac with abcde might be interested in this fix on askubuntu:

How can I rebuild the faac package to get mp4/m4a support and higher bitrates?
[http://askubuntu.com/q/739686/57576](http://askubuntu.com/q/739686/57576)

Feel free to criticise this technique on that thread and vote it up so I can achieve world domination through askubuntu :)

---

### Post by andrew.46 on 2016-04-06
abcde 2.7.2 has been released with a quite reasonable changelog:

```

abcde 2.7.2

  * When using musicbrainz, don't assume that there will be release
    events attached to a particular CD release. Bug fix for the addition
    of year information support in 2.7.1. Thanks to Ed Oehler and Alan W.
    Kerr for debugging help.
  * Support for output to the Matroska container (mka). Encoder
    is FFmpeg (or avconv). Typical conf file syntax would be:

     MKAENCODERSYNTAX=ffmpeg
     FFMPEG=ffmpeg
     FFMPEGENCOPTS="-c:a ac3 -b:a 448k"
     OUTPUTTYPE="mka"

    Thanks to Shantiq and Fakeoutdoorsman of the Ubuntu Forums
    for the idea.
  * Add id3tag mp3 tagger as this is the tagger available to
    OpenBSD users. Thanks to Christopher Zimmermann for the
    notification and patch.
  * Allow for cddb response 500. Thanks again to Von Welch for the
    bug report and patch. This closes Issue 26:
    http://abcde.einval.com/bugzilla/show_bug.cgi?id=26
  * Fix for 'expansion of $REDIR' bug on MacOSX. Thanks to Von Welch
    for the bug report. This closes Issue 22:
    http://abcde.einval.com/bugzilla/show_bug.cgi?id=22
  * Makefile adjusted to allow the sample abcde.conf file to be
    installed by default to /etc rather than $(prefix)/etc.
    Thanks to Volker Schmidt from archlinux for the bug report:
    https://bugs.archlinux.org/task/46671
  * Allow getalbumart to correctly place cover image when single
    track is selected. Thanks to Nino Burini for the bug report
    and also the fix. This closes Issue 25:
    http://abcde.einval.com/bugzilla/show_bug.cgi?id=25

```

Two big fixes were for musicbrainz and the final fix for the REDIR bug for MacOSX which was a bug reintroduced by myself :(. The joys of tinkering with a shell script of that size!!

---

### Post by Yellow Pasque on 2016-04-06
> **andrew.46 said:**
> Any Ubuntu users still using faac with abcde might be interested in this fix on askubuntu:
Feel free to criticise this technique on that thread and vote it up so I can achieve world domination through askubuntu :)

Wouldn't a PPA be a better solution? Also, I think (not sure) Ubuntu comes without source repos enabled by default, which is needed for apt-get build-dep to work correctly.

---

### Post by andrew.46 on 2016-04-06
> **Temüjin said:**
> Wouldn't a PPA be a better solution? 

Against the tide of popular opinion I am not so keen on PPAs...

> Also, I think (not sure) Ubuntu comes without source repos enabled by default, which is needed for apt-get build-dep to work correctly.

I suspect you are right there, I shall add to the mini-guide....

---

### Post by mc4man on 2016-04-11
A couple of things - 
The instructs on Ac web page for qaac seem to presume user has wine installed **&** configured. That obviously wouldn't be the case if one was doing (installing wine) just for this. So to note that .wine  isn't created by the wine install, users need to 1st run - 
winecfg

Here the posted for loop on flac, (command of qaac), does not work  with the alias, the script needs the full path for qaac
(at least in the case of the for loop command being a script in $PATH

---

### Post by andrew.46 on 2016-04-12
> **mc4man said:**
> A couple of things - The instructs on Ac web page for qaac seem to presume user has wine installed **&** configured. That obviously wouldn't be the case if one was doing (installing wine) just for this. So to note that .wine  isn't created by the wine install, users need to 1st run - 
winecfg

Good point, I shall add that in...

> Here the posted for loop on flac, (command of qaac), does not work  with the alias, the script needs the full path for qaac
(at least in the case of the for loop command being a script in $PATH

I have always meant to add in the loop I use with qaac for embedding albumart It uses [a newer version of AtomicParsley]("https://bitbucket.org/wez/atomicparsley") which gets around an earlier issue with abcde where inline tags failed:

```

# Post encode function to embed album art when using qaac:

post_encode ()
{
ARTISTFILE="$(mungefilename "$TRACKARTIST")"
ALBUMFILE="$(mungefilename "$DALBUM")"

if [ "$VARIOUSARTISTS" = "y" ] ; then
FINDPATH="$(eval echo "$VAOUTPUTFORMAT")"
else
FINDPATH="$(eval echo "$OUTPUTFORMAT")"
fi

FINALDIR="$(dirname "$OUTPUTDIR/$FINDPATH")"
cd "$FINALDIR"

if [ -e "cover.jpg" ] ; then
for i in *.m4a
do
AtomicParsley "$i" --artwork cover.jpg --overWrite 
done
 	
rm cover.jpg
vecho "Your files have had the album art embedded..." >&2
else
vecho "No album art found so no image embedded..." >&2
fi
}


```

---

### Post by mc4man on 2016-04-12
> **andrew.46 said:**
> Good point, I shall add that in...



I have always meant to add in the loop I use with qaac for embedding albumart It uses [a newer version of AtomicParsley]("https://bitbucket.org/wez/atomicparsley") which gets around an earlier issue with abcde where inline tags failed:


This was more for my current method born from needing to lighten my possessions so will have to leave my 100's of cd's behind or elsewhere.
So basically ripping to flac only & storing on ext. ssd's 
For use in the auto & portable devices qaac (aac/m4a) seems best, just maxing as space isn't an issue. 
(-got a bunch of these [tiny drives]("http://www.amazon.com/Kingston-Digital-Ultra-Compact-DTMC3-32GB/dp/B00ZRHX7GK"), ea. can hold 120 or so albums on the 16GB ones, they fit nice on a little metal ring.

So for whatever reason when the 4 loop is called from a script the qaac command is not found (qaac works fine from a terminal
So just a altered a bit to suit & work - 
```
#!/bin/bash
for f in *.flac; do
   title=$(metaflac --show-tag=title "$f" | cut -d '=' -f 2)
   artist=$(metaflac --show-tag=artist "$f" | cut -d '=' -f 2)
   album=$(metaflac --show-tag=album "$f" | cut -d '=' -f 2)
   date=$(metaflac --show-tag=date "$f" | cut -d '=' -f 2)
   track=$(metaflac --show-tag=tracknumber "$f" | cut -d '=' -f 2)
   genre=$(metaflac --show-tag=genre "$f" | cut -d '=' -f 2)
  wine ~/.wine/drive_c/qaac/qaac.exe --tvbr 127 --quality 2 --verbose \
  --title "$title" --artist "$artist" --album "$album" \
  --date "$date" --track "$track" --genre "$genre" --comment "" \
  --artwork cover.jpg \
  "$f" -o "${f%.flac}.m4a"
done
mkdir "$artist-$album" && mv *.m4a "$artist-$album" 
```

---

### Post by andrew.46 on 2016-04-12
Very nice, I have copied this and stored it away in my growing collection of useful scripts :)

---

### Post by andrew.46 on 2016-04-13
Oh I am so thick!! Just now realised what you were talking about :). The for loop is of course mine on the qaac page.....

Anyway I see what you mean, as a copy and paste job the script runs fine with the bash alias, I might be just as well to give the full path to avoid any confusion (which for the most part has been mine!!)

**Edit:** I have altered the page as you have suggested. On re-reading it seems a reasonable page. Courtesy of reasonable rankings with Google I get a bit of mail from there... Thanks again mc4man!

---

### Post by DGedye on 2016-04-14
I'm just an ordinary linux user but thanks to Andrew's guide I am now using ABCDE 2.7.2 to rip my CDs to *.ogg and simultaneously download album art by opening my music folder in the terminal and entering ```
abcde -G -l -N -p -V -x
``` From then on its just a matter of loading in the CDs and hitting arrow up and enter to recall the command and run it for the next CD.  But then I wondered why I couldn't do that automatically on CD insert. I have searched widely on this topic but I have not been able to find a straightforward or satisfactory answer. Has anyone here found a way to autorun ABCDE on cd insert?

---

### Post by andrew.46 on 2016-04-14
> **DGedye said:**
> I'm just an ordinary linux user...

Hopefully you can get an answer here, don't forget to try #abcde on Freenode as well and see if Steve has some ideas. He is the real brains behind abcde and probably has some thoughts on the subject...

---

### Post by DGedye on 2016-04-14
Steve suggested udev.  I'll look into it. there is a good write up at [https://wiki.archlinux.org/index.php/udev](https://wiki.archlinux.org/index.php/udev)

---

### Post by mc4man on 2016-04-14
> **DGedye said:**
> I'm just an ordinary linux user but thanks to Andrew's guide I am now using ABCDE 2.7.2 to rip my CDs to *.ogg and simultaneously download album art by opening my music folder in the terminal and entering ```
abcde -G -l -N -p -V -x
``` From then on its just a matter of loading in the CDs and hitting arrow up and enter to recall the command and run it for the next CD.  But then I wondered why I couldn't do that automatically on CD insert. I have searched widely on this topic but I have not been able to find a straightforward or satisfactory answer. Has anyone here found a way to autorun ABCDE on cd insert?

It's actually quite simple, the details may vary depending on which Ubuntu release. So for example in Ubuntu you - 
create a .desktop that runs your command in a terminal
pick that .desktop as the action for audio cd insertion

As long as the command works for you in a terminal then it will work via the .desktop. If any part of the command fails then the terminal will close immediately.

Ex. for 14.04 Ubuntu
1. create the .desktop, blue can be anything, red is the command which can be changed if need be.
```
mkdir -p .local/share/applications && gedit .local/share/applications/abcde-rip.desktop 
```

Insert this, save, exit gedit - 
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=sh -c '[COLOR="#FF0000"]abcde -G -l -N -p -V -x[/COLOR]' %U
Name=[COLOR="#0000CD"]Cd Ripper[/COLOR]
Icon=
MimeType=x-content/audio-cdda;
``` 

Then log out/in. When back go to System Settings > Details > Removable Media > click the drop down for Cd Audio > Other applications.. > find & choose Cd Ripper or whatever you named it.

**If** it doesn't show in that list then you can manully add to mimeapps.list ( in 16.04 mimeapps.list is now in .config/
```
gedit .local/share/applications/mimeapps.list
```
In the [Default Applications] section either add or edit this line to look like this - 
```
x-content/audio-cdda=abcde-rip.desktop
```
In the [Added Associations] section if there is a x-content/audio-cdda= line then add abcde-rip.desktop; to the front, ex. here - 
> x-content/audio-cdda=abcde-rip.desktop;aud-cd.desktop;

Note that:
When abcde is done the terminal will close, if for some reason you wanted it keep alive then you'd need to run abcde via a script & make the Exec= line be Exec=scriptname or Exec=/path/to/scriptname

The %U after the command is to help the .desktop be found in System Settings ...

The orig. name used to create a .desktop is what's used to edit that .desktop & what's used or will show up in mimeapps.list. The name used on the Name= line in the .desktop is the name displayed to the user. You can always change the Name= if desired, you can never change the actual file name after creation.

Myself no longer use -N as I want to be able to review & in many cases edit the cddb data.

---

### Post by DGedye on 2016-04-14
> **mc4man said:**
> It's actually quite simpleThat works perfectly for me!  Thank you, I've spent hours wading through webpages advising me to set up cron jobs or installing packages that no longer exist ;->

---

### Post by andrew.46 on 2016-04-20
I have posted a very brief 'Question and Answer' guide that deals with album art under Trusty:

How can I use abcde to rip to mp3 and embed album art under Trusty?
[http://askubuntu.com/q/755722/57576](http://askubuntu.com/q/755722/57576)

Hmmm.... looks like I missed the embedding bit in the answer.....

---

### Post by Bruce_Feuillette on 2016-05-09
Hello !

I'm using abcde 2.7.2 with icedax to extract the CD-TEXT informations. It seems that the album title and artist name are mixed. 
Here's the cd-text extraction result 
```

CDINDEX discid: ec4eV_yuX46NGXvyGjV9qXDNevk- 
CDDB discid: 0x990b500a 
CD-Text: detected 
CD-Extra: not detected 
Album title: 'Abbath'   [from Abbath] 
Track  1: 'To war'  
Track  2: 'Winter bane'  
Track  3: ' Ashes of the damned'  
And so on. 

```

The problem is on the album title : Album title: 'Abbath'   [from Abbath] 
After the rip, abcde create a folder named "Album title: 'Abbath'   [from Abbath]" containing "Album title: 'Abbath'   [from Abbath]" then all the tracks : 'Abbath'   [from Abbath]/'Abbath'   [from Abbath]/tracks
It should have been Abbath/Abbath/tracks.  
It's not limited to this album, it was the same with a Therion album named "Les épaves". 

Any idea ?

---

### Post by andrew.46 on 2016-05-09
> **Bruce_Feuillette said:**
> Hello !

I'm using abcde 2.7.2 [...]


Thanks for making the big effort as 2.7.2 has only recently been released :)


> The problem is on the album title : Album title: 'Abbath'   [from Abbath] 
After the rip, abcde create a folder named "Album title: 'Abbath'   [from Abbath]" containing "Album title: 'Abbath'   [from Abbath]" then all the tracks : 'Abbath'   [from Abbath]/'Abbath'   [from Abbath]/tracks
It should have been Abbath/Abbath/tracks.  
It's not limited to this album, it was the same with a Therion album named "Les épaves". 

If you are using an ~/.abcde.conf file it would be interesting to see what you have set as OUTPUTFORMAT, this governs the directory structure for the output files. Can you show this?

BTW this Forum is fine but don't forget 'live' help is usually available on Freenode at #abcde where the 2 current developers are usually lurking...

**Edit:** I saw your posts on #abcde, hang around a bit longer next time :)

---

### Post by Bruce_Feuillette on 2016-05-10
I will stay longer, I just need to configure mIRC for Freenode. :D

My output is the default one with a minor change on the filename.
OUTPUTFORMAT='${ARTISTFILE}/${ALBUMFILE}/${TRACKNUM} - ${TRACKFILE}'
It works well with musicbrainz.
The problem only occurs with CD-Text.

---

### Post by andrew.46 on 2016-05-10
> **Bruce_Feuillette said:**
> I will stay longer, I just need to configure mIRC for Freenode. :D

mIRC runs under Linux? I have great memories of mIRC in my Windows days :)

---

### Post by Bruce_Feuillette on 2016-05-10
My computer runs under Windows. :) I'm just using abcde with a raspberry pi 3.

---

### Post by andrew.46 on 2016-05-11
> **Bruce_Feuillette said:**
> My computer runs under Windows. :) I'm just using abcde with a raspberry pi 3.

Hey, my computer at work runs Windows: we all cannot be perfect :). I confess to never having looked at CDTEXT but I believe that when I had a look at the #abcde logs you had half worked something out?

---

### Post by Bruce_Feuillette on 2016-05-11
Yes, but I don't get something.
What I've done is deleting the ***[from Artist]*** from the CD-TEXT with a sed command.
The point is that I can't manage to find where the Artist name is set on abcde. I guess it's coming from ***DTITLE***, so removing the ***[from]*** tag isn't a solution.
Yesterday I saw that Musicbrainz returns ***Album name / Artist*** in the cddbread.1. So maybe the solution will be to clean the ***[from Artist]*** and change it to ***/ Artist***, as Musicbrainz do.
But I'm only guessing. :)
And as I'm at work, I can't try ! :D

---

### Post by Bruce_Feuillette on 2016-05-22
I eventually sorted it.
In abcde, line 2474 had to be modified with
```
ATITLE=$(grep -e '^Album title:' "${ABCDETEMPDIR}/cd-text" | cut -c14- |  sed -e "s/'\(.*\)'[[:blank:]]\[from \(.*\)\]/\2 \/ \1/g" )
```
So it captures the album name, without the first and last single quote, and the artist, swaps them and put a / in the middle.
For more fun, it can be extended to have album and artist name with only the first character of each word capitalize
```
ATITLE=$(grep -e '^Album title:' "${ABCDETEMPDIR}/cd-text" | cut -c14- | sed -e "s/'\(.*\)'[[:blank:]]\[from \(.*\)\]/\2 \/ \1/g"  | tr '[:upper:]' '[:lower:]' | sed -e 's/\([a-z]\)\([a-zA-Z0-9]*\)/\u\1\2/g' )
```

---

### Post by andrew.46 on 2016-06-03
I note that the[ newest version of qaac ]("https://sites.google.com/site/qaacpage/news")offers input support using the preview version of wavpack 5:

```


[qaac] release 2.59
posted May 11, 2016, 12:30 AM by nu 774

    Fix: Was failing encoding mono AAC to AAC.
    Support Wavpack v5 interface (with large file support) 

Wavpack version 5 is still in alpha state, and DLL is not officially provided.
If you want to try it, you have to build it yourself from the source code.

This version of qaac supports both of old and new Wavpack DLL (they are
binary compatible). When new functions provided in version 5 library are
detected, qaac will use them.

```

so I have updated the little win32 dll pack I run here:

Using qaac under linux
[http://www.andrews-corner.org/qaac.html#installation](http://www.andrews-corner.org/qaac.html#installation)

Full installation now gives:

```

andrew@ilium~$ **[COLOR="#FF0000"]qaac --check[/COLOR]**
qaac 2.59, CoreAudioToolbox 7.9.9.6
libsoxconvolver 0.1.0
libsoxr-0.1.2
libsndfile-1.0.25
libFLAC 1.3.1
wavpackdll 5.0.0-alpha2
tak_deco_lib 2.3.0 compatible
andrew@ilium~$ 

```

I have tested the new wavpack dll (which I cross compiled under Xenial) with no issues but I would be grateful for another set of eyes testing it out...

---

### Post by shantiq on 2016-06-26
A little tip here which will stop you from banging your head against your computer  ...    had not used abcde for a while and had forgotten this info which is almost nowhere to be seen ...   program works a treat apart from that :]

*it is not in --help or man it seems and should be added *



[Multiple]("https://doc.ubuntu-fr.org/abcde")[ exact matches]("https://doc.ubuntu-fr.org/abcde")

At the first stage, before the extraction, abcde connects to the CDDB database to retrieve the list of CD tracks (see chapter: Database). It is possible that this database contains two lists or more  (starting with # 1, # 2 ...), in this case you will need to choose what is the one that seems to be better. Once selected from the list, [COLOR=#800000]***press q to ******exit the menu***[/COLOR] and then enter the number of the selected list (1, 2 ...).

---

### Post by andrew.46 on 2016-06-26
> **shantiq said:**
> A little tip here which will stop you from banging your head against your computer

The problem being that this output is passed to the user's pager which can vary from distro to distro, thus the exit command can also vary. Choices hardwired into abcde are found in the page function:


```

# page [file]
# Finds the right pager in the system to display a file
page ()
{
	PAGEFILE="$1"
	# Use the debian sensible-pager wrapper to pick the pager
	# user has requested via their $PAGER environment variable
	if [ -x "/usr/bin/sensible-pager" ]; then
		/usr/bin/sensible-pager "$PAGEFILE"
	elif [ -x "$PAGER" ]; then
		# That failed, try to load the preferred editor, starting
		# with their PAGER variable
		$PAGER "$PAGEFILE"
		# If that fails, check for less
	elif [ -x /usr/bin/less ]; then
		/usr/bin/less -f "$PAGEFILE"
		# more should be on all UNIX systems
	elif [ -x /bin/more ]; then
		/bin/more "$PAGEFILE"
	else
		# No bananas, just cat the thing
		cat "$PAGEFILE" >&2
	fi
}

```

So giving an exact key code could be problematic. This issue could be added to the abcde FAQs though which I will look at on the weekend....

---

### Post by shantiq on 2016-06-26
Thanx Andrew .for clarifications.. :) there is always more to the picture than meets the eye 
Anyway the info is on the forum now ... Maybe i should tag it more solidly

#abcdemultipleexactmatches  [  multiple exact matches ]

:)

---

### Post by mc4man on 2016-06-26
> **shantiq said:**
> Thanx Andrew .for clarifications.. :) there is always more to the picture than meets the eye 
Anyway the info is on the forum now ... Maybe i should tag it more solidly

#abcdemultipleexactmatches

:)
Likely not that many choices, in Ubuntu/Debian I'd guess any of these, 1st. being 'easiest' - 
q  :q  Q  :Q  ZZ

---

### Post by andrew.46 on 2016-07-17
> **mc4man said:**
> Likely not that many choices, in Ubuntu/Debian I'd guess any of these, 1st. being 'easiest' - 
q  :q  Q  :Q  ZZ

Hmmm. so which pagers do the commands tie into? I believe that less and more both exit with 'q'. Officially:

[LIST]
[*]exit 'less' = q or Q or :q or :Q or ZZ
[*]exit 'more' = q or Q or INTERRUPT
[*]
[/LIST]

The remaining culprits are '/usr/bin/sensible-editor' which I believe under a Debian system points to the required pager but I am not sure what that is under a modern system. The final option of 'cat' I suspect should not actually need exiting...

**Edit: **Just remembered I have at least one Debian colleague who can answer the sensible-pager question :)

---

### Post by andrew.46 on 2016-08-02
OK [thanks and acknowledgement ]("https://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=commit;h=cb230e6b22bf98afed9b7ebb7ceb303ae8e5d0e2")to shan and mc4man for prodding me to add the mention to abcde of the magic letter 'q' to exit the multi-result CDDB entry page. 

Looks like I have a bit of time to work some more on abcde so hopefully some good additions coming! Anybody who is interested in abcde in general can join #abcde on Freenode where Steve and I are usually lurking...

---

### Post by andrew.46 on 2016-11-29
Renovations complete on the abcde section of the site:

abcde: Command Line Music CD Ripping for Linux
[http://www.andrews-corner.org/linux/abcde/index.html](http://www.andrews-corner.org/linux/abcde/index.html)

Now I have 25 ~/.abcde.conf files in place and that marks the end of my efforts with these pages. Mind you it looks like I might be able to get windows lossless (WMAL) encoding in place....

---

### Post by andrew.46 on 2017-07-17
After a vacation away from abcde I have added in AIFF support:

[https://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=summary](https://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=summary)

and I have created a conf file for this:

[http://www.andrews-corner.org/linux/abcde/abcde_lossless.html#aiff](http://www.andrews-corner.org/linux/abcde/abcde_lossless.html#aiff)

Works flawlessly here but the user who requested the enhancement is having some troubles. Could a skilled Ubuntu Forums user test it out for me?

Note the new command-line option -Q which selects the cddb method, this gets around a few issues I have noted with the new cddb/musicbrainz crossover options. For example:

```
abcde -Q cddb -z -o aiff
```

uses cddb lookup, uses the 'testing only' run for abcde (only brief encodes for each track) and uses the new aiff container.

---

### Post by mc4man on 2017-07-17
works fine here, no issue. Tested with tester command & also for real with your sample .config, only change there was I use cd-paranoia

snippet
> Ripping from sector      32 (track  1 [0:00.00])
	  to sector     107 (track  1 [0:01.00])

outputting to /home/doug/Desktop/dddd/abcde.f8115212/track01.wav

 (== PROGRESS == [                              | 000107 00 ] == :^D * ==)   

Done.


 echo Encoding track 01 of 18: (Opening Intro)...
Encoding track 01 of 18: (Opening Intro)...
encodetrack-aiff-01 nice -n 10 ffmpeg -i /home/doug/Desktop/dddd/abcde.f8115212/track01.wav -write_id3v2 1 -id3v2_version 4 -metadata artist=Tom Waits -metadata album=Nighthawks at the Diner -metadata title=(Opening Intro) -metadata track=01 -metadata date=1975 -metadata genre=Blues -metadata comment=abcde version 2.8.2 /home/doug/Desktop/dddd/abcde.f8115212/track01.aiff
ffmpeg version 3.3.2-1~xenial2 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
.......
Guessed Channel Layout for Input Stream #0.0 : stereo
Input #0, wav, from '/home/doug/Desktop/dddd/abcde.f8115212/track01.wav':
  Duration: 00:00:01.01, bitrate: 1411 kb/s
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 44100 Hz, stereo, s16, 1411 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le (native) -> pcm_s16be (native))
Press [q] to stop, [?] for help
Output #0, aiff, to '/home/doug/Desktop/dddd/abcde.f8115212/track01.aiff':
  Metadata:
    artist          : Tom Waits
    album           : Nighthawks at the Diner
    title           : (Opening Intro)
    track           : 01
    date            : 1975
    genre           : Blues
    comment         : abcde version 2.8.2
    encoder         : Lavf57.71.100
    Stream #0:0: Audio: pcm_s16be (NONE / 0x454E4F4E), 44100 Hz, stereo, s16, 1411 kb/s
    Metadata:
      encoder         : Lavc57.89.100 pcm_s16be
size=     175kB time=00:00:01.01 bitrate=1413.8kbits/s speed= 853x    
video:0kB audio:175kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.183494%
encodetrack-01 true
 echo Tagging track 01 of 18: (Opening Intro)...
Tagging track 01 of 18: (Opening Intro)...
tagtrack-aiff-01 true
tagtrack-01 true
movetrack-01 mv /home/doug/Desktop/dddd/abcde.f8115212/track01.aiff /home/doug/Music/aiff/Tom Waits-Nighthawks at the Diner/01.(Opening Intro).aiff
movetrack-output-aiff true



Edit: as far as tags they're good in all players checked except audacious..

---

### Post by andrew.46 on 2017-07-17
> **mc4man said:**
> works fine here, no issue. [...]

Thanks very much for that mc4man, I was starting to doubt my own work :).

---

### Post by shantiq on 2017-07-18
Yes Andrew all good here too and thanx whole bunch of formats now



```
 echo Encoding track 03 of 11: New Song...
Encoding track 03 of 11: New Song...
encodetrack-aiff-03 nice -n 10 ffmpeg -i /home/shantiq/abcde.a30c090b/track03.wav -write_id3v2 1 -id3v2_version 4 -metadata artist=Warpaint -metadata album=Heads Up -metadata title=New Song -metadata track=03 -metadata date=2016 -metadata genre=Indie Rock -metadata comment=abcde version 2.7.1 /home/shantiq/abcde.a30c090b/track03.aiff
ffmpeg version N-82997-g557c0df Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
  configuration: --prefix=/home/shantiq/ffmpeg_build --pkg-config-flags=--static --extra-cflags=-I/home/shantiq/ffmpeg_build/include --extra-ldflags=-L/home/shantiq/ffmpeg_build/lib --bindir=/home/shantiq/bin --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-nonfree
  libavutil      55. 43.100 / 55. 43.100
  libavcodec     57. 70.101 / 57. 70.101
  libavformat    57. 61.100 / 57. 61.100
  libavdevice    57.  2.100 / 57.  2.100
  libavfilter     6. 68.100 /  6. 68.100
  libswscale      4.  3.101 /  4.  3.101
  libswresample   2.  4.100 /  2.  4.100
  libpostproc    54.  2.100 / 54.  2.100
Guessed Channel Layout for Input Stream #0.0 : stereo
Input #0, wav, from '/home/shantiq/abcde.a30c090b/track03.wav':
  Duration: 00:04:16.44, bitrate: 1411 kb/s
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 44100 Hz, stereo, s16, 1411 kb/s
Output #0, aiff, to '/home/shantiq/abcde.a30c090b/track03.aiff':
  Metadata:
    artist          : Warpaint
    album           : Heads Up
    title           : New Song
    track           : 03
    date            : 2016
    genre           : Indie Rock
    comment         : abcde version 2.7.1
    encoder         : Lavf57.61.100
    Stream #0:0: Audio: pcm_s16be (NONE / 0x454E4F4E), 44100 Hz, stereo, s16, 1411 kb/s
    Metadata:
      encoder         : Lavc57.70.101 pcm_s16be
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le (native) -> pcm_s16be (native))
Press [q] to stop, [?] for help
size=   44176kB time=00:04:16.44 bitrate=1411.2kbits/s speed=2.14e+03x    
video:0kB audio:44176kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.000668%
encodetrack-03 true
 echo Tagging track 03 of 11: New Song...
Tagging track 03 of 11: New Song...
tagtrack-aiff-03 true
tagtrack-03 true
movetrack-03 mv /home/shantiq/abcde.a30c090b/track03.aiff Music/aiff/Warpaint-Heads Up/03.New Song.aiff
Grabbing track 04: The Stall...
cdparanoia III release 10.2 (September 11, 2008)
```

---

### Post by andrew.46 on 2017-07-18
> **shantiq said:**
> Yes Andrew all good here too and thanx all bunch of formats now

Thanks Shan :)

---

### Post by shantiq on 2017-07-18
"whole bunch of formats"   :]

---

### Post by andrew.46 on 2017-07-28
In another change before I back off for a little bit from abcde development I have added in *experimental* support for embedding album art with ogg files. Not the easiest thing as it turns out and possibly a few bugs in there as well.

Some testing would be nice and you could consider using either of the following command lines:

```

abcde -Q cddb -B -o ogg
abcde -Q cddb -B -o ogg,m4a,flac,wv,mp3

```

I use the above command line in combination with the following ~/.abcde.conf file:

```

# -----------------$HOME/.abcde.conf----------------- #
# 
#  A sample configuration file to convert music cds to 
#  MP3, Ogg Vorbis, FLAC, Musepack, AAC, WavPack, Opus,
#  Monkey's Audio (ape), True Audio, AC3, mp2 and AIFF.
#          12 formats at the same time!
#  Using abcde version 2.8.2 pre-release version.
# 
#   http://andrews-corner.org/linux/abcde.html
# -------------------------------------------------- #

# Encode tracks immediately after reading. Saves disk space, gives
# better reading of 'scratchy' disks and better troubleshooting of
# encoding process but slows the operation of abcde quite a bit:
LOWDISK=y

# Specify the method to use to retrieve the track information,
# the alternative is to specify 'musicbrainz':
CDDBMETHOD=cddb

# Make a local cache of cddb entries and then volunteer to use 
# these entries when and if they match the cd:
CDDBCOPYLOCAL="y"
CDDBLOCALDIR="$HOME/.cddb"
CDDBLOCALRECURSIVE="y"
CDDBUSELOCAL="y"

OGGENCODERSYNTAX=oggenc                        # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                          # Specify encoder for MP3
FLACENCODERSYNTAX=flac                         # Specify encoder for FLAC
MPCENCODERSYNTAX=mpcenc                        # Specify encoder for Musepack
AACENCODERSYNTAX=fdkaac                        # Specify encoder for AAC
OPUSENCODERSYNTAX=opusenc                      # Specify encoder for Opus
WVENCODERSYNTAX=wavpack                        # Specify encoder for Wavpack
APENCODERSYNTAX=mac                            # Specify encoder for Monkey's Audio
TTAENCODERSYNTAX=tta                           # Specify encoder for True Audio
MP2ENCODERSYNTAX=twolame                       # Specify encoder for MP2
MKAENCODERSYNTAX=ffmpeg                        # Specify encoder for MKA
AIFFENCODERSYNTAX=ffmpeg                       # Specify encoder for AIFF

OGGENC=oggenc                                  # Path to Ogg Vorbis encoder
LAME=lame                                      # Path to MP3 encoder
FLAC=flac                                      # Path to FLAC encoder
MPCENC=mpcenc                                  # Path to Musepack encoder
FDKAAC=fdkaac                                  # Path to the AAC encoder
OPUSENC=opusenc                                # Path to Opus encoder
WVENC=wavpack                                  # Path to WavPack encoder
APENC=mac                                      # Path to Monkey's Audio encoder
TTA=tta                                        # Path to True Audio encoder
TWOLAME=twolame                                # Path to MP2 encoder
FFMPEG=ffmpeg                                  # Path to FFmpeg (for AC3 and AIFF)

OGGENCOPTS='-q 6'                              # Options for Ogg Vorbis
LAMEOPTS='-V 2'                                # Options for MP3 
FLACOPTS='-s -e -V -8'                         # Options for FLAC
MPCENCOPTS='--extreme'                         # Options for Musepack
FDKAACENCOPTS='-p 2 -m 5 -a 1'                 # Options for fdkaac
OPUSENCOPTS="--vbr --bitrate 128"              # Options for Opus
WVENCOPTS="-hx3"                               # Options for WavPack
APENCOPTS="-c4000"                             # Options for Monkey's Audio
TTAENCOPTS=""                                  # Options for True Audio
TWOLAMENCOPTS="--bitrate 320"                  # Options for MP2
FFMPEGENCOPTS="-c:a ac3 -b:a 448k"             # Options for MKA (AC3 via FFmpeg)
AIFFENCOPTS="-write_id3v2 1 -id3v2_version 4"  # Options for AIFF  

OUTPUTTYPE="ogg,mp3,flac,mpc,m4a,opus,wv,ape,tta,mp2,mka,aiff"  # Encode to 12 formats!

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac. New to abcde 2.7 is 'libcdio'.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options,
# if using libcdio set 'CD_PARANOIA=cd-paranoia'.
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/Music"               

# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean

# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# This function takes out dots preceding the album name, and removes a grab
# bag of illegal characters. It allows spaces, if you do not wish spaces add
# in -e 's/ /_/g' after the first sed command.
mungefilename ()
{
  echo "$@" | sed -e 's/^\.*//' | tr -d ":><|*/\"'?[:cntrl:]"
}

MAXPROCS=2                                # Run a few encoders simultaneously
PADTRACKS=y                               # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=2                            # Useful for debugging
COMMENT='abcde version 2.8.2'             # Place a comment...
EJECTCD=y                                 # Please eject cd when finished :-)

```

I will not easily admit how long it took to get even this preliminary effort of ogg embedding going :).

---

### Post by shantiq on 2017-07-28
hm good here Andrew but had to add
```
sudo apt install glyrc
```   to my setup


and it is downloading the jpg and adding it to folder but no embedding .. could be my mistake



from URL


```
abcde -d /dev/sr0  -Q cddb -B -o ogg
CDDB method 0: cddb
Executing customizable pre-read function... done.
Getting CD track info... Querying the CD for audio tracks...
Grabbing entire CD - tracks: 01 02 03 04 05 06 07 08 09 10 11
abcde: attempting to resume from /home/shantiq/abcde.a30c090b..
Creating playlist...
trying to get cover with glyrc for Warpaint / Heads Up
- Artist   : warpaint
- Album    : heads up
- Language : en
- Type     : cover

---- Triggering: musictree local coverartarchive 
#[00/01] Checking image-types: [- DLError: Couldn't resolve host name [6]
- DLError: Couldn't resolve host name [6]
!!] (-2 item(s) less)
---- Triggering: lastfm jamendo musicbrainz 
#[00/01] Checking image-types: [.] (-0 item(s) less)
---- 

///// ITEM #1 /////
WRITE to '/home/shantiq/abcde.a30c090b/cover.jpg'
FROM: <https://lastfm-img2.akamaized.net/i/u/300x300/168051c0c085671fcb26eff2ffd05e45.png>
PROV: lastfm
SIZE: 57698 Bytes
MSUM: ee5ae2e0fe403ebfc0e15c84d2f23263
TYPE: cover
SAFE: No
RATE: 0
STMP: 0.000000
FRMT: png
DATA: <not printable>

////////////////////
# => 1 item in total.
/home/shantiq/abcde.a30c090b/cover.jpg PNG 300x300 300x300+0+0 8-bit sRGB 57.7KB 0.000u 0:00.000
Do you want to enter URL or local path for the album art [y/N]? y
Enter URL or local path (ENTER to cancel) :https://lastfm-img2.akamaized.net/i/u/300x300/168051c0c085671fcb26eff2ffd05e45.png
copying cover to target directory Music/ogg/Warpaint-Heads Up
Grabbing track 06: Don't Wanna...
cdparanoia III release 10.2 (September 11, 2008)

Ripping from sector  109968 (track  6 [0:00.00])
      to sector  126672 (track  6 [3:42.54])

outputting to /home/shantiq/abcde.a30c090b/track06.wav

 (== PROGRESS == [                              | 126672 00 ] == :^D * ==)   

Done.


 echo Encoding track 06 of 11: Don't Wanna...
Encoding track 06 of 11: Don't Wanna...
encodetrack-ogg-06 nice -n 10 oggenc -o /home/shantiq/abcde.a30c090b/track06.ogg /home/shantiq/abcde.a30c090b/track06.wav
Opening with wav module: WAV file reader
Encoding "/home/shantiq/abcde.a30c090b/track06.wav" to 
         "/home/shantiq/abcde.a30c090b/track06.ogg" 
at quality 3.00
    [100.0%] [ 0m00s remaining] | 

Done encoding file "/home/shantiq/abcde.a30c090b/track06.ogg"

    File length:  3m 42.0s
    Elapsed time: 0m 02.9s
    Rate:         76.8503
    Average bitrate: 99.2 kb/s

encodetrack-06 true
 echo Tagging track 06 of 11: Don't Wanna...
Tagging track 06 of 11: Don't Wanna...
tagtrack-ogg-06 nice -n 10 vorbiscomment -R -w /home/shantiq/abcde.a30c090b/track06.uncommented.ogg /home/shantiq/abcde.a30c090b/track06.ogg
tagtrack-06 true
movetrack-06 mv /home/shantiq/abcde.a30c090b/track06.ogg Music/ogg/Warpaint-Heads Up/06.Dont Wanna.ogg


```

---

### Post by andrew.46 on 2017-07-28
Hey Shan! You have the most recent git abcde?

---

### Post by shantiq on 2017-07-29
yes Andrew this snapshot   [tested on Audacious/VLC/mpv]  the pic is downloaded and put in folder but not embedded at this point on my setup

> 20 hours ago     Andrew Strong    Experimental support for embedding album art to ogg master     commit | commitdiff | tree | snapshot

```
#!/bin/bash
# Copyright (c) 1998-2001 Robert Woodcock <rcw@debian.org>
# Copyright (c) 2003-2006 Jesus Climent <jesus.climent@hispalinux.es>
# Copyright (c) 2009-2012 Colin Tuckley <colint@debian.org>
# Copyright (c) 2012-     Steve McIntyre <93sam@@debian.org>
# Copyright (c) 2015-2016 Andrew Strong <andrew.david.strong@gmail.com>
# This code is hereby licensed for public consumption under either the
# GNU GPL v2 or greater, or Larry Wall's Artistic license - your choice.
#
# You should have received a copy of the GNU General Public License along
# with this program; if not, write to the Free Software Foundation, Inc.,
# 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

VERSION='2.8.2-UNRELEASED'

usage ()
{
echo "This is abcde v$VERSION."
echo "Usage: abcde [options] [tracks]"
echo "Options:"
echo "-1     Encode the whole CD in a single file"
echo "-a <action1[,action2]...>"
echo "       Actions to perform:"
echo "       cddb,read,getalbumart,embedalbumart,normalize,encode,tag,move,replaygain,playlist,clean"
#echo "-A     Experimental actions (retag, transcode)"
echo "-b     Enable batch normalization"
echo "-B     Embed albumart (this also activates getalbumart)"
echo "-c <file>"
echo "       Specify a configuration file (overrides system and user config files)"
echo "-C <discid#>"
echo "       Specify discid to resume from (only needed if you no longer have the cd)"
echo "-d <device>"
echo "       Specify CDROM device to grab (flac uses a single-track flac file)"
echo "-D     Debugging mode (equivalent to sh -x abcde)"
echo "-e     Erase encoded track information from status file"
echo "-f     Force operations that otherwise are considered harmful. Read \"man abcde\""
echo "-g     Use \"lame --nogap\" for MP3 encoding. Disables low disk and pipes flags"
echo "-G     Get album art by using the 'getalbumart' action"
echo "-h     This help information"
#echo "-i    Tag files while encoding, when possible (local only) -NWY-"
echo "-j <#> Number of encoder processes to run at once (localhost)"
echo "-k     Keep the wav tracks for later use"
echo "-l     Use low disk space algorithm"
echo "-L     Use local CDDB storage directory"
echo "-m     Modify playlist to include CRLF endings, to comply with some players"
#echo "       WARNING: Deprecated. Use \"cue\" action"
#echo "-M     Create a CUE file"
echo "-n     No lookup. Don't query CDDB, just create and use template"
echo "-N     Noninteractive. Never prompt for anything"
echo "-o <type1[,type2]...>"
echo "       Output file type(s) (vorbis,mp3,flac,spx,mpc,wav,m4a,opus,mka,wv,ape,mp2,tta,aiff). Defaults to vorbis"
echo "-p     Pad track numbers with 0's (if less than 10 tracks)"
echo "-P     Use UNIX pipes to read+encode without wav files"
echo "-Q     Select CDDBMETHOD from the command line. Choice is cddb or musicbrainz".
echo "-r <host1[,host2]...>"
echo "       Also encode on these remote hosts"
echo "-s <field>"
echo "       Show fields from the CDDB info (year,genre)"
echo "-S <#> Set the CD speed"
echo "-t <#> Start the track numbering at a given number"
echo "-T <#> Same as -t but modifies tag numbering"
echo "-U     Do NOT use UNICODE (UTF8) tags and comments"
echo "-v     Show version number and exit"
echo "-V     Be a bit more verbose about what is happening behind the scenes"
echo "-x     Eject CD after all tracks are read"
echo "-w <comment>"
echo "       Add a comment to the CD tracks"
echo "-W <#> Concatenate CDs: -T #01 -w \"CD #\""
echo "-z     Use debug CDROMREADERSYNTAX option (needs cdparanoia)"
echo ""
echo "Tracks is a space-delimited list of tracks to grab."
echo "Ranges specified with hyphens are allowed (i.e., 1-5)."
echo ""
#echo "Double hyphens are used to concatenate tracks"
}
```

---

### Post by andrew.46 on 2017-07-29
Hmmmm..... I am not sure about that then. You need xxd and base64 but this are part of an Ubuntu base install. Mediainfo does not show an embedded file?

---

### Post by shantiq on 2017-07-29
when i run mediainfo it shows

```
mediainfo *
General
Complete name                            : 09.Heads Up.ogg
Format                                   : OGG
File size                                : 3.61 MiB
Duration                                 : 4mn 57s
Overall bit rate mode                    : Variable
Overall bit rate                         : 102 Kbps
Album                                    : Heads Up
Track name                               : Heads Up
Track name/Position                      : 09
Track name/Total                         : 11
Performer                                : Warpaint
Genre                                    : Indie Rock
Recorded date                            : 2016
Comment                                  : abcde version 2.8.1
CDDB                                     : a30c090b

Audio
ID                                       : 754546434 (0x2CF97702)
Format                                   : Vorbis
Format settings, Floor                   : 1
Duration                                 : 4mn 57s
Bit rate mode                            : Variable
Bit rate                                 : 112 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 3.97 MiB
Writing library                          : libVorbis (&#9924;&#9924;&#9924;&#9924;) (20150105 (&#9924;&#9924;&#9924;&#9924;))




```

maybe my .abcde.conf interferes?

```
# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#     Apple Lossless Audio Codec (alac) using qaac 
#         and abcde version 2.8.1-UNRELEASED
# 
#       http://andrews-corner.org/qaac.html
# -------------------------------------------------- #


CDROM=/dev/sr1

# Encode tracks immediately after reading. Saves disk space, gives
# better reading of 'scratchy' disks and better troubleshooting of
# encoding process but slows the operation of abcde quite a bit:
LOWDISK=y

# Specify the method to use to retrieve the track information,
# the alternative is to specify 'cddb':

# Specify the method to use to retrieve the track information,
# the alternative is to specify 'musicbrainz':

CDDBMETHOD=cddb

# Make a local cache of cddb entries and then volunteer to use 
# these entries when and if they match the cd:
CDDBCOPYLOCAL="y"
CDDBLOCALDIR="$HOME/.cddb"
CDDBLOCALRECURSIVE="y"
CDDBUSELOCAL="y"




# IF YOU WANT AN ALAC FILE CHANGE NEXT LINE  from fdkaac to qaac  IF YOU WANT A HE-AACv2 FILE CHANGE TO fdkaac >>
#   ALSO added ffmpeg as an option [see below]
#AACENCODERSYNTAX=qaac
FDKAAC=fdkaac

#   to set up qaac   see here >> http://www.andrews-corner.org/qaac.html#abcde
#   and place your qaac.exe the way it is below here [create folder if need be]

QAAC="$HOME/.wine/drive_c/qaac/qaac.exe"
QAACENCOPTS="--alac"   

# Output type for alac:
OUTPUTTYPE="m4a"

# For fdkaac options see 'fdkaac --help' THIS HERE BELOW WILL GIVE YOU A HE-AACv2 FILE
FDKAACENCOPTS='-p 29  -b 38000 -I' 


FFMPEG=ffmpeg
FFMPEGENCOPTS="-c:a aac -b:a 320k -strict -2"
OUTPUTTYPE="m4a"

# tta True Audio settings below
#OUTPUTTYPE="tta"
#TTA=tta
#TTAENC=ttaenc
#TTAENCODERSYNTAX=ttaenc




# flac
OUTPUTTYPE="flac"
FLACENCODERSYNTAX=flac
FLAC=flac
METAFLAC=metaflac 
FLACOPTS="--silent -8"

# mp3
OUTPUTTYPE=mp3 
LAMEOPTS="-b 320k"
LAME=lame   

#mka

OUTPUTTYPE="mka"

MKAENCODERSYNTAX=ffmpeg
FFMPEG=ffmpeg
FFMPEGENCOPTS="-c:a ac3 -b:a 640k"
OUTPUTTYPE="mka" 

WVENCODERSYNTAX=wavpack                   
WVENC=wavpack 
OUTPUTTYPE="wv"
WVENCOPTS="-hx3" 
            

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac. New to abcde 2.7 is 'libcdio'.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options,
# if using libcdio set 'CD_PARANOIA=cd-paranoia'.
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid   

# Give the location for the 'compatibility layer software application'
# known as Wine:
WINE=wine          
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="Music"


# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean

OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# This function takes out dots preceding the album name, and removes a grab
# bag of illegal characters. It allows spaces, if you do not wish spaces add
# in -e 's/ /_/g' after the first sed command.
mungefilename ()
{
  echo "$@" | sed -e 's/^\.*//' | tr -d ":><|*/\"'?[:cntrl:]"
}

# What extra options?
MAXPROCS=2                                # Run a few encoders simultaneously
PADTRACKS=y                               # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=2                            # Useful for debugging
COMMENT='abcde version 2.8.1'  # Place a comment...
EJECTCD=n                                # Please eject cd when finished :-)
```

---

### Post by mc4man on 2017-07-29
> **shantiq said:**
> 

and it is downloading the jpg and adding it to folder but no embedding .. could be my mistake


Do you want to enter URL or local path for the album art [y/N]? y



couple of things - 
The embedding is done after the complete rip is done, not per track
That query is a little confusing, the most common response would be n, abcde will then copy the dl'ed one to rip folder..

So it works here...
> ripping, encoding, tagging....blah, blah
Successfully embedded the album art into your ogg tracks
Finished.

---

### Post by shantiq on 2017-07-29
i seeeeee   ...    I only did one track to test and no embedding    ....    will run it again later and report :]
and ditto on the query ....    it is confusing

EDIT:    better
```
 echo Tagging track 10 of 10: Shou El hal...
Tagging track 10 of 10: Shou El hal...
tagtrack-ogg-10 nice -n 10 vorbiscomment -R -w /home/shantiq/abcde.860afc0a/track10.uncommented.ogg /home/shantiq/abcde.860afc0a/track10.ogg
tagtrack-10 true
movetrack-10 mv /home/shantiq/abcde.860afc0a/track10.ogg Music/ogg/Elissa-Aàyshalak/10.Shou El hal.ogg
mkdir: cannot create directory ‘Music/ogg/Elissa-Aàyshalak/albumart_backup’: No such file or directory
mv: cannot move 'cover.jpg' to 'Music/ogg/Elissa-Aàyshalak/albumart_backup': No such file or directory
Successfully embedded the album art into your ogg tracks
Finished.


```

Mental note to self >

&#10122; ```
sudo apt install glyrc
```
&#10123; Do whole album to get embedded files


And thanx maestro! one more embellishment to the Swiss knife

---

### Post by andrew.46 on 2017-07-30
Thanks guys, looks like the experimental support for ogg embedding at least works! I shall probably slide back into quietness on the abcde front for a while now. Until the next little thing tweaks my curiosity :)

---

### Post by andrew.46 on 2018-03-07
New release for abcde: version 2.9. Huge changelog making it a very worthwhile upgrade:

```

abcde 2.9

 * Add some documentation for the aged CD ripper dagrab. Thanks to 
   Teika Kazura for the notification and suggested documentation. This 
   closes Issue 50: https://abcde.einval.com/bugzilla/show_bug.cgi?id=50
 * Work by Matthias Andree <matthias.andree@gmx.de> to address the issue
   where abcde fails with accented characters from CD-TEXT. The issue and
   partial fix applied here documented in Issue 53:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=53
   and also in the abcde mailing list:
   https://lists.einval.com/pipermail/abcde-users/2017-January/000232.html
 * Allow for embedding of  album art downloaded by the getalbumart function. 
   Currently this is available for flac (using metaflac), mp3 (using eyed3),
    m4a (using AtomicParsley) and WavPack aka wv (using wvtag).
    This can be invoked in 3 ways:
     
     1. Use the commandline '-B' option (this will also call getalbumart)
     2. Use the commandline '-a embedalbumart' option to add to list of actions
     3. Use 'embedalbumart' in the 'ACTIONS' list in ~/.abcde.conf
     
   Still needs more development but it is perfectly usable at the moment!
 * Use md5 rather than md5sum under macOS. Thanks to JCount for the bug
   report and also the fix. This solves Issue 59:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=59
 * Support added for encoding with Audio Interchange File Format (AIFF). 
   Thanks to Massimo Villa for the feature request. FFmpeg is required
   for the encoding, the container and suffix are 'aiff'.
 * Allow selection of either cddb or musicbrainz from the command line:
 
  -Q   Select CDDBMETHOD from the command line. Choice is cddb or musicbrainz.
  
   Command line letters are fast running out but the 'Q' option quite neatly
   stands for 'Query'!
 * Allow for embedding with do_embedalbumart() for single track encodes when
   OUTPUTFORMAT and ONETRACKOUTPUTFORMAT are different. Thanks to Ashley Gittins
   for the bug report. This closes Issue 63:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=63
 * Experimental support for embedding albumart with ogg files. The slightly
   tortuous technique drawn from 2 sources:

   1. https://github.com/biapy/howto.biapy.com/blob/master/various/mussync-tools
   2. https://github.com/acabal/scripts/blob/master/ogg-cover-art
   
   Testing is strongly encouraged, perhaps the simplest way to test is with:
   
       abcde -o ogg -B
    
    Or the appropriate settings in an ~/.abcde.conf file.
 * Massive rework of CD lookup code so support multiple sources
   better. Thanks to Gabriel Rosenkoetter for his initial idea in this
   area, and to Tomasz Goli&#324;ski on irc for initial inspiration on how
   this should work better.
   There are now 3 different options for CD lookup: cddb, musicbrainz and
   cdtext. They can all be listed in a comma-separated list for
   CDDBMETHOD and the code will now call all of them in the sequence
   listed. All the results will be combined into one list at the end for
   the user to select, just like would have previously worked for one
   source only. Closes Issue 42:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=42
 * Fix Musicbrainz ID calculation in makeids()
   Apply fix suggested by petecollins24@gmail.com; add PREGAP to
   LEADOUT to correct Musicbrainz ID calculation. Hopefully closes
   Issue 54: https://abcde.einval.com/bugzilla/show_bug.cgi?id=54
 * Fix abcde.mkcue() when handling the --wholedisk option. Thanks to
   Nino Burini for the patch. Closes Issue 47 and maybe also 45:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=47
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=45
 * Add more comprehensive examples for filename munging in the example
   config file. Closes Issue 49:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=49
 * Add a more better fix for the year lookup problem in abcde-musicbrainz-tool
   Thanks to Tom Samstag for the patch. Closes Issue 57:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=57
 * Redirect stderr on "which" calls to clear up error noise on some
   systems. Closes Issue 56:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=56
 * Add Irix support, based on a patch by abcde@canavan.de. Closes Issue 29:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=29
 * Rework abcde-musicbrainz-tool to work with WebService::MusicBrainz 1.x
   Thanks to Nicolas Guillaumin for the patch. Closes Issue 60:
   https://abcde.einval.com/bugzilla/show_bug.cgi?id=60
   Also added a specific dependency on version 1.0.4 or newer, so
   abcde-musicbrainz-tool will abort if the version found is too old.
   Since tweaked to deal with multi-artist albums and tracks more
   completely.
 * Add resume support in do_getalbumart()
 * Fix getopts setup for "P". Thanks to Alan W. Kerr for reporting this.
 * Major set of code cleanups to fix up lots of warnings found with
   shellcheck, and a few other style issues:
   + Lots of quoting fixes
   + Use $( instead of `
   + Stop using -o and -a syntax with if [ - use || or && instead
   + Wrap and shorten some very long lines
 * Wrap some output messages so they fit on a standard width console
 * Factor out repeated code and make page() more useful
 * Add version check before resuming from an old ripping run
   
 -- Steve McIntyre <93sam@debian.org>  Thu, 08 Mar 2018 00:14:56 +0000

```

I am no longer an active developer for abcde so kudos to Steve for pushing this work through!!

---

### Post by mc4man on 2018-03-09
Just noticed that as of current libcdio (18.04) there is no longer a cd-paranoia binary so using libcdio will no longer work, only shared objects provided now..
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=888053](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=888053)

Edit; apparently the cd-paranoia binary has been moved to the libcdio-paranoia source. However Debian & Ubuntu forgot to have that source install it.. It could either be added to the  libcdio-paranoia2 package install or deb multimedia puts it in a new separate package, cd-paranoia.

(- Ubuntu has failed to respond a severe bug in libcdio17 so 18.04 users atm won't be able to use audio cd's in any fashion anyway.., if they can't get their act together i'll provde a patched version

---

