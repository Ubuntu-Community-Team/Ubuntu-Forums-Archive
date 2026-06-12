---
title: "Convert ape to mp3"
date: 2009-02-28
forum: Multimedia Software
---

### Post by Robbyx on 2009-02-28
I thought VLC would do the conversion but I have not been able to see how to do it. I wish to convert quite a few ape files to a format that will play on a cd player. What is the best way to do it? If VLC will do the conversion then my problem was that when I chose media--convert/save it did not recognise the file extension via the filter option. Strangely it could play the ape file

---

### Post by Robbyx on 2009-02-28
Since posting the message I have found a nautilus script to convert  audio files. I get an error message when I run it:

you don't have the right codec to decode the selected file. missin' codec: mac

Do you know where to get this missing codec?

Robin

---

### Post by mc4man on 2009-02-28
For an app maybe  soundkonverter or soundconverter. I see soundkonverter supports Ape (mac)

Otherwise ffmpeg could easily batch convert to ?? (you never said.

If your intention is to burn to a cd then I'd convert to .wav


Edit. grabbed a .ape sample and on a machine with both soundkonverter and soundconverter it was not accepted by soundkonverter (no mac codec), but was by soundconverter (though it butchered the run time

Was quite simple to convert with ffmpeg on my main box

---

### Post by Robbyx on 2009-03-01
Thank you for that advice. I have just installed ffmpeg from synaptic.  

Here is an example of a batch that needs converting. It is getting very tedious to make this work. It keeps reporting no such directory. If there is no gui that will make this easy what would you suggest. My failed proposal to combine the 5 files to one wav file is as follows. 
 
 ffmpeg -i '/media/video/Music/Grimaud-Beethoven Piano Concerto No.5/'%Beathoven Concerto No 5.ape  /media/video/Music/beethoven.wav


/media/video/Music/Grimaud-Beethoven Piano Concerto No.5/%Beathoven: no such file or directory

It looks as if ffmpeg has limited wild card ability.  So I renamed the five files listed below to 1Beathoven Concerto No 5.ape (incrementing each one)




/media/video/Music/Grimaud-Beethoven Piano Concerto No.5/7 Beethoven - Piano Sonata No.28 - IV - Allegro.ape
/media/video/Music/Grimaud-Beethoven Piano Concerto No.5/6 Beethoven - Piano Sonata No.28 - III - Adagio, ma non troppo, con affetto.ape
/media/video/Music/Grimaud-Beethoven Piano Concerto No.5/5 Beethoven - Piano Sonata No.28 - II - Vivace alla Marcia.ape
/media/video/Music/Grimaud-Beethoven Piano Concerto No.5/4 Beethoven - Piano Sonata No.28 - I - Allegretto, ma non troppo.ape
/media/video/Music/Grimaud-Beethoven Piano Concerto No.5/3 Beethoven - Concerto No. 5 - III - Rondo. Allegro.ape
/media/video/Music/Grimaud-Beethoven Piano Concerto No.5/2 Beethoven - Concerto No. 5 - II - Adagio un poco mosso.ape
/media/video/Music/Grimaud-Beethoven Piano Concerto No.5/1 Beethoven - Concerto No. 5 - I - Allegro.ape

---

### Post by vanadium on 2009-03-01
You are mixing up two problems. Can ffmpeg convert a single ape file? If yes, then we can look into batch encoding. If not, your first problem remains to decode the ape files.

I have been using the linux command line utility "mac" which I installed from [www.rarewares.org](www.rarewares.org). Previously, I have used the graphical Windows utility under wine. I have converted all my ape's to flac, which was a truly free format from the beginning and is much better supported on different platforms than Monkey's audio.

---

### Post by Robbyx on 2009-03-01
My ffmpeg now converts ape files to wav or mp3 using the following command line:

ffmpeg -i '/media/video/Music/1Chopin Piano Concerto No. 1 (Zimerman)/(01) Chopin Piano Concerto No. 1 - I. Allegro maestoso.ape'   /media/video/Music/chopin.mp3

As you can see I have had to put the path and name in inverted comma.

Any suggestions as to batch processing?

Robin

---

### Post by mc4man on 2009-03-01
If your going to use ffmpeg then you don't need to type in the path, track name ect.
You can do this from the cli or create a script, in either case you'd just cd to the directory (folder) containing your tracks and then run this basic command.

It can be adapted for mp3 or other formats, additional actions ect.
This will convert to .wav using the existing track names.

Basic command for batch converting

```
for f in *.ape; do ffmpeg -i "$f" "${f%.ape}.wav"; done

```

I've got to go out, here's a post with some more info, I don't use mp3 but it would be fairly easy to use the above to convert to mp3 (within whatever parameters ffmpeg will accept for mp3

[http://ubuntuforums.org/showthread.php?t=1081958](http://ubuntuforums.org/showthread.php?t=1081958)

---

### Post by vanadium on 2009-03-01
Great trick with { % } to avoid the "basename" function!

---

### Post by mc4man on 2009-03-01
I found the "mac" source code that 'appears' to have built and installed properly in 8.10
Whether it's of any value I'm not sure, will have to test later, though something I'm about to build did find it. (pacpl
> checking for mac... yes


Anyone you wants to test it's here (appears to be a patched ver.

[http://etree.org/shnutils/shntool/support/formats/ape/unix/3.99-u4-b5/s4/mac-3.99-u4-b5-s4.tar.gz](http://etree.org/shnutils/shntool/support/formats/ape/unix/3.99-u4-b5/s4/mac-3.99-u4-b5-s4.tar.gz)

A straight configure seemed to work, did find this, though didn't try (were 2 large groups of warnings, didn't look at
> a) for unix targets:

    % CXXFLAGS="-DSHNTOOL" ./configure


@ vanadium
 you can use that 'style' for a lot of things, while I don't need to run neroAacEnc as a standalone (use rubyripper) was just fooling around
```
for f in *.wav; do neroAacEnc -if "$f" -of "${f%.wav}.m4a" -q 0.65; done
```


Edit: 
well it's works fine as an encoder/decoder (.wav to .ape, .ape to .wav )
> doug@doug-desktop:~/Desktop/monk$ mac "see.wav" "see.ape" -c2000
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Compressing (normal)...
Progress: 100.0% (0.0 seconds remaining, 8.5 seconds total)          
Success...
doug@doug-desktop:~/Desktop/monk$ mac "see.ape" "see1.wav" -d
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Decompressing...
Progress: 100.0% (0.0 seconds remaining, 12.4 seconds total)          
Success...


Reedit;
Batch decompress .ape to .wav, basic command (after installing 'mac'), 

```
for f in *.ape; do mac "$f" "${f%.ape}.wav" -d; done
```

here's a recent thread semi related (ape to flac
[http://ubuntuforums.org/showthread.php?t=1084665&](http://ubuntuforums.org/showthread.php?t=1084665&)

It also links to a ppa with debian packages of mac
[http://ppa.launchpad.net/eudoxos/ubuntu/pool/main/m/](http://ppa.launchpad.net/eudoxos/ubuntu/pool/main/m/)

You might also post in that thread - see if he's got a script to do ape->mp3 directly

---

### Post by Robbyx on 2009-03-04
> **mc4man said:**
> If your going to use ffmpeg then you don't need to type in the path, track name ect.
You can do this from the cli or create a script, in either case you'd just cd to the directory (folder) containing your tracks and then run this basic command.

It can be adapted for mp3 or other formats, additional actions ect.
This will convert to .wav using the existing track names.

Basic command for batch converting

```
for f in *.ape; do ffmpeg -i "$f" "${f%.ape}.wav"; done

```

I've got to go out, here's a post with some more info, I don't use mp3 but it would be fairly easy to use the above to convert to mp3 (within whatever parameters ffmpeg will accept for mp3

[http://ubuntuforums.org/showthread.php?t=1081958](http://ubuntuforums.org/showthread.php?t=1081958)


I have just tried your code and it works very well with either wav or mp4. Thank you.

I am disappointed with the mp4 results because the music is not sounding full blooded. It is mooted down when the music gets loud. The music is also sounding thin. Do you know if there are any settings which would bring back the full tone and depth?

Robin

---

### Post by Robbyx on 2009-03-04
Pending your reply I have converted the ape files to wav and the  result was very satisfactory. I have then gone to another folder with more ape files and this time it will not work.

```
rob@rob-desktop:/media/video/Music/VA - Ultimate Liszt/CD 01$ for f in *.ape; do ffmpeg -i "$f" "${f%.ape}.wav"; done
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
[mp3 @ 0xb7ec1388]Could not find codec parameters (Audio: mp3, 8 kb/s)

```

I do not understand why it is referring to mp3 when I am trying to convert to wav. Can anyone spot why this time it will not convert? 

Robin

---

### Post by mc4man on 2009-03-04
> Can anyone spot why this time it will not convert?
Not really, are you sure they're ape files.

Anyway I'd just use mac to decompress the .ape's to .wav instead of ffmpeg and then encode to what you wish, or burn to cd 

If you tried neroAacEnc and didn't like then try faac either from cli or with any number of apps. I'm not aware of any aac (m4a) parameters other using -br or -q (i think -q is superior

I was just looking thru the source of soundkonverter and noticed it will convert ape (which it did in a quick test though it named everything 'unknown', so your better off just decompressing to .wav yourself, ect., ect.

if you have cue files
 then ck. out that that script I linked to (ape to flac), or post there and see if he's got one for ape to mp3 (tagging from cue?)

Otherwise maybe go (if you have cues) ape to flac, then flac to mp3 (tagging from flac metadata

Any app like soundkonverter would do that or if you want more control of lame parameters here's a script to convert flac to mp3 with tags

[http://ubuntuforums.org/showthread.php?p=6827629#post6827629](http://ubuntuforums.org/showthread.php?p=6827629#post6827629)

---

### Post by Robbyx on 2009-03-05
Although they had an extension of ape I think they were actually apeless because I was able to convert some other ape files with no problems. I would like to put your script into a file so that I can run it when needed. Can you please suggest the way to do this.

Robin

---

### Post by Robbyx on 2009-03-11
```
for f in *.ape; do ffmpeg -i "$f" "${f%.ape}.wav"; done
```

This piece of code has worked wonderfully. Changes in inputs have enable it to work with flac as well.

How do I attach it to an icon so I can click on the icon to run the code rather than having to hunt for the code when I need it?

Robin

---

### Post by mc4man on 2009-03-11
you could make a simple little script, then at the dir. prompt just call the script with path to script/scriptname

I still think it may be better to use mac to decompress to wav than ffmpeg, though maybe no difference.
I linked to the source but meanwhile found a .deb (made for jaunty, doesn't matter, I just installed on hardy.

[https://launchpad.net/~quintasan/+archive/ppa/](https://launchpad.net/~quintasan/+archive/ppa/)
Don't add his repo, just expand the mac listing and scroll down to the "package files" listing and d. click to dl and install

so a simple script (using mac) would be this, added a basic way to separate .wav's from .ape's. You can modify in several ways. Notice the path to save .wav's, ./temp/ is directly in front of "${f%.ape}.wav" 
you could path to anywhere in same manner

```
#!/bin/bash
mkdir temp
for f in *.ape; do mac "$f" ./temp/"${f%.ape}.wav" -d; done
```

To use create a text file, name it something, ape2wav is what I'd use and paste in code.
Put it either loose in home dir. or make a folder named scripts, then right click on the script -> properties -> permissions and mark as executable.

Then at the dir. prompt for the folder with the .ape's go
~/scripts/ape2wav

---------------------------------------------------------------------
maybe of no use to you but ....

I was just making myself a little interactive script to convert .m4a (encoded w/ neroAacEnc) to mp3's with tags so I can add to an ipod.
If you still wanted to go from .ape to .mp3 w/ tags give it a try, below I changed it to ape2mp3

You'll need to install id3v2 and if you want to use genre with #'s id3 to get list.
```
sudo apt-get install id3 id3v2
```
to see the number list for genre open a separate terminal and go 
```
id3 -L
```

If you want to you can remove the genre and year echo's and line below them if not wanted  (if you remove an echo remove the read line below, you must Keep at a min the artist and album

You can enter any number of valid lame commands as shown

I have a line rm *.wav, you could change to rm *.ape or remove the line

Your .apes should have a 'track' number, preferably like either (for tracks 1-9
01- name of track
02 - name of track
( otherwise if the folder is loaded into a player and you have 1-trackname, 2-trackname then 10 - 19 will be loaded above 2 - 9, 20 - 29 above 3-9, ect.


ape2mp3

[PHP]#!/bin/bash
echo "Artist name?"
a= read a
echo "Name of album?"
A= read A
echo "genre?"
g= read g
echo "year?"
y= read y
for f in *.ape; do mac "$f" "${f%.ape}.wav" -d; done
mkdir "$a"'-'"$A"
for f in *.wav; do lame --vbr-new -V2 --replaygain-accurate -q 2 "$f" ./"$a"'-'"$A"/"${f%.wav}.mp3"; done
rm *.wav
cd ./"$a"'-'"$A"
for f in *.mp3; do id3v2 "$f" -t "${f%.mp3}" -a "$a" -A "$A" -y "$y" -g "$g"; done[/PHP]

Example of terminal entries
> doug@doug-desktop:~/Music/Jackson Browne/Late For The Sky$ ~/ape2mp3
Artist name?
Jackson Browne
Name of album?
Late for The Sky
genre?
81
year?
1974
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Decompressing...
Progress: 100.0% (0.0 seconds remaining, 14.5 seconds total) ...... ect, ect..................
LAME 3.98 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: MMX (ASM used), SSE (ASM used), SSE2
Using polyphase lowpass filter, transition band: 18671 Hz - 19205 Hz
Encoding  01 - Late For The Sky.wav
      to ./Jackson Browne-Late for The Sky/ 01 - Late For The Sky.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III VBR(q=2)....ect.


screen shows resulting tag info, loads fine into the ipod

---

### Post by Robbyx on 2009-03-12
Thank you for that very helpful and comprehensive reply.

Robin

---

