---
title: "Target bitrate for gtkpod FLAC converter"
date: 2009-06-24
forum: Multimedia Software
---

### Post by ricardisimo on 2009-06-24
gtkpod has finally gotten it's on-the-fly FLAC-to-mp3 converter working properly, which is great. However, I'm noticing that its target bitrate seems a bit low. It just seems a shame to take a FLAC file and shrink it below 192 average bitrate, and sometimes well below. Personally, I'd prefer an average between 224 and 256.

Is there a way to edit the script that performs this conversion? Thanks.

---

### Post by ricardisimo on 2009-06-24
Hmmm... I can't even find the script any longer. It used to be "convert-flac2mp3.sh", but it has either been renamed, or it's no longer done by shell script. Does anyone know which?

---

### Post by ricardisimo on 2009-06-24
Found it... "gtkpod-convert-common.sh"

Here's what I believe are the pertinent parts:
```
# The following command line arguments are being used
#
#       -x      Print converted filename extension and exit
#       -f      Set converted filename
# 	-a	Artist tag
#	-A 	Album tag
#	-T	Track tag
#	-t	Title tag
#	-g	Genre tag
#	-y	Year tag
#	-c	Comment tag
[COLOR="Red"]**#	-q	Quality (overwrites standard encoder options)**[/COLOR]
#               For mp3 files this could be "--vbr-new -V<number>".
```
and...
```
# Get parameters
while getopts q:a:A:T:t:g:c:y:f:x opt ; do
	case "$opt" in
	        x)      echo "$extension"; exit 0 ;;
	        f)      outfile="$OPTARG" ;;
		a)	artist="$OPTARG" ;;
		A)	album="$OPTARG" ;;
		T)	track="$OPTARG" ;;
		t)	title="$OPTARG" ;;
		g)	genre="$OPTARG" ;;
		y)	year="$OPTARG" ;;
		c)	comment="$OPTARG" ;;
**[COLOR="Red"]		q)	ENCODER_OPTS="$OPTARG" ;;[/COLOR]**
	        ?)      exit 7 ;;
	esac
done
shift $(($OPTIND - 1))
```
So, what number should I be putting in where it should say "V<number>", but where it actually says "ENCODER_OPTS='$OPTARG'"? What's the syntax? Is it just a plain old number, like "8"? Thanks.

---

### Post by shirilover on 2009-06-24
You would probably want to use --vbr-new -V0.

---

### Post by ricardisimo on 2009-06-25
0? Really? In the gstreamer pipeline options in rhythmbox, for example, it reads
```
vbr-quality=6
```
0 seems either a bit high or way too low. Is zero at the high end or low?

---

### Post by mc4man on 2009-06-25
the -V parameter is 0-9 with 0 being highest quality. 9 the lowest

What you could do is test for youself and see what works for you

A simple way would be to create a test folder, put a flac in it and then cd to it in a terminal.
Then use flac to decode to .wav (flac -d [COLOR="Blue"]filename[/COLOR].flac ) and use lame to encode some .mp3's using various -V [COLOR="Red"]n[/COLOR]'s and see what your happy with

basic lame encode line
 > lame [COLOR="Blue"]filename[/COLOR].wav -V[COLOR="Red"]3[/COLOR]  [COLOR="Blue"]filename[/COLOR].mp3

---

### Post by ricardisimo on 2009-06-25
Cool. Now, just to be clear, I'm only replacing the text that says
```
$OPTARG
```
and I'm leaving everything else untouched, including the quotation marks. Correct?

---

### Post by mc4man on 2009-06-25
> Now, just to be clear, I'm only replacing the text that says

Personally would have no clue, never used gtkpod before (convert and encode to mp3 thru some scripts I made, add w/ amarok to ipod.

Did just now install gtkpod (hardy) and w/ your proposed edit no good, wouldn't encode.

Then removed gtkpod and installed gtkpod-aac. In this case /usr/share/gtkpod-aac/scripts/convert-2mp3.sh had an obvious line to edit and the conversion went as expected. 
(used -V 0 though for an ipod  a higher -V (2 or3 ) would probably be fine. (note  that you can use any valid lame parameters (see lame --longhelp

From gtkpod-aac conversion log

> 02 - Summertime.flac: done         
LAME 3.98 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: MMX (ASM used), SSE (ASM used), SSE2
Using polyphase lowpass filter, transition band: 19383 Hz - 19916 Hz
Encoding <stdin>
      to /home/doug/.gtkpod/conversion_cache/Porgy & Bess/Summertime_02-0x87083b0-0.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III VBR(q=0)

from /usr/share/gtkpod-aac/scripts/convert-2mp3.sh 


> # Constants
extension="mp3"
ENCODER_OPTS="[COLOR="Blue"]-V 0[/COLOR]"
ENCODER="lame"


---

### Post by ricardisimo on 2009-06-26
Excellent! Thank you. But what about the first part of that line? The part that says "--vbr-new"? Will it still encode in variable bitrate without that tidbit?

---

### Post by shirilover on 2009-06-26
Yes, it will still be VBR.
-V 0 should give ~245 kbps.
For more information regarding LAME settings, look here -> [http://wiki.hydrogenaudio.org/index.php?title=LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME)

---

### Post by ricardisimo on 2009-06-26
Very cool. Thanks again.

Somewhat related, but not really: why do all of the Gnome CD-ripping apps rip to mp3 at 128 CBR no matter what options you enter?

---

