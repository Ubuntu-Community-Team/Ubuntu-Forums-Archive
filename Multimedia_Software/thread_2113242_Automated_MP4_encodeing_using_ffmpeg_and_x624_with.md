---
title: "Automated MP4 encodeing using ffmpeg and x624 with hardsubing and chapters insertion."
date: 2013-02-06
forum: Multimedia Software
---

### Post by Wolfpup on 2013-02-06
See here for how I started : [http://ubuntuforums.org/showthread.php?t=2112462](http://ubuntuforums.org/showthread.php?t=2112462)

Using the recommendations there i now have this script:
```

#!/bin/bash
vidfile='<show name and number>'
mkvextract chapters -s $vidfile.mkv > $vidfile.txt
ffmpeg -i $vidfile.mkv -map 0:s:0 <show name and number>.ass
ffmpeg -i $vidfile.mkv -vf "ass=<show name and number>.ass" -c:v libx264 -profile:v high -level 4.1 -crf 18 -preset veryslow -tune animation -deblock -2:-2 -x264opts qpmin=10:qpmax=28:aq-mode=2:no-mbtree:threads=auto -c:a copy $vidfile.mp4 2>&1 | tee $vidfile-enc.log

```Here is my problem now. I get mkv anime shows from different sub groups and I'm wanting to make the above script more generic so i can put in a centralized bin folder for running.
Example of file name ( some file names have '_' instead of ' ' in the file name):[INDENT][<fansub group name>] <show name> - <eposide number> [<bit depth>][<resolution>][<crc number>].mkv

or

[<sub group>]_<show name>_-_<epnumber>_[<v pix>x<h pix>][<crc>].mkv
[/INDENT]Example file contents(generated using mkvmerge --identify  on one of the files I currently have):
```

File '[<sub group>]_<show name>_-_<epnumber>_[<v pix>x<h pix>][<crc>].mkv': container: Matroska
Track ID 1: video (V_MPEG4/ISO/AVC)
Track ID 2: audio (A_AAC)
Track ID 3: subtitles (S_TEXT/ASS)
Attachment ID 1: type 'application/x-truetype-font', size 75156 bytes, file name 'Caxton_Book_BT.ttf'
Attachment ID 2: type 'application/octet-stream', size 5872144 bytes, file name 'DFKKS9.TTC'
Attachment ID 3: type 'application/octet-stream', size 5754084 bytes, file name 'KaiC_0.ttc'
Attachment ID 4: type 'application/x-truetype-font', size 98272 bytes, file name 'TektonPro-Bold.otf'
Attachment ID 5: type 'application/x-truetype-font', size 97260 bytes, file name 'TektonPro-BoldCond.otf'
Attachment ID 6: type 'application/x-truetype-font', size 99808 bytes, file name 'TektonPro-BoldExt.otf'
Attachment ID 7: type 'application/x-truetype-font', size 111532 bytes, file name 'TektonPro-BoldObl.otf'
Attachment ID 8: type 'application/x-truetype-font', size 65492 bytes, file name 'UVNThangVu.TTF'
Attachment ID 9: type 'application/x-truetype-font', size 104372 bytes, file name 'VINERITC.TTF'
Attachment ID 10: type 'application/x-truetype-font', size 30980 bytes, file name 'ABYSSTSFONT.TTF'
Attachment ID 11: type 'application/x-truetype-font', size 70180 bytes, file name 'cwelegnc.ttf'
Chapters: 5 entries

```Currently I'm using mkvextract to rip the subs to a new file but it is not pulling the fonts out plus i have to manually create the sub file name and insert it in the above script in the needed places.


I need the script to process the shows name so that it will pull the subs to a file that is named for the show minus the group name, bit depth, resolution, and crc number( for use in the encode process). 
Then pull all the fonts contained in the file and put them in $HOME/.fonts with their name and type intact so that they are usable by the system. 
Do the encode and incert chapters into the mp4.

Resultant file name :  [<fansub group name>]_<show name>_-_<eposide number>_[<h pix>p].mp4


All Help is greatly welcomed.

---

### Post by labsin on 2013-02-07
So you need to run:
mkvextract --identify
and get all the id's from it somehow (we see that later)

Next:
mkvextract attachments <file> <id>:Output (output may be black so it uses the filename inside the mkv)
So try:
mkvextract attachments <file> 1:
and
mkvextract attachments <file> 1
Edit: so it is the second one

Could you attach the file geven by
mkvextract --identify > identify.txt

And also add a file list exaple of your mkv files: (just cut out a few if you don't want to)
ls > ls.txt

---

### Post by Wolfpup on 2013-02-07
> **labsin said:**
> So you need to run:
mkvextract --identify
and get all the id's from it somehow (we see that later)

Next:
mkvextract attachments <file> <id>:Output (output may be black so it uses the filename inside the mkv)
So try:
mkvextract attachments <file> 1:
and
mkvextract attachments <file> 1

Could you attach the file geven by
mkvextract --identify > identify.txt

And also add a file list exaple of your mkv files: (just cut out a few if you don't want to)
ls > ls.txt
Attached is three ls.text files. 
ls.txt   -> list of one series
ls2.txt -> list of different shows
ls3.txt -> list of different series

---

### Post by JimS on 2013-02-07
...
I'm new to this field, but I found the following:
On YouTube ==> [http://www.youtube.com/watch?v=R-L_E6oS1PY](http://www.youtube.com/watch?v=R-L_E6oS1PY)[/B]
Text to the code mentioned in above url, see
[http://ohheyitslou.blogspot.com/](http://ohheyitslou.blogspot.com/)
...

---

### Post by labsin on 2013-02-07
Ok, I have a test. Open it and fill in the file variable and then run it from that folder using sh test1.sh

Edit: added one that should be close.
If you have problems, or don't have a clue what happens. Please feel free to ask.

---

### Post by Wolfpup on 2013-02-17
Now I have the following script and it is semi-functional for what I want it to do.
```

#!/bin/bash
echo "Time Start: "$(date +%m%d%Y%I%M%S%p)
shopt -s nullglob
for f in *.mkv
do
  echo "Trying file $f"
  info=$(mkvmerge --identify "$f")
  echo "mkvmerge --identify: $info"
  fonts=$( echo "$info" | sed -n 's/^[^0-9]*\([0-9]*\): type .application\/x-truetype-font.*$/\1/p')
  for font in $fonts
  do
    echo 'Extract attachment $font from $f'
    mkvextract attachments "$f" $font
  done
  mkdir -p $HOME/.fonts/
  shopt -s nullglob
  mv -f *.?t? $HOME/.fonts
  mv -f *.?T? $HOME/.fonts
done
sudo fc-cache -fv
for f in *.mkv
do
  newName=$( echo "$f" | sed "s/^\[[^]]*\][_ ]\([^[]*\)[ _].*$/\1/")
  echo "Going to encode $f into $newName.mp4"
  mkvextract chapters -s "$f" > $newName.txt
  ffmpeg -i "$f" -map 0:s:0 $newName.ass
  echo "Time Encode Start: "$(date +%m%d%Y%I%M%S%p)
  ffmpeg -i "$f" -vf "ass=$newName.ass" -c:v libx264 -profile:v high -level 4.1 -crf 18 -preset veryslow -tune animation -x264opts qpmin=10:qpmax=28:aq-mode=2:no-mbtree:threads=auto -c:a copy $newName.mp4
  MP4Box -add $newName.mp4#video -add $newName.mp4#audio -chap $newName.txt $newName-chaps.mp4
  echo "Time Encode Done : "$(date +%m%d%Y%I%M%S%p)
done
echo "Time Done: "$(date +%m%d%Y%I%M%S%p)

```I still have to manually rename the final mp4 to the format I want because if I try to name the file in the way I want I get bash errors.

I also have to manually delete the intermediate encode files because when i try to use rm to delet the files via the script i get '".*" diectory not found when i have the command rm $newfilename.* in the script right after the MP4Box command.

---

