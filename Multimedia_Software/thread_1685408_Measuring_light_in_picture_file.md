---
title: "Measuring light in picture file"
date: 2011-02-10
forum: Multimedia Software
---

### Post by kjartani on 2011-02-10
Hello.
I need a solution to measure the light in a picture file or the image stream from a webcam.
Would like to use a command line program that can return a value for brightness.

Regards

Kjartan Iversen

---

### Post by kidders on 2011-02-12
Hi there,

It'd be helpful to know a little more about what you're trying to achieve ... Exactly what you mean by "light" makes a big difference. For example, one approach would be to measure the mean grey level values of black & white versions of your pictures. Then again, that might be too blunt/insensitive a measurement to be any use at all!

One way or another, I'd be surprised if ImageMagick isn't the solution ... or at least part of it.

---

### Post by kjartani on 2011-02-13
Well I have a camera taking picture every minute and present it on my website.
To avoid presenting too dark pictures I want to "freeze" the "last" bright picture. To do this I need to measure the light of the pictures.

Kjartan

---

### Post by kidders on 2011-02-13
Ah... Sounds like ImageMagick'll do the trick, alright.

You could convert your images to greyscale & grab their average colour (ie greyness) with "identify". Alternatively, you could just scale them down to 1x1px and use the brightness of the remaining pixel to estimate a value for an entire image (ie pull the colour in HSB form, rather than RGB).

You'll have to experiment a little to find the right threshold though. Depending on what you're taking pictures of, and whether the camera is stationary, you might find you get better fidelity by measuring the darkest colour instead, or by cropping your images a certain way before you take a measurement.

For example, something like ...```
convert test_image.png -colorspace gray -scale 1x1 txt:- | grep -v '^#' | sed 's/.*graya(\([^,]*\),.*/\1/'
```... might be a good place to start. You could test out various thresholds with something along the lines of ...```
for f in *.jpg; do [ "`convert etc...`" -lt 200 ] && echo DISCARD || echo KEEP; done
```

I hope that helps.

---

### Post by kjartani on 2011-02-14
Wow.
I understand a little bit more now thanks to you. Though I see I have some work to do.

Ill post a message when I have tried it out.

Thanks again.

Kjartan

---

### Post by kjartani on 2011-02-21
Hello.

Thanks to kidders......

I have now a working solution that:
1: Saves picture one per minute using motion - software

2: Using following script to "measure" pic and upload it

----------------------
#!/bin/bash -x
# Shell script to measure light in picture and upload file to remote FTP server if picture is not to dark
# using convert - function from imagemagic to "measure" light
# using ncftpput to upload file
host="myftphost"
user="myftpusername"
pass="myftppassword"
declare -i LIGHTINT
REMOTEDIR="myremotedir"
LOCALFILE="mylocalfilename"
LOCALFTPFILE="mylocalfilenametoupload"
LOCALDIR="mylocaldirectory"
FTP="/usr/bin/ncftpput"
CONVERT="convert"
# commandline to "measure" the light 
LIGHT="`$CONVERT $LOCALFILE -colorspace gray -scale 1x1 txt:- | grep -v '^#' | sed 's/^.*rgb([0-9]*,[0-9]*,//' | sed 's/\([0-9]*\).*/\1/'`"
LIGHTINT=$LIGHT
# commandline to send ftp
CMD="$FTP -d $DEBUGLOG -e $ERRORLOG -u $user -p $pass $host $REMOTEDIR $LOCALFTPFILE"
if [ $LYSINT -ge 100 ];then
cp $LOCALFILE $LOCALFTPFILE
$CMD
fi
------------------------------

3. Using cron to call this script once a minute

4. Webpage on server refreshes picture every minute.

   ( [http://kjartan.iverstek.no/privat/kamera/kamera.php](http://kjartan.iverstek.no/privat/kamera/kamera.php) )


LA la la la la

---

