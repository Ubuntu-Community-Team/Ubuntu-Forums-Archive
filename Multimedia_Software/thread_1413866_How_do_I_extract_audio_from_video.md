---
title: "How do I extract audio from video ?"
date: 2010-02-23
forum: Multimedia Software
---

### Post by mrpenguin on 2010-02-23
I have a video file I wish to extract the audio from .... its a seminar that was recorded in mpeg but all i need is the audio into mp3  ... any idea how to do this ?

---

### Post by LuridCinema on 2010-02-23
you can use ffmpeg if you have it installed...
open a terminal in the folder as the mpg file and try:
ffmpeg -i file.mpg  output.mp3

with file.mpg being the name of the file you wish to extract the audio from

---

### Post by mrpenguin on 2010-02-23
Thanks .... but i just keep on getting the same error message, must be doing something wrong

> jaques@jaques-netbook:~$ ffmpeg -i  seminar.avi output.mp3
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
seminar.avi: no such file or directory


---

### Post by d3v1150m471c on 2010-02-23
```

#!/bin/bash
echo -n "Enter the name of the video INCLUDING the format and path: "
    read vin
#
#
#
echo -n "Enter the name of the new video WITHOUT an format behind the file: "
    read vout
#
#
#
mencoder "$vin" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o "$vout".avi
#
#
#
mencoder -of rawaudio -ovc copy -oac mp3lame -o "$vout".mp3 "$vout".avi
rm "$vout".avi
rm divx2pass.log
exit 0

```copy and save this as any filename you like **in your home folder.** 
then enter this command:
```

chmod +x filenameyouchose

./filenameyouchose

```This will convert the video to avi, extract the mp3, and then delete the new video.
The mp3 will be pasted in your home folder.

---

### Post by mrpenguin on 2010-02-23
I have tried different things but it keeps on saying the file dont exist

> jaques@jaques-netbook:~$ chmod +x convert
jaques@jaques-netbook:~$ ./convert
file:///home/jaques/%20seminar.avi: 
file:///home/jaques/%20seminar: 
./convert: line 12: mencoder: command not found
./convert: line 16: mencoder: command not found
rm: cannot remove `.avi': No such file or directory
rm: cannot remove `divx2pass.log': No such file or directory


> #!/bin/bash
echo -n "file:///home/jaques/%20seminar.avi: "
    read vin
#
#
#
echo -n "file:///home/jaques/%20seminar: "
    read vout
#
#
#
mencoder "$vin" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o "$vout".avi
#
#
#
mencoder -of rawaudio -ovc copy -oac mp3lame -o "$vout".mp3 "$vout".avi
rm "$vout".avi
rm divx2pass.log
exit 0

maybe the %20 should not be there .... in movie player I clicked on the file name and clicked on copy location and this is what I got 
file:///home/jaques/%20seminar.avi

the file name is just : seminar.avi

---

### Post by andrew.46 on 2010-02-23
Hi mrpenguin,

> **mrpenguin said:**
> Thanks .... but i just keep on getting the same error message, must be doing something wrong

The name of the file or the path to the file must be incorrect (possibly a space in front of the name?). Can you post the results of:

```
find $HOME -iname '*seminar.avi'
```

Andrew

---

### Post by d3v1150m471c on 2010-02-23
Don't include the percentage.

you just want:

/path/to/file

---

### Post by chillicampari on 2010-02-23
> **andrew.46 said:**
> Hi mrpenguin,



The name of the file or the path to the file must be incorrect (possibly  a space in front of the name?). Can you post the results of:

```
find $HOME -iname '*seminar.avi'
```Andrew

  I was wondering the same.

---

### Post by d3v1150m471c on 2010-02-23
Don't alter the script I wrote the way you did or it won't run properly. Just copy and save it. It will prompt you for the video in which case you'll type in the path to the file with the format.

example:
```

~/videos/videotouse.mp4

```

Next it will ask you for the name of the sound/song you want to extract _without_ a format extension:
```

newsong

```

It will run mencoder, convert the video to .avi, then extract the mp3 with the name you gave it, then it will delete the .avi video it made to extract from.

---

### Post by mrpenguin on 2010-02-23
> jaques@jaques-netbook:~$ find $HOME -iname '*seminar2.avi'
/home/jaques/seminar2.avi
jaques@jaques-netbook:~$ 


i added a 2 to the file name

I am still getting the same error even after removing the %

> jaques@jaques-netbook:~$ chmod +x /home/jaques/seminar2.avi
jaques@jaques-netbook:~$ ./home/jaques/seminar2.avi
bash: ./home/jaques/seminar2.avi: No such file or directory
jaques@jaques-netbook:~$ 


---

### Post by d3v1150m471c on 2010-02-23
no...
copy the script I wrote and save it in your **home folder**. Use something like kate or gedit.
then in your terminal:
```

chmod +x nameyousavedthescriptas

```
...then:
```

./nameyousavedthescriptas

```

---

### Post by mrpenguin on 2010-02-23
> jaques@jaques-netbook:~$ chmod +x convert
jaques@jaques-netbook:~$ ./convert
file:/home/jaques/seminar2.avi: 
file:/home/jaques/seminar2: 
./convert: line 12: mencoder: command not found
./convert: line 16: mencoder: command not found
rm: cannot remove `.avi': No such file or directory
rm: cannot remove `divx2pass.log': No such file or directory
jaques@jaques-netbook:~$ 


is is the gedit file named convert

> #!/bin/bash
echo -n "file:/home/jaques/seminar2.avi: "
    read vin
#
#
#
echo -n "file:/home/jaques/seminar2: "
    read vout
#
#
#
mencoder "$vin" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o "$vout".avi
#
#
#
mencoder -of rawaudio -ovc copy -oac mp3lame -o "$vout".mp3 "$vout".avi
rm "$vout".avi
rm divx2pass.log
exit 0

---

### Post by d3v1150m471c on 2010-02-23
use the script i originally posted. not the one someone modified. it should be my first post.

If you do that you'll get something like this in your terminal:

```

d3v11@d3v11m4ch1n3:~$ ./gank
Enter the name of the video INCLUDING the extension and path: ~/Videos/tool_stinkfist.flv
Enter the name of the new video WITHOUT an extension behind the path: stinkfist

```

---

### Post by mrpenguin on 2010-02-23
This is my gedit file right now


> #!/bin/bash
echo -n "/home/jaques/seminar2.avi: "
    read vin
#
#
#
echo -n "/home/jaques/seminar2: "
    read vout
#
#
#
mencoder "$vin" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o "$vout".avi
#
#
#
mencoder -of rawaudio -ovc copy -oac mp3lame -o "$vout".mp3 "$vout".avi
rm "$vout".avi
rm divx2pass.log
exit 0


still getting the same error

---

### Post by d3v1150m471c on 2010-02-23
you're still not using the code I originally posted. secondly, it prompts you for the file to extract from then it will prompt you to input a name for the new song/sound you want to extract...you have to type these in. if you leave them blank then mencoder will do absolutely nothing.

---

### Post by mrpenguin on 2010-02-23
I coped and pasted your file but changed the file path like it said
which part is wrong ?

---

### Post by mrpenguin on 2010-02-23
> jaques@jaques-netbook:~$ chmod +x convert
jaques@jaques-netbook:~$ ./convert
/home/jaques/seminar2.avi: ~/home/jaques/seminar2.avi
/home/jaques/seminar2: seminar
./convert: line 12: mencoder: command not found
./convert: line 16: mencoder: command not found
rm: cannot remove `seminar.avi': No such file or directory
rm: cannot remove `divx2pass.log': No such file or directory



> jaques@jaques-netbook:~$ chmod +x convert
jaques@jaques-netbook:~$ ./convert
/home/jaques/seminar2.avi: ~/home/jaques/seminar2.avi
/home/jaques/seminar2: /home/jaques/seminar2
./convert: line 12: mencoder: command not found
./convert: line 16: mencoder: command not found
rm: cannot remove `/home/jaques/seminar2.avi': No such file or directory
rm: cannot remove `divx2pass.log': No such file or directory


i cant figure out what i am doing wrong

---

### Post by Yellow Pasque on 2010-02-23
[http://www.avidemux.org/admWiki/index.php?title=Save_only_audio](http://www.avidemux.org/admWiki/index.php?title=Save_only_audio)

---

### Post by mrpenguin on 2010-02-23
what i have realized now is that when I do all of that in the terminal it deletes my avi file ????

---

### Post by d3v1150m471c on 2010-02-23
It will only delete the avi file it creates and/or you gave the path to. I dunno, not to be rude put I've put everything quiet plainly so you'll have to reread it and do it correctly, learn how to use mencoder, or learn how to use avidemux.

---

### Post by chillicampari on 2010-02-23
Quick question, are we all certain mencoder is even installed? And I'm still wondering if there are still any hidden special characters in the file name. 

avidemux (like Temujin mentioned) may actually be an easier route for the OP, or Sound Converter (which if isn't installed by default since I don't remember, is probably in the repositories).

---

### Post by mc4man on 2010-02-23
moved

---

### Post by mrpenguin on 2010-02-23
thanks for all the help
will go over it again and see what i am doing wrong


i dont remember installing mencoder
and i looked again, i dont see any special characters

---

### Post by chillicampari on 2010-02-23
Just for grins I would give Sound Converter a try.

Edit- yeah, I really don't remember if mencoder comes with the default install. If not, it's handy to have (and you need it for that script in this thread). 

If you renamed the file, and you completely retyped it, the space should be gone now. Beginning (and trailing) spaces can be a lot harder to spot. Spaces in general in file names can do wonky things.

Good luck and I hope you get it split out okay.

---

### Post by NightwishFan on 2010-02-23
Soundconverter or Oggconvert would probably work, considering they use Gstreamer. That is a good suggestion.

I was thinking along the lines of this:
```
ffmpeg -i /path/to/input/file.avi -vn -acodec libmp3lame /path/to/output/file.mp3
```

---

### Post by mrpenguin on 2010-02-23
I used avidemux ... it worked pretty good, was able to extract the audio and make an mp3 file

thanks everybody

---

### Post by megamania on 2010-02-23
> **mrpenguin said:**
> I have tried different things but it keeps on saying the file dont exist

./convert: line 12: mencoder: command not found

As somebody else pointed out, are you sure that mencoder is installed?

In the terminal, type 
```
mencoder
```
and post the output here.

---

### Post by jalirious on 2010-04-11
You can make mpg (audio files) from dvds using the latest k9copy.

---

