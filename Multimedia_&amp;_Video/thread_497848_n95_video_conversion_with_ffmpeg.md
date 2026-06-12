---
title: "n95 video conversion with ffmpeg"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by Verlaine on 2007-07-10
I knocked together this little script to convert videos for the nokia n95.

I used the replacement version of ffmpeg from medibuntu follow the section "Fixing ffmpeg on Ubuntu" [https://help.ubuntu.com/community/iPodVideoEncoding]("https://help.ubuntu.com/community/iPodVideoEncoding")


the ffmpeg setting are as follows.

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
```

and the script itself is n95enc

```

#! /bin/bash
clear
if [ -n "$1"]; then
	echo "please specify file to convert"
	
else

	if [ -n "$2"]; then
		newName=$(echo $1 | cut -d '.' -f1)
	
	else
		newName=$2
	fi

	echo "coverting $1 to $newName.mp4"

	ffmpeg -i "$1" -f mp4 -vcodec mpeg4 -b 250000 -r 15 -s 320x240 -acodec aac -ar 24000 -ab 64 -ac 2 "$newName.mp4"

fi

``` 

usage is very simple 

```
n95enc input-filename output-filename 
```

The output filename is optional if none is given it defaults to the same file name as the original.

Hope this useful to someone took me a while googling to put it together.

---

### Post by DaveQB on 2008-01-08
I'll give this a whirl, I am not sure which ffmpeg I have atm.  I guess I'll find out soon enough :-)

---

### Post by DaveQB on 2008-02-19
A few errors in the script

lines 4 and 7 need spaces added:

"$1"] needs to become "$1" ]

and

"$2"] needs to become "$2" ]

Also, testing -n means NOT null, meaning its testing if the variable (in this case $1) has a value, that is, not null, and if it does hold a value, it echo's "please specify file to convert" and exits.

Just got an encode going now, I am very curious to see how it turns out.

Thanks for the script, I am going to intergrate it into my Video Swiss Army Knife script I have.

---

