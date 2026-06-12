---
title: "Totem /xine/ Flash--No Sound"
date: 2006-03-03
forum: Multimedia &amp; Video
---

### Post by cefola on 2006-03-03
Running Totem 1.2.1 with xine-lib version 1.0.1 on a Breezy Box.
Totem plays Flash (flv) files just fine ----- but no sound.
Any thoughts, advice, help !!!!!!!!!!.
"Intermediate Level" with Linux.

---

### Post by medya on 2006-04-24
i have the same problem, flash and flv , have no sound.

---

### Post by Steve S. on 2006-05-28
Hey, cefola, I hope you don't mind me chiming in.

I am having the same issue with not being able to get sound for flash/flv files.

I posted here, regarding no sound in totem:
[http://ubuntuforums.org/showthread.php?p=1062886#post1062886](http://ubuntuforums.org/showthread.php?p=1062886#post1062886)

and here, regarding no sound in kaffeine.  Was able to figure out how to get kaffeine to play flv files, but no sound yet.
[http://www.ubuntuforums.org/showthread.php?t=170418](http://www.ubuntuforums.org/showthread.php?t=170418)

I am posting this with the hopes that the ideas in these threads may produce some leads as to how to fix the sound problem.  I hope it helps.

cefola, if you figure it out, would you please post for the rest of us?  thx.

---

### Post by Steve S. on 2006-05-28
All right!  Figured out a way around it.

I had heard that ffmpeg could do a lot of conversion, so I went into Synaptic Package manager and got it and anything related to it that I thought would be useful.

Then, I happened accross this site that gives a relatively good overview to less-than-adept-command-line-users like myself:
```
http://asuaf.org/~jj/blog/index.php/2006/01/08/convert-google-video-flvs-into-avi-mpg-etcin-linux/
```
and it explained how to convert an flv file to an mpg using ffmpeg.

It worked great!

The basic comand line is this (he explains it further on the site):
```
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 s 320x240 test.mpg
```
This converts video.flv file to test.mpg.

Hope that helps!

---

### Post by pek on 2006-06-11
i use as a frontend iriverter :p

---

### Post by henriquemaia on 2006-06-26
[quote=Steve S.]All right!  Figured out a way around it.

I had heard that ffmpeg could do a lot of conversion, so I went into Synaptic Package manager and got it and anything related to it that I thought would be useful.

Then, I happened accross this site that gives a relatively good overview to less-than-adept-command-line-users like myself:
```
http://asuaf.org/~jj/blog/index.php/2006/01/08/convert-google-video-flvs-into-avi-mpg-etcin-linux/
``` and it explained how to convert an flv file to an mpg using ffmpeg.

It worked great!

The basic comand line is this (he explains it further on the site):
```
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 s 320x240 test.mpg
``` This converts video.flv file to test.mpg.

Hope that helps![/quote] 
I just came across your post and tried it out. Works like a charm, thanks a lot. 

One thing, on the command line, you have 

```
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 s 320x240 test.mpg
``` and that gives me an error:

[INDENT] Unable for find a suitable output format for 's'
[/INDENT] 
because you forgot the **-** before the **s**, like this:

```
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 test.mpg
``` 
Thanks again for posting this.

---

### Post by Lunar_Lamp on 2006-08-02
I wrote the following script that deals with converting, and deleting the original flv file if desired.  I post it here in case it's of any use to anyone.

```
#!/bin/bash
#
# script written by Ed Hargin to convert flvs from places like youtube and googlevideos to mpg files.
#
# note to self: $1 = 'flv filename'
#
#   todo:
# - make the script able to deal with multiple files
# - enable input variable to be the url, and make the script find the correct url to download and then convert?

flv_file=$1

####################
# Convert Function #
####################
#this coverts the flv file specified ($1) to mpg

function convert {
	ffmpeg -i $flv_file -ab 56 -ar 22050 -b 500 -s 320x240 $name.mpg
}  

# Variables declared in above line (brackets are defaults used if option is omitted) 
#
# -ab = averate bitrate of music in kbit/s (default = 64)
# -ar = audio sampling frequency (default = 44100 Hz)
# -b  = video bitrate in kbit/s (default = 200 kb/s)
# -s  = set frame size (wxh) (default = 160x128)

###################
# Rename Function #
###################
#this function asks what you want to call the new file created, and acts accordingly.

rename ()
{
echo "By default the file will be named $flv_file.mpg - do you want to change this? (Y/N)"
read rename_answer
	if [ "$rename_answer" = "y" ];
		then echo "What do you want to call it? (.mpg will automatically be appended to the filename)"
		read name
		echo "Converting flv file to $name.mpg"

	else [ "$rename_answer" = "n" ];
		name=$flv_file.mpg
		echo "Converting file to $name"

	fi
}


#####################
# Deletion Function #
#####################
#this function asks if you want to delete the original file and acts accordingly.

function flvdelete {

	echo "Do you want to delete the original flv file? (Y/N)"

	read reply

	if [ "$reply" = "y" ];
 		then rm $flv_file
		echo "File deleted: $flv_file"  #should I build in some kind of detection of 'need to be root to delete'?

	elif [ "$reply" = "n" ];
 		then echo "Leaving file alone: $flv_file"

	fi
}

###############
# Main Script #
###############

rename ;
convert ;
flvdelete 

exit

```

---

### Post by cantormath on 2006-08-02
use this
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by lqyjzmms on 2006-10-12
The following worked fine for me, too:
```
ffmpeg -i video.flv -acodec copy -b 500 -s 320x240 test.mpg
```

Instead of recoding the audio to mp2, it is just left in whatever format it was before (mp3 from Google Video in my case).
So at least one lossy recompression process less.

---

### Post by pippy on 2007-04-10
> **Lunar_Lamp said:**
> I wrote the following script that deals with converting, and deleting the original flv file if desired.  I post it here in case it's of any use to anyone.


Thanks a lot for that! it really helped me out =D

BTW for those who who don't know how to use the script, right click where you saved your fla, create document> empty file. name it something, then double click and paste the script in.

then open applications>terminal, and cd into where you saved the script. if its on the Desktop type cd Desktop. then type bash <what you named script> fla file

---

### Post by jms830 on 2007-04-26
if you are using nautilus-actions, unzip this file, then import the schema file into it and when you right click on a FLV file you will be able to quickly convert it. I used the ffmpeg command found in this post.

---

