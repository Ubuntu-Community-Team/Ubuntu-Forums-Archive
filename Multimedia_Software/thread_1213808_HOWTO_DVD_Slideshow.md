---
title: "HOWTO: DVD Slideshow"
date: 2009-07-15
forum: Multimedia Software
---

### Post by Unterseeboot_234 on 2009-07-15
With the popularity of digital photography I would have thought there was a solution for a DVD Slideshow. Not yet. I've searched the web and the 'buntu Forums. I would like to share what I've learned and hope somebody can correct me or make this better.

I used a friend's Nikon D90 to shoot on HiRes. The resulting photos are remarkable in detail, but also remarkable in file size -- each photo was 5+ megs. I used ImageMagick to convert to resample at 72dpi and 720 x 480 format for NTSC. I wrote the python script to automate a whole folder of 500+ pictures. The conversion took about 30 minutes, but the resulting jpegs were sharp in details, even in the shadows. If you are interested in the script, post to this thread. ImageMagick has its own script engine, but I prefer python.

ImageMagick should have also made the mpeg, but ImageMagick needs temporary files and while trying to make 300 photos into an mpeg I maxed out a 30gig partition. The video could not be made. Not to mention I banged the ceiling on my AMD64 CPU.

I did find dvd-slideshow in the Synaptic repositories. You need dvd-slideshow and you also need dir2slideshow -- not in the repositories. I got a deb from **[Dir2slideshow]("http://dvd-slideshow.sourceforge.net/wiki/Dir2slideshow")**. dir2slideshow writes a script for you to use with dvd-slideshow. Both programs are command-line. Use the tutorial I found at this blog: **[Command-line Slideshow]("http://www.freesoftwaremagazine.com/columns/command_line_media_editing")** 

From that results, which I previewed with xine, I burned with ManDVD.

There is an outdated GUI for dvd-slideshow, but I could not get it to work with Ubuntu's version of gamba. I realize this is a "bandaid" fix, but it works. I hope some of you find it useful.

---

### Post by igorzwx on 2009-07-15
perhaps, picasa can do such things too
[http://en.wikipedia.org/wiki/Picasa](http://en.wikipedia.org/wiki/Picasa)

---

### Post by Unterseeboot_234 on 2009-07-15
But my suggestion is for a universal DVD using optimized photos, from a digital camera, and viewable on DVD players or computers. I do recall Picasa. It is a great indexer.

---

### Post by rgb1701 on 2009-07-15
Try-

[http://www.dvdstyler.de/](http://www.dvdstyler.de/)


Q DVD Author states:  
"You can generate a dvd-slideshow."
"You can create a full blown DVD without knowing the command line tools."

[http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

---

### Post by Unterseeboot_234 on 2009-07-16
I welcome any and all comments upon this subject... I have search for a more comprehensive solution many, many times. Video production eats your time away.

I have tried everything from the repositories and suggestions for other packages. My experiences were some don't recognize external USB devices, some manufacture a DVD that won't run on a playback machine.

You need to optimize the huge digital photo files with ImageMagick. This should be a bulk operation. To drag each photo into a DVD software and let it convert results in high-contrast visual results. kdenlive will make a slideshow, limited to 85 slides and like I said, if you didn't optimize, the results are contrasty.

dvd-slideshow makes any length slideshow, you can loop a background audio track. I wished it had interactivity buttons in the final product. If I didn't want a DVD, I would use OpenOffice Presentation.

ManDVD has its problems. We have to be perfect configuring the thumbnails and other setups until ready to burn media. ManDVD won't let you change any setup. If you want to change something, you start over.

So, Linux is known for not having a comprehinsive video solution. We have to use multiple tools. That could change with JavaFX, maybe in a year's time. JavaFX promises interactive random-access video which should revolutionize game programming.

I will be watching for anybody's suggestions or comments, and thank you Forum. The Forum beats the man pages command any day.

---

### Post by rgb1701 on 2009-07-16
> **Unterseeboot_234 said:**
> I welcome any and all comments upon this subject... I have search for a more comprehensive solution many, many times. Video production eats your time away.

I have tried everything from the repositories and suggestions for other packages. My experiences were some don't recognize external USB devices, some manufacture a DVD that won't run on a playback machine.

You need to optimize the huge digital photo files with ImageMagick. This should be a bulk operation. To drag each photo into a DVD software and let it convert results in high-contrast visual results. kdenlive will make a slideshow, limited to 85 slides and like I said, if you didn't optimize, the results are contrasty.

dvd-slideshow makes any length slideshow, you can loop a background audio track. I wished it had interactivity buttons in the final product. If I didn't want a DVD, I would use OpenOffice Presentation.

ManDVD has its problems. We have to be perfect configuring the thumbnails and other setups until ready to burn media. ManDVD won't let you change any setup. If you want to change something, you start over.

So, Linux is known for not having a comprehinsive video solution. We have to use multiple tools. That could change with JavaFX, maybe in a year's time. JavaFX promises interactive random-access video which should revolutionize game programming.

I will be watching for anybody's suggestions or comments, and thank you Forum. The Forum beats the man pages command any day.


Did you try Q-DVD Author and DVD Styler?

---

### Post by Unterseeboot_234 on 2009-07-17
QDVD is non-intuitive and really gets frustrating at the point where you add movie clips. It looks like I will wrestle with that program again and try to make it work. The official tutorials for QDVD suk. I did find this:

**[QDVD HowTo www.linuxforums.org]("http://www.linuxforums.org/articles/how-to-make-dvds-with-menus-using-q-dvd-author_266.html")**

QDVD is possible to do multi-level menus.

manDVD is limited in what formats it will work with and moreover, the formats acceptable to manDVD, the user has to provide perfect files with the proper bitrates for audio and vid bandwidth, the audio must not have any gaps.

I think it was K3B (I don't have it installed now). K3B took one peek at my hardware, doesn't see the external USB DVD burner and turns off half the features to make a video. What good is that? It should at least produce an ISO.

I'll look at DVD Styler, but I noticed kDenLive and Kino are set up to work with DVDAuthor / qDVDAuthor.

But, one thing about it. Nero only burns DVD+R. The Linux programs go ahead and format a DVD-R and produce a DVD. Nero makes a coaster for you with DVD-R.

---

### Post by ad_267 on 2009-07-17
I've used Kdenlive for this. You can add a folder of images to a project and it creates a slideshow for you. It also has a built in DVD creator.

It's still a bit buggy but the result turned out alright.

---

### Post by vingb on 2009-07-17
Hey, I have interest in the script.
thx

---

### Post by Unterseeboot_234 on 2009-07-17
A couple (or two) of notes

kdenlive is limited to 85 slides. Make many folders if you want a big slide show.

QDVD works, but...
1. Once it starts crashing, it keeps crashing. I'm trying to locate the hidden temp file that runs QDVD and delete it and maybe the crashes will stop.
2. QDVD will happily accept any audio format you pass in and not convert it. Should you get to the final DVD, it won't have sound unless you gave it muxed mpeg with .AC3 audio format.

manDVD still gives predictable results provided you have clean mpeg video. manDVD converts any audio to .AC3. QDVD needs a button to do this, but it doesn't have one. QDVD's purpose in life is to write a shell script and then run the shell script. One could edit the DVDauthor .xml file, but QDVD won't stop at the script, it keeps going forward and makes the DVD folder structure -- a lot of wasted time before you can edit.

The best mpeg, quality, sound, colors is exporting from cinelerra. You export (render) in yuv4mpeg [video only] to .m2v file format, then export .AC3 formatted audio. Then a command-line mux the audio and vid together using ffmpeg. Here is a tutorial, disregard his advice about Microsoft .wav audio unless you use manDVD. **[Cinelerra Export to DVD]("http://crazedmuleproductions.blogspot.com/2007/06/beginners-guide-to-exporting-video-from.html")**

Really and truly Cinelerra gives the best results because it has its own internal engine manipulating the vid before handing it off to ffmpeg. Other video editors are trying to make ffmpeg / mencoder do the work.

I have a small stack of coasters proving some of this to myself.

---

### Post by Unterseeboot_234 on 2009-07-17
The python script. You must have ImageMagick and Python installed on your system. If you are reading this from a Windows machine, I can't help you.

The purpose is to read a whole folder of hi-res digital photos, resample down to 72 dpi and then do a new dimensions for either PowerPoint or video. The script could be better.

////////////////////


```
# photo_convert.py

import os, sys

"""
A command-line tool to use imagemagick-lib, a free, open-source image 
manipulation software that is especially good doing bulk operations.

Put this script inside a folder of images. use a console window, > cd into that folder and run python photo_convert.py.  

In this case, the images are a folder of my digital camera .jpeg and I want to convert the whole folder of .jpeg into .gif file format.
"""

# -------------------------
"""	use Python method os.listdir() and 
	in this case the (.) directory, or cwd -- current working directory
	and where is the location of launching and running the script.
	photo_convert.py resides with your fotos.
	You have used terminal to cd into the folder.
	invoke with:
	python photo_convert.py
	"""

dlist = os.listdir('.')

# make an empty list var that will be a command-line list
converto = []

# use an itenerator, look at every item in list dlist

for filenam in dlist:

	# take each dlist element, split it where period is
	temp = filenam.split('.')

	# in this case, we're looking for file_xx.JPG
	# we want the portion of the string at the "."
	# and make it lower case to compare
	temp[1] = temp[1].lower()
	if temp[1] == 'jpg' or temp[1] == 'jpeg':
		converto.append(filenam)

# -------------------------------
""" imagemagick (not part of python) wants:   COMMAND filename filename
	in this case:
	convert filename.jpeg newFilename.jpg
	'convert' is the command, a file.jpeg to a file.jpg
"""
# ------------------------------
for filenam in converto:
	#split the filename again to make a name + .JPG
	temp = filenam.split('.')

	# code is a string with two string placeholders
	# use 600x400 for PowerPoint, 720x480 for NTSC
	# note ImageMagick takes best fit of the two dimensions
	# keeping the picture ratio correct, see ImageMagick for options

	code = 'convert -resample 72 -resize "600x400" %s _%s.JPG'

	# define two string values as a tuple
	values = (filenam, temp[0])

	# put the tuple into the code string
	# let the os.system accept the string as a terminal command
	os.system(code % values)

	# safety and/or sanity check
	print code % values

```

---

### Post by ridgeland on 2009-07-18
I use manDVD (limit of 99 slides) and DeVeDe to make DVD slide shows with music to play on the TV's DVD player.  To make a slideshow for YouTube is a similar process.  I made a slideshow and how-to and posted to YouTube:
[http://www.youtube.com/watch?v=zw69GMOS9jA](http://www.youtube.com/watch?v=zw69GMOS9jA)
I used xvidcap to make the how-to.

---

### Post by Unterseeboot_234 on 2009-07-18
Thanks, ridgeland. Your comment made me go back to DeVeDe and try it. The version from the Repositories, vers.3.11 is better than the last time I tried it. Nice that we can add basic menus. Also nice that DeVeDe accepts dvRAW files and converts both the video and audio streams to what works on a DVD player.

1. Sony DVSC10, DV-firewire capture -- Kino
2. Cinelerra edit, render out as rawDV
3. DeVeDe, menus and ISO

Best picture sharpness. Best audio sound. Teensy loss of color, but very acceptable. Friends comment on the stereo sound quality of that Sony HandyCam.

1. Nikon D90, at HiRes
2. My amateur python script to resample a selected group from the Nikon pics
3. Command-line Dir2slideshow
4. Command-line dvd-slideshow -- makes a .vob
5. ( can edit the .vob in Cinelerra, change audio / slice). Save out to rawDV
6. DeVeDe, menus and ISO

Unlimited number of slides possible. No interactivity however. But good color, some loss of photo clarity, but still the sharpest. Best audio sound.

And, if I find the time, go back to a shell script or python to automate some of the above. I tossed QDVDAuthor.

---

### Post by rgb1701 on 2009-07-21
Have you tried Smile?

[http://smile.tuxfamily.org/?q=node/33](http://smile.tuxfamily.org/?q=node/33)

[http://www.getdeb.net/app/Smile](http://www.getdeb.net/app/Smile)

---

### Post by ridgeland on 2009-07-21
SMILE like manDVD is by Stéphane Gibault.  He is also working on 2manDVD.
man no doubt is for Mandriva.  
I've tried SMILE before and it only crashed.  I tried the latest 0.9.3 and it was stable.  I created a short flash video.  
Having used manDVD I was able to make a slideshow with music.  The interface needs more work, not yet 1.0.  Two nice things were the option to adjust slideshow length to fit the music length and the flash output.  In earlier Smile releases I saw lots of transition options now just 1 or none.
I'll stay with manDVD for now and look forward to SMILE 1.0 and 2manDVD.

---

### Post by ianmillington on 2009-08-21
I note you are using 8.10. You might try going outside the box here. The version of digikam that shipped with 8.10 (0.94) when the Kipi plugins are installed has a great Mpeg slideshow function, which enabled me to do a slideshow to music. The resulting MPEG could then be put on DVD with any one of a number of DVD authoring programs.

This function s not yet available in the version of Digikam that ships with Jaunty - I miss it- but it sounds like it might just be what you are looking for.

---

### Post by JavaBeanHead on 2009-08-22
I just wanted to bump this thread because it took me a long time to find it, and I really got a lot out of it.  I appreciate your efforts .  .  . still a learner here and was dying to find a replacement for other M$-based DVD creator / video editing software like Roxio Creator.

---

### Post by heartwarmer on 2009-08-27
> **ridgeland said:**
> I use manDVD (limit of 99 slides) and DeVeDe to make DVD slide shows with music to play on the TV's DVD player.  To make a slideshow for YouTube is a similar process.  I made a slideshow and how-to and posted to YouTube:
[http://www.youtube.com/watch?v=zw69GMOS9jA](http://www.youtube.com/watch?v=zw69GMOS9jA)
I used xvidcap to make the how-to.

is there a way to add more than one song to the slideshow in mandvd?

---

### Post by ridgeland on 2009-08-27
Not simple but you can.
I use Audacity to splice multiple songs together into one mp3 then use the composite mp3 with manDVD. SMILE may simplify&#65279; multiple songs.

---

### Post by news75 on 2009-08-27
hi guy,

I have changed a little bit the code I hope you could appreciate...
now is possible set two option -i for input directory and -o for output directory. If no options are used the behaviour is the same that the previous code.


```

#! /usr/bin/python

import os, sys
import getopt
import os.path

def help():
    print '\nphoto_convert '+ version
    print'\n\
Description:\n\
A command-line tool to use imagemagick-lib, a free, open-source image\n\
manipulation software that is especially good doing bulk operations.\n\
\n\
Usage:\n\
photo_convert [-i <input_directory>] [-o <output_directory>]'

version = "0.1"   

def convert(dir_in, dir_out):
   
    filext = lambda f: os.path.splitext(f)[1].lower() 
    converto = [filenam for filenam in os.listdir(dir_in) if filext(filenam) == '.jpg' or \
                                                              filext(filenam) == '.jpeg']   

    changeName = lambda f: '_%s.JPG'%(os.path.splitext(f)[0])
    for filenam in converto:
        sourceFile = os.path.join(dir_in,filenam)
        destFile = os.path.join(dir_out,changeName(filenam))
        command = 'convert -resample 72 -resize "600x400" %s %s' % (sourceFile, destFile)
        os.system(command)
        print command
       
input_dir = os.getcwd()
output_dir = os.getcwd()

try:
    opts, args = getopt.getopt(sys.argv[1:], "hi:o:", ["help"])
except getopt.GetoptError:
    help()
    sys.exit(2)
   
for opt,arg in opts:
    if opt == "-i":
        input_dir = arg
    elif opt == "-o":
        output_dir = arg
    elif opt in ("-h","--help"):
        help()
        sys.exit()
   
def checkdir(dir):
    if os.path.isdir(dir)==False:
        print dir + ' is not a valid directory'
        sys.exit(2)
   
checkdir(input_dir)
checkdir(output_dir)       
   
print 'input_dir: '+input_dir
print 'output_dir: '+output_dir
print 'started...'
convert(input_dir, output_dir)
print 'done'    

```

by by

 n.

---

### Post by heartwarmer on 2009-08-27
> **ridgeland said:**
> Not simple but you can.
I use Audacity to splice multiple songs together into one mp3 then use the composite mp3 with manDVD. SMILE may simplify&#65279; multiple songs.

thats what i did!! :D thanks

---

### Post by Oiolosse on 2009-10-18
I have been struggling to create a DVD slideshow as well as a DVD montage. This is for my wedding and should have been created weeks ago, but you know, procrastination breeds last minute creativity!

Anyway, I would like to find a handful of programs to create both..any recommendations?

Avidemux wants me to index my .jpg's as xxxx0000.jpg, xxxx00001.jpg, ...., etc.. I really do not want to change the name of 507 photos manually..so I looked into Imagemagick but am having a hard time understanding how to accomplish this renaming task.

I then looked into ManDVD but am not too happy that it can't handle all 507 photos, but rather a measly <100...and then not sure if avidemux can handle .vob (not sure what that filetype is anyway)..so is cinelerra superior?

"**Unlimited number of slides possible.** No interactivity however. But good color, some loss of photo clarity, but still the sharpest. Best audio sound." -Unterseeboot_234

HOW? Which programs are you using?

Thanks for the help!

---

### Post by ridgeland on 2009-10-18
Use Thunar to rename files (use Synaptics to install it)
Load it then in Accessories look for "Bulk Rename".  You may need to edit menus to see it (Right click on the main menu).
I hope you make a full backup before you start playing with renaming and resizing etc.
Humm....
Who is the world will set through 507 slides of your marriage?  Will your spouse do that?
I think the DVD limit of 100 is a sane thing.  But I wished to guarantee the viewer would fall asleep I would use DVD to create slide shows of 99 slides then use kdenlive to splice six slideshows of 99 together to achieve the objective.  
I am only joking.  I did make a slide show from my wedding photos, back then 36mm film did not result in 507 slides.
Have fun.  Thunar and kdenlive are tools to look at.

---

### Post by Oiolosse on 2009-10-18
Thunar is amazing, thank you! I needed to rename the files bc some of them contained spaces, commas, etc. and dvd-slideshow and dir2slideshow would not recognize them as images when attempting to build the .txt and .xml files..so thank you for this rec, it's fantastic!

Downloading Kdenlive now, did you say that this will make the DVD or only splice the slideshows together? I'll find out soon. 

Ha, to explain the 507 photos..our reception hall has these projector screens that can be used as a photo wall..so, we intend to have childhood pictures and the like running in the background.

Thanks again. I'll post progress!

---

### Post by ridgeland on 2009-10-19
If you are using a slide show on a video wall what will be the input?  An avi file?  A folder with pictures?  An SD camera card with the photos on it?  The project might be able to connect to a laptop as a monitor, like my LCD TV does.

I can do a slideshow on many TV's just by putting the photos in a folder on an SD card and plugging it into a slot on the TV, same with a TV's DVD player and a DVD.

Try the very simplest route first.  Do you have to have a sound track in synch with the photos or can you just use a independent sound system?

Another simple tool is "recordmydesktop" which does just that.  You play your slides and it records it to a movie format.  I've used it but don't remember the details, like is there sound.  Just set gthumb to change the photo every 5 seconds.  Kdenlive can trim the start and stop excess.  Xvidcap is a similar option.

---

### Post by Oiolosse on 2009-10-19
The projector screens (there are ten) are hooked up to DVD players. If I am able to make a slideshow on a laptop and connect it to the DVD player then that would be great. My fiance and I are taking a trip there in the next several hours, so I'll be able to find that out. How would (if I could) I connect a laptop to a DVD player anyway? These things are basic, run-of-the-mill memorex players, not too many connections if I remember.

There is no sound as we will have dance music playing during the reception. 

I posted this [http://ubuntuforums.org/showthread.php?t=1295103&highlight=dvd+slideshow](http://ubuntuforums.org/showthread.php?t=1295103&highlight=dvd+slideshow)

but at 3:30 I was not able to clearly articulate myself so I may not get a response :) -- I've learned so much but still have nothing to show! Uburonic!

Thanks again!

---

### Post by ridgeland on 2009-10-19
My first effort would be burn a DVD with a folder with the slides.  Then take that DVD to the hall and ask them to play it.  Works for most TV DVD players (some really old ones have issues about DVD+R DVD-R etc)
Good luck.

---

### Post by hiflyer780 on 2009-10-19
You might want to take a look at this:

[http://slcreator.sourceforge.net/]("http://slcreator.sourceforge.net/")

I stumbled upon it when I was looking for video editing software

---

### Post by Oiolosse on 2009-10-20
Well, kdenlive is a pretty good program! But, as fast as my computer is, loading 99 images at 5-10 mg each is a slow process..even rendering takes about 7 minutes...but! Imagemagick is amazing.

mogrify -resize dimensions *.jpg

I plan to write a very comprehensive guide on installing and doing what I am doing now for the next novice!

---

