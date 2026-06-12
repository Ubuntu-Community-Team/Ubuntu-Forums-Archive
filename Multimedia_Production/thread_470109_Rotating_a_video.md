---
title: "Rotating a video"
date: 2007-06-10
forum: Multimedia Production
---

### Post by groeswenphil on 2007-06-10
You know when a total idiot like myself takes a brilliant piece of video but has turned the camera to portrait fashion..............well is there an application that would turn it around?
I suppose I could lie on my side or turn the monitor around, but there must be a neater fix to my problem.
Yours in anticipation.
Phil Edwards

---

### Post by finite9 on 2007-06-11
you're not the only one to have done this...i have the same problem after filming on a Canon ixus.  I looked at Kino but it only mirrors or flips it doesnt rotate.  Sorry I don't have a solution, but you can rule out Kino at least.  Maybe one of the other editors like Cinelerra or kdenlive or lives has this function.

---

### Post by AlexMR on 2007-06-11
Hello Phil,

Avidemux has a plugin which enables rotating video clips:

[http://www.getdeb.net/release.php?id=478](http://www.getdeb.net/release.php?id=478)

Greetings,
Alex

---

### Post by finite9 on 2007-06-19
I found out that you can do this easily with mplayer...

```
mplayer -vo xv -vf rotate file.avi
```

to play it from the CLI

or if you want to convert the video and save it then use the -vf rotate filter in your encoding script

---

### Post by drushka on 2007-07-06
> Avidemux has a plugin which enables rotating video clips:
> [http://www.getdeb.net/release.php?id=478](http://www.getdeb.net/release.php?id=478)

Hi Alex, that didn't seem very helpful.
I've installed avidemux from feisty repos, it's 2.3.0 and does not come with any plugins.
Which package do I onstall for plugins (or where do I find them)?

Thanks, d

---

### Post by bridd on 2007-07-08
> **drushka said:**
> > 
Hi Alex, that didn't seem very helpful.
I've installed avidemux from feisty repos, it's 2.3.0 and does not come with any plugins.
Which package do I onstall for plugins (or where do I find them)?


A bit of confusion on terminology I think -Avidemux calls 'em Filters rather than plugins.

Open your video up, select Video menu->Filters (or control+alt+f).  From here you can set whatever filter you want, including the Rotate one ! :cool:

---

### Post by hartz on 2007-08-06
You can also do this in VLC media player.  Just install it with Synaptic.

Then 
1. Open your video file in VLC player
2. Click Settings -> Extended GUI
3. Click Transformation.  This will achieve a 90 degree rotation.

If you want a 180 degree or a 270 degree rotation, click Settings, then Preferences, then go to Video -> Filters -> Transformation and change it there :-)

---

### Post by vitt84 on 2007-09-24
hi..
i opened a MOV file in avidemux to rotate it.
then, i added the Rotate filter.
if i click file->save the output file isn't rotated. why? what i am doing wrong?

thanks in advance

---

### Post by andrew.46 on 2007-09-24
Hi,

 Read your post while chasing mplayer info:

> **finite9 said:**
> I found out that you can do this easily with mplayer...```
mplayer -vo xv -vf rotate file.avi
```
to play it from the CLI or if you want to convert the video and save it then use the -vf rotate filter in your encoding script

 And of course in typical mplayer fashion there are many options to this:

```
       rotate[=<0-7>]
              Rotates  the  image  by 90 degrees and optionally flips it.  For
              values between 4-7 rotation is only done if the  movie  geometry
              is portrait and not landscape.

                 0    Rotate by 90 degrees clockwise and flip (default).

                 1    Rotate by 90 degrees clockwise.

                 2    Rotate by 90 degrees counterclockwise.

                 3    Rotate by 90 degrees counterclockwise and flip.

```

 For an extra touch of coolnes mplayer will take your movie and output each frame as a gif, png or jpg with various options for each format!

               Andrew

---

### Post by henriquemaia on 2007-12-09
> **AlexMR said:**
> Hello Phil,

Avidemux has a plugin which enables rotating video clips:

[http://www.getdeb.net/release.php?id=478](http://www.getdeb.net/release.php?id=478)

Greetings,
Alex

Heh, nice! I have tried avidemux but failed to see that one. Thanks for pointing it out.

---

### Post by DaveQB on 2008-04-02
> **vitt84 said:**
> hi..
i opened a MOV file in avidemux to rotate it.
then, i added the Rotate filter.
if i click file->save the output file isn't rotated. why? what i am doing wrong?

thanks in advance

Same problem here.  I don't know whats up with avidemux2

Thank god for MEncoder.

---

### Post by cotcot on 2008-04-02
Blender and Cinelerra can rotate video.

---

### Post by DaveQB on 2008-04-02
Oh cool.  I have been trying to get started on some tutorials for both of those applications. 

How good is Blender for video editing ?

---

### Post by cotcot on 2008-04-03
> **DaveQB said:**
> Oh cool.  I have been trying to get started on some tutorials for both of those applications. 

How good is Blender for video editing ?
Very good. I thought blender was for 3D animation. When somebody on this forum told us that video editing in blender is very good but unknown I started to learn it and to see that he was right.

---

### Post by nolan- on 2008-05-06
> **vitt84 said:**
> hi..
i opened a MOV file in avidemux to rotate it.
then, i added the Rotate filter.
if i click file->save the output file isn't rotated. why? what i am doing wrong?

thanks in advance

I was having the same problem but I figured it out, you have to select the **VIDEO** menu on the left of the screen, **NOT** from the top menu. You have to change it from **COPY** to whatever format you wish. Just select the AVI option. This then allows you to select filters menu (just below the copy menu still in video section) which was previously unavailable. Apply the rotate filter and select angle then save.

I think if you apply the filter from the top video menu but leave the side menu alone then you will just save a copy of the original file. Thats why it doesn't rotate

Hope this helps.

---

### Post by adhuvi on 2008-06-10
> **andrew.46 said:**
> Hi,

 Read your post while chasing mplayer info:



 And of course in typical mplayer fashion there are many options to this:

```
       rotate[=<0-7>]
              Rotates  the  image  by 90 degrees and optionally flips it.  For
              values between 4-7 rotation is only done if the  movie  geometry
              is portrait and not landscape.

                 0    Rotate by 90 degrees clockwise and flip (default).

                 1    Rotate by 90 degrees clockwise.

                 2    Rotate by 90 degrees counterclockwise.

                 3    Rotate by 90 degrees counterclockwise and flip.

```

 For an extra touch of coolnes mplayer will take your movie and output each frame as a gif, png or jpg with various options for each format!

               Andrew

How exactly can I do that?! Creating png images out of every frame of a mpg video. Using either mencoder or mplayer? 
I was trying to rotate a video and i already achieved that with mplayer :D
thanks!

---

### Post by Creative2 on 2008-06-11
fuoco tools--------->Video Filter------>to Rotate--->Rotate   by 90 degrees clockwise (this is for 640 for 480 anyway just to give you an example)

```
mencoder INPUT -ofps 25 -ovc xvid -oac copy -vf scale -zoom -xy 640 -xvidencopts bitrate=700 -vf rotate=1 -o OUTPUT
```

---

