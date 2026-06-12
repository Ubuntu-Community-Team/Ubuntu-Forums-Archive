---
title: "How do I do frame-by-frame video editing?"
date: 2008-02-05
forum: Multimedia Production
---

### Post by King_Critter on 2008-02-05
Ok, so I just filmed my and a friend whacking away at each other with toy lightsabers (probably the first thing everyone does when they first get a video camera :P) and I want to rotoscope in some cool lightsaber effects using the gimp. 

Problem: how do I get the frames to edit? Is there a tool I use to extract the frames and then composite them back together, or is there a Gimp plugin that handles that?

---

### Post by Gannin on 2008-02-05
There is a Gimp type program for working with video, I believe it's called Film Gimp or something like that.  You could also try using Blender.  Even though it's a 3D modeling program, it also has video editing capabilities.

---

### Post by Creative2 on 2008-02-05
i don't know if it's usefull or not ;

ffmpeg -i movie.mpg -f image2 -vcodec mjpeg menu%d.jpg

this create photo form your movie  then you can create the movie from phot with this 

ffmpeg -f image2 -i img%d.jpg  -newaudio  AUDIOFILE  /tmp/a.mpg

---

### Post by philc on 2008-02-05
> **Gannin said:**
> There is a Gimp type program for working with video, I believe it's called Film Gimp or something like that. 

That'd be Cinepaint :)

[http://www.cinepaint.org/](http://www.cinepaint.org/)

From their website:

"CinePaint is used for motion picture frame-by-frame retouching..."

Sounds promising.

---

### Post by philc on 2008-02-05
> **Creative2 said:**
> i don't know if it's usefull or not ;

ffmpeg -i movie.mpg -f image2 -vcodec mjpeg menu%d.jpg

this create photo form your movie  then you can create the movie from phot with this 

ffmpeg -f image2 -i img%d.jpg /tmp/a.mpg

I too was going to suggest FFmpeg, but as far as I know it is only possible to extract images per second, not per frame. i.e. one image per second, not 25 (or 29 or 30) images per second.

I'd be happy to be told I'm wrong.

---

### Post by Creative2 on 2008-02-05
> **philc said:**
> I too was going to suggest FFmpeg, but as far as I know it is only possible to extract images per second, not per frame. i.e. one image per second, not 25 (or 29 or 30) images per second.

I'd be happy to be told I'm wrong.

you can for with this for example 

 ffmpeg -i dsci0040.AVI -f image2 -r 1  imagines%d.jpg
[B]
-r 1 [/B]

-ss 30 -t 30  time option..

xD i wil write command line for my Converter fuoco tools :)

---

### Post by philc on 2008-02-05
> **Creative2 said:**
> you can for with this for example 

 ffmpeg -i dsci0040.AVI -f image2 -r 1  imagines%d.jpg
[B]
-r 1 [/B]

-ss 30 -t 30  time option..



So, the above command has set the framerate to 1 and forced the format to image2.

What if I, or the original poster, wants to extract all 25 frames contained within the first 1 second of video as individual images files?

---

### Post by Creative2 on 2008-02-05
ah i am sorry , i have read bad :

i think default option extract every photo , i mean 2 sec of movie at 25 fps = 
50 photos extracted , well this is what i remember not sure 100% so skip -r 1 option ..

---

### Post by Amr_not_Amr on 2008-02-05
Have you tried LiVES ?
[http://lives.sourceforge.net/](http://lives.sourceforge.net/)

---

### Post by eye208 on 2008-02-05
> **King_Critter said:**
> Ok, so I just filmed my and a friend whacking away at each other with toy lightsabers (probably the first thing everyone does when they first get a video camera :P) and I want to rotoscope in some cool lightsaber effects using the gimp.
There is a [lightsaber plugin effect](http://wiki.blender.org/index.php/Manual/Sequence_Plugins#Lightsaber_Plugin_Effect) for Blender.

---

### Post by King_Critter on 2008-02-06
Well, thanks for all the replys, but I found out I could do it all with very easily with Cinerella. :)

If anyone's interested, here's the steps:

load the movie you want to split into frames. Click File > Render. Pick the folder you want to save it to, as well as the filename (minus extension). Then choose JPEG Sequence as the File Format. Check the "Render video tracks" box, and, if you want audio, that box as well. Leave everything else alone, and hit the big green checkmark.

To get the frames back into a video file, click File > Load Files. Navigate to the directory you saved the jpeg sequence in, and open the first file only, the one that doesn't have a number tacked on the end (this actually isn't a picture at all even though the extension is jpg -- open it up with  a text editor and take a look). Choose insertion strategy as "Create new resource only" and hit the checkmark. If you have a lot of frames, this may take a while. Then look in the media folder in the resources window, and you should see a file. Drag that onto the timeline, and viola! ^_^ You can then render the movie as whatever you want.

---

### Post by philc on 2008-02-06
> **philc said:**
> 
What if I, or the original poster, wants to extract all 25 frames contained within the first 1 second of video as individual images files?

I'm glad King_Critter found a solution with Cinelerra.

I just wanted to follow up on my own previously posed question. 

Extracting all frames, for example 25 frames per second, from a video file is possible for sure with FFmpeg.

Here's the command I used:

```
ffmpeg -i input.dv -r 25 -f image2  images%05d.png
```

So quite close to what Creative2 suggested.

From a video that was 104 seconds long, this created 2600 png image files in the current directory.

If you just wanted 25 frames from the first 1 second, then this line will work:

```
ffmpeg -i input.dv -r 25 -t 00:00:01 -f image2  images%05d.png
```

Or, perhaps all frames from 5 seconds of footage, beginning at the tenth second, then:

```
ffmpeg -i input.dv -r 25 -ss 00:00:10 -t 00:00:05 -f image2  images%05d.png
```

Or a single indicative poster frame of the video clip from the first second of footage:

```
ffmpeg -i input.dv -r 1  -t 00:00:01 -f image2  images%05d.png
```

If you want the poster frame from a different part of the clip, the specify which second to take it from using the -ss tag, in conjunction with the line above.

Lastly, if you wanted to create a thumbnail story board, showing action throughout the entire length of the video clip, you'll need to specify the output image dimensions. Use the following line:

```
ffmpeg -i input.dv -r 1  -f image2 -s 120x96 images%05d.png
```

My original file was 720x576. 

I hope this helps someone.

---

