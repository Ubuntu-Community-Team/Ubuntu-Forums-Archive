---
title: "script to cut selected scenes from a video"
date: 2011-10-07
forum: Multimedia Software
---

### Post by scarob3000 on 2011-10-07
Hi
i need help to cut select scenes from a video.

I have a video of a volleyball game. 
I have the start time of every action, example
0 15
15 27
27 39
39 55
55 72
72 90
start, end values of the action are in seconds.
Now I want to create a new video with only selected actions ( for example action n.1, n.5 and n.6)

it's possible? with mplayer? with a script?
the source file can be a .*vob file?

Please help me

---

### Post by WasMeHere on 2011-10-07
Hi scarob3000,

I suggest you do it interactively with *OpenShot*, a video editor and converter. The program is in the repositories, so you can easily download it using ```
sudo apt-get install openshot
```

Have fun
Olle

---

### Post by thatguruguy on 2011-10-07
> **scarob3000 said:**
> Hi
i need help to cut select scenes from a video.

I have a video of a volleyball game. 
I have the start time of every action, example
0 15
15 27
27 39
39 55
55 72
72 90
start, end values of the action are in seconds.
Now I want to create a new video with only selected actions ( for example action n.1, n.5 and n.6)

it's possible? with mplayer? with a script?
the source file can be a .*vob file?

Please help me

It's pretty easy, I think, from a command line using ffmpeg.  At least,  I've done it with .mpg files, and it should be doable with a .vob file.

You'd rip the various scenes as follows. Assuming your file is called something like "volleyball.vob", you'd open a terminal, go to where the file is and type:
```
ffmpeg -i volleyball.vob -sameq -t 00:00:15.000 scene1.mpg
```... to rip the first scene. After that runs, type:
```
ffmpeg -i volleyball.vob -sameq -ss 00:00:15.000 -t 00:00:12.000 scene2.mpg
```... and so forth, until you've ripped each individual scene.  The "-**i**" means "input", the "-sameq" means "encode at the **same** **q**uality" the "-ss" mean start time (measured as hours:minutes:seconds.milliseconds) and "-t" is the length of the clip.  Notice that there is no dash at the beginning of the name of the clip that will be rendered.

After you've ripped the individual scenes, you can recombine them with the following short line.  Assuming you want scenes 1, 3 and 6, and place them together in a video called "newvolleyballvid.mpg", you'd do something like this:
```
cat scene1.mpg scene3.mpg scene6.mpg | ffmpeg -f mpeg -i - -vcodec copy -acodec copy newvolleyballvid.mpg
```The "cat" statement puts the three videos together into one file. The ffmpeg statement copies the new file, as its generated, into an .mpg file (-f mpeg) using the same video codec and audio codec as originally used (-vcodec copy and -acodec copy).

---

### Post by scarob3000 on 2011-10-07
work perfecty!!!
Now, is possible to put the START and DURATION in a file txt and generate the sceneNN.mpg file automatically with a script?

---

### Post by thatguruguy on 2011-10-07
Probably. But I just keep a text file handy with the instructions, and copy and paste them into a terminal. I never created an over-arching script for this, because I didn't think it would save me any time vs. simply copying and pasting.

As far as the ripping of the files goes, you can actually open several different terminals at once, and have a process running for each file.  Then, once all of them are done, you can do the last step to make the new, truncated video.

---

### Post by FakeOutdoorsman on 2011-10-07
> **thatguruguy said:**
> "-sameq" means "encode at the **same** **q**uality"
This is an unfortunate result of poorly written documentation. This has been changed upstream to:
```
-sameq        use same quantizer as source (implies VBR)
```
An improvement, but I admit it's still not very descriptive to the general user.

sameq works in some situations: when the input and output share the same "quantizer scale" in the same range, which usually means the linear MPEG quantizer scale, and in FFmpeg these are: flv/h263/h263+/mpeg1/mpeg2/mpeg4/msmpeg* (by flv I mean the format, not the container). Quantizer and quality are loosely correlated, and sameq is useful if you know exactly what you're doing, and I don't always understand, so I hardly ever use it.

In this case, since vob should be cat friendly if I remember correctly, I don't think you should have to re-encode at all and can slightly modify thatguruguy's example:
```
ffmpeg -ss 15 -i volleyball.vob -t 12 -vcodec copy -acodec copy scene2.mpg
```
I used seconds as the *ss* and the *t* values just to show that these options can accept seconds in addition to the *hours:minutes:seconds:milliseconds* format. A more [verbose explanation](http://ubuntuforums.org/showpost.php?p=10113019&postcount=7) of these options.

---

### Post by scarob3000 on 2011-10-07
I need a script because  in a game there are between 120 and 200 action!
I need to generate automatically the sceneNN.mpg file...

After I need to creare 8-10 short clips each with 8-10 action and  this I can do it with the simply copy and paste

---

### Post by scarob3000 on 2011-10-07
SOLVED!

in the text file intime.txt i have the START, DURATION values
```

0 15
15 12
27 42
42 15
57 70
70 90

```

the script createscene.sh:

```

#!/bin/bash
i="1"

while read FIRST SECOND
do
ffmpeg -i 1.avi -sameq -ss $FIRST -t $SECOND scene$i.mpg &
i=$[$i+1]
done < intime.txt

```

with ./createscene.sh i have all the single action-scenes!!!
THANK you!!!!!!

---

### Post by thatguruguy on 2011-10-07
> **FakeOutdoorsman said:**
> This is an unfortunate result of poorly written documentation. This has been changed upstream to:
```
-sameq        use same quantizer as source (implies VBR)
```An improvement, but I admit it's still not very descriptive to the general user.

sameq works in some situations: when the input and output share the same "quantizer scale" in the same range, which usually means the linear MPEG quantizer scale, and in FFmpeg these are: flv/h263/h263+/mpeg1/mpeg2/mpeg4/msmpeg* (by flv I mean the format, not the container). Quantizer and quality are loosely correlated, and sameq is useful if you know exactly what you're doing, and I don't always understand, so I hardly ever use it.

In this case, since vob should be cat friendly if I remember correctly, I don't think you should have to re-encode at all and can slightly modify thatguruguy's example:
```
ffmpeg -ss 15 -i volleyball.vob -t 12 -vcodec copy -acodec copy scene2.mpg
```I used seconds as the *ss* and the *t* values just to show that these options can accept seconds in addition to the *hours:minutes:seconds:milliseconds* format. A more [verbose explanation]("http://ubuntuforums.org/showpost.php?p=10113019&postcount=7") of these options.

Thanks for the info!

As an aside, I got into the habit of using the hh:mm:ss:milli format, because I used it to cut commercials out of recorded programs.  That way, I could do a better job of controlling where the cuts were.

---

