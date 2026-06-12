---
title: "Batch convert entire music directory to 320kbps MP3"
date: 2011-01-02
forum: Multimedia Software
---

### Post by mrwall-e on 2011-01-02
I have a large (~60GB) collection of music in various formats on my hard drive. It is organised in the form Artist/Album/*.ext

The formats include M4A, FLAC, MP3, and OGG. What I would like to do is convert the entire directory, keeping subfolders and ID3 information intact. I would preferably like to be able to do this with a single script.

I am running Ubuntu 10.10 x86_64. I am fairly adept with BASH and the command line, so I foresee no problems there. If I have  to write my own script, these are the things I'm not sure about:

(a) maintaining the directory structure.
(b) how to tell the script which converter tool to use (LAME, FLAC, etc.
(c) keeping ID3 tags.

Thanks

---

### Post by eddier on 2011-01-03
I could be wrong but I think the bit rate is determined at the time of ripping (from a cd/dvd). I'm fairly sure there is no advantage to converting up once the ripping has been done,data has already been dumped.

As for converting from one preset to another the WinFF can work on complete folders.

eddie

---

### Post by dli8ilb on 2011-01-03
hello.  i have used SoundConverter with good results.  it's in the repos, and i believe it will handle exactly what you need..but as eddier said, beware of transcoding one lossy format to another (eg. mp3 to ogg, mp3 to mp3 etc.) as this will cause even more quality loss and result in file bloat.

---

### Post by cascade9 on 2011-01-03
> **eddier said:**
> I'm fairly sure there is no advantage to converting up once the ripping has been done,data has already been dumped.

Right. Lossy-> lossy transcodes will always have worse quality than the original file. It  doesnt matter if the new file is bigger or smaller than the original file.

---

### Post by Bucky Ball on 2011-01-03
If the originals are 320kbps or greater you're fine. If less, you might get some odd results.

---

### Post by mrwall-e on 2011-01-03
If this is the case, (Lossy -> Lossy creates a lower quality file) is there anyway to make then program skip existing MP3's so that there is no quality loss? All I want is my entire library in as HQ as possible MP3's that will work on MP3 players, as I've noticed FLAC/OGG etc. does not.

Thanks

---

### Post by Yellow Pasque on 2011-01-03
Get better MP3 players ;)

---

### Post by Vaphell on 2011-01-03
> If this is the case, (Lossy -> Lossy creates a lower quality file)
it is the case, every time you encode with lossy codec some information is cut off (high frequencies, near zero levels, whatever) and what's been removed is not possible to be restored later, thus quality is degraded.

it's easy to skip mp3s, simply don't include them in the expression selecting the files
here is a quickly googled example how to convert flac to mp3 with a short script, with all the id3 magic and stuff
[https://wiki.archlinux.org/index.php/Convert_Flac_to_Mp3](https://wiki.archlinux.org/index.php/Convert_Flac_to_Mp3)

---

### Post by AlphaLexman on 2011-01-03
I was trying to upgrade my music a while back, and needed to find low bitrate files, compare bitrates of an album recorded in ogg vs mp3, etc.

I ended up writing a script that adds the bitrate to the filename so you know by just looking at the filename if you have a better quality recording or if you want to keep it.

Here is my thread as I figured it out: [here.]("http://ubuntuforums.org/showthread.php?t=1598576")

I never really finished it for all of my goals, but it handled 98% of my mp3 and ogg collection.

Here it the latest version if anyone is interested.

```
#!/bin/bash

# TO_DO:

# maybe add options to the script... 	# would use the 'case' statement.

#	-r	recursive option (no spaces in filenames)
#	-m	mp3 files only
#	-o	ogg files only
#	-s	spaces in filenames

# End TO_DO.

	set -e
	echo "Working..."
	LESSTHAN=0
	NOCHANGE=0
	MP3_TOTAL=$(find . -name "*.mp3" | wc -l)
	OGG_TOTAL=$(find . -name "*.ogg" | wc -l)
	MP3_AND_OGG=$(( $MP3_TOTAL + $OGG_TOTAL )) 
	
# choose SEARCH_METHOD ...

	# use this to recursively search directories
	# will not work if filenames have spaces!
	for FILENAME in $(find . -name "*.mp3" -o -name "*.ogg"); do

	# need to check for symbolic links here.
		#if [[ -f $FILENAME ]]

			#echo something

		#fi

# OR,

	# use this for directory specific,
	# or if filenames have spaces
	#find ./*.mp3 -print | while read FILENAME; do

# end choose SEARCH_METHOD.


		# test if audio file already has bitrate in filename?
		# here we use 'sed' to test the three characters before the
		# extension to see if they are numeric characters or not.
		# some songs will still fail here, like 'REM/Star69.mp3'
		while [[ `echo $FILENAME | sed 's/^.*\(...\)\..*/\1/'` != *[0-9]* ]]

			do

				break
				NOCHANGE=$(( $NOCHANGE + 1 ))

			done

		
		if [[ `echo $FILENAME | sed 's/^.*\(...\)\..*/\1/'` != *[0-9]* ]]; then

			# split filename into the 'base' and 'extenstion'
			BASENAME="${FILENAME%.[^.]*}"
			EXT="${FILENAME:${#BASENAME} + 1}"

			# mp3 or ogg
			if [[ $EXT = "mp3" ]]; then

				# is mp3 file a vbr?
				VBR=$(checkmp3 -v "$FILENAME" 2>/dev/null | \
					grep VBR_AVERAGE | cut -c 21-23) 

				if [[ -n "$VBR" ]]; then

					BITRATE=$VBR
					MP3_VBR_COUNT=$(( $MP3_VBR_COUNT + 1 ))

				else	# CBR

					BITRATE=$(checkmp3 -v "$FILENAME" 2>/dev/null | \
						grep BIT_RATE | cut -c 21-23)	
					MP3_CBR_COUNT=$(( $MP3_CBR_COUNT + 1 ))

				fi


				if [[ $BITRATE -lt 100 ]]; then

					# the '$COLOR' variable(s) come from ~/.bashrc
					LESSTHAN=$(( $LESSTHAN + 1 ))
					echo -e "$CYAN Bitrate is less than 100. $WHITE"
					BITRATE=0${BITRATE:0:2}

				fi

			elif [[ $EXT = "ogg" ]]; then 

			# Choose AVERAGE or NOMINAL bitrate!
			# FIX: make a test for OGG-VBR vs. OGG-CBR!
				
				# AVERAGE Bitrate
					#BITRATE=`ogginfo "$FILENAME" | \
						#grep "Average Bitrate" | cut -c 19-21`

			# OR, ->

				# NOMINAL bitrate
					BITRATE=`ogginfo "$FILENAME" | \
						grep "Nominal Bitrate" | cut -c 18-20`

			
			fi

			#echo -e "$BASENAME.$BITRATE.$EXT " #1>/dev/null
			# remove 'comment' below to ACTUALLY rename files			
			mv -Tv $FILENAME $BASENAME.$BITRATE.$EXT

		fi

	done

	echo	# intentional blank line

	if [[ $MP3_AND_OGG -ne 0 ]]; then	

		echo "    $MP3_AND_OGG	Audio Files"

	else

		echo >&2 "    Could not find any audio files!"
		exit 1

	fi



	if [[ $MP3_TOTAL -ne 0 ]]; then

		echo "    $MP3_TOTAL	MP3"

	fi



	if [[ $MP3_CBR_COUNT -ne 0 ]]; then

		echo "    $MP3_CBR_COUNT	CBR"

	fi



	if [[ $MP3_VBR_COUNT -ne 0 ]]; then

		echo "    $MP3_VBR_COUNT	VBR"

	fi



	if [[ $LESSTHAN -ne 0 ]]; then

		echo "    $LESSTHAN	Sub-Par!"

	fi



	if [[ $OGG_TOTAL -ne 0 ]]; then

		echo "    $OGG_TOTAL	OGG"

	fi



	if [[ $NOCHANGE -ne 0 ]]; then

		echo "    $NOCHANGE	unchanged"

	fi

exit 0


```

---

### Post by Bucky Ball on 2011-01-03
Nice one, AlphaLexman. ;)

---

### Post by AlphaLexman on 2011-01-03
Glad you like it. I take it as a compliment.

Thank you.

---

### Post by cascade9 on 2011-01-04
> **Temüjin said:**
> Get better MP3 players ;)

+1. Lots of the linux friendly media players will play ogg and flac......its the cheapo 'yum cha' and 'corporate' (microsoft, apple, sony, etc) media players that dont support ogg and flac.

---

### Post by Bucky Ball on 2011-01-04
> **cascade9 said:**
> +1. Lots of the linux friendly media players will play ogg and flac......its the cheapo 'yum cha' and 'corporate' (microsoft, apple, sony, etc) media players that dont support ogg and flac.

++1. FLAC all the way for me. I shopped for about two months and ended up with the iAudio7. One purchase I just don't regret. Couple that with some Sennheiser HD555s and ....

Well, FLAC and iAudio rule! ;)

That is not the only one on the block of course, but forget the iPod after that experience! A friend and I did some comparisons one night.

---

### Post by mrwall-e on 2011-01-04
Are there any MP3 players you can specifically recommend? I am looking into getting a new one... These are the sorta specs I'm looking for:

Additional format support (FLAC, OGG, M4A, etc.)
16GB+ capacity
Linux compatible
Fairly good sound quality for nicer headphones.
~$200 USD give or take $30

Thanks... I hope I'm not asking for too much, just interested in your opinions. Honestly I've been looking at the Sansa Clip, but they only go up to 8GB.

Thanks again

PS. Nice script. I've been looking through my library more and realised only a couple artists have FLAC album, but one of these artists has ~20GB of FLAC files. I'm hoping to do a script that transfers ID3 information, and just converts those two artists. My only problem would be recursively doing it... One of the artists has like 10+ albums.

---

### Post by Bucky Ball on 2011-01-04
As mentioned, this is what I have.

[http://www.cowonglobal.com/](http://www.cowonglobal.com/)

FLAC, brilliant sound, I have the 8Gb version but there is a 16Gb. Should be about the price you mention, works out of the box with Linux (and Windows and Mac for that matter).

---

### Post by cascade9 on 2011-01-05
iRiver e100/150/200 would do it. Only avaible in 2, 4 and 8GB models, but you can use mircoSD cards (up to 8GB) to expand the memory. They are really cheap these days. 

BTW, I havent tried the e150 or e200 with linux. If they have the same mode as the e100 there should be no problems (a quick search showed me that the e150 should be fine, but the e200 I still dont know about).

---

### Post by Bucky Ball on 2011-01-05
iRiver, they are cheap. And you get what you pay for. Not impressed with them but then I'm a bit of an audiophile.

---

### Post by cascade9 on 2011-01-06
> **Bucky Ball said:**
> iRiver, they are cheap. And you get what you pay for. Not impressed with them but then I'm a bit of an audiophile.

Not all iriver players have the same sound quality.......even the 'bad' ones arent that bad, I've use older branded media players and generic 'yum cha' players with far worse sound.

---

### Post by shantiq on 2011-01-06
_**To mp3 320kbps (lossy)** _(here from flac but simply replace word flac by name of codec you start from)

  cd to where the files are in your terminal then run

```
for f in *.flac; do ffmpeg -i "$f" -ab 320k "${f%.flac}.mp3"; done

```



ok and then adding ogg and m4a of course as someone pointed out already no point in converting from lower kbps to 320 so i discount mp3 here

```
for f in *.flac , *.m4a , *.ogg ; do ffmpeg -i "$f" -ab 320k "${f%.flac}.mp3"; done

```




and then you need to find someone who knows how to write a line to say go into every folder to do this

beyond my very limited competence    but i guess easy    hope someone writes it here :KS:KS:KS

had to do this this morning to get stuff onto my mp3 player
altho on my machine i deem mp3 to be too "thin" and always rip to lossless


[COLOR="Sienna"]but i think one more line of code for entering **ALL** folders in your music folder and you are good to go
[/COLOR]
**ps**   this


if you want to delete the original files add
```
&& rm "$f"

```   before ```
; done
```    to complete the line


from h[ere]("http://ubuntuforums.org/showthread.php?t=1609760")   funny i added that line today hours before i saw your post

---

### Post by mrwall-e on 2011-01-08
Thanks for all your replies. I have found a script ([music-collection-sync]("http://code.google.com/p/music-collection-sync/"))that does this sorta thing, and I wish I had found it earlier. It finds various file types and if they're FLAC converts them to mp3, etc. Otherwise they copy over.

Thanks,

Walter

---

