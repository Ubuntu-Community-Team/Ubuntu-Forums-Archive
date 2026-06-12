---
title: "Script: Create audio book with chapters from mp3 files"
date: 2010-02-28
forum: Multimedia Software
---

### Post by hasenbaer on 2010-02-28
Inspired by [this blog post]("http://froebe.net/blog/2009/12/24/how-to-create-an-itunesipod-compatible-audiobook-mpeg4-m4b-on-linux-using-mp4box-and-mp4v2-v1-9-1-it-can-be-done/") I made a python script to create an audio book with chapter marks from mp3 files.

[**Get the script here**]("http://pastie.org/846576")

_Instructions:_

[LIST]
[*]Requires  ffmpeg, MP4Box, mp4chaps, mutagen, libmad, mp3wrap
[LIST]
[*]To install use: [FONT=Courier New]sudo apt-get install ffmpeg python-mutagen python-pymad gpac mp3wrap
[/FONT]
[*]To install mp4chaps, download [mp4v2 v1.9.1]("http://mp4v2.googlecode.com/files/mp4v2-1.9.1.tar.bz2") ([Website at Google Code]("http://code.google.com/p/mp4v2/")), extract it, and use
[FONT=Courier New]./configure
make
sudo checkinstall[/FONT]
[/LIST]
 
[*]Rip your audio book to mp3 from the cd.
[LIST]
[*]Note: The mp3 files should have proper ID3 tags. The "title" tag of each mp3 file is used as the corresponding chapter title. The "artist" and "album" tags of the first file are used as tags for the complete audio book.
[*]Note: To have the chapters in the correct order, the filenames have to be sortable (e.g. "01 - First chapter.mp3", "02 - Second chapter.mp3").
[/LIST]
 
[*]Run the script in the directory with the mp3 files: [FONT=Courier New]python create_audiobook.py[/FONT]
[*]See the output directory for the audio book (m4b) file.
[*]To make the chapter marks show up on the iPod use gtkPod>=v0.99.14 or iTunes for transferring the audio book.
[/LIST]
Hope it work's for you!

---

### Post by sameat on 2010-03-08
Awesome script, worked perfectly.  Thanks a lot.

A couple of notes:

1. You have to have aac encoding enabled for ffmpeg (obviously).  It apparently doesn't work by default in Karmic, but is easy enough to sort out.  I used option c from [this post]("http://ubuntuforums.org/showthread.php?t=1117283")

2. The m4b file sizes were substantially larger than the originals (roughly twice as big, regardless of original bitrate).  Not a big deal to me, and well worth the convenience.

Edit:  As I got further in to this, the file sizes started to become a problem.  Would there be a n easy way to tweak the script to force the aac output to 64 kbps?

Thanks again.

---

### Post by moddinati on 2010-04-03
Thanks, awesome script.


@sameat

If you open the python script in a text editor, there will be the following line
```
ffmpeg = 'ffmpeg -i output/output_MP3WRAP.mp3 -y -vn -acodec libfaac -ab 128k -ar 44100 -f mp4 output/output.aac'
```replace the "128k" with "64k" to make the aac output be 64k

---

### Post by jhogan on 2011-02-24
Hey,
I'm creating a bash script similar to your python script. I read your comments here ([http://froebe.net/blog/2009/12/24/how-to-create-an-itunesipod-compatible-audiobook-mpeg4-m4b-on-linux-using-mp4box-and-mp4v2-v1-9-1-it-can-be-done/](http://froebe.net/blog/2009/12/24/how-to-create-an-itunesipod-compatible-audiobook-mpeg4-m4b-on-linux-using-mp4box-and-mp4v2-v1-9-1-it-can-be-done/)) and noticed you were having a problem which is similar to the one I'm having now. When I put the m4b in itunes the duration shows as several hundreds of hours and the m4b doesn't work in my ipod. You said you fix this problem for yourself. Do you remember what you did. I think it may be that my chapters file rounds to the nearest second (01:01:01.000) for its duration. Thanks in advance.

---

### Post by e-San on 2011-03-24
Need small help, i hope i get it from You.

I used iTunes to convert all my albums to m4a files since this should be the best encoder and im trying to put thet together as one file (m4b) onto my iPod. 

```
MP4Box -cat a1.m4a -cat a2.m4a newfile.mp4
``` 
does the job without reconverting but i have no idea how to create proper chapters file. tags are checked and complete.

Best regards!

edit.
Getting close!
```
san@eeepc:~/Publiczny/sd/Ext01/kiss/b$ MP4Box -info  a1.detroit.rock.city.\(intro\).flac.m4a | grep Dura
	Timescale 44100 - Duration 00:01:23.406
Track # 1 Info - TrackID 1 - TimeScale 44100 - Duration 00:01:23.406
```

edit2
quite dirty and uncool, but it works...
```
MP4Box -info  a1.detroit.rock.city.\(intro\).flac.m4a | grep Track | tr -d [:alpha:],' '| cut -f 4 -d -
00:01:23.406
```
what next?

---

### Post by e-San on 2011-03-25
tadam!

```
artist="Arroyo"
album="Arroyo"

hs=0
ms=0
ss=0
ns=0
cn=0 #chapter number

for i in *.m4a; do

((cn++))
czas=`MP4Box -info "$i" | grep -m2 Duration | tr -d [:alpha:],' ' | cut -f4 -d -`

h=`echo $czas | cut -d  ':' -f 1` 
m=`echo $czas | cut -d  ':' -f 2` 
sn=`echo $czas | cut -d  ':' -f 3` 
s=`echo $czas | cut -d  ':' -f 3 | cut -d '.' -f1` 
n=`echo $czas | cut -d  ':' -f 3 | cut -d '.' -f2` 

nazwa=`echo $i | sed 's#\.flac##g' |  sed 's#\.m4a##g'`

echo CHAPTER$cn=`echo 0$hs | tail -c3`:`echo 0$ms | tail -c3`:`echo 0$ss | tail -c3`.`echo 00$ns | tail -c4` >> chapter_info
echo CHAPTER"$cn"NAME=$nazwa >> chapter_info

hs=`echo $(( 10#$hs + 10#$h))`
ms=`echo $(( 10#$ms + 10#$m))`
ss=`echo $(( 10#$ss + 10#$s))`
ns=`echo $(( 10#$ns + 10#$n))`

#ns
if [ $ns -gt 999 ]
then
#	echo too much ns
	ns=`echo $(( 10#$ns - 1000 ))`
	ss=`echo $(( 10#$ss + 1 ))`
fi

#s
if [ $ss -gt 59 ]
then
#	echo too much sek
	ss=`echo $(( 10#$ss - 60 ))`
	ms=`echo $(( 10#$ms + 1 ))`
fi

#m
if [ $ms -gt 59 ]
then
#	echo too much min
	ms=`echo $(( 10#$ms - 60 ))`
	hs=`echo $(( 10#$hs + 1 ))`
fi

MP4Box -cat "$i" album_tmp.mp4

done

MP4Box -add album_tmp.mp4 -chap chapter_info album_chap.mp4
mp4chaps --convert --chapter-qt album_chap.mp4

#mp4tags -album "$album" -artist "$artist" -song "$album (complete album)" -albumartist $artist album_chap.m4b 
mv album_chap.mp4 "$artist - $album (iTunes+) [$hs." `echo 0$ms | tail -c3`".m4b

echo Duration: `echo 0$hs | tail -c3`:`echo 0$ms | tail -c3`:`echo 0$ss | tail -c3`.`echo 00$ns | tail -c4`
echo Chapters: $cn
```

actually it does not read artist and album from nowhere, it is set at the beggining of script. todo, later.

---

### Post by e-San on 2011-03-26
It is my, propably, last word:

```
san@eeepc:~$ cat /usr/sbin/mp4chapters
hs=0
ms=0
ss=0
ns=0
cn=0 #chapter number

for i in *.m4a; do

((cn++))
time=`MP4Box -info "$i" | grep -m2 Duration | tr -d [:alpha:],' ' | cut -f4 -d -`

if [ $cn == 1 ]; then
	artist=`mp4info "$i" | grep Artist | cut -d ":" -f2 | cut -b 2-`
	album=`mp4info "$i" | grep Album -m1| cut -d ":" -f2 | cut -b 2-`
	track_album=`mp4info "$i" | grep Track: | cut -d ":" -f2 | cut -d 'f' -f2 | tr -d ' '`
fi 

name=`mp4info "$i" | grep Name | cut -d ":" -f2 | cut -b 2-`
track_num=`mp4info "$i" | grep Track: | cut -d ":" -f2 | cut -d 'o' -f1 | tr -d ' '`

h=`echo $time | cut -d  ':' -f 1` 
m=`echo $time | cut -d  ':' -f 2` 
sn=`echo $time | cut -d  ':' -f 3` 
s=`echo $time | cut -d  ':' -f 3 | cut -d '.' -f1` 
n=`echo $time | cut -d  ':' -f 3 | cut -d '.' -f2` 

echo CHAPTER$cn=`echo 0$hs | tail -c3`:`echo 0$ms | tail -c3`:`echo 0$ss | tail -c3`.`echo 00$ns | tail -c4` >> /dev/shm/chapter_info
echo CHAPTER"$cn"NAME=`echo 0$track_num  | tail -c3`. "$artist" - "$name" >> /dev/shm/chapter_info

hs=`echo $(( 10#$hs + 10#$h))`
ms=`echo $(( 10#$ms + 10#$m))`
ss=`echo $(( 10#$ss + 10#$s))`
ns=`echo $(( 10#$ns + 10#$n))`

#ns
if [ $ns -gt 999 ]
then
#	echo too much ns
	ns=`echo $(( 10#$ns - 1000 ))`
	ss=`echo $(( 10#$ss + 1 ))`
fi

#s
if [ $ss -gt 59 ]
then
#	echo too much sek
	ss=`echo $(( 10#$ss - 60 ))`
	ms=`echo $(( 10#$ms + 1 ))`
fi

#m
if [ $ms -gt 59 ]
then
#	echo too much min
	ms=`echo $(( 10#$ms - 60 ))`
	hs=`echo $(( 10#$hs + 1 ))`
fi

echo Adding $i as a chapter.
MP4Box -cat "$i" -tmp /dev/shm /dev/shm/album_tmp.mp4 > /dev/null

done

if [ 10#$cn == 10#$track_album ] ; then
#	echo "Album complete"
	echo "Added $cn tracks of $track_album in album."
else
	echo "Error! Chapters number is $cn while there is $track_album tracks on album."
fi 

echo Adding chapters informations.
MP4Box -tmp /dev/shm -add /dev/shm/album_tmp.mp4 -chap /dev/shm/chapter_info /dev/shm/album_chap.mp4 > /dev/null
rm /dev/shm/album_tmp.mp4 /dev/shm/chapter_info
mp4chaps --convert --chapter-qt /dev/shm/album_chap.mp4 > /dev/null

echo Adding album informations.
mp4tags -album "$album" -artist "$artist" -song "$album (complete album)" -albumartist "$artist" /dev/shm/album_chap.mp4 > /dev/null

file_name="$artist - $album (iTunes+) [$hs.`echo 0$ms | tail -c3`].m4a"

echo Renaming to "$file_name".
mv /dev/shm/album_chap.mp4 "/media/Ext03/iTunes/$file_name"

echo " " 
echo Duration: `echo 0$hs | tail -c3`:`echo 0$ms | tail -c3`:`echo 0$ss | tail -c3`.`echo 00$ns | tail -c4`
echo Chapters: $cn
echo " "
echo Enjoy!
```

I will have to check if there is no 500ns gap betwen chapters, but i am quite shure there is no.
You will propably want to change "/media/Ext03/iTunes/$file_name" to Your own output directory.

Regards and thanks for help!

---

