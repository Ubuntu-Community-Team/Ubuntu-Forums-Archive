---
title: "Script to convert M4a to MP3 - why is it truncating file names?"
date: 2009-06-16
forum: Multimedia Software
---

### Post by raffraffraff on 2009-06-16
Hi all. 

I wrote this script to convert a few thousand m4a file to mp3. But it's doing some really weird stuff, so I thought I'd see if anybody else has encountered it... The script is attached.

It runs fine on some files, but randomly truncates the start of some filenames. This causes it to fail on those files obviously, with a 'file not found' message. I can't see any pattern to this. 

This version of the script uses a while loop, but I also tried a for loop and it did the same thing. It even does it if I 'find' all m4a files and output the list to a tmp file, and then run the script against the tmp file.

Any ideas?

```

# Set directories
music=/media/backup/raffraffraff/Music

#For each m4a, run the loop...
find $music -iname "*.m4a" | while read m4afile; do

	clear

	#Set mp3 file name
	mp3file="${m4afile/.m4a/.mp3}"

	#Get tags
	mp4info "$m4afilei" > /tmp/mp4info
	title=`grep "Name:" /tmp/mp4info | sed 's/ Name: //g'`
	artist=`grep "Artist:" /tmp/mp4info | sed 's/ Artist: //g'`
	album=`grep "Album:" /tmp/mp4info | sed 's/ Album: //g'`
	year=`grep "Year:" /tmp/mp4info | sed 's/ Year: //g'`
	track=`grep "Track:" /tmp/mp4info | awk '{ print $2 }'`
	comment=`grep "Comment:" /tmp/mp4info | awk '{ print $2 }'`
	genre=`grep "Genre:" /tmp/mp4info | sed 's/ Genre: //g'`

	#verbose
	echo "$m4afile"
	echo "$mp3file"
	echo "$track. $artist $title"
	echo "Released in $year"
	echo "$genre"
	echo "Rated: $comment"

	echo "Converting to WAV using MPlayer..."

	#Make wav
	mplayer "$m4afile" -really-quiet -vo null -vc dummy -ao pcm:waveheader:file="/tmp/m4a2mp3.wav"

	echo "Encoding WAV to MP3 with LAME..."

	#Make mp3
	lame --preset standard "/tmp/m4a2mp3.wav" --add-id3v2 --tt "$title" --ta "$artist" --tl "$album" --ty "$year" --tc "$comment" --tn "$track" --tg "$genre" -o "$mp3file"

	echo "Setting ReplyGain..."

	#Correct gain
	aacgain -k -r -s r -d 3 "$mp3file"

	echo "Deleting the original m4a file..."

	#Delete original m4a
	rm "$m4afile"

#End loop
done

```

---

### Post by Bachstelze on 2009-06-16
I added the text of the script to the post to make it easier to read.

---

