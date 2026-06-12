---
title: "How can I make videos from several pictures?"
date: 2007-05-25
forum: Multimedia Production
---

### Post by jsmidt on 2007-05-25
I have hundreds of snapshots (jpegs) of research I am working on.  I want to combine them into a movie like cartoons do.  Which program should I use do do that?

---

### Post by nedecor on 2007-05-25
Try stopmotion. [http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/index.php](http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/index.php)

sudo apt-get install stopmotion

You must have Universe Repositories enabled.

---

### Post by koosfoto.hu on 2007-05-27
Hi!

I have tried out StopMotion... but it did not work for me.

I have just learnt about ManSlide... and it seems to be exciting!

However, I do not know how to install it under my Ubuntu.

So, I suggest you to have a look at it, and if you know how to install itt, please, share it with me!

Buy the way, I used already ManDVD for the same thing, and it is GREAT! It is available under Ubuntu, as well... However, it has a limitation of 99 pictures in a show.

Greetings,

Tamas

---

### Post by 4ebees on 2007-09-28
Hi there,

If you're still looking for an option, Kino will do the job.

It has the ability to import images from a file en masse.

You can then add sound if you wish, make various changes and add bits and pieces of various effects, then export as a DVD compatible mpeg.

Then, using something like DVDStyler or ManDVD, you can create menus etc and put out a great product... I do this regularly.

---

### Post by koosfoto.hu on 2007-09-29
Thanks 4ebees!

I have Kino, I re-installed it today... and I still do not find the option where it takes photo files. 

Where and how does this Kino imports the jpg photos? 

THANKS,

Tamas
(an e-bee?)

---

### Post by 4ebees on 2007-10-18
> **koosfoto.hu said:**
> Thanks 4ebees!

I have Kino, I re-installed it today... and I still do not find the option where it takes photo files. 

Where and how does this Kino imports the jpg photos? 

THANKS,

Tamas
(an e-bee?)

Hi there. Sorry for the delay. I didn't get a notice that you'd posted to the thread. :(

I noticed in the very latest version of Kino that you can no longer import a number of images in the same fashion. Bugger.

Put all your images in one folder then run:

image2raw -a -r <enter digits for the number of times you wish it to repeat each image>*.jpeg > file.dv

eg. image2raw -a -r 25 *.jpeg > file.dv

If you had 20 files, this will give you raw video showing 20 images, each of one second long (25 frames per second for PAL).

You can run this in a terminal:

man image2raw

and it will provide you with the manual for this application.

Hope this helps. If you get stuck, PM me as well as leaving a message here.

---

### Post by yabbies on 2007-10-19
take a look at cinepaint

---

### Post by ruibernardo on 2007-10-19
What worked for me was qdvdauthor. It can create a video from pictures. It's a GUI for dvdauthor and dvd-slideshow and it can create a movie from pictures like a slideshow.

When I tried qdvdauthor (back in April and on Feisty), the package of dvd-slideshow (the real program that do the work) did not support widescreen (16:9), but I've downloaded the SVN and it worked very well (It might be in Gutsy now).

[http://dvd-slideshow.sourceforge.net/wiki/Main_Page](http://dvd-slideshow.sourceforge.net/wiki/Main_Page)

To use only the command line with dvd-slideshow (without qdvdauthor) is very easy:[INDENT]Create a configuration file for the pictures[/INDENT][INDENT]```
dir2slideshow -n 'Album_Name' -t 10 directory_where_pictures_are/
```Create the movie
```
dvd-slideshow -p -w Album_Name.txt
```Test the movie
```
mplayer -sid 0 "Album_Name.vob"
```[/INDENT]

---

### Post by ellster456 on 2007-10-23
In the command line part where you're supposed to put directory_where_pictures_are what do you actually put there? I put the /home/user/folder there (with correct names in place of default names of course) and it said the file was wrong.

---

### Post by ruibernardo on 2007-10-23
> **ellster456 said:**
> In the command line part where you're supposed to put directory_where_pictures_are what do you actually put there? I put the /home/user/folder there (with correct names in place of default names of course) and it said the file was wrong.

It works here. What's the error? If your directory name has spaces (I'm guessing it might be your problem), try:

```
dir2slideshow -n 'Album_Name' -t 10 "directory where pictures are/"

```

---

### Post by ellster456 on 2007-10-23
I'm going to just completely copy/paste what is shown in terminal.

[B]tinkerbell@tinkerbell-desktop:~$ dvd-slideshow -n "Socks" -t 10 "/home/tinkerbell/socks/"
[dvd-slideshow]            dvd-slideshow 0.7.5
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2006 by Scott Dylewski
[dvd-slideshow]            
[dvd-slideshow] ERROR: Input file /home/tinkerbell/socks/ does not exist.
tinkerbell@tinkerbell-desktop:~$ [/B]

My username is tinkerbell... the folder  name is Socks where my pictures are.

---

### Post by loell on 2007-10-23
you can also make videos from pictures using picasa for linux

by

selecting the picture --> in **create menu** --> **movie**

---

### Post by ruibernardo on 2007-10-23
> **ellster456 said:**
> I'm going to just completely copy/paste what is shown in terminal.

[B]tinkerbell@tinkerbell-desktop:~$ [COLOR=Red]dvd-slideshow[/COLOR] -n "Socks" -t 10 "/home/tinkerbell/[COLOR=Blue]s[/COLOR]ocks/"
[dvd-slideshow]            dvd-slideshow 0.7.5
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2006 by Scott Dylewski
[dvd-slideshow]            
[dvd-slideshow] ERROR: Input file /home/tinkerbell/socks/ does not exist.
tinkerbell@tinkerbell-desktop:~$ [/B]

My username is tinkerbell... the folder  name is [COLOR=Blue]**S**[/COLOR]ocks where my pictures are.

First - maybe you are trying to point to a directory that doesn't exist. Check if the first letter in the directory name is uppercase.

Second - you must run dir2slideshow before running dvd-slideshow, as I've posted on my previous posts.

If you find it too hard, you can try qdvdauthor (it uses dvdslideshow from a GUI - point & click and you're done) or try the other options posted here and available on the repositories.

:popcorn:

---

### Post by nhandler on 2007-10-24
I tried following the steps given in this thread, but I can't get them to work. As dvd-slideshow finishes running, I get this:
> [dvd-slideshow] Concatenating all audio files...
[dvd-slideshow] Creating ac3 audio...
[dvd-slideshow] ERROR during ffmpeg execution!


How do I fix the ffmpeg error. I currently have it installed from the Gutsy repositories.

---

### Post by ellster456 on 2007-10-24
I was able to successfully install qdvdauthor, and made a slideshow. I don't suppose there's a way to upload it to Youtube is there? I know there's ways to upload dvds to Youtube but was hoping I could skip the dvd step and upload directly.

---

### Post by ruibernardo on 2007-10-24
I'm not sure of this but If you have the *.vob files, try to rename them to *.mpeg (that's what vob files are, a mpeg container). Test if you can see these *.mpeg files on you computer. If they work, mpeg is a common video file type, so I think that Youtube should accept them.

---

### Post by timcredible on 2007-10-24
i use digikam to make movies from photos, you can add sound also.  it makes mpeg files so you can upload them to youtube.  works very well.  install digikam and kipi-plugins via synaptic.

you can take the digikam-created mpegs and make them into a dvd if you want with any number of dvd creation programs (dvdstyler, qdvdauthor, deeveedee, etc.) if you want.

---

### Post by 4ebees on 2007-10-25
> **ellster456 said:**
> I was able to successfully install qdvdauthor, and made a slideshow. I don't suppose there's a way to upload it to Youtube is there? I know there's ways to upload dvds to Youtube but was hoping I could skip the dvd step and upload directly.

Hi ellster,

You'd probably have to import the video to Kino and then edit it according to the youtube requirements. Or become familiar with ffmpeg:

[http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html](http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html)

HTH

---

### Post by ellster456 on 2007-10-26
Ok I apparently don't know how to make a slideshow in qdvdauthor afterall. I thought it made it but it didn't. 

I also downloaded digikam. It works, but I don't know how to use it either. I tried looking for an online guide but the guide said nothing about slideshows. 

Where can I find information on how to make slideshows using these programs?

---

### Post by moeFinley on 2007-10-26
How about an Mencoder solution.  This comes straight out of the manual and would convert all the .jpg files in the source folder to a single MPEG4 video.

```
mencoder "mf://*.jpg" &#8722;mf fps=25 &#8722;o output.avi &#8722;ovc lavc &#8722;lavcopts vcodec=mpeg4
```

---

### Post by 4ebees on 2007-10-26
> **ellster456 said:**
> Ok I apparently don't know how to make a slideshow in qdvdauthor afterall. I thought it made it but it didn't. 

I also downloaded digikam. It works, but I don't know how to use it either. I tried looking for an online guide but the guide said nothing about slideshows. 

Where can I find information on how to make slideshows using these programs?

Hi there,

Check out this thread.

[http://ubuntuforums.org/showthread.php?t=339956](http://ubuntuforums.org/showthread.php?t=339956)

I'm certain it will help.

If not, get back to me and let me know.

Regards,

4ebees

---

### Post by ellster456 on 2007-10-27
Ahh wonderful 4ebees! Turns out I had to get that kipi plugin stuff. 

I just did a test slideshow, and at the last second right when I thought it was going great it spit me out this error:

[B]Encoding audio file...

/usr/bin/images2mpg: line 874: /usr/bin/mpg123: No such file or directory
-----------------------------------------------

EXIT STATUS : error during encoding process.[/B]

Is this as easily fixed as me going under /usr/bin and creating a folder and calling it mpg123 or do I need to install something more?

---

### Post by loell on 2007-10-27
do
```
sudo apt-get install mpg123
```

---

### Post by ellster456 on 2007-10-27
It works! And I didn't even have to convert from XVCD to mpeg it became an mpg all by itself and uploaded to Youtube effortlessly. 

Thank you all for your help!

---

### Post by xc3RnbFO8P on 2007-10-27
try [http://www.getdeb.net/search.php?keywords=mandvd]("http://www.getdeb.net/search.php?keywords=mandvd")

---

### Post by 4ebees on 2007-10-28
> **ellster456 said:**
> It works! And I didn't even have to convert from XVCD to mpeg it became an mpg all by itself and uploaded to Youtube effortlessly. 

Thank you all for your help!

It was really just a matter of helping you with all YOUR work :))

No probs.

Glad to be of help.
:KS

---

### Post by shane2peru on 2007-12-20
> **4ebees said:**
> Hi there. Sorry for the delay. I didn't get a notice that you'd posted to the thread. :(

I noticed in the very latest version of Kino that you can no longer import a number of images in the same fashion. Bugger.

Put all your images in one folder then run:

image2raw -a -r <enter digits for the number of times you wish it to repeat each image>*.jpeg > file.dv

eg. image2raw -a -r 25 *.jpeg > file.dv

If you had 20 files, this will give you raw video showing 20 images, each of one second long (25 frames per second for PAL).

You can run this in a terminal:

man image2raw

and it will provide you with the manual for this application.

Hope this helps. If you get stuck, PM me as well as leaving a message here.

That is a slick and easy trick!  Sure beats playing around with bulky slow GUI programs!  :)  Thanks!

Shane

---

### Post by 4ebees on 2007-12-22
> **shane2peru said:**
> That is a slick and easy trick!  Sure beats playing around with bulky slow GUI programs!  :)  Thanks!

Shane

Definitely more than welcome. I love little hacks like that and equally like passing them on.

Merry Christmas and a Happy New Year to all!

---

### Post by scotty64 on 2007-12-30
I had a similar problem: Make a time lapse movie out of over 7000 still images. I tried cinelerra and stopmotion - both a no-go for me. Cinelerra tries to load everything at once what means it eats up your memory. Stopmotion simply crashed after a couple of thousand images. What works excellent is Blender!
Blender is not just an excellent 3D-animation program, it has a built in powerful Video Sequence Editor (VSE). 
You can add a strip of thousands of stills in the VSE and Blender only loads what is needed - no gigs of RAM and constantly swapping thing. The speed-effect even allows stretching your moviestrip to slow it down or compress it to speed it up. As an example: I needed a kind of "high speed slideshow" with an output of 2 frames per second with a smooth transition between the frames. Blender transformed my 7000 frames movie into 93000 and created smooth transitions between the keyframes from my original movie with the "enable frame blending" option enabled. And, last but not least, as Blender has built in ffmpeg, you can render your movie (including audio) in many different formats and bandwidths.
Take a look at [www.blender.org](www.blender.org) for the software and blenderartists.org for an excellent forum. The Blender Wiki has docs about the VSE: [http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing](http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing)

---

### Post by koosfoto.hu on 2007-12-31
Hello Scotty64,

This solution is a nice present for the New Year!
We just started here the 2008... some 27 minutes ago...

Thanks a lot for the idae... and may I wish to You, and to the Whole World a [COLOR="Red"][SIZE="4"]very happy 2008![/SIZE][/COLOR]


I have checked the program... wow... it seems rather complex to me... 

In it I have found the VSE (top left corner, little menu-icon)... however, after I was lost... How to add the pictures,. what to do and how?
I went to see the docs, as well... and I am still lost.

Please, please, if you may... could you put together a little "how to"?

Thanks a lot,

Tamas

---

### Post by eye208 on 2008-01-02
> **koosfoto.hu said:**
> In it I have found the VSE (top left corner, little menu-icon)... however, after I was lost... How to add the pictures,. what to do and how?
I went to see the docs, as well... and I am still lost.

Please, please, if you may... could you put together a little "how to"?
How to read a manual, part one:

"Blender comes with a few screen layouts, one of which is *5-Sequence*."

This is the first line of [http://wiki.blender.org/index.php/Manual/Sequence_Screen_Layout](http://wiki.blender.org/index.php/Manual/Sequence_Screen_Layout), yet instead of changing the screen layout you used the top left icon which changes the view for only one window. It's no surprise you got stuck at that point since nothing really changed on screen. Please try again.

[http://wiki.blender.org/index.php/Manual/Using_VSE#Rendering_a_Video_from_an_Image_Sequence_Set](http://wiki.blender.org/index.php/Manual/Using_VSE#Rendering_a_Video_from_an_Image_Sequence_Set) is labeled "Rendering a Video from an Image Sequence Set". I think that's exactly what you are looking for. It's all in the manual, you just have to read it.

---

### Post by scotty64 on 2008-01-04
> **koosfoto.hu said:**
> Hello Scotty64,

This solution is a nice present for the New Year!
We just started here the 2008... some 27 minutes ago...

Thanks a lot for the idae... and may I wish to You, and to the Whole World a [COLOR="Red"][SIZE="4"]very happy 2008![/SIZE][/COLOR]

Please, please, if you may... could you put together a little "how to"?

Thanks a lot,

Tamas

I agree, blender IS a very complex program. And I would suggest to you to have a look at the docs and tutorials as well. The interface seems odd on the first look, but once you have done some work with Blender you will learn to love it more and more. A tip for the VSE here:
Every window in blender's GUI can display everything. So you can even open the VSE twice by selecting it e.g. in both upper windows. This is good, as you can use one VSE to work with your pictures and strips and you can set the second one to "image preview" that allows you seeing the frames and the movie when you run the animation. Image preview is the option with the face on it in the dropdown box right of the "Strip" menu.

---

### Post by CheeseEatingBulldog on 2008-01-07
You can do this in Kino by going to FX tab and using a picture and defining the time you want it to run, and then just click render. This will make a kino rendered video file. Do this for all the pictures you want and then go to export and make sure to select all. Export to format you want. Reopen file you exported in kino and add sound, then export again to have video with music/sound.

/Not behind  my pc at the moment, but that is how I did it.

---

### Post by Patterson on 2008-01-07
I  used dreamity for combining my pictures.

---

### Post by 4ebees on 2008-01-07
> **Patterson said:**
> I  used dreamity for combining my pictures.

Hi there,

I gather this is a Windows only program? Is that right? Do you run it under Wine? 

Regards,

4ebees

---

### Post by 4ebees on 2008-01-07
Hi CEB :)

If you look at one of the earlier posts I made in this thread, you'll see that you can do this much more easily using a command line hack.

Regards,

4ebees 


> **CheeseEatingBulldog said:**
> You can do this in Kino by going to FX tab and using a picture and defining the time you want it to run, and then just click render. This will make a kino rendered video file. Do this for all the pictures you want and then go to export and make sure to select all. Export to format you want. Reopen file you exported in kino and add sound, then export again to have video with music/sound.

/Not behind  my pc at the moment, but that is how I did it.

---

### Post by Patterson on 2008-01-08
> **4ebees said:**
> Hi there,

I gather this is a Windows only program? Is that right? Do you run it under Wine? 

Regards,

4ebees

Yes, this is a windows program, i have used it in my win Xp

---

### Post by Rewil on 2008-01-08
Like Cheater, I am also getting an error message when I run dvd-slideshow:

Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
[dvd-slideshow] ERROR during ffmpeg execution!

If I preserve the temporary files, the video.mpg file plays in Movie Player as I expect, and the properties seem to be correct.

I have been following the instructions from epimeteo's post (except the second line should have "-f" instead of "-w"), so the source was first created with dir2slideshow, then dvd-slideshow was run.

Any ideas on how to find the problem?

---

### Post by basbeek on 2008-02-17
Hi Rewil,

Sorry to revive this old post but I may have a solution to your problem.

You need to change the parameter for ffmpeg in /usr/bin/dvd-slideshow

from -ab 192 to -ab 192k

In other words every where you see ffmpeg in /usr/bin/dvd-slideshow add the letter 'k' to the end of the -ab option.

That did the trick by me

---

### Post by fadain on 2008-02-17
^ Yes that solves the problem, thank you basbeek.

---

