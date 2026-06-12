---
title: "Batch convert FLAC to mp3"
date: 2012-07-05
forum: Multimedia Software
---

### Post by ZootHornRollo on 2012-07-05
Hi,

I ahave a large coolection of FLAC files converted from my CD collection - over 10,000 tracks.

I would like to create a second copy of it in mp3 in order to have access to it on my Nokia Lumia phone.

I have tried using Sound Converter to do it as one batch but have so far had no success.  I have tried doing it as one batch,splitting it in two, and now even trying to do all the A's, all the B's etc but it every time it hangs endlessly.  I have left it overnight in its hang status and there is no progress. It is a random track each time - never the same track/album twice.  sometimes it'll do 20 tracks, sometimes 200.

the output from terminal shows no error, it displays the normal message that it is converting a track and this remains until i kill it.

any ideas what could be the problem?

or any suggestions as to another way i can complete the task?

Thanks,

G.

p.s. The PC is a Pentium D 3.0 Ghz with 3GB RAM - should be enough for the job, no?

p.p.s. I imported my library into rythymbox and removed the tracks that showed as import errors in order to try to remove potentially corrupt files.

---

### Post by ajgreeny on 2012-07-05
Do you have the necessary codecs for encoding as mp3 on your system?

Being able to play mp3s and being able to encode as mp3 are not the same thing.

---

### Post by SeijiSensei on 2012-07-05
This is a common request.  Did you search the forum archive first?  I just put "batch mp3 flac" into the search box and got a number of threads, some of which provide clear ways to do this with a bash script.

---

### Post by ZootHornRollo on 2012-07-05
> **ajgreeny said:**
> Do you have the necessary codecs for encoding as mp3 on your system?

Being able to play mp3s and being able to encode as mp3 are not the same thing.

yes, it does convert a number of files before hanging.

Thanks.

---

### Post by ZootHornRollo on 2012-07-05
> **SeijiSensei said:**
> This is a common request.  Did you search the forum archive first?  I just put "batch mp3 flac" into the search box and got a number of threads, some of which provide clear ways to do this with a bash script.

hi, I tried a couple of different bash scripts but didn't have any success. Flac2mp3 being one example.
I am not well versed in using bash scripts.

i was hoping that sound converter would work.  Is there something that prevents it working on large batches?

Thanks.

---

### Post by ron999 on 2012-07-05
...

---

### Post by O2Blevel on 2012-07-05
You can try these:

find -name "*.flac" -exec ffmpeg -i {} -acodec libmp3lame -ab 128k {}.mp3 \;

rename 's/\.flac//' *.mp3

Run the first command to convert to mp3 which will create a file name.flac.mp3, and the second command will give you name.mp3. Your flac and mp3 files will be in the same folder, you can easily move the mp3 files to a different folder. Change 128k to whatever, and I would recommend breaking your 10,000 into a number of smaller folders, or invest in a water-cooled computer.:D

---

### Post by FakeOutdoorsman on 2012-07-05
What about [MP3FS](http://khenriks.github.com/mp3fs/)?
> MP3FS is a read-only FUSE filesystem which transcodes audio formats (currently FLAC) to MP3 on the fly when opened and read. This was written to enable me to use my FLAC collection with software and/or hardware which only understands the MP3 format e.g. gmediaserver to a Netgear MP101 MP3 player.
It's available in the repository.

---

### Post by shantiq on 2012-07-06
say all your music files are in   Music


```
cd Music
```    then as one block [   it goes into each folder and does conversion then gets out and to next one and leaves **original flac** there too]





```
for i in  */
do
  cd "$i"
for f in *.flac ; do   ffmpeg -i "$f" -ab 320k "${f%.flac}.mp3"  ; done
  cd ..
done
```


or same and get rid of original flac after conversion[use carefully if at all]


> for i in */
do
  cd "$i"
for f in *.flac ; do   ffmpeg -i "$f" -ab 320k "${f%.flac}.mp3"   [COLOR="DarkRed"]** && rm *.flac**[/COLOR]; done
  cd ..
done

---

### Post by ZootHornRollo on 2012-07-07
i am running this just now.  Has converted 4 albums thus far and still running.  WIll let yo know how i get on.

Many thanks.

```
for i in  */
do
  cd "$i"
for f in *.flac ; do   ffmpeg -i "$f" -ab 320k "${f%.flac}.mp3"  ; done
  cd ..
done
```

---

### Post by ZootHornRollo on 2012-07-07
> **FakeOutdoorsman said:**
> What about [MP3FS](http://khenriks.github.com/mp3fs/)?

It's available in the repository.

i did stumble across that and tried it but i couldn't get it to mount my music file - presumably because it was already mounted.  However this wouldn't solve my issue as i need to boot into windows in order to sync my windows phone, the phone doesn't mount as a USB drive.

thanks.

---

### Post by ZootHornRollo on 2012-07-07
hi,

The conversion has now ceased and i get theis output in terminal 
O```
utput #0, mp3, to 'Arab Strap - Elephant Shoe - 02 - One Four Seven One.mp3':
  Metadata:
    ACCURATERIPRESULT: AccurateRip: Not in database   Secure: Yes   [69EDB342]
    ACCURATERIPDISCID: 011-00184f1d-00d22b65-980d540b-2
    TPOS            : 1
    TIT2            : One Four Seven One
    TPE1            : Arab Strap
    TALB            : Elephant Shoe
    TDRL            : 1999
    TRCK            : 2
    TPE2            : Arab Strap
    TRACKTOTAL      : 11
    DISCTOTAL       : 1
    TEMPO           : 181
    TSSE            : Lavf53.21.0
    Stream #0.0: Audio: libmp3lame, 44100 Hz, 2 channels, s16, 320 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press ctrl-c to stop encoding
Multiple frames in a packet from stream 0
```

---

### Post by ZootHornRollo on 2012-07-07
Noticed Update Manger installed an update for SoundConverter this morning so tried again....  appears to work fine now so going for it in several smaller batches.

---

### Post by abajaj on 2012-07-21
I tried:
___
for i in  */
do
  cd "$i"
for f in *.flac ; do   ffmpeg -i "$f" -ab 320k "${f%.flac}.mp3"  ; done
  cd ..
done

______
as an executable script in the main MP3 folder and it worked great to convert all .flac files in all subfolders into .mp3. 
Then ran the following command from command line after the conversion: 

find . -name "*.flac" -exec rm {} \;

to clean up the flac files. 
thanks Ubuntu forums! 
-abajaj

---

### Post by LHammonds on 2012-07-22
Thanks for sharing the solution and letting us know it worked for you.

I would make one modification to that bash script (for loop) so that if it failed and crashed, a subsequent run would not require re-creating any MP3 files you already have converted.  I would have the for loop call a function that simply checks to see if the MP3 equivalent of the FLAC file already exists, if so, it would skip the conversion so it can continue on until it reaches a FLAC file that does not yet have an associated MP3 file.

LHammonds

---

### Post by shantiq on 2012-07-23
please LH    could you write this out in full for the ones of us who do not code

i put the thing up but it was cobbled from earlier sources [i am no coder]

if you could write it out as you describe I , and i am sure others, will be grateful       thanx

---

### Post by evilsoup on 2012-07-23
```
#/bin/bash
#
#Convert every FLAC file in a directory (and subdirectories)
#into MP3 files, while keeping the originals
#
main_function()
{
if [ -e "${f%.flac}.mp3" ]; then
echo "File already exists!"
else
ffmpeg -i "$f" -ab 320k "${f%.flac}.mp3"
fi
}

for i in */
do
cd "$i"
for f in *.flac ; do $(main_function); done
cd ..
done
exit 0
```Should do it.

Also, you can put it in your bin folder ($HOME/bin), saved as say 'flactomp3', and then you can summon it from the command line with just the name.

Also, a bit rate of 320k is almost ludicrously high-quality: unless you are using high-end headphones and a high-end player, you would be better off using 192k or so. This will give you smaller files, and you probably won't notice the difference.

---

### Post by FakeOutdoorsman on 2012-07-23
> **evilsoup said:**
> Also, a bit rate of 320k is almost ludicrously high-quality: unless you are using high-end headphones and a high-end player, you would be better off using 192k or so. This will give you smaller files, and you probably won't notice the difference.

Another option is to use *-aq* instead of *-ab*. This will result in VBR instead of CBR audio and will allow you to achieve a desired quality level. It is mapped to the *-V* option in *lame* (**the** MP3 encoder), and I believe this is the default if you use *lame* directly (default value is *-V 4*). See [Recommended LAME encoder settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_encoder_settings) for an idea of what *-aq / -V* to use.

---

