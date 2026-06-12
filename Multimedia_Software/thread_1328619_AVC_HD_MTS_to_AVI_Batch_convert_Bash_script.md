---
title: "AVC HD MTS to AVI Batch convert Bash script"
date: 2009-11-16
forum: Multimedia Software
---

### Post by L14UX_1NS1D3 on 2009-11-16
So My father and I do freelance Multimedia recording and editing and recently bought an AVCD HD Digital video recorder. Because The camera records into solid state memmory (16GB class 6 SD card) We were able to cut down on capturing time. However, the format that the camera recorded to is known as [H.264]("http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC"); a format that is becoming an industry standard because of it's excellent compression rate. However, because the recorded files have strange .MTS format appended to it We were not able to play it through any convention video player in windows although VLC player on linux has the proper codecs to play the files. :p

So I searched around to see if anyone had come up with *free* way to convert MTS files to a playable format. I found a shareware windows program that converts MTS files but I wanted something on linux. Not finding on linux shell scripts online either, I decided to create my own!

It took me the greater part of three days to make a working script that will convert any number of MTS files in the current working directory into avi files that have the same video and audio quality of the corresponding MTS file. I scoured numerous website pertaining to shell scripting. I took snippets of bash code from some pages so I should give credit where credit is but I've since forgot what the websites were. Anway, I'm by no means an expert. I'm barely a novice when it come to scripting so this is my first major step with creating a shell script. ):P

Here's the code

```
#!/bin/bash
#script to convert all .MTS video files in the current directory to avi

 
#concatinate the number of MTS files currently in dir
#AVICOUNT=`ls | grep avi | tr -d [0-9] | nl | tail -n 1 | cut -b '5-6'`
MTSCOUNT=`ls | grep MTS | tr -d [0-9] | nl | tail -n 1 | cut -b '5-6'`



##### Track time ##################
timestart=`echo "$(date +%I:%M)"`
timestop=`echo "$(date +%I:%M)"`
timestat=` echo "started $timestart finished $timestop"`
MTSSIZE_TOTAL=`du -ch *MTS | tr -d [a-z] | tail -n 1`

echo $timestart

echo "*********************************************************************" 	 							
echo "$PWD $MTSDIR contains$MTSCOUNT AVCD MTS files totaling $MTSSIZE_TOTAL" 
echo "*********************************************************************" 	 
 
sleep 3

for mtsfiles in *.MTS ; do 
echo "n" | ffmpeg -i $mtsfiles -s   hd1080  -aspect 16:9 -sameq -b  15000k -ac 2   -tvstd NTSC "${mtsfiles%.MTS}.avi"
done

echo $timestop

clear ; echo >&2 
 
AVICOUNT=`ls | grep avi | tr -d [0-9] | nl | tail -n 1 | cut -b '5-6'`
AVISIZE_TOTAL=`du -ch *avi | tr -d [a-z] | tail -n 1`


echo $timestat  
echo "*************************************************************"
echo "$AVICOUNT .MTS files converted to avi totaling $AVISIZE_TOTAL" 
echo "*************************************************************"



```

Don't forget to chmod +x the script.
On my system I copied the script into /usr/bin so now I can execute the script from any directory.

Please, please, please give me some feedback! I would like to know how I can make it better! If you find this useful tell me! I'd like to know.

Oh, I'm also working on a script to stitch the the avi files together, index the resulting file and then possibly convert it to mpg for dvd. I've already done some preliminary tests doing just that but converting to mpeg takes **soooooooooooooo** long ](*,)

Thanks!!

---

### Post by pelgrim on 2009-12-06
Well,
I have my HD video recorder now for a year,
and converting to avi in hd resolution works fine
but what I really want is to edit in hd resolution to
compile a new video from a bunch of source files.

I keep in mind that in x years the dvd format (720*576)
will be replaced with full hd, but in any case,
I want to keep the high quality of my recordings in the end result
and having the choise if that result is converted to dvd
or another format.

---

### Post by FakeOutdoorsman on 2009-12-06
> **L14UX_1NS1D3 said:**
> We were not able to play it through any convention video player in windows although VLC player on linux has the proper codecs to play the files. :p
I also use a video camera that records to MTS, and VLC Player in Windows is able to play them just fine.  These are 720p though.  I don't use the 1080i setting, but I don't see why VLC for Windows won't play those either.

> **L14UX_1NS1D3 said:**
> ```
echo "n" | ffmpeg -i $mtsfiles -s   hd1080  -aspect 16:9 -sameq -b  15000k -ac 2   -tvstd NTSC "${mtsfiles%.MTS}.avi"
```

You're using *-sameq* and *-b* in the same command, but you should only use one or the other, and in your case *-qscale* is probably being ignored because *-b* is listed after it.  Anyway, *-sameq* should only be used when the input and output use the same "quantizer scale".  The following supported FFmpeg formats use the mpeg type quantizer scale: flv (the video format, not the container), h263, h263+, mpeg1, mpeg2, mpeg4, msmpeg*.

A better option than *-b* may be *-qscale*, where 3-5 is a good range, and 2 is roughly visually lossless, as in *-qscale 2*.  Use *-b* if you want to limit your output to a certain file size.

---

