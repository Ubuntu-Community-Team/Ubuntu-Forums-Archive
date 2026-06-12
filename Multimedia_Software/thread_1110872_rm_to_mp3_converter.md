---
title: "rm to mp3 converter"
date: 2009-03-30
forum: Multimedia Software
---

### Post by freezashu on 2009-03-30
can anyone help me to get a software to convert rm to mp3... thanks in advance

---

### Post by freezashu on 2009-03-30
tht is video converter right... i want a audio converter to convert rm to mp3..... can u send me a link.... i'm not able to find it

---

### Post by stumbleUpon on 2009-03-30
> **freezashu said:**
> can anyone help me to get a software to convert rm to mp3... thanks in advance

This is a script i wrote sometime back to convert an rm file to an mp3 file. It uses mplayer and lame (both installable from ubuntu repositories). The script converts the rm file to an intermediate wav file using mplayer and then finally to an mp3 file using lame.

Save the code below as a file named 'rm2mp3'. Make it executable by
chmod +x rm2mp3. Then in a terminal rm2mp3 filename.rm to get an mp3 file named filename.mp3


#!/bin/sh
inputfile=$1
inputfilename=`basename $1 rm`
ext='mp3'
outputfilename=$inputfilename$ext

echo 'CONVERTING TO WAV FORMAT' 
mplayer $inputfile -ao pcm

echo 'CONVERTING WAV FORMAT TO MP3'
lame -h -b 256 audiodump.wav $outputfilename

rm -f audiodump.wav

echo 'DONE...!'

---

### Post by logos34 on 2009-03-30
> **stumbleUpon said:**
> This is a script i wrote sometime back to convert an rm file to an mp3 file.

I get an error:

> user@ubuntu:~/audio$ **~/./rm2mp3.sh**
CONVERTING TO WAV FORMAT
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 2600+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
CONVERTING WAV FORMAT TO MP3
[COLOR="Red"]Could not find "audiodump.wav".[/COLOR]
DONE...!

Any ideas?

---

### Post by andrew.46 on 2009-03-30
Hi,

Looks like a piece is missing from here:

```
echo 'CONVERTING TO WAV FORMAT' 
mplayer $inputfile -ao pcm
```

I suspect it should be something like:

```
echo 'CONVERTING TO WAV FORMAT'
mplayer $inputfile -vc null -vo null -ao pcm:fast:waveheader:file=audiodump.wav
```

Plus I have added some frills as well :-). Incidentally if you alter the 'basename' naming strategy this should work for all media files that MPlayer can play. Can 'basename' take regexp?

Andrew

---

### Post by SuperSonic4 on 2009-03-30
I'm guessing this would work as a general converter by changing rm to say m4a in line 3?

---

### Post by FakeOutdoorsman on 2009-03-30
You can use FFmpeg as well, but first you will need to install the **libavcodec-unstripped-51** package if you're using Intrepid (it is included in the ubuntu-restricted-extras metapackage):
```
ffmpeg -i input.rm -acodec libmp3lame -ab 96k output.mp3
```
Adjust the bitrate (-ab) as necessary. If omitted FFmpeg will use a default of 64 kb/s.

---

### Post by andrew.46 on 2009-03-30
Hi,

Well it is just a start but the following modification of stumbleUpon's script should work with *any* audio file that MPlayer can handle, convert it to mp3 and name it properly:

```

#!/bin/sh

inputfile=$1
inputfilename=$(echo $1 | sed 's/\.[^.]*$//')
ext='.mp3'
outputfilename=$inputfilename$ext

echo 'CONVERTING TO WAV FORMAT'
mplayer $inputfile -vc null -vo null -ao pcm:fast:waveheader:file=audiodump.wav

echo 'CONVERTING WAV FORMAT TO MP3'
lame -h -b 256 audiodump.wav $outputfilename

rm -f audiodump.wav

echo 'DONE...!'

```

But this could all do with some tidying up. Any offers? 

Andrew

---

### Post by logos34 on 2009-03-30
> **andrew.46 said:**
> Hi,

Well it is just a start but the following modification of stumbleUpon's script should work with *any* audio file that MPlayer can handle, convert it to mp3 and name it properly:


i keep getting the same error...must be my machine or somehting

---

### Post by andrew.46 on 2009-03-30
Hi logos34,

> **logos34 said:**
> i keep getting the same error...must be my machine or somehting

The way stumbleUpon has set his script (and I have not altered this part) you need to give the filename of the input media file as well. So the commandline would actually be:

```
rm2mp3.sh **[COLOR="Red"]myfile.rm[/COLOR]**
```

Then all should work as long as the paths are correct. The sed magic I added simply strips off the *final* '.' and everything following it = effectively the suffix. This enables the script to convert *all* audio files playable by MPlayer to mp3 rather than *only* .rm. It all works quite nicely and I have filed it away for future work. Thanks for that stumbleUpon :-).

Andrew

---

### Post by logos34 on 2009-03-30
> **andrew.46 said:**
> Hi logos34,



The way stumbleUpon has set his script (and I have not altered this part) you need to give the filename of the input media file as well. So the commandline would actually be:

```
rm2mp3.sh **[COLOR="Red"]myfile.rm[/COLOR]**
```


oh, I was using wildcard...Thnx, I'll try again

---

### Post by andrew.46 on 2009-03-30
Hi logos34,

> **logos34 said:**
> oh, I was using wildcard...Thnx, I'll try again

I have added a little 'catcher' to remind people to use a filename:

```

#!/bin/sh

inputfile=$1
inputfilename=$(echo $1 | sed 's/\.[^.]*$//')
ext='.mp3'
outputfilename=$inputfilename$ext

if [ -z "$1" ]; then
	echo "Usage: rm2mp3.sh <filename>"
	exit 1
fi

echo 'CONVERTING TO WAV FORMAT'
mplayer $inputfile -vc null -vo null -ao pcm:fast:waveheader:file=audiodump.wav

echo 'CONVERTING WAV FORMAT TO MP3'
lame -h -b 256 audiodump.wav $outputfilename

rm -f audiodump.wav

echo 'DONE...!'

```

I really have to leave this alone, I have always found shell scripts a little addictive :-).

Andrew

---

### Post by mc4man on 2009-03-30
I don't know why you wouldn't just use a simple for loop and not worry about filenames.

if the limitations of ffmpeg's mp3 encoding aren't an issue then then main command of your script could simply be (red is editable

```
for f in *.rm; do ffmpeg -i "$f" -ab [COLOR="Red"]128[/COLOR]k  "${f%.rm}.mp3"; done

```

Or to use lame then first go to .wav, then call lame the same way

```
for f in *.rm; do ffmpeg -i "$f" "${f%.rm}.wav"; done
```
or
```
for f in *.rm; do mplayer "$f" -ao pcm:fast:waveheader:file="${f%.rm}.wav"; done
```

you could then structure your script to do whatever you want
simple example with mplayer to wav to mp3, no tags, remove .wav

```
#!/bin/bash
for f in *.rm; do mplayer "$f" -ao pcm:fast:waveheader:file="${f%.rm}.wav"; done
mkdir [COLOR="Red"]temp[/COLOR]
for f in *.wav; do lame [COLOR="Red"]--vbr-new -V2  -q 2[/COLOR] "$f" ./[COLOR="Red"]temp[/COLOR]/"${f%.wav}.mp3"; done
rm *.wav
```

you could certainly expand upon that to include tagging the mp3's with some simple echo and reads to set tag info and finish with an id3v2 loop

(the lame end of my current conversion scripts for untagged sources sets artist, album, trackname, track number, genre and year from a batch convert
The same idea works for pretty much any source mat. (with the exception for me of .flac which being already tagged can be decompressed and piped directly to lame/id3

---

### Post by andrew.46 on 2009-03-30
Hi mc4man,

But the beauty of the little script I have been tinkering with is that not only does it neatly alter the filenames, which I will admit is purely cosmetic, but it will accept input from *multiple* audio types, not just .rm files and then cleanly output all of these filetypes to mp3.

I can see that your script could easily be altered to cater for any such files but my revised script (thanks again stumbleUpon!) requires no such alteration. Mind you your version actually addresses what the OP was after while I am increasingly branching off on my own tangent :-).

All the best,

Andrew

---

### Post by stumbleUpon on 2009-03-31
@andrew.46

Thanks for pointing out the missing part in the conversion to wav file. That part had missed out during the copy-paste process. You are welcome to modify the script as you want. And yes it can be used to convert any supported audio format to mp3.


Thanks to everyone else for such a lot of interest in this little script...!! :)

---

### Post by naderb on 2009-04-11
there is a program called SoundConverter 1.3.2 
can convert any audio file even RM file to MP3 or wave 
its easy to use 
you can get it from synaptic 

after installing it from the edit >> preferences >>
and you will find everything you need just there 

Enjoy,

---

### Post by andrew.46 on 2009-04-17
Hi,

Well I have set a little time here and there to work on this script and the very barest bones are in place now. It needs a decent clean out, the encoding options optimised and the if syntax tightened up. But I would love comments on beta 1 :-).

```

#!/bin/sh

# ----------------------------------------------------------------- #
#
#        The synax is: convert2.sh <filename> <format>
#
# This little script exploits the svn MPlayer's ability to playback 
# almost any audio file. The script then converts the file to high 
# quality mp3, ogg or m4a. 
#
#   Requirements are:
# 
#      1. The svn MPlayer
#      2. lame 3.98 for mp3 encoding
#      3. oggenc for ogg encoding
#      4. faac 1.28 for aac encoding
#
#      Formats supported:  mp3, ogg, m4a.
#           
# ----------------------------------------------------------------- #

INPUTFILE=$1
EXT=$2
INPUTFILENAME=$(echo $1 | sed 's/\.[^.]*$//')
OUTPUTFILENAME=$INPUTFILENAME.$EXT
MPLAYEROPTS='-vc null -vo null -ao pcm:fast:waveheader'
LAMEOPTS='--preset fast standard'
OGGOPTS='-q 5'
FAACOPTS='-q 200 -c 22000 -w -s'

# ----------------------------------------------------------------- #

#--> Can the input file be found?
if [ ! -f "$1" ] 
then
    echo "I cannot find '$1'. Please check your path..."
    exit 
fi

#--> Have 2 fields been given?
if [ $# -ne 2 ] 
then
    echo "Usage: convert2.sh <filename> <format>"
    exit
fi

#--> Is the extension requested valid?
if [ "$2" != mp3 ] && [ "$2" != ogg ] && [ "$2" != m4a ] 
then
    echo "I cannot convert to '$2'. Valid options are 'mp3','ogg' or 'm4a'"
    exit
fi

set -e

# ----------------------------------------------------------------- #

mplayer $INPUTFILE $MPLAYEROPTS:file=audiodump.wav

# ----------------------------------------------------------------- #

if [ $2 = mp3 ]; then
   lame $LAMEOPTS audiodump.wav $OUTPUTFILENAME
fi 
if [ $2 = ogg ]; then
   oggenc $OGGOPTS audiodump.wav -o $OUTPUTFILENAME
fi

if [ $2 = m4a ]; then
   faac $FAACOPTS -o $OUTPUTFILENAME audiodump.wav
fi

# ----------------------------------------------------------------- #

rm -f audiodump.wav

echo 'Enjoy your music!!!'


```

I am going to potter around with this every now and then when I have a bit of free time I suspect but the general idea is there: take any audio format that MPlayer can address and convert it.

Andrew

---

### Post by FakeOutdoorsman on 2009-04-17
Nice script, Andrew.  Does *-h -b 256* create CBR mp3?  According to [Hydrogenaudio Knowledgebase - LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME):
> CBR encoding is not efficient. Whereas VBR and ABR modes can supply more bits to complex music passages and save bits on simpler ones, CBR encodes every frame at the same bitrate.
Would a better option be -V4 or -V3?  I'm just guessing here since I don't use lame often.

---

### Post by andrew.46 on 2009-04-17
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> Nice script, Andrew.  Does *-h -b 256* create CBR mp3?  According to [Hydrogenaudio Knowledgebase - LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME):

Would a better option be -V4 or -V3?  I'm just guessing here since I don't use lame often.

Well I would estimate he script is about 15% complete :-). The Lame settings I very lazily absorbed straight from stumbleUpon's original short script and you are quite correct VBR is better. I have altered my own post above to reflect this + added version numbers to Lame as it looks like there have been some changes.

Can I say that I am enjoying playing with this script immensely :-). Next project is to look into encoding with faac 1.28 as the options I have used are guess-timates really.

Andrew

---

### Post by bdsatish on 2010-02-13
This thread is dormant, but hey, thanks to all ! 
It works like a charm !

---

### Post by Swagman on 2010-09-23
I've just looked in the prefs of sound converter and RM is not listed ?

---

