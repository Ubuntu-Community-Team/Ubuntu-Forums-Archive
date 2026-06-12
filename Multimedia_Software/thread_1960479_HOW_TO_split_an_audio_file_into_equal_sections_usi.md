---
title: "HOW TO split an audio file into equal sections using SoX??"
date: 2012-04-17
forum: Multimedia Software
---

### Post by shantiq on 2012-04-17
ok so far i have used this kind of code to split a six hour file into 6 one hour

>       sox input.mp3 1output.mp3 trim 0 60:00 && sox input.mp3 2output.mp3 trim 60:00 60:00 && sox input.mp3 3output.mp3 trim 1:20:00 60:00 && sox input.mp3 4output.mp3 trim 1:80:00 60:00 && sox input.mp3 5output.mp3 trim 2:40:00 60:00 && sox input.mp3 6output.mp3 trim 3:00:00 60:00


but there must a neater way to do this    thing is i cannot understand the syntax given in man sox

any of you do?

> trim {[=|&#8722;]position}

Cuts portions out of the audio. Any number of positions may be given; audio is not sent to the output until the first position is reached. The effect then alternates between copying and discarding audio at each position.

If a position is preceded by an equals or minus sign, it is interpreted relative to the beginning or the end of the audio, respectively. (The audio length must be known for end-relative locations to work.) Otherwise, it is considered an offset from the last position, or from the start of audio for the first parameter. Using a value of 0 for the first position parameter allows copying from the beginning of the audio.

All parameters can be specified using either an amount of time or an exact count of samples. The format for specifying lengths in time is hh:mm:ss.frac. A value of 1:30.5 for the first parameter will not start until 1 minute, thirty and ½ seconds into the audio. The format for specifying sample counts is the number of samples with the letter ‘s’ appended to it. A value of 8000s for the first parameter will wait until 8000 samples are read before starting to process audio.



what i mean is something simplified as in those here Ron999 showed for [video]("http://ubuntuforums.org/showpost.php?p=11842769&postcount=1")

ie

> MP4Box -split 900 filename.mp4
> 
mkvmerge -o new_filename.mkv --split 900s filename.mkv


There has to be a way there. I simply cannot see it ...

---

### Post by ron999 on 2012-04-17
> **shantiq said:**
> 
There has to be a way there. I simply cannot see it ...
Hi
I don't know how to do the job with SoX.
Maybe there is a tool specifically for mp3...
but in the meantime **mkvmerge** and **mkvextract** will do it.

Split the mp3 file into 1 hour **mka** files:-
```
mkvmerge -o output.mka --split 3600s input.mp3
```

Then extract them all:-
```
for f in *.mka; do mkvextract tracks "$f" 1:${f%.mka}.mp3; done
```

---

### Post by shantiq on 2012-04-18
Thanx Ron interesting;   but of course here simply seeking a solution for native mp3


Another thing that is amazing about simply those video cutting programs is how quick it is
Almost instant

the long line i use with sox takes forever


i think it reencodes every section   :KS

---

### Post by Yellow Pasque on 2012-04-18
mp3splt is for splitting mp3's without reencoding.
```
sudo apt-get install mp3splt
```

---

### Post by flurospar on 2012-04-18
Or even ffmpeg!

Install it:
```

sudo apt-get install ffmpeg ubuntu-restricted-extras

```

Then, trim the file:
```

ffmpeg -ss [hh]:[mm]:[ss].[ms] -t [sec] -i [filename] -acodec copy [output_file]

```

where:

"-ss [hh]:[mm]:[ss].[ms]" (ms for millisecond) states the starting position.

"-t [sec]" is the number of seconds of the media that should be extracted.

---

### Post by shantiq on 2012-04-18
> **Temüjin said:**
> mp3splt is for splitting mp3's without reencoding.
```
sudo apt-get install mp3splt
```



[SIZE="3"]**thnk you Temüjin**[/SIZE]   exactly what the doctor ordered   Takes about 10 seconds since no re-encode

to split in 1 hour sections


```
mp3splt -f -t 60.0 -a -d split inputfile.mp3
```


**[extra info click!]("http://wiki.librivox.org/index.php/How_To_Split_With_Mp3Splt")**   

> All the command line options are listed farther below. Here's an explanation of the recommended options: 

-f: for MP3 files only, increases precision and is needed if the MP3 files are variable bit rate (VBR). 

-t TIME: specifies the length, measured in time, to make each piece. You will replace `TIME` with a numerical value expressed in minutes, such as 4.0 for four minutes or 7.30 for seven minutes, thirty seconds. In our example, we picked four minute pieces, so the command line will be 

```
mp3splt -f -t 4.0 -a -d split *.mp3

```
-a: automatically adjusts the split points to occur during silences, which avoids splitting in the middle of a word. 
Therefore, the pieces will vary in their exact length. 

-d split: writes the split files to a sub-folder named split(you may pick any name you wish). The folder will be created if it doesn't already exist. It's more convenient if you don't put the split files in the same folder with the original ones. 

*.mp3: process all the MP3 files in the current folder. If you are splitting Ogg Vorbis files, change this to *.ogg.



will even cut it to hundredth of a second   here 4 minutes 30 seconds 55/100 second  :KS:KS


```
mp3splt -f -t 4.30.55 -a -d split inputfile.mp3

```



> EXAMPLES

mp3splt album.mp3 54.32.19 67.32 -o out 
mp3splt album.ogg 54.32.19 67.32 -o out

This is the standard use of mp3splt for constant bitrate mp3 or for any ogg. You specify a begin time (which in this case uses hundredths, 54.32.19), an end time and an output file.

mp3splt -f -d newdir album.mp3 album2.mp3 145.59 234.2

This is frame mode for variable bitrate mp3 and multiple files. You can see that time format uses min.sec even if minutes are over 60. Output files in this case will be: album_145m_59s_0h__234m_2s_0h.mp3 and album2_145m_59s_0h__234m_2s_0h.mp3 because user didn't specify it and they will be in the directory named newdir.

mp3splt -nf album.mp3 0.12 21.34.7 25.3 30.40 38.58

This is the use of -n option and multiple splitpoints. Four files will be created and will not contain ID3 informations.

mp3splt -w album_MP3WRAP.mp3

This is Wrap mode. You can use this when mp3 is a file wrapped with Mp3Wrap or AlbumWrap. You can specify an output directory with the -d option.

mp3splt -lq album.mp3

This is List mode. You can use this when you want to list all tracks of a wrapped file without extracting them. With quiet option (-q), program will not calculate CRC!

mp3splt -s f.mp3 or mp3splt -s -p th=-50,nt=10 f.mp3

This is silence option. Mp3splt will try to automatically detect splitpoints with silence detection and in the first case will split all tracks found with default parameters, while in the second 10 tracks (or less if too much) with the most probable silence points at a threshold of -50 dB.


mp3splt -a -c file.cddb album.mp3

This is CDDB mode with auto-adjust option (default parameters). Splitpoints will be adjusted with silence detection in a range of 30 seconds before and after cddb splitpoints.

mp3splt -a -p gap=15,th=-23,rm -c file.cddb album.mp3

This is CDDB mode with auto-adjust option. Splitpoints will be adjusted with silence detection in a range of 15 seconds before and after cddb splitpoints, with a threshold of -23 dB, and silence will be removed.

mp3splt -c query album.mp3 -n -o @n_@t

This is CDDB mode with internet query with Frame mode, NoID3 and Output format. Output filenames will be named like: 01_Title.mp3

mp3splt -t 10.00 album.mp3

This is -t option. It will split album.mp3 in many files of 10 minutes each.  



---

### Post by Ferralll on 2012-04-18
I just made a simple batch file to do this using sox
NOTE: I am not that much of a programmer for these things, so I am sure that there is a better way to do this.  But this is the one that I wrote.


You just have to find the length of your file and put that in length.  Then set 
"track" to the length that you want.

Then just set your file names.  (I was doing DUNE_II in this one)

```

track=3600
j=$track
length=95422
for ((  i = 0 ;  i <= length;  i= i+$j  ))
do
	if test `expr $i + $j` -gt $length
	then
		echo "too long need to change j to `expr $length - $i`  "
		j=$(( length - i ))
		echo "j is $j should be zero `expr $i + $j - $length`"
	fi
	if test `expr $i / $track + 1` -lt 10
	then 
	     number="0`expr $i / $track + 1`"
	else
	     number="`expr $i / $track + 1`"
	fi

 	 echo "track $number start at $i end at `expr $i + $j` "
	 sox DUNE_II.mp3 DUNE_II_$number.mp3 trim $i $j
	 j=$track

done

```

---

