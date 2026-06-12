---
title: "HOW T&#927;: Split flac file according to cue and convert to mp3s"
date: 2010-10-28
forum: Multimedia Software
---

### Post by TeoBigusGeekus on 2010-10-28
Many have been the cases when I've come across a single flac file of a whole cd, accompanied by its cue file.
My objective being to split the file to its individual tracks, rename accordingly and convert to mp3s, I made a script to do the job for me. I've found solutions for the tasks separately, but never on a single script.

[COLOR="Red"]1: Dependencies[/COLOR]
The script uses cuetools and shntool to split the flac file. You'll need of course the flac package as well. So:
```
sudo apt-get install cuetools shntool flac
```

[COLOR="#ff0000"]2: Script assumptions[/COLOR]
The script supposes that it functions in a folder containing a log file, a cue file and a flac file.

[COLOR="#ff0000"]3: The script[/COLOR]
```
#!/bin/bash
rm *.log
c="`ls *.cue`"
f="`ls *.flac`"
#split flac according to cue
cuebreakpoints "$c"| shnsplit -o flac "$f"
#create a file - tt - with the songs' titles
sed '1,6'd "$c"|grep TITLE|sed 's/^.\{11\}//g'|sed 's/"//g'|sed 's/.$//'>tt
#rename flacs according to titles in tt
for i in {1..9}
do 
 j=`sed -n ''$i'p' tt`
 echo $j
mv split-track0$i.flac 0$i-"$j".flac
done
for i in {10..99}
do 
 j=`sed -n ''$i'p' tt`
 echo $j
mv split-track$i.flac $i-"$j".flac
done
#delete cue file, flac file, titles file
rm "$f" "$c" tt
#convert flacs to mp3s
for f in *.flac
 do ffmpeg -i "$f" -acodec libmp3lame -ab 320k  "${f%.flac}.mp3"
done
#delete flacs
rm *.flac

```

Firstly, it deletes the unnecessary log file. 

It then splits the flac file according to the cue one. 

A file called tt (dummy file) is created from the cue file with the tracks' titles.

The split flac files are renamed according to the titles in the dummy file.

The initial flac file, the cue file and the dummy file are deleted.

The flac files are converted to mp3s (320k).

The flac files are deleted, thus leaving only the mp3s in the folder.

Save it with whatever name you want, say flac_2_mp3s_320k, make it executable
```
chmod +x flac_2_mp3s_320k
```
paste it in your flac-cue folder and execute it.

_WARNING:_ Come to think of it, better use it on a copy of the original folder, as the script erases everything.

---

### Post by myth88 on 2010-12-25
Many thanks for this one!
I adepted it to not delete FLAC files as I want them just splitted! 

:KS

---

### Post by TeoBigusGeekus on 2010-12-25
> **myth88 said:**
> Many thanks for this one!
I adepted it to not delete FLAC files as I want them just splitted! 

:KS

You're welcome mate.

---

### Post by myth88 on 2010-12-26
Hi, after all I have a problem after splitting the file:

```
sed: -e expression #1, char 3: unknown command: `.'

mv: cannot stat `split-track0{1..9}.flac': No such file or directory
sed: -e expression #1, char 4: unknown command: `.'

mv: cannot stat `split-track{10..99}.flac': No such file or directory
```

---

### Post by vanadium on 2010-12-26
I have a slightly more simple approach for this:
```

shntool split <yourflacfile> -f <yourcuefile> -t '%n - %t' -o 'cust ext=mp3 lame --quiet -V 2 --vbr-new - %f'

```

Perhaps someone has a hint on how to fill the tags in the mp3 files.

For ogg vorbis, the last part can be: 'cust ext=ogg oggenc -q 6 - -o %f'

---

### Post by myth88 on 2010-12-26
Ok, with yours as template I tested a bit and have this now:
```
#!/bin/bash
c="`ls *.cue`"
f="`ls *.flac`"
cuebreakpoints "$c"| shnsplit -o flac "$f" -f "$c" -t '%n. %p - %t'
```

Works great!:popcorn:

---

### Post by intel352 on 2011-06-02
Try Flacon instead, has gui, splits FLAC/APE/CUE to various formats. Found it last night in Software Center, worked perfect.

---

### Post by Dondermans on 2011-07-25
> **intel352 said:**
> Try Flacon instead, has gui, splits FLAC/APE/CUE to various formats. Found it last night in Software Center, worked perfect.

Thank you for the suggestion. With Flacon a lot of the tedious work (like renaming the 'split-file*xx*', copying the files to a separate directory) is automated.

A wonderful tool indeed!

---

