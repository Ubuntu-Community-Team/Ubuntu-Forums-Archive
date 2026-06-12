---
title: "Converting large amounts of music files"
date: 2008-04-28
forum: Multimedia Software
---

### Post by GabrielWolff on 2008-04-28
I have a very large collection of music (about 40.000 files) on a HDD.

The files are in various different formats, mainly ogg, flac, mp3 and ape.

I'd like to find a tool with which I can convert **all the files** to one format, preferably mp3, without having to open dozens of folders and hundreds of sub-folders.

Any chance?

---

### Post by poliltimmy on 2008-04-28
I converted 8500 songs with sound converter. was simple and faster than any windows app I've used.

---

### Post by artir on 2008-04-28
There is a program called mp32ogg. You do: mp32ogg *.mp3 (or *.*) and it will convert anything to .ogg.
To open each folder... maybe a script with a loop. But i dont know :(

---

### Post by ivze on 2008-04-28
The task is easily solved by sox and lame and the attached script. 
* Sox is capable for converting music files across different formats, but not capable for encoding into mp3. To see which formates are supported - see aptitude: search for sox and look at installed sox libs.
* Lame is capable for creating mp3-s from several of audio formats, sox can convert to.

There are troubles with saving additional data: e.g. comments - from audio files. If you are not afraid of loosing those, the suggested solution is for you.

To convert you music archives you need:

1. sudo apt-get install lame sox libsox-fmt-all

2. copy the whole source music archive to a new place, where the resulting converted archive will be. Despite this might seem to be a useless operation, this helps a lot.

3.take this script :
```

#!/bin/bash
#The script takes a music filename as it's first argument and converts it to mp3format. The source file is deleted.
set -e # break at any error
if [ $# -ne 1 ]
then
	echo Wrong parameters.
	exit 1
fi
#our first parameter is the filename, we will to convert.
rawname="$1"
#is this mp3? If it is, the work's done allready!
suff="${rawname##*.}"
if [ "$suff" = "mp3" ]
then
	echo Skipping $rawname.
	exit 0
fi
#extracting pure name
name="${rawname%.*}"
tmp="/tmp/pid-$$-temporary-audio-file.aiff"
#converting to intermediate format
sox "$rawname" "$tmp"
#lame-converting to mp3
lame "$tmp" "$name.mp3"
#if we are here, no errors have happen - deleting source.
rm -f "$tmp"
rm -f "$rawname"
exit 0

```
put it to a file "recode.sh" and execute ```
chmod u+x recode.sh
``` over the file to make it executable.

4. place recode.sh in the root of the newely-copied musics archive.

5. open a terminal window and cd to the archive root directory (where recode.sh resides).

6.run 
```

find . -type f -exec ./recode.sh "{}" ";"

```

7. wait some days...:)

As soon as a new music file gets recoded, the source is deleted.
Any file, that sox don't understand, is omited.

You may break the loop at any time.
After restarting, it will skip any mp3 file and go on recoding the rest.

The recoding is single-threaded. If you have multiple CPU-s, you may split the archive into two parts and run two instances of encoder separately.

---

### Post by GabrielWolff on 2008-04-28
Great, this look *exactly* what I was looking for.

I'll try it and let you know when it'll be done.

---

### Post by GabrielWolff on 2008-04-28
6.run 
```

find . -type f -exec ./recode.sh "{}" ";"

```

A first question before even starting:

How do I change the sample rate/quality of the mp3s? I see no parameters in the script...

---

### Post by disturbedite on 2008-04-28
i use soundkonverter.  it is excellent.

---

### Post by ivze on 2008-04-28
To specify the bitrate you need to add "-b NN" parameter to lame. 

To set a bitrate equal to 112 for the whole batch just modify the script so that it contains the next lines:
...
#lame-converting to mp3
lame -b 112 "$tmp" "$name.mp3"
...

Just modify the script as you need. See "man lame" for more details and fine tunings.

---

### Post by GabrielWolff on 2008-04-29
OK, I tried.

The output was basically two different things: Skipping the mp3 files, and:
```
./recode.sh: line 22: sox: command not found
```

Why was the command not found?
Line 22 is: ```
sox "$rawname" "$tmp"
```

---

### Post by GabrielWolff on 2008-04-29
Sorry, ignore that, there was a problem with my sox installation...

---

### Post by GabrielWolff on 2008-04-29
OK, here are the real problems:

1) The script skipped all folders between the middle of "B" and "R":
```
Skipping ./Black Ox Orkestar - Ver Tanzt (2004)/13.Di Khasene.mp3.
Skipping ./Roberto Aussel - Piazzolla - Cinco Piezas para Guitarra (1996)/01.Campero.mp3.

```
How come? It missed like 70 or 80 folders in the middle... at a second and third try it skipped other folders. But always skipped some...

2) It doesn't recognize flac files:
```
sox soxio: Failed reading `./Bach/Bach - Les Suites pour Violoncelle seul (Jean-Guihen Queyras)/Cd1/05 - Suite N°1 en Sol Majeur V. Menuets I & II.flac': unknown file type `auto'

```
Any clue how I could install that option?

3) It doesn't recognize ogg files:
```
sox soxio: Failed reading `./Il Giardino Armonico - Vivaldi, The Four Seasons/Oboe Concerto op 89 RV 454 2 II.ogg': unknown file type `auto'
```

?

---

### Post by amohanty on 2008-04-29
just a comment, converting files between lossy formats i.e. mp3, ogg, e.t.c will lead to _worse_ sound quality than before. if you have the files in flac or wav that is not a problem. so you might want to reconsider the transcoding effort. 

am

---

### Post by GabrielWolff on 2008-04-29
> **amohanty said:**
> just a comment, converting files between lossy formats i.e. mp3, ogg, e.t.c will lead to _worse_ sound quality than before. if you have the files in flac or wav that is not a problem. so you might want to reconsider the transcoding effort. 

am

I see what you say, and I agree with you: recoding will lead to a loss of quality. But I have to say what no one seems to agree with: that hardly bothers me. The music stays the same; good music isn't downgraded by worse a quality

Plus, let's admit that other when we are editing sound we hardy use equipment with which we actually can hear the difference, do we?

:)

---

### Post by amohanty on 2008-04-29
> **GabrielWolff said:**
> I see what you say, and I agree with you: recoding will lead to a loss of quality. But I have to say what no one seems to agree with: that hardly bothers me. The music stays the same; good music isn't downgraded by worse a quality

Plus, let's admit that other when we are editing sound we hardy use equipment with which we actually can hear the difference, do we?

:)

fair enough :)

am

---

### Post by disturbedite on 2008-04-29
> **GabrielWolff said:**
> I see what you say, and I agree with you: recoding will lead to a loss of quality. But I have to say what no one seems to agree with: that hardly bothers me. The music stays the same; good music isn't downgraded by worse a quality.
no, that isn't correct.  lossy throws away quality no matter what.  that is why the term "lossy" exists.  lossless is the only way to not degrade quality.

---

### Post by GabrielWolff on 2008-05-07
OK, I'm in the middle of converting the files, and here are a few of the issues I experience:

1) The script converts all .m3u file lists in full albums. So the result is folders which have all the tracks separately and then the whole album as one big track.

2) The script gets busy converting .MP3 files into .mp3 files. Confused? So was I. It doesn't recognize the extension when written in capitals and then converts the files within the same format. Guess it adds some loss of sound, but it mainly takes yet more time...

---

### Post by GabrielWolff on 2008-05-07
> **disturbedite said:**
> no, that isn't correct.  lossy throws away quality no matter what.  that is why the term "lossy" exists.  lossless is the only way to not degrade quality.

Yes, you misunderstood me. I am aware of the sound quality issue. I am a musician and sound technician. What I'm saying is: The music quality isn't effected by the sound quality. You could hear outstanding music on a tape someone recorded for you live. It still would be outstanding music. I don't see why everyone makes such a mess of the lossy and non-lossy formats. As long as it's for your own entertainment, you hardly enjoy music simply **because it is recorded in good quality**.

Just think of great recordings you like. Like Jazz? Think of the concert in Massey Hall. Horrible sound quality!! Still one of the biggest moments in western music of the 20th century... :)

---

### Post by GabrielWolff on 2008-05-16
Tried it.

It worked great for a lot of folders, until it started a loop. It wasn't even possible to copy paste the content anymore.

I attach a screenshot of what happend.

Any clue how to fix that? There are still lots of flac and ape files to convert...

G

---

### Post by Nicram on 2008-10-15
> **Jiraya said:**
> Soundconverter is the best choice, no doubt.

Well, I doubt ;)
I've tried many, but _for me_ the best option is **SoundKonverter** (KDE)
"One frontend to rule them* all"
---------------------------------------------------------------------------------------
* various audio converters

---

