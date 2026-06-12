---
title: "getting kino to import ogg correctly (shellscript help needed)"
date: 2008-03-12
forum: Multimedia Production
---

### Post by oskar2000 on 2008-03-12
When I import an ogg video captured with gtk-recordMyDestop to Kino it will sometimes work, but most of the time it will only encode the first 12 frames or so.

I can however convert those ogg files to dv from the command line and then import them to kino with ffmpeg:

```
ffmpeg -i inputmovie.ogg -target ntsc-dv output.dv
```

How can I incorporate this into the script that kino uses to import files - which is located at::

/usr/share/kino/scripts/import/media.sh

and looks like this:
```
#!/bin/sh
# A Kino script that tries to convert anything to raw DV

IN="$1"
OUT="$2"
normalisation="$3"
aspect="$4"
# frequency="$5"
# FFMPEG can only write 48KHz DV audio
frequency="48000"
size=`[ "$normalisation" = "pal" ] && echo "720x576" || echo "720x480"`
pixfmt=`[ "$normalisation" = "pal" ] && echo "yuv420p" || echo "yuv411p"`

sighandler()
{
	kill -KILL $FFMPEG_PID 2> /dev/null
	kill -KILL $AMENCODER_PID 2> /dev/null
	kill -KILL $VMENCODER_PID 2> /dev/null
	exit 0
}
trap sighandler TERM INT

atexit()
{
	rm -f "$AUDIO_FIFO" "$VIDEO_FIFO" 2>&1 >/dev/null
}
trap atexit EXIT

# Use local ffmpeg, if available
which ffmpeg-kino > /dev/null
[ $? -eq 0 ] && ffmpeg="ffmpeg-kino" || ffmpeg="ffmpeg"

# It appears some formats just don't work well with menoder (Ogg Theora)
mencoder_blacklist=$(echo $IN | grep -e '^.*\.\(ogg\)$')

which mencoder > /dev/null
if [ $? -eq 0 ] && [ -z $mencoder_blacklist ]; then
	AUDIO_FIFO="$1".pcm
	VIDEO_FIFO="$1".i420
	rm -f "$AUDIO_FIFO" "$VIDEO_FIFO" 2>&1 >/dev/null
	mkfifo "$AUDIO_FIFO"
	mkfifo "$VIDEO_FIFO"
	
	if [ "$normalisation" = "pal" ]; then
		width=`[ "$aspect" = "4:3" ] && echo "768" || echo "1024"`
		expand=`[ "$aspect" = "4:3" ] && echo "$width:576" || echo "$width:576"`
		ofps="25"
	else
		width=`[ "$aspect" = "4:3" ] && echo "640" || echo "852"`
		expand=`[ "$aspect" = "4:3" ] && echo "$width:480" || echo "$width:480"`
		ofps="30000/1001"
	fi

	mencoder -o "$AUDIO_FIFO" -of rawaudio -ofps $ofps -oac pcm -vf harddup \
		-af channels=2,volnorm,resample=48000:0:1 -ovc copy "$1" &
	AMENCODER_PID="$!"
	
	mencoder -o "$VIDEO_FIFO" -of rawvideo -nosound -ofps $ofps -ovc raw -xy $width -zoom \
		-vf dsize=${expand}:0,scale,expand=${expand},format=I420,harddup "$1" &
	VMENCODER_PID="$!"
	
	$ffmpeg -f s16le -ar 48000 -ac 2 -i "$AUDIO_FIFO" \
		-f rawvideo -pix_fmt yuv420p -r $normalisation -s $expand -i "$VIDEO_FIFO" \
		-s $size -r $normalisation -aspect $aspect \
		-ac 2 -ar $frequency -pix_fmt $pixfmt -y "$OUT" &
	FFMPEG_PID="$!"
	wait $AMENCODER_PID $VMENCODER_PID $FFMPEG_PID

else
	$ffmpeg -i "$IN" -s $size -r $normalisation -aspect $aspect \
		-ac 2 -ar $frequency -pix_fmt $pixfmt -y "$OUT" &
	FFMPEG_PID="$!"
	wait $FFMPEG_PID
fi
```

I'm sorry if this is obvious... I'm not good with shellscript. :sad:

Alternatively... how could I modify the script so it would go through every ogg file in a folder and convert them to a dv file of the same name (for continuity)... of course it can have a different extention, but it needs to be in the same numerical order.

---

### Post by eye208 on 2008-03-12
> **oskar2000 said:**
> I can however convert those ogg files to dv from the command line
Why not use a video editor that handles .ogg files directly?

---

### Post by Creative2 on 2008-03-12
i suggest to install the last version of kino (search getdeb on google) and install it if you havce ffmpeg installed it can do automatically, 

if you want convert many video i suggest to install fuoco tools, on my signature there is the link, and the add files and go in extra--to--kino--pal dv or ntsc dv

---

### Post by oskar2000 on 2008-03-12
> **eye208 said:**
> Why not use a video editor that handles .ogg files directly?

Suggestions welcome!

Both openmovieeditor (latest from subversion) and cinelerra crash if I try to open those files. 
The files seem to be somewhat faulty... The command I gave puts out errors, but continues converting, and the results are usable. Thanks to some guys on linuxquestions.org, I got this working:

```
for input in out.ogg*; do 
   ffmpeg -i $input -target ntsc-dv ${input%.ogg}.dv
done
```
This converts all the ogg files to dv in the folder, and renames them intelligently. I can import the resulting files into kino.

Fuoco Tools looks really nice... thanks for the link!
I was under the impression that I had the latest version of Kino... I did not!. I just got 1.3.0 from getdeb.net, but again... it stops the conversion at frame number 12, and never continues.

---

### Post by Creative2 on 2008-03-12
mmm cinelerra doesn't crash on ogg file how have you installed ? with repository?

---

### Post by oskar2000 on 2008-03-12
> **Creative2 said:**
> mmm cinelerra doesn't crash on ogg file how have you installed ? with repository?

It's been a while since I installed it. It's even possible that I compiled it from source. I have a couple of alien repositories enabled... is there a way to tell where a deb packages is located?
I was wrong by the way... cinelerra does import them correctly, but it crashes a lot during the editing process.



---
diff tells me that there have been some changes to the media.sh in the new version of kino... here's the new one:

```
#!/bin/sh
# A Kino script that tries to convert anything to raw DV

IN="$1"
OUT="$2"
normalisation="$3"
aspect="$4"
# frequency="$5"
# FFMPEG can only write 48KHz DV audio
frequency="48000"
size=`[ "$normalisation" = "pal" ] && echo "720x576" || echo "720x480"`
pixfmt=`[ "$normalisation" = "pal" ] && echo "yuv420p" || echo "yuv411p"`

sighandler()
{
	kill -KILL $FFMPEG_PID 2> /dev/null
	kill -KILL $AMENCODER_PID 2> /dev/null
	kill -KILL $VMENCODER_PID 2> /dev/null
	exit 0
}
trap sighandler TERM INT

atexit()
{
	rm -f "$AUDIO_FIFO" "$VIDEO_FIFO" 2>&1 >/dev/null
}
trap atexit EXIT

# Use local ffmpeg, if available
which ffmpeg-kino > /dev/null
[ $? -eq 0 ] && ffmpeg="ffmpeg-kino" || ffmpeg="ffmpeg"

# It appears some formats just don't work well with menoder (Ogg Theora)
mencoder_blacklist=$(echo $IN | grep -e '^.*\.\(ogg\)$')

# Try mencoder piped to ffmpeg first
which mencoder > /dev/null
if [ $? -eq 0 ] && [ -z $mencoder_blacklist ]; then
	# Create named pipes
	AUDIO_FIFO="$1".pcm
	VIDEO_FIFO="$1".i420
	rm -f "$AUDIO_FIFO" "$VIDEO_FIFO" 2>&1 >/dev/null
	mkfifo "$AUDIO_FIFO"
	mkfifo "$VIDEO_FIFO"
	
	# Compute desired resolution
	if [ "$normalisation" = "pal" ]; then
		width=`[ "$aspect" = "4:3" ] && echo "768" || echo "1024"`
		expand=`[ "$aspect" = "4:3" ] && echo "$width:576" || echo "$width:576"`
		ofps="25"
	else
		width=`[ "$aspect" = "4:3" ] && echo "640" || echo "852"`
		expand=`[ "$aspect" = "4:3" ] && echo "$width:480" || echo "$width:480"`
		ofps="30000/1001"
	fi

	# Run mencoder to decode audio to pipe
	mencoder -o "$AUDIO_FIFO" -of rawaudio -ofps $ofps -oac pcm -vf harddup \
		-af channels=2,volnorm,resample=48000:0:1 -ovc copy "$1" &
	AMENCODER_PID="$!"

	# Run mencoder to decode video to pipe
	mencoder -o "$VIDEO_FIFO" -of rawvideo -nosound -ofps $ofps -ovc raw -xy $width -zoom \
		-vf dsize=${expand}:0,scale,expand=${expand},format=I420,harddup "$1" &
	VMENCODER_PID="$!"

	# Encode from pipes to raw DV
	$ffmpeg -threads 2 -f s16le -ar 48000 -ac 2 -i "$AUDIO_FIFO" \
		-f rawvideo -pix_fmt yuv420p -r $normalisation -s $expand -i "$VIDEO_FIFO" \
		-s $size -r $normalisation -aspect $aspect \
		-ac 2 -ar $frequency -pix_fmt $pixfmt -y "$OUT" &
	FFMPEG_PID="$!"
	wait $AMENCODER_PID $VMENCODER_PID $FFMPEG_PID

	# If file is empty, try straight ffmpeg transcode
	if [ ! -s "$OUT" ]; then
		$ffmpeg -threads 2 -i "$IN" -s $size -r $normalisation -aspect $aspect \
			-ac 2 -ar $frequency -pix_fmt $pixfmt -y "$OUT" &
		FFMPEG_PID="$!"
		wait $FFMPEG_PID
	fi

else
	# If mencoder is not availble, just use ffmpeg
	$ffmpeg -threads 2 -i "$IN" -s $size -r $normalisation -aspect $aspect \
		-ac 2 -ar $frequency -pix_fmt $pixfmt -y "$OUT" &
	FFMPEG_PID="$!"
	wait $FFMPEG_PID
fi
```

---

### Post by Creative2 on 2008-03-12
[http://cv.cinelerra.org/getting_cinelerra.php#ubuntu](http://cv.cinelerra.org/getting_cinelerra.php#ubuntu)

for hardy for example
 
 sudo wget [http://repository.akirad.net/dists/hardy.list](http://repository.akirad.net/dists/hardy.list) -O /etc/apt/sources.list.d/akirad.list
 
 wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install cinelerra

---

### Post by oskar2000 on 2008-03-12
Yup, I have that in my list. So chances are that's where I got it from...
I'll play a little with cinelerra. Maybe it will work out.

---

### Post by eye208 on 2008-03-12
Blender handles .ogg out of the box. Make sure to enable gutsy-backports in software sources to get the latest version (2.45).

The manual is [here](http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing).

---

### Post by oskar2000 on 2008-03-12
I did a bit of editing, and cinelerra crashed on me again...

I love blender... I heard that it has video editing now, but I haven't tried it... I'll give it a shot. Thank's for the tip.


[edit]
well... do you happen to have a link to a tutorial?
I can't quite figure this out. The manual isn't that conclusive either.
And it also crashed once while I was playing around with it. As I said... the ogg movies are faulty, so it is probably not the programs fault that they can't handle them.

---

### Post by eye208 on 2008-03-13
> **oskar2000 said:**
> well... do you happen to have a link to a tutorial?
Yes, but it's old.

[http://wiki.blender.org/index.php/Tutorials/Video_Sequence_Editor](http://wiki.blender.org/index.php/Tutorials/Video_Sequence_Editor)

---

