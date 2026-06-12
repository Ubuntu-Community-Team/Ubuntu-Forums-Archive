---
title: "HOWTO: Make Time Lapse Videos from Photographs"
date: 2012-07-10
forum: Multimedia Software
---

### Post by CyberAngel on 2012-07-10
After looking around, searching, reading and experimenting, I ended up with a bunch of commands to quickly make high quality time lapse videos under Linux. One of the hardest (almost impossible) things to find, is software for photo deflickering so for solving this (or at least improve the results), I created my own little Perl script to compute and change the average luminance (brightness) of all of the photographs.

If some of the commands below are not working, you might need to apt-get install some extra software, but all of it is available in the repositories :)

[SIZE="4"]A Quick Introduction to Time Lapse Videos[/SIZE]
From Wikipedia: *Time-lapse photography is a technique whereby the frequency at which film frames are captured (the frame rate) is much lower than that used to view the sequence. When played at normal speed, time appears to be moving faster and thus lapsing. For example, an image of a scene may be captured once every second, then played back at 30 frames per second. The result is an apparent 30-times speed increase. Time-lapse photography can be considered the opposite of high speed photography or slow motion.*


[SIZE="4"]How to take good pictures to compose a time lapse video afterwards[/SIZE]
The rest of the steps might not be reproducable with compact point and shoot cameras.

[SIZE="3"]Tripod[/SIZE]
First of all the camera needs to be very stable between shots to make the composition easy later on, therefore, a tripod needs to be used. 

[SIZE="3"]Intervalometer[/SIZE]
Choose how many total pictures need to be taken and set your camera to take one picture every some predefined interval (for example one every 5 seconds). This can be done either with computer software, or the camera itself. Some cameras have a built in intervalometer or they can accept external accessories. 

[SIZE="3"]Calculate Final Video Length[/SIZE]
If you choose to take 300 pictures, and you make a final video running at 10 frames per second, then your video will be 30 seconds long (300/10=30s). At 25 frames per second, the same video will be only 12 seconds long (300/25=12s). It is a good idea to plan the desired length for your video beforehand, and take some more photographs to achieve a smoother movement with higher frame rates (especially when moving objects are near your camera).

[SIZE="3"]Camera Settings[/SIZE]
For a good time lapse video, the camera needs to be set to Manual mode and choose a non changing Aperture (A), Shutter speed (S), ISO and Focus. This will reduce flickering (different brightness between pictures) a lot as the overall brightness of the pictures will not be changing between shots. 
What I usually do, is that I put the camera on the tripod and take pictures in auto mode until I am satisfied with the result. Then I look at the chosen from the camera settings (A, S, ISO), change the mode to manual and use the same settings as the camera did in auto mode. The auto focus is used to focus on the main object properly, and before starting the intervalometer, I change it to manual focus as well as the other settings, because all of the pictures need to have exactly the same focus.

There are certain cases (sunset is one of them) that lighting conditions might change a lot during your shots, and a fixed set of A, S and ISO settings might not give good results after sometime. In this case, I always choose a stable Aperture to avoid changes in the depth of field (DOF), ISO and focus, and let the shutter speed vary (Usually the A or Aperture mode of your camera can do this). This technique will introduce more flickering because the exposure metering of your camera will calculate slightly different values sometimes. 

[SIZE="4"]Making the Video[/SIZE]
This is the actual purpose of this tutorial. To show you how to use Linux to put everything together fast.

[SIZE="3"]Step 1[/SIZE]
Make a new folder and copy all of your photographs taken for the time lapse into it. Sort the images by capture date/time and store them in a new folder called "renamed". This is useful if your camera messes up the filename ordering when it starts counting from 0001 after reached the highest possible number (e.g. ..., DSC_9998, DSC_9999.jpg, DSC_0001, DSC_0002).

```
mkdir source_folder_of_pictures
cp /media/cf/* source_folder_of_pictures/
cd source_folder_of_pictures
mkdir renamed
counter=1
ls -1tr *.jpg | while read filename; do cp $filename renamed/$(printf %05d $counter)_$filename; ((counter++)); done
cd renamed
```

[SIZE="3"]Step 2[/SIZE]
Resize the images first to 1920x1080 to get a Full HD output or 3840x2160 if you need 4K output. All the rest of the operations will be much much faster if you do this now since you will be working with smaller sized files.

```
mkdir resized
mogrify -path resized -resize 1920x1080! *.JPG # If you want to keep the aspect ratio, remove the exclamation mark (!)
# You can also use the mogrify from graphicsmagick package which is faster, I use it in combination with the command "parallel" in order to utilize all of my CPU cores and perform the resize much faster.
# Of course, you can use the command "parallel" with the imagemagick mogrify
# parallel --progress gm mogrify -quality 100 -output-directory resized -resize 1920x1080! ::: *.JPG # Similar as before, remove the exclamation mark in order to keep the aspect ratio.
cd resized

```

[SIZE="3"]Step 3 (OPTIONAL)[/SIZE]
If you photos have noticeable flickering which is caused by slightly different exposure between taken photos, download the attached script, put it in the directory *source_folder_of_pictures/renamed/resized/*, make it executable and run it. The script will create a subdirectory "source_folder_of_pictures/renamed/resized/Deflickered" to store the processed photos.
You can get the latest version of the script at [https://github.com/cyberang3l/timelapse-deflicker/blob/master/timelapse-deflicker.pl]("https://github.com/cyberang3l/timelapse-deflicker/blob/master/timelapse-deflicker.pl")

```
sudo apt-get install libfile-type-perl libterm-progressbar-perl
chmod +x timelapse-deflicker.pl
./timelapse-deflicker.pl -h
./timelapse-deflicker.pl -v
cd Deflickered
```

[SIZE="3"]Step 4[/SIZE]
Use ffmpeg to combine all of the photos in one video without losing quality! This will create a big file as it will only put all of the JPG files together in a single uncompressed video. Change the "**-r 25**" in the following command, to match your frames per second you wish to get in the final video.
**[COLOR="#FF0000"]Note[/COLOR]**: Use ONLY ONE of the following 3 commands. I usually choose the first one if I am working with jpeg files, as it will simply copy the source images and each one will occupy one frame in the resulting video. It is also ultra fast since it doesn't do any re-compression.
```
ffmpeg -r 25 -pattern_type glob -i '*.jpg' -c:v copy output.avi # Change -r 25 to define the frame rate. 25 here means 25 fps.
# Alternative commands, but your jpeg images will be recompressed (maybe you want to use one of these if you have png or any other kind of images, or you want a smaller sized video)
ffmpeg -r 25 -pattern_type glob -i '*.jpg' -c:v mjpeg -q:v 2 output.avi # -q:v can get a value between 2-31. 2 is best quality and bigger size, 31 is worst quality and least size)
ffmpeg -r 25 -pattern_type glob -i '*.jpg' -c:v ljpeg output.avi # Lossless jpeg resulting in a huuuuuuuge file. Even larger in size than the sum of all of the input pictures together in the case of jpg images.

```

[SIZE="3"]Step 5 (OPTIONAL)[/SIZE]
Here you might want to use a non linear editor like kdenlive (which is the best non linear video editor I have found for Linux so far) to add some music to your video and introduce some effects (like smooth fade from black in the beginning of the video or fade to black in the end), but remember to export in a lossless quality format so that you won't get any noticable loss in quality.

On my latest attempt to create a 4k video with kdenlive, I had to create a custom 4k project profile (accessible from Settings -> Manage Project Profiles)

[ATTACH=CONFIG]258719[/ATTACH]

and a custom rendering profile (Project -> Render -> Create new profile) with the following contents:
```
acodec=ac3 ab=448k ar=44100 ac=2 vcodec=libx264 crf=15 rc-lookahead=60 coder=1 flags=+loop cmp=+chroma partitions=+parti8x8+parti4x4+partp8x8+partp4x4+partb8x8 me_method=umh subq=10 me_range=24 g=250 keyint_min=25 sc_threshold=40 i_qfactor=0.71 b_strategy=2 qcomp=0.6 qmin=0 qmax=51 qdiff=4 bf=8 refs=9 directpred=1 flags2=+mixed_refs+dct8x8+fastpskip+mbtree cqp=0 wpredp=2 trellis=2 weightp=2 deblock=1:0:0 direct=auto muxer=auto aspect=%dar
```

[ATTACH=CONFIG]258718[/ATTACH]


[SIZE="3"]Step 6[/SIZE]
Use ffmpeg to compress the video into a high quality Full HD one.
```
ffmpeg -i output.avi -c:v libx264 -preset slow -crf 15 output-final.mkv
```

If you created a 4k video and you want to resize it to 1080p, use the following command:
```
ffmpeg -i output.mkv -s 1920x1080 -c:v libx264 -preset slow -crf 15 output-final.mkv
```

Check here for more encoding options: [https://trac.ffmpeg.org/wiki/Encode/H.264](https://trac.ffmpeg.org/wiki/Encode/H.264)

You should definitely take a look in this post from FakeOutdoorsman: [http://ubuntuforums.org/showthread.php?t=2022316&page=5&p=13191696#post13191696](http://ubuntuforums.org/showthread.php?t=2022316&page=5&p=13191696#post13191696)
You can find many nice tips.

You are done!
Congratulations! Enjoy and brag for your own time lapse video :)

---

### Post by chili555 on 2012-07-11
Awesome! I have been experimenting unsuccessfully with time lapse for some time now. I have used a variety of tutorials and have been disappointed with the result. I just tried your steps and, with one exception, found it perfect. 

I have been an interval shooter for some time and have been strict with aperture, shutter speed and ISO. I also hardly ever shoot *any* photographs without a tripod, even the cat! Accordingly, I skipped the deflicker step and can't say if it works or doesn't. All the other steps produced an excellent result. I appreciate your hard work and, moreover, your generosity in posting it here. I have bookmarked and printed your posting and can hardly wait to get out under the stars for three or four hours with my Nikon, some Irish coffee and my best gal!

---

### Post by CyberAngel on 2012-07-11
Makes me happy that this information was found useful for someone else except me :)

Here are three videos I made with this technique:

[http://www.youtube.com/watch?v=lI75_Uce-2w](http://www.youtube.com/watch?v=lI75_Uce-2w)
[http://www.youtube.com/watch?v=BWjC2KOZTIc](http://www.youtube.com/watch?v=BWjC2KOZTIc)
[http://www.youtube.com/watch?v=yWgASCOfHng](http://www.youtube.com/watch?v=yWgASCOfHng)

The first two of them, use a variable shutter speed (you will see that the sun sets but the video is still bright) and for the 3rd one with the stars all of the settings are fixed. I wasn't out there with the camera and an Irish coffee though cause it was -20 degrees... I chose the cabin instead hehe

None of these videos use the deflickering script as this is something I made a couple of days ago.
The results of the deflickering script can be seen here:
[http://www.youtube.com/watch?v=SNfq__chC5M](http://www.youtube.com/watch?v=SNfq__chC5M)

---

### Post by chili555 on 2012-07-11
-20 degrees? But you use that funny centigrade there, don't you? You are right, that's cabin time for me, too. I usually quit about -10 C.

Very nice work there! I enjoyed them all.

Of course, this guy is the master: [http://www.timescapes.org/](http://www.timescapes.org/)  I love his moving stars. He uses a dolly for the camera, as well. 

I find myself doing more photography these days after midnight.

Thanks again for your excellent tutorial.

---

### Post by CyberAngel on 2012-07-11
> **chili555 said:**
> -20 degrees? But you use that funny centigrade there, don't you? You are right, that's cabin time for me, too. I usually quit about -10 C.

Very nice work there! I enjoyed them all.

Of course, this guy is the master: [http://www.timescapes.org/](http://www.timescapes.org/)  I love his moving stars. He uses a dolly for the camera, as well. 

I find myself doing more photography these days after midnight.

Thanks again for your excellent tutorial.

Yes, we use Celcius here :)

I didn't know timescapes.org! Indeed the master...

Terje Sorgjerd is another great one! Take a look here:
[http://vimeo.com/terjes](http://vimeo.com/terjes)

---

### Post by dckirba on 2012-08-16
Hi CyberAngel,

I was hoping to try your deflickering script but I ran into an error:

> Can't locate File/Type.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at ./timelapse-deflicker.pl line 25.
BEGIN failed--compilation aborted at ./timelapse-deflicker.pl line 25.

Any idea what I'm doing wrong or if there's anything I need to install?

Thanks in advance,
David

Edit: Learnt how to install the necessary PERL modules. Running the script right now :)

---

### Post by CyberAngel on 2012-08-21
> **dckirba said:**
> Hi CyberAngel,

I was hoping to try your deflickering script but I ran into an error:



Any idea what I'm doing wrong or if there's anything I need to install?

Thanks in advance,
David

Edit: Learnt how to install the necessary PERL modules. Running the script right now :)

Nice that you found solved the problem on your own :)

Did you see any improvement in the flickering?

---

### Post by dckirba on 2012-08-22
> **CyberAngel said:**
> 

Did you see any improvement in the flickering?

I definitely did. I'm trying to upload both version on Vimeo and I'll post links here. I was shooting around sunset so I guess the lighting lends itself to even more flickering than usual ;) Thanks for the script!

---

### Post by CyberAngel on 2012-08-22
Anyone knows why I cannot edit the first post to make some corrections?

I ran into some problems for some time lapses with this line of code:

```
ls -1tr | grep -v files.txt > files.txt
```

It should be:

```
ls -1 | grep -v files.txt > files.txt
```

---

### Post by MG&amp;TL on 2012-08-22
> **CyberAngel said:**
> Anyone knows why I cannot edit the first post to make some corrections?

I ran into some problems for some time lapses with this line of code:

```
ls -1tr | grep -v files.txt > files.txt
```It should be:

```
ls -1 | grep -v files.txt > files.txt
```


Hi CyberAngel, 

there are two points to make:

1. There is now a post-editing limit in force. You are now only allowed to edit your posts before 7 days have elapsed.

2. Tutorials and tips should now be made into wiki pages on the Ubuntu wiki: see [http://ubuntuforums.org/showpost.php?p=11802464&postcount=1](http://ubuntuforums.org/showpost.php?p=11802464&postcount=1)

---

### Post by denisf88 on 2012-08-24
Dear All,

Thank you for your post, which exactly meets my requirements : deflickering images for timelapse in ubuntu.

I meet the same error than dckirba, and gasped ! when seeing that he found the solution and did not share it !
> **dckirba said:**
> 
Edit: Learnt how to install the necessary PERL modules. Running the script right now :)

I think I found it by myself. I added the following packages through Synaptic :
libclass-methodmaker-perl (2.18-1build2)
libfile-type-perl (0.22-1.1)
libgstreamer-perl (0.16-1build1)
libterm-progressbar-perl (2.10-1)
libterm-readkey-perl (2.30-4build3)

Hoping this help some fellows and many thanks again for having shared this post and this script !

Denis

---

### Post by CyberAngel on 2012-08-24
> **denisf88 said:**
> Dear All,

Thank you for your post, which exactly meets my requirements : deflickering images for timelapse in ubuntu.

I meet the same error than dckirba, and gasped ! when seeing that he found the solution and did not share it !


I think I found it by myself. I added the following packages through Synaptic :
libclass-methodmaker-perl (2.18-1build2)
libfile-type-perl (0.22-1.1)
libgstreamer-perl (0.16-1build1)
libterm-progressbar-perl (2.10-1)
libterm-readkey-perl (2.30-4build3)

Hoping this help some fellows and many thanks again for having shared this post and this script !

Denis

You also need perlmagick :)

---

### Post by coldraven on 2012-09-01
Nice thread! I feel inspired to try some time lapse photography.
Can you recommend a camera? I don't have much cash so a second hand one would do.
My budget would be about £150 ($225)
Thanks.

---

### Post by CyberAngel on 2012-09-01
> **coldraven said:**
> Nice thread! I feel inspired to try some time lapse photography.
Can you recommend a camera? I don't have much cash so a second hand one would do.
My budget would be about £150 ($225)
Thanks.

Any DSLR will work with an external 15$-20$ intervalometer similar to this: [http://www.ebay.com/itm/New-Timer-Intervalometer-Remote-Shutter-Control-F-Nikon-D700-D300-D800-D200-D1-/280930533456?pt=Camera_Camcorder_Remotes&hash=item4168c3c050](http://www.ebay.com/itm/New-Timer-Intervalometer-Remote-Shutter-Control-F-Nikon-D700-D300-D800-D200-D1-/280930533456?pt=Camera_Camcorder_Remotes&hash=item4168c3c050)

Now if you have a computer nearby, you can use one of the fully supported cameras by gphoto2 or even a webcam: 
[http://www.moreno.marzolla.name/software/time_lapse_movies/](http://www.moreno.marzolla.name/software/time_lapse_movies/)

List of cameras supported by libgphoto2:
[http://www.gphoto.org/doc/remote/](http://www.gphoto.org/doc/remote/)

---

### Post by chili555 on 2012-09-01
Don't forget a sturdy tripod.

---

### Post by coldraven on 2012-09-03
@CyberAngel and Chili555 - Thanks for the links and tips.

---

### Post by chili555 on 2012-10-19
[https://vimeo.com/49848789](https://vimeo.com/49848789)

Created using your awesome tutorial. The Milky Way from the front deck of our vacation cabin in Arizona. Thanks again for your help.

---

### Post by CyberAngel on 2012-10-19
Awesome!

What camera did you use? Can you please share your settings?

---

### Post by chili555 on 2012-10-19
A Nikon D700 and a Rokinon, aka Samyang, 14mm f/2.8 lens on a tripod of course. 30 secs. at ISO 3200 on interval timer (built in to the D700) set for a new shot every 32 seconds for 75 shots. White balance was set to 3030K.

I shot RAW and then used ufraw-batch.

My next experiment will be longer and hopefully more interesting! 

I am fascinated with the Milky Way. [http://www.flickr.com/photos/chili5558/8052602911/in/photostream/lightbox/](http://www.flickr.com/photos/chili5558/8052602911/in/photostream/lightbox/)

---

### Post by CyberAngel on 2012-10-20
> **chili555 said:**
> A Nikon D700 and a Rokinon, aka Samyang, 14mm f/2.8 lens on a tripod of course. 30 secs. at ISO 3200 on interval timer (built in to the D700) set for a new shot every 32 seconds for 75 shots. White balance was set to 3030K.

I shot RAW and then used ufraw-batch.

My next experiment will be longer and hopefully more interesting! 

I am fascinated with the Milky Way. [http://www.flickr.com/photos/chili5558/8052602911/in/photostream/lightbox/](http://www.flickr.com/photos/chili5558/8052602911/in/photostream/lightbox/)

Milky way is amazing! I love it as well but my Nikon D300 produces lots of noise when the ISO is set at 3200.

Have you made any further processing?
It's impressive how low noise you get with the D700!

---

### Post by chili555 on 2012-10-20
> **CyberAngel said:**
> 
Have you made any further processing?
It's impressive how low noise you get with the D700!Certainly no noise processing. I do sharpening and a tiny bit of contrast but that's it. The high ISO performance of the D700 is indeed amazing but I wish I could get the family treasurer to make a better decision between a D800 and food on the table. I understand it's even *more* impressive! 

Will you be shooting the Orionids tonight?

---

### Post by CyberAngel on 2012-10-20
> **chili555 said:**
> Certainly no noise processing. I do sharpening and a tiny bit of contrast but that's it. The high ISO performance of the D700 is indeed amazing but I wish I could get the family treasurer to make a better decision between a D800 and food on the table. I understand it's even *more* impressive! 

Will you be shooting the Orionids tonight?

Start the diet then :) hehe

Well, I wish I could but Oslo is very rainy these days with no exception for tonight :(

---

### Post by FakeOutdoorsman on 2012-10-22
Nice howto, but I have a few suggestions.

> **CyberAngel said:**
> ```
mogrify -path resized -resize 1920x1080! *.jpg
```

I think preserving aspect ratio is more important than forcing the images to be exactly 1920x1080; otherwise the images may look weird due to stretching/shrinking of width/height to exactly fit 1920x1080. If you remove the ! then the aspect ratio will be preserved and width or height (whichever is biggest) will be limited to your declared values. Alternatively, if you just declare 1920, then "width given, height automagically selected to preserve aspect ratio", and if you just declare *x1080* then "height given, width automagically selected to preserve aspect ratio" (see [ImageMagick Image Geometry](http://www.imagemagick.org/www/command-line-processing.html#geometry) for more options).

> **CyberAngel said:**
> 
```
ffmpeg -i output.avi -y -s hd1080 -sameq output-final.avi
```


The *-sameq* option has been removed upstream. Also see [sameq does not mean "same quality"](http://superuser.com/a/478550/110524). Encoding to high-quality H.264 would provide excellent quality. See the CRF section of the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide).

I also recommend leaving out *-s hd1080* since you already resized the images with mogrify, and *-s hd1080* will force a resize to 1920x1080, ignoring aspect ratio.

---

### Post by CyberAngel on 2012-10-22
> **FakeOutdoorsman said:**
> Nice howto, but I have a few suggestions.....

Thanks for the recommendations :)
I will make some tests first and then change the needed lines!

---

### Post by evilonod on 2013-04-04
Glad you figured it out on your own too, but go ahead and share your solution.   I'm not having any luck figuring out where Type.pm is supposed to come from.  The script failed not finding Magick.pm and that was easy.  It was in the perlmagick package.  "Type" is too generic a term and I'm having trouble with my searches.

---

### Post by CyberAngel on 2013-04-04
> **evilonod said:**
> Glad you figured it out on your own too, but go ahead and share your solution.   I'm not having any luck figuring out where Type.pm is supposed to come from.  The script failed not finding Magick.pm and that was easy.  It was in the perlmagick package.  "Type" is too generic a term and I'm having trouble with my searches.

Usually all these perl libraries follow this package naming scheme in the repositories: libXXX-perl

If you see the source code, it is using **File::Type** library. So search for *lib file type perl* like this ```
apt-cache search lib file type perl
```

You will get a bunch of results and I think it is this one you need: libfile-type-perl

---

### Post by evilonod on 2013-04-04
Yep...Thanks CyberAngel...

Here's the next failed dependency:

Can't locate Term/ProgressBar.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /home/dolive/bin/timelapse-deflicker.pl line 26.

I assumed a curses type thing but libcurses-ui-perl didn't help.  

But I did find "libterm-progressbar-perl" had the right file.

Evilo

---

### Post by CyberAngel on 2013-08-18
Updated steps 5 and 7 to provide better results

---

### Post by nepomo on 2013-10-12
Would be nice to let other people know what you did to solve the PEARL module issue. I ran into the same problem. Thanks.

---

### Post by mgerber on 2014-01-05
Hello,

Nice tutorial. Just one problem for me. I've got an output.avi of say, 89MB, and a MKV of 100M. What's the best option to compress that properly.

I use following command line to convert it:
> avconv -y -i output.avi -c:v libx264 -preset slow -crf 15 output.mkv

---

### Post by mgerber on 2014-01-05
Hello,

Nice tutorial. Just one problem for me. I've got an output.avi of say, 89MB, and a MKV of 100M. What's the best option to compress that properly.

I use following command line to convert it:
> avconv -y -i output.avi -c:v libx264 -preset slow -crf 15 output.mkv

Thanks

---

### Post by CyberAngel on 2014-01-06
> **mgerber said:**
> Hello,

Nice tutorial. Just one problem for me. I've got an output.avi of say, 89MB, and a MKV of 100M. What's the best option to compress that properly.

I use following command line to convert it:


Thanks

Check this link for more encoding options:
[https://trac.ffmpeg.org/wiki/x264EncodingGuide](https://trac.ffmpeg.org/wiki/x264EncodingGuide)

I guess if you change CRF to a higher value (23 is the default one) and/or play with bitrate, you will achieve the compression level you need.

My intention with the command mentioned in this tutorial is to get a high quality video without artifacts, rather than compressing the video much (in your case obviously it's the opposite.. The final output is bigger).

---

### Post by mgerber on 2014-01-06
Thank you for the guide. I'll check it out.

My purpose is to have a good quality/size ratio. When I'm travelling, videos and pics take a lot of space. And I don't need highest quality yet. If I'll publish it, it will only save time (as in some third world countries internet connections are fairly slow) if it's not too big.

---

### Post by Light-kun on 2014-05-29
Nice tutorial, thanks!

1) I've  ran into segfault when trying to do a TL video from more than 1000 pictures:
 Segmentation faultf (38%) 11.87fps Trem:   2min 809mb  A-V:0.000 [77605:0]
After this error I'm getting the video which consists of 1000 pics.

I know I can make few parts and stick them together in another utility, but I want to make  this process easier.

2)  >> I ran into some problems for some time lapses with this line of code:
 >> ls -1tr | grep -v files.txt > files.txt
 >> It should be:
 >> ls -1 | grep -v files.txt > files.txt

Why? I have no problems with first command. Even the first command is better in my case:
I have camera which makes number to pictures from 0001.JPG to 9999.JPG and after last number it creates another directory and starts over from  0001.JPG.
so time sorting in ls command makes my video proper, when name sorting wil lscrew my video up.

---

### Post by CyberAngel on 2014-05-29
> **Light-kun said:**
> Nice tutorial, thanks!

1) I've  ran into segfault when trying to do a TL video from more than 1000 pictures:
 Segmentation faultf (38%) 11.87fps Trem:   2min 809mb  A-V:0.000 [77605:0]
After this error I'm getting the video which consists of 1000 pics.

I know I can make few parts and stick them together in another utility, but I want to make  this process easier.


Was it mencoder gave you the segmentation fault?
I never tried to make a timelapse with more than 1000 pictures before, but I could give it a try :)

> **Light-kun said:**
> 
2)  >> I ran into some problems for some time lapses with this line of code:
 >> ls -1tr | grep -v files.txt > files.txt
 >> It should be:
 >> ls -1 | grep -v files.txt > files.txt

Why? I have no problems with first command. Even the first command is better in my case:
I have camera which makes number to pictures from 0001.JPG to 9999.JPG and after last number it creates another directory and starts over from  0001.JPG.
so time sorting in ls command makes my video proper, when name sorting wil lscrew my video up.

I don't remember exactly what was the problem, but I remember that for a specific set of pictures, they were not in order. However, with ls -1 everything was fine.

---

### Post by Vik Vasilev on 2014-06-21
Oh my god! I spent hours of searching and trying to this with ffmpeg. and now its working!!! Thank you! I LOVE YOU DUDE!

---

### Post by CyberAngel on 2014-06-21
Glad you found this thread helpful :)

---

### Post by Denkogami on 2014-08-22
I used to use this technique and got great results. I'm using Ubuntu 14.04 and recently am running into problems using mencoder. When I run this command
```
mencoder -idx -nosound -noskip -ovc lavc -lavcopts vcodec=ljpeg -o output.avi -mf fps=15 'mf://@files.txt
```

I get the following output (I'm cutting the middle of the output out, since the same three lines are repeated over and over)
```
MEncoder 1.1-4.8 (C) 2000-2012 MPlayer Team
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] number of files: 45
[demux_mf] file type was not set! trying 'type=JPG'...
VIDEO:  [IJPG]  0x0  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:0x0  fps:15.000  ftime:=0.0667
libavcodec version 54.35.0 (external)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f14907c2640]BICUBIC scaler, from yuv422p to yuv420p using MMXEXT
videocodec: libavcodec (1920x1080 fourcc=47504a4c [LJPG])
[ljpeg @ 0x7f148fcc4b00]Error getting output packet of size 24899584.
Muxer frame buffer cannot allocate memory!
Pos:   0.0s      1f ( 2%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]


...


Flushing video frames.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:     -nan kbit/s  (-2147483648 B/s)  size: 0 bytes  0.000 secs  46 frames

```

And an output file that cannot be opened. Any help would be much appreciated :)

---

### Post by CyberAngel on 2014-08-23
@Denkogami, I tried to make a time lapse today, and mencoder gives me the same error on Kubuntu 14.04!
I guess it is something related to the libavcodec.
I'll try to find a solution since I want to make some time lapses myself :)

If anybody has a solution already, please post it here.

Thanks!

---

### Post by CyberAngel on 2014-08-24
Just updated the how-to and changed the mencoder command with ffmpeg which is working fine for me on Kubuntu 14.04!
Start reading from Step 1 again, because I do the file sorting in the first step.

---

### Post by Denkogami on 2014-08-25
Thanks CyberAngel!

Had a bit of trouble installing ffmpeg, but managed to get that working.

With the codecs/settings you recommend I get a bizarre diagonal on the timelapses when the images move fast and furiously. It's like the two parts of the movie don't sync up on either side of this diagonal.

But the following doesn't present this issue. Dunno if the issue is on the encoding side or the viewing one...

```
ffmpeg -framerate 30 -pattern_type glob -i '*.JPG' -s:v 1280x720 -c:v libx264 -profile:v high -crf 20 -pix_fmt yuv420p  output.avi

```

---

### Post by macburgerjunior on 2014-09-21
Hi,
thanks for sharing this...
When i try using ffmpeg I get this message:
> *** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

and also I get this error:
> Unrecognized option 'pattern_type'Failed to set value 'glob' for option 'pattern_type'



and also something changed how ffmpeg/avconv wants the input source: it wants > ./*.jpg

---

### Post by FakeOutdoorsman on 2014-09-21
You're using the counterfeit "ffmpeg" from a fork of FFmpeg called Libav. As far as I know the fake "ffmpeg" and avconv do not have support for the glob pattern type.

You can download, extract, and run a static build of real ffmpeg available via links on the [FFmpeg Download](https://ffmpeg.org/download.html) page. Or you can [compile ffmpeg](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

---

### Post by CyberAngel on 2014-09-21
@macburgerjunior, FakeOutdoorsman gave you the answer.

However, I think you could use avconv just by changing the following line in the first step from:

```
ls -1tr *.jpg | while read filename; do cp $filename renamed/$(printf %05d $counter)_$filename; ((counter++)); done
```

to:

```
ls -1tr *.jpg | while read filename; do cp $filename renamed/$(printf %05d $counter).jpg; ((counter++)); done
```

Then you know that all of your renamed picture will have a name composed of 5 digits and a ".jpg" extension and something like the following "should" work.

```
avconv -r 15 -i '%05d.jpg' -c:v copy output.avi
```

I haven't tried it though, so you might need to experiment a little bit.

---

### Post by Jonathan_F.V. on 2014-09-29
Hey, I just wanted to thank you CyberAngel for the deflickering script. I just made a timelapse with my tripod on a walkway by the sea at twilight, and many people passed with flashlights, changing the exposure. Your script made a HUGE difference in the quality of the timelapse.

---

### Post by CyberAngel on 2014-09-29
Glad to know it is useful not only for me :D

---

### Post by CyberAngel on 2014-12-21
My first 4k time lapse video that is based on this technique :)

[https://www.youtube.com/watch?v=nEBFQj8oid0](https://www.youtube.com/watch?v=nEBFQj8oid0)

Edited the video with kdenlive. Added Fade from black and Fade to black effects plus music.

Rendered with a custom project 4k profile (3840x2160 @ 25fps) and the following custom rendering profile (Lossless 4k MKV):

```
acodec=ac3 ab=448k ar=44100 ac=2 vcodec=libx264 crf=15 rc-lookahead=60 coder=1 flags=+loop cmp=+chroma partitions=+parti8x8+parti4x4+partp8x8+partp4x4+partb8x8 me_method=umh subq=10 me_range=24 g=250 keyint_min=25 sc_threshold=40 i_qfactor=0.71 b_strategy=2 qcomp=0.6 qmin=0 qmax=51 qdiff=4 bf=8 refs=9 directpred=1 flags2=+mixed_refs+dct8x8+fastpskip+mbtree cqp=0 wpredp=2 trellis=2 weightp=2 deblock=1:0:0 direct=auto muxer=auto aspect=%dar
```

Converted to 1080p:

```
avconv -i 4k.avi -scale 1920x1080 -c:v libx264 -preset slow -crf 15 1080p.mkv
```

In youtube, I uploaded only the 4k video and youtube provides the rest of the available resolutions.

---

### Post by CyberAngel on 2014-12-21
Just updated the main thread to include some more info about the options used on kdenlive in order to get a 4k output.

I also added an alternative "mogrify" option for multi core resizing using the command "parallel".

---

### Post by chili555 on 2014-12-21
Simply awesome! Thank you for giving us your processing details. Very impressive.

---

### Post by FakeOutdoorsman on 2014-12-21
Nice post. Here is some info that you may be able to use:

[size=+2]ffmpeg[/size]

[list]
[*]Use **-framerate** instead of **-r** as an input option for the [image file demuxer](https://ffmpeg.org/ffmpeg-formats.html#image2-1). It is more forgiving than -r in case the images somehow vary in frame size or pixel format.
[*]In your last ffmpeg example you can use the [scale filter](https://ffmpeg.org/ffmpeg-filters.html#scale) instead of -ss: **-vf scale=1920:-2**. It will keep the aspect ratio.
[*]Since FFmpeg development is so active, and because Ubuntu lacks this package until 15.04, I recommend users get a recent build before each major timelapse session ([download](http://johnvansickle.com/ffmpeg/), [PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media), or [compile](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)).
[/list]

[size=+2]jpegtran[/size]

JPEG images can be losslessly rotated using jpegtran (part of the libjpeg-progs package, I believe). This is useful if the camera was mounted upside-down.
```
jpegtran -rotate 180 -optimize -copy none -perfect -v input.jpg > output.jpg
```
Some extra options are in this example:
[list]
[*]**-optimize** will "perform optimization of entropy encoding parameters", which can be slow but can also significantly reduce the size of the image. Probably a waste of time here though since you're likely to re-encode anyway.
[*]**-copy none** will remove all excess baggage such as comments, Exif info, thumbnails etc. This can save file size too, but sometimes that info is useful. Use **-copy all** if you want to keep everything.
[*]**-perfect** will halt with an error message if the transformation is not considered perfect. The man page doesn't say much else, but I've never had an imperfect one yet.
[/list]

Alternatively use exifautotran, also in libjpeg-progs, to rotate according to the Exif Orientation Tag:
```
exifautotran *.jpg
```

[size=+2]Kdenlive[/size]

In Kdenlive you should use the x264 presets instead of attempting to declare a legion of options. So your profile can go from:
```
acodec=ac3 ab=448k ar=44100 ac=2 vcodec=libx264 crf=15 rc-lookahead=60 coder=1 flags=+loop cmp=+chroma partitions=+parti8x8+parti4x4+partp8x8+partp4x4+partb8x8 me_method=umh subq=10 me_range=24 g=250 keyint_min=25 sc_threshold=40 i_qfactor=0.71 b_strategy=2 qcomp=0.6 qmin=0 qmax=51 qdiff=4 bf=8 refs=9 directpred=1 flags2=+mixed_refs+dct8x8+fastpskip+mbtree cqp=0 wpredp=2 trellis=2 weightp=2 deblock=1:0:0 direct=auto muxer=auto aspect=%dar
```
to (untested example):
```
acodec=libopus ab=128k vcodec=libx264 crf=18 preset=slower muxer=auto aspect=%dar
```
[list]
[*]It will probably be hard to notice a difference between crf 15 vs 18, but the file size will likely be roughly 25% smaller (a bad guess). See [FFmpeg Wiki: H.264 Video Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264).
[*]libopus, libfdk_aac, libvorbis, and libmp3lame will usually provide better quality per bitrate than ac3, but then it may not be compatible with your desired output container format or playback device/player, or your ffmpeg build may not support these encoders. See [FFmpeg Wiki: Guidelines for high quality lossy audio encoding](http://trac.ffmpeg.org/wiki/Encode/HighQualityAudio).
[/list]

---

### Post by CyberAngel on 2014-12-21
Wow! Thanks for the tips :)
I will definitely take a look to your suggestions for improvement!
For the moment, I will simply add a reference to your post in order for others to be able to find these tips easily.

Thanks again!

---

### Post by Light-kun on 2015-01-10
Brilliant article! Helped to make cool videos from a bunch of pictures!

Few days ago I've tried to use your way to make a video but got an error message
[mjpeg @ 0x7ff955194b00]Specified pix_fmt is not supported
Could not open codec.
FATAL: Cannot initialize video driver.
Exiting...

my uname -a
Linux tool 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
mencoder version:
MEncoder 1.1-4.8 (C) 2000-2012 MPlayer Team

I didn't update my software after I have successfully made a video last time as far as I remember

Any tips?

Full -v output:
> $ mencoder -idx -nosound -noskip -ovc lavc -lavcopts vcodec=mjpeg -v -o out.avi -mf fps=24 'mf://@files.txt' 
MEncoder 1.1-4.8 (C) 2000-2012 MPlayer Team
get_path('codecs.conf') -> '/home/drey/.mplayer/codecs.conf'
Reading optional codecs config file /home/drey/.mplayer/codecs.conf: No such file or directory
Reading optional codecs config file /etc/mplayer/codecs.conf: No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/drey/.mplayer/fonts'
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-radio --enable-radio-capture --disable-arts --language=all --disable-dvdread-internal --disable-libdvdcss-internal --disable-libmpeg2-internal --disable-ffmpeg_a --enable-runtime-cpudetection --enable-debug --enable-joystick --disable-gui
STREAM: [mf] mf://@files.txt
STREAM: Description: Multiple files input
STREAM: Author: Benjamin Zores, Albeu
STREAM: Comment: 
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] number of files: 125
[demux_mf] file type was not set! trying 'type=JPG'...
==> Found video stream: 0
VIDEO:  [IJPG]  0x0  24bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:0x0  fps:24.000  ftime:=0.0417
[file] File size is 0 bytes
STREAM: [file] out.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
libavcodec version 54.35.0 (external)
Configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:9.11-2ubuntu2' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-swscale --enable-libcdio --enable-x11grab --enable-libx264 --enable-libxvid --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
[mjpeg @ 0x7ff955194b00]marker=d8 avail_size_in_buf=563250
[mjpeg @ 0x7ff955194b00]marker parser used 0 bytes (0 bits)
[mjpeg @ 0x7ff955194b00]marker=e0 avail_size_in_buf=563248
[mjpeg @ 0x7ff955194b00]marker parser used 16 bytes (128 bits)
[mjpeg @ 0x7ff955194b00]marker=e1 avail_size_in_buf=563230
[mjpeg @ 0x7ff955194b00]marker parser used 31680 bytes (253440 bits)
[mjpeg @ 0x7ff955194b00]marker=db avail_size_in_buf=531547
[mjpeg @ 0x7ff955194b00]index=0
[mjpeg @ 0x7ff955194b00]qscale[0]: 0
[mjpeg @ 0x7ff955194b00]marker parser used 67 bytes (536 bits)
[mjpeg @ 0x7ff955194b00]marker=db avail_size_in_buf=531478
[mjpeg @ 0x7ff955194b00]index=1
[mjpeg @ 0x7ff955194b00]qscale[1]: 1
[mjpeg @ 0x7ff955194b00]marker parser used 67 bytes (536 bits)
[mjpeg @ 0x7ff955194b00]marker=c0 avail_size_in_buf=531409
[mjpeg @ 0x7ff955194b00]sof0: picture: 1440x1080
[mjpeg @ 0x7ff955194b00]component 0 2:1 id: 0 quant:0
[mjpeg @ 0x7ff955194b00]component 1 1:1 id: 1 quant:1
[mjpeg @ 0x7ff955194b00]component 2 1:1 id: 2 quant:1
[mjpeg @ 0x7ff955194b00]pix fmt id 21111100
[ffmpeg] aspect_ratio: 1.333333
VDec: vo config request - 1440 x 1080 (preferred colorspace: Planar 422P)
Trying filter chain: expand lavc
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale expand lavc
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (1440x1080->1440x1080,flags=0,'MPlayer',0x50323234)
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x7ff955c91640]BICUBIC scaler, from yuv422p to yuv420p using MMXEXT
[swscaler @ 0x7ff955c91640]1440x1080 -> 1440x1080
[swscaler @ 0x7ff955c91640]lum srcW=1440 srcH=1080 dstW=1440 dstH=1080 xInc=65536 yInc=65536
[swscaler @ 0x7ff955c91640]chr srcW=720 srcH=1080 dstW=720 dstH=540 xInc=65536 yInc=131072
REQ: flags=0x401  req=0x0  
REQ: flags=0x401  req=0x0  
videocodec: libavcodec (1440x1080 fourcc=47504a4d [MJPG])
[mjpeg @ 0x7ff955194b00]Specified pix_fmt is not supported
Could not open codec.
FATAL: Cannot initialize video driver.
[mjpeg @ 0x7ff955194b00]marker parser used 17 bytes (136 bits)
[mjpeg @ 0x7ff955194b00]marker=c4 avail_size_in_buf=531390
[mjpeg @ 0x7ff955194b00]class=0 index=0 nb_codes=11
[mjpeg @ 0x7ff955194b00]marker parser used 30 bytes (240 bits)
[mjpeg @ 0x7ff955194b00]marker=c4 avail_size_in_buf=531358
[mjpeg @ 0x7ff955194b00]class=1 index=0 nb_codes=242
[mjpeg @ 0x7ff955194b00]marker parser used 92 bytes (736 bits)
[mjpeg @ 0x7ff955194b00]marker=c4 avail_size_in_buf=531264
[mjpeg @ 0x7ff955194b00]class=0 index=1 nb_codes=9
[mjpeg @ 0x7ff955194b00]marker parser used 28 bytes (224 bits)
[mjpeg @ 0x7ff955194b00]marker=c4 avail_size_in_buf=531234
[mjpeg @ 0x7ff955194b00]class=1 index=1 nb_codes=242
[mjpeg @ 0x7ff955194b00]marker parser used 70 bytes (560 bits)
[mjpeg @ 0x7ff955194b00]escaping removed 1989 bytes
[mjpeg @ 0x7ff955194b00]marker=da avail_size_in_buf=531162
[mjpeg @ 0x7ff955194b00]component: 0
[mjpeg @ 0x7ff955194b00]component: 1
[mjpeg @ 0x7ff955194b00]component: 2
[mjpeg @ 0x7ff955194b00]marker parser used 529172 bytes (4233376 bits)
[mjpeg @ 0x7ff955194b00]marker=d9 avail_size_in_buf=0
[mjpeg @ 0x7ff955194b00]mjpeg decode frame unused 0 bytes
[ffmpeg] aspect_ratio: 1.333333
VDec: vo config request - 1440 x 1080 (preferred colorspace: Planar 422P)
Trying filter chain: scale expand lavc
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (1440x1080->1440x1080,flags=0,'MPlayer',0x50323234)
REQ: flags=0x401  req=0x0  
REQ: flags=0x401  req=0x0  
videocodec: libavcodec (1440x1080 fourcc=47504a4d [MJPG])
[mjpeg @ 0x7ff955194b00]Specified pix_fmt is not supported
Could not open codec.
FATAL: Cannot initialize video driver.

Exiting...


---

### Post by CyberAngel on 2015-01-10
I also had some problems with the latest versions of mencoder, so I have updated the article to include information on how to make a video with the use of ffmpeg.
Read the first post in the thread and follow the updated steps :)

In order to use the "real" ffmpeg, you can use [this]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") PPA repository.

---

### Post by Light-kun on 2015-01-12
Many thanks for fast help! Works like a charm!

---

### Post by John_Lindam on 2015-08-09
Thanks, this was the best tutorial I've found and it worked flawlessly!

---

### Post by sp_nayak82 on 2016-01-11
I have a created a C++ program for deflickering timelapse images. Program is influenced by the perl script, but have added more features to it. It does luminance calculation & creation of new images in different threads each assigned to different CPU cores. It can crop the images before writing the new images to standard **HD, 2K** and** 4K** dimensions. 

You can download the tool thru PPA [https://launchpad.net/~sandeep-pn/+archive/ubuntu/timelapse-deflicker](https://launchpad.net/~sandeep-pn/+archive/ubuntu/timelapse-deflicker), by adding this line to sources.list 

"deb [http://ppa.launchpad.net/sandeep-pn/timelapse-deflicker/ubuntu](http://ppa.launchpad.net/sandeep-pn/timelapse-deflicker/ubuntu) trusty main "

and then


[B]# sudo apt-get update
# sudo apt-get install timelapse-deflicker
[/B]

**Usage : **

# timelapse-deflicker -d ./ -t 4

This will search images in current directory ( -d . ) and run 4 threads on 4 CPU cores to do processing. See "**timelapse-deflicker --help**" for more information.

You can use **Blender 3D** to generate timelapse videos from the images. See this tutorial on doing the same, [https://www.youtube.com/watch?v=xHnIZKvDNIc](https://www.youtube.com/watch?v=xHnIZKvDNIc)

---

### Post by CyberAngel on 2016-01-12
Wow :)

Thank you very much for the C++ implementation!

I haven't tried it yet, but I'll do soon.

Do you have any github repository that hosts your code?

---

