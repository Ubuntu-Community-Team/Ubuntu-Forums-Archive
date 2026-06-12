---
title: "Create Video from JPEGs"
date: 2010-01-18
forum: Multimedia Software
---

### Post by Cavsfan on 2010-01-18
My 1st and only grandson turned 1 year old and we have taken about 1 million pics of him.
I wanted to make a video from pictures taken in the past year. The first one is an ultra sound picture.
The last one was taken this last Saturday. I have 153 12 MPixel pictures in a folder. 
They are named C001.jpg - C153.jpg (I can rename them if needed).

Does anyone have experience doing this? I had noticed mencoder or ffmpeg can create movies from jpegs. 
But, I didn't think about the frames per second. Would I need to make like 20 copies of each picture and then 
make it like 10 FPS? or something like that? Optimally, I would like to have a video where each picture lasts for 
8-10 seconds or so and I would be able to add a song as audio. (I think I know how to use mencoder to add the audio). 

Your help will be very much appreciated and I will take notes and learn from this! :D
It's painful to have to ask twice for the same help!

Thanks in advance!

---

### Post by ron999 on 2010-01-18
HI
I don't think it's a 'video', as such, I think that you will be making a 'slideshow'.
But I don't know how to go about doing this.
:)

---

### Post by SPazzo on 2010-01-18
OK, so there are a couple things you can do.  You can, as ron999 said, show them as a slideshow.  F-spot has that option.  Just make a directory that has **only** the pictures you want in the slideshow, open the first one with f-spot, and press F5 (or View > Slideshow).  That will have a full screen slideshow of all of the pictures in that directory.

There is an alternate method.  You can use a Video editing software to make a video file.  On that video file would basically be the a slideshow, of all of the pictures you want, for how long you want.  This is a little more complicated, but if you want to try it, try downloading [Slideshow Creator]("http://slcreator.sourceforge.net/") or [LiVES]("http://lives.sourceforge.net/").  Both are fairly easy to use and would probably work for your needs.  LiVES is in the software centre, and Slideshow Creator has a .deb on their website.

Good luck.

---

### Post by Cavsfan on 2010-01-19
Thanks for the replies! Yes, I definitely want a slideshow! I will look into this!

---

### Post by Cavsfan on 2010-01-19
What I want to do is create a slideshow, but I want the output to be AVI (if possible).
I would like to be able to upload it to YouTube and possibly make a DVD for my daughter.
I have seen examples of **Mencoder** being able to do this. 

I tried this command with 25 FPS:
mencoder "mf://*.jpg" -mf fps=25 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4
But, the output went way too fast. It lasted like 1 second!).

Then I tried this one with 1 FPS:
mencoder "mf://*.jpg" -mf fps=1 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4
But, it only showed 3 pictures (I think) and was only 3 seconds long.

Is there any knowledgeable mencoder users out there that can tell me how to modify the 
above command to make it read the entire 153 pics and display them for a reasonable amount of time? 
The pictures are not all exactly the same size and I was hoping this would not matter.
Right now it seems I just have a FPS and a time length issue.

Thanks in advance!

---

### Post by Jose Catre-Vandis on 2010-01-19
Check that you have a contigious list of filenames, no gaps and all the same format e.g. 001.jpg, 002.jpg, 003.jpg and so on. Also ensure that they are all jpgs. 

You can set fps below 1, e.g 0.5 (2 second display), .02 (5 second display)

or you could play about with the speed setting and slow the whole thing down.

Then you can add some music to it :)

---

### Post by chewearn on 2010-01-19
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html)

---

### Post by chewearn on 2010-01-19
[]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html")It seemed the pictures have to be the same dimension, and the width must be integer multiple of 4.

EDIT
Further investigation on resizing the images.  I tried using "convert" which comes from "imagemagick" package.

The commands below will run through all the files in the directory "in", convert each to 800x600 with black border padding, and dump the output into directory "out".

```

mkdir out
for a in $( ls in ); do convert "in/$a" -resize 800x600 -background black -gravity center -extent 800x600 "out/$a"; done

```Your mencoder command with fps=1 should be working then.

---

### Post by Cavsfan on 2010-01-19
Thanks! You all are great and this is the best forum! :D

I will look over these! Thanks again!

---

### Post by Cavsfan on 2010-01-19
OK, I guess I have never really ran a script before.
On the desktop I have the In folder with the pictures.
I copied you script and added the top line:

CD /home/Cavsfan/Desktop
mkdir out
for a in $( ls in ); do convert "in/$a" -resize 800x600 -background black -gravity center -extent 800x600 "out/$a"; done

I tried adding .sh to the end of the gedit text file I saved this as.
(That changed the coloring of the text)
Then I checked Nautilus preferences > behavior  to Run Executable Text files when they are opened.
But still nothing!
Sometimes you feel so insignificant and dumb over the smallest things and this is one of them for me. ](*,)

Thanks! :oops:

---

### Post by chewearn on 2010-01-19
The commands are supposed to be entered directly into terminal.  But if you want to put into a script, add this as the first line:
```

#!/bin/bash

```

So it should look like this:
```

#!/bin/bash

mkdir out[FONT=monospace]
[/FONT]for a in $( ls in ); do
convert "in/$a" -resize 800x600 -background black -gravity center -extent 800x600 "out/$a"
done


```

---

### Post by Cavsfan on 2010-01-19
That script worked [COLOR=Red]fantastic [/COLOR]and I did just enter it in the terminal.
I am learning. But the AVI still came out only 3 seconds long with FPS=1
This is the command I entered inside the out directory:

mencoder "mf://*.jpg" -mf fps=1 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4

It is 3 seconds long and displays the first 3 pictures in the folder.

Thanks for all of your help!

---

### Post by Cavsfan on 2010-01-19
Something is wrong with pic 2 and 3 and that must be why it only displays 3 pictures
no matter what the FPS is set to. I look at the properties > image and instead of displaying 
800 x 600 like the rest it just says loading...

Trying to figure that out...

---

### Post by Cavsfan on 2010-01-19
I deleted the contents of out and ran the script again, but the exact same results occurred.
Picture 2 and 3 indicate loading... on the properties instead of 800 x 600.
All of the rest of them show the correct resolution 800 x 600.

I cannot figure this out! It is messed up after the script converts the files, but I don't know why.

:confused:

---

### Post by amoeba801 on 2010-01-19
Hi,

I can't help you with the mencoder problem, but note that making slides using mencoder is limited as it doesn't provide transitions from slide to slide, etc. You might want to consider some alternatives (both of which I successfully use):

From the command line, I use [dvd-slideshow]("http://dvd-slideshow.sourceforge.net/wiki/Main_Page"). The author gives a complete guide to creating a standalone DVD [here]("http://dvd-slideshow.sourceforge.net/wiki/Complete_Example"). 

Alternatively, [imagination]("http://imagination.sourceforge.net/") is a GUI based program.  It is still in development, but works for my simple needs.

---

### Post by chewearn on 2010-01-20
> **Cavsfan said:**
> I deleted the contents of out and ran the script again, but the exact same results occurred.
Picture 2 and 3 indicate loading... on the properties instead of 800 x 600.
All of the rest of them show the correct resolution 800 x 600.

I cannot figure this out! It is messed up after the script converts the files, but I don't know why.

:confused:

Since it's two pictures only, perhaps you could manually convert these two, e.g. using GIMP.

---

### Post by Cavsfan on 2010-01-21
> **chewearn said:**
> Since it's two pictures only, perhaps you could manually convert these two, e.g. using GIMP.

I have been trying different things and I got past the first few pictures, but for some reason ImageMagick 
is not really seeing all 153 pictures. 
When I enter this identify command in the out directory, it is only seeing 38 of the 153 still.

All 153 of the images display 800 x 600 in properties.
(Inside of out directory I enter "[COLOR=Red]identify *.jpg[/COLOR]" and this is the output (notice how it skips around e.g. going from C021 to C034):

```
C001.jpg JPEG 800x600 800x600+0+0 8-bit DirectClass 269kb 
C002.jpg[1] JPEG 800x600 800x600+0+0 8-bit DirectClass 84.3kb 
C003.jpg[2] JPEG 800x600 800x600+0+0 8-bit DirectClass 77.8kb 
C004.jpg[3] JPEG 800x600 800x600+0+0 8-bit DirectClass 129kb 
C005.jpg[4] JPEG 800x600 800x600+0+0 8-bit DirectClass 136kb 
C006.jpg[5] JPEG 800x600 800x600+0+0 8-bit DirectClass 131kb 
C007.jpg[6] JPEG 800x600 800x600+0+0 8-bit DirectClass 131kb 
C008.jpg[7] JPEG 800x600 800x600+0+0 8-bit DirectClass 134kb 
C009.jpg[8] JPEG 800x600 800x600+0+0 8-bit DirectClass 338kb 
C010.jpg[9] JPEG 800x600 800x600+0+0 8-bit DirectClass 143kb 
C011.jpg[10] JPEG 800x600 800x600+0+0 8-bit DirectClass 135kb 
C012.jpg[11] JPEG 800x600 800x600+0+0 8-bit DirectClass 95.2kb 
C013.jpg[12] JPEG 800x600 800x600+0+0 8-bit DirectClass 121kb 
C014.jpg[13] JPEG 800x600 800x600+0+0 8-bit DirectClass 112kb 
C015.jpg[14] JPEG 800x600 800x600+0+0 8-bit DirectClass 104kb 
C016.jpg[15] JPEG 800x600 800x600+0+0 8-bit DirectClass 135kb 
C017.jpg[16] JPEG 800x600 800x600+0+0 8-bit DirectClass 123kb 
C018.jpg[17] JPEG 800x600 800x600+0+0 8-bit DirectClass 115kb 
C019.jpg[18] JPEG 800x600 800x600+0+0 8-bit DirectClass 120kb 
C020.jpg[19] JPEG 800x600 800x600+0+0 8-bit DirectClass 119kb 
C021.jpg[20] JPEG 800x600 800x600+0+0 8-bit DirectClass 114kb 
C034.jpg[21] JPEG 800x600 800x600+0+0 8-bit DirectClass 61.1kb 
C035.jpg[22] JPEG 800x600 800x600+0+0 8-bit DirectClass 98.8kb 
C036.jpg[23] JPEG 800x600 800x600+0+0 8-bit DirectClass 107kb 
C038.jpg[24] JPEG 800x600 800x600+0+0 8-bit DirectClass 67.1kb 
C041.jpg[25] JPEG 800x600 800x600+0+0 8-bit DirectClass 59.1kb 
C042.jpg[26] JPEG 800x600 800x600+0+0 8-bit DirectClass 40.2kb 
C043.jpg[27] JPEG 800x600 800x600+0+0 8-bit DirectClass 67.5kb 
C044.jpg[28] JPEG 800x600 800x600+0+0 8-bit DirectClass 56.4kb 
C045.jpg[29] JPEG 800x600 800x600+0+0 8-bit DirectClass 68.4kb 
C051.jpg[30] JPEG 800x600 800x600+0+0 8-bit DirectClass 54.8kb 
C052.jpg[31] JPEG 800x600 800x600+0+0 8-bit DirectClass 50.2kb 
C053.jpg[32] JPEG 800x600 800x600+0+0 8-bit DirectClass 74.5kb 
C058.jpg[33] JPEG 800x600 800x600+0+0 8-bit DirectClass 51.3kb 
C059.jpg[34] JPEG 800x600 800x600+0+0 8-bit DirectClass 50.7kb 
C060.jpg[35] JPEG 800x600 800x600+0+0 8-bit DirectClass 47.1kb 
C069.jpg[36] JPEG 800x600 800x600+0+0 8-bit DirectClass 70.9kb 
C125.jpg[37] JPEG 800x600 800x600+0+0 8-bit DirectClass 296kb 

```Even "ls" and "ls *.jpg" entered in the out directory yield different results.
("ls" lists all files, but only the 38 displayed above are kind of a pink color and the rest are black, while "ls *.jpg" lists only the 38 that are displayed above and all are pink)

So, the problem would be in the convert command and not in the mencoder command.
Would you have any idea why?

Thanks!
PS Thanks to everyone else, but I am on a mission with mencoder right now and it is doing exactly what I want, except for this issue.

---

### Post by Cavsfan on 2010-01-21
I think I discovered something :idea:

Only the images that end in .jpg are the ones that are working.
The ones that end in .JPG are not!

If I can figure out a way to get them all to small letters, I think it would work.
And I have found that the properties displaying 800 x 600 do not matter.

Only the jpg vx JPG appears to matter.

---

### Post by chewearn on 2010-01-21
> **Cavsfan said:**
> Even "ls" and "ls *.jpg" entered in the out directory yield different results.
("ls" lists all files, but only the 38 displayed above are kind of a pink color and the rest are black, while "ls *.jpg" lists only the 38 that are displayed above and all are pink)

The different colour meant that Ubuntu has somehow identified the files as different type.  I think pink are images; black are probably text files.  I'm not sure why you ended up with text files.

You could add "-verbose" switch to the "convert" command to see some output during conversion.  It might gave a clue.

> Only the images that end in .jpg are the ones that are working.
The ones that end in .JPG are not!

Since ext3 file system is case sensitive, "ls *.jpg" and "ls *.JPG" give different results.

---

### Post by chewearn on 2010-01-21
> **Cavsfan said:**
> If I can figure out a way to get them all to small letters, I think it would work.

I forgot this part; to rename "JPG" to "jpg":
```
rename -v 's/JPG/jpg/' *.JPG
```

---

### Post by michy99 on 2010-01-21
This will rename all the JPG to jpg.```
rename 's/\.JPG/.jpg/' *.JPG
```

EDIT: someone beat me to it.

---

### Post by thatguruguy on 2010-01-21
You can also consider using blender to create the video.  That way, you can manipulate the pictures in some cool ways and make something more than a flat slide show.  Here's one I made with some photographs modified with gimp and blender: [http://www.youtube.com/watch?v=vI35Gk2rmps](http://www.youtube.com/watch?v=vI35Gk2rmps)

---

### Post by Cavsfan on 2010-01-21
> **chewearn said:**
> I forgot this part; to rename "JPG" to "jpg":
```
rename -v 's/JPG/jpg/' *.JPG
```

Man, you guys are good!
I found this while googling: "rename -v 's/\.JPG$/\.jpg/' *.JPG"
and I believe it is the same as what you all are saying!  :popcorn:

It worked and all of the images in the out folder are "pink" with the ls command
and they are all small (.jpg) vs. caps (.JPG!

Thanks a lot! I am learning a lot too! I love this stuff!!! :guitar:

And I did not mean anything bad by saying "Man" and "guys" above! This is just a habit and I do not mean
to diminish the intelligence of any females out there! I know there are super smart females out there and plenty of them!

Thanks a lot! I know it will work now and I can make that DVD of my grandson's 1st year of life!
It's going to be sweet!

Too bad everyone in the world aren't as helpful as the people in this forum! :D
Thanks again! And I will let you know when this video is made. I have put MP3 with movies before, so I should be able to handle that!

---

### Post by Cavsfan on 2010-01-21
> **thatguruguy said:**
> You can also consider using blender to create the video.  That way, you can manipulate the pictures in some cool ways and make something more than a flat slide show.  Here's one I made with some photographs modified with gimp and blender: [http://www.youtube.com/watch?v=vI35Gk2rmps](http://www.youtube.com/watch?v=vI35Gk2rmps)

That is a super nice video!!! I will look into that, but right now my mind "hurts" from all of the thinking! LOL 
Linux is definitely where you learn something every day! 
One who thinks they know everything there is to know, would have to be either a genius or a fool!
Thanks!!!

---

### Post by Cavsfan on 2010-01-21
Well I have a video that displays the 153 pictures for 2 seconds each and it looks good!

**Thatguruguy**, is there much of a learning curve with blender? It looks pretty intimidating as I installed it and started it up. 
But, most things are at first. I really do like your video!

And in my previous post I meant no offense as I realize there are probably quite a lot of people on here that can figure out 
anything! I would venture to say that there quite a lot of geniuses using Linux too.

Thanks for everyone's help! I certainly do appreciate it!

---

### Post by thatguruguy on 2010-01-21
There is a learning curve involved in learning to use Blender.  However, they maintain a lot of tutorials (see [http://www.blender.org/education-help/](http://www.blender.org/education-help/)), there's a pretty good forum for the users of Blender ([http://blenderartists.org/forum/](http://blenderartists.org/forum/)) and there are a ton of how-to videos on youtube.  It's worth playing around with.

---

### Post by uniomni on 2012-08-10
Thank you so much. This command (with different frame rates) worked a treat:

mencoder "mf://*.jpg" -mf fps=10 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4

Thanks again for posting something that works :-)
o


> **Cavsfan said:**
> What I want to do is create a slideshow, but I want the output to be AVI (if possible).
I would like to be able to upload it to YouTube and possibly make a DVD for my daughter.
I have seen examples of **Mencoder** being able to do this. 

I tried this command with 25 FPS:
mencoder "mf://*.jpg" -mf fps=25 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4
But, the output went way too fast. It lasted like 1 second!).

Then I tried this one with 1 FPS:
mencoder "mf://*.jpg" -mf fps=1 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4
But, it only showed 3 pictures (I think) and was only 3 seconds long.

Is there any knowledgeable mencoder users out there that can tell me how to modify the 
above command to make it read the entire 153 pics and display them for a reasonable amount of time? 
The pictures are not all exactly the same size and I was hoping this would not matter.
Right now it seems I just have a FPS and a time length issue.

Thanks in advance!

---

### Post by Cavsfan on 2012-08-10
> **uniomni said:**
> Thank you so much. This command (with different frame rates) worked a treat:

mencoder "mf://*.jpg" -mf fps=10 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4

Thanks again for posting something that works :-)
o

Glad you could benefit from it. I got that to work and made a movie DVD of my grandson with pictures.
But, it's been so long ago I don't remember much about it.

---

