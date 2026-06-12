---
title: "Trouble shrinking mp3"
date: 2014-03-21
forum: Multimedia Software
---

### Post by sowieso on 2014-03-21
Hi there

I´m quite new to making posts here... but here it goes.

My problem is following. I have a folder full of mp3 files (4.3 GB) that I want to shrink and put on my phone.

I am going to use lame with the command lame -b 32. Trouble is that we are talking about more than 100 files.

So I got this going on the command line: find . -exec lame -b 32 "{}" "{}.shrink.mp3" \; 

That leaves me with double so many files in the folder (I thought about using ls | grep ".shrink" - but I don´t know how to finish that string).

I also made a script that kind of worked but just kept making new .mp3 files with shrink extensions ad infinitum.

#!/bin/bash
clear

echo 
for f in `find $1 home/simon/Documents . -name "*.mp3"`

do
    lame $f -b 32 $f.resized.mp3

done

I think the coolest thing would be making a bash script which shrinks the whole folder and then deletes the old files - or makes the smaller files in a new directory. But being new to Bash I´m not sure how. 

If anyone would like to help me out with the problem I would be super grateful! I just threw out windows to try out Ubuntu and Linux and explore this system :)

---

### Post by tgalati4 on 2014-03-21
You need to find some cheap flash drives and store some of your music on them.  Deleting the music files (especially if they are higher-quality, higher bitrate) means you will lose them forever.  So find a way to store them.  You can store 20K songs on Google Play, you can get free storage at dropbox, or Ubuntu One.  But a few, inexpensive flash drives would hold your 4.3 GB collection easily.

There are quite a few scripts on these forums that do something similar to what you want.  Search *transcode*.

There are also music managers that will transcode on-the-fly to your device.  You just have to set them up in preferences.  That way, you can keep the higher-quality tracks on your computer and the more-compressed tracks on your phone.

---

### Post by sowieso on 2014-03-21
@[**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895")

Thanks for the reply. Sure there are ways to store music, on the cloud and flash. 

This problem I have is more out of curiosity then need. It´s just when you start doing something you want to finish it.

I´ll search for the transcode threads and keep on trying!

---

### Post by Yellow Pasque on 2014-03-22
> #!/bin/bash
clear

echo
for f in `find $1 home/simon/Documents . -name "*.mp3"`

do
lame $f -b 32 **$f.resized.mp3**

done

You should put the output files in a different directory or the loop is going to use the output files as input...

---

