---
title: "How do I convert .OGM files?"
date: 2009-01-14
forum: Multimedia Software
---

### Post by yolsl on 2009-01-14
I am producing videos using Windows based software, and I intended to use clips that I record with gtk-recordmydesktop, however my video editor doesn't support this format the recordmydesktop uses called .ogg, in fact no software I have uses it except for VLC media player. So I've been looking around for a long time trying to find a way to convert them to .avi or any common video format. From what I can tell they are actually .OGM files and .OGG is the audio format, but the files are wrongly saved with an .OGG extension, I haven't had to deal with .ogg/.ogm files at all in the past so I don't know.

So was just wondering if anyone tell me if converting these files is something I could easily accomplish

---

### Post by andrew.46 on 2009-01-17
Hi,

You will need to know exactly what these files contain as .ogm denotes an 'ogg media' file, a container format which can hold a few different audio and/or video streams.

To find out what is in the files you can use either MPLayer or ffmpeg:

**MPlayer:**

```
mplayer -identify -frames 0 **[COLOR="Red"]myfile.ogm[/COLOR]** 
```

**ffmpeg:**

```
ffmpeg -i **[COLOR="Red"]myfile.ogm[/COLOR]**
```

This information should provide a starting point if you wish to convert to another container.

Andrew

---

### Post by arachnegl on 2009-01-17
I am guessing that your windows doesn't support theora based codecs (the open source standard ones)

Once you have identified the codecs used (with the above answer) you can then choose to change the codec using mencoder (or transcode or ffmpeg) on the command line. (There are graphic tools, but I dont use them)

Google them to find docs and example commands. You do have to gain an understand about encoding and the various formats to reach full potential of these tools.

You can then change the codecs used (to mpeg for example) but also the container format (from ogg to avi for example).

---

### Post by placidoaps on 2009-02-09
I use mendocer to conver OGV files from recodmydesktop to MP4 (H264/MP3) format.
You'll have to install **mencoder**

```
mencoder *out*.ogg -of lavf -lavfopts format=mp4 -oac mp3lame -lameopts cbr:br=128 -ovc x264 -x264encopts bitrate=1000 -o *final*.mp4

```

This command extract the MP3 to a sound file
```
mencoder *final*.mp4 -of rawaudio -oac mp3lame -ovc copy -o *file*.mp3

```

If you understand a little bit of Unix scripting like me, here a script that convert all files inside a "ogv" directory. put the resulting MP4 files in a "mp4" directory and put the processed files in a "ogv_done" directory.
You have to create this directories previously.

As you can see I scale the video for Youtube usage.

```

#! /bin/bash

#input_file_directory=$1
#output_file_path=$2
input_file_directory="ogv"
output_file_path="mp4"
cd $input_file_directory

for file in `dir -d *` ; do
	echo "$input_file_directory"/"$file"
	mp4file=${file%.ogv}.mp4
	/usr/bin/mencoder "$file" -vf scale=480:360:0:0,harddup -sws 10 -of lavf -lavfopts format=mp4 -oac mp3lame -lameopts cbr:br=128 -ovc x264 -x264encopts bitrate=1000 -o "../$output_file_path"/"$mp4file"
	mv "$file" ../ogv_done/"$file"
done

```

---

### Post by Anubis on 2010-01-17
> **yolsl said:**
> I am producing videos using Windows based software, and I intended to use clips that I record with gtk-recordmydesktop, however my video editor doesn't support this format the recordmydesktop uses called .ogg, in fact no software I have uses it except for VLC media player. So I've been looking around for a long time trying to find a way to convert them to .avi or any common video format. From what I can tell they are actually .OGM files and .OGG is the audio format, but the files are wrongly saved with an .OGG extension, I haven't had to deal with .ogg/.ogm files at all in the past so I don't know.

So was just wondering if anyone tell me if converting these files is something I could easily accomplish

[http://handbrake.fr/](http://handbrake.fr/)

HandBrake  is an open-source, GPL-licensed, multiplatform, multithreaded video transcoder, available for MacOS X, Linux and Windows.

---

