---
title: "Transcode Script for Transcoding Your Videos to Playstation 3 Compatible Format"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by KaridaSerious on 2007-11-15
Hi there!

I've been searching around the forums for information concerning about how to convert my video library to ps3 compatible format, so I could stream it through my WLAN network to my PS3.

Well none of the threads haven't helped me much, so I made a little research about this and found an excellent script from Doom9 forums, made by Jarkko Vatjus-Anttila, which converts your videos to H.264 AVC format. 

So I'll attach the script at the end of this post and lets see if this helps any of you guys when transcoding your favorite videos to a format that PS3 understands.

The script is pretty simple to use. You just need to specify the name of the input and output file and the script will do the rest of the work for you. Optionally you can also specify a subtitle file to be attached to the output file.

For example this command will transcode your video to mp4 container, using h.264 video codec and faac audio codec:

```

ps3_transcode.sh -input input.avi -output output.mp4

```

If you have a subtitle file that you want to add just insert "-subtitle" tag at the end of the line:

```

ps3_transcode.sh -input input.avi -output output.mp4 -subtitle subtitle.srt

```

The script uses VBR feature, included in h.264 codec, so you dont need to worry about bitrates. That's good thing to me :). The script contains also many other features but I haven't looked into those yet.

Before you can use this script make sure you have all the dependencies installed to your system. The script needs following packages to be installed:

mplayer
x264
faac
mp4box
bc
ffmpeg

To install:
```

sudo apt-get install mplayer x264 libfaac gpac ffmpeg bc

```

More information can be found at Doom9 forum, where Jarkko explains more about this script. The script located at the Doom9 forum is a bit outdated.
Script attached here is the newest version at the moment (received it yesterday from the author).

Doom9 URL: [http://forum.doom9.org/showthread.php?t=127998](http://forum.doom9.org/showthread.php?t=127998)

Hope you find this useful, I certainly did. Happy transcoding :)


*UPDATE*

PS3 Transcode script has been updated!

Changelog:

v1.0.1 (25th Jan 2008 )
- Added error checking for streams that do not report
resoluton and/or FPS correctly.

- Added -fps, -xres and -yres options to override the
detected values

- KDS

---

### Post by soc91 on 2007-11-20
The script works like a charm, but when I try to play the file on my ps3 I get an error that says that the file is not supported. Have anyone tryed this script? Are there any modifications that needs to be done to make the files work on ps3?

---

### Post by KaridaSerious on 2007-11-20
I've been using it without problems. I just gave the input and output filenames and script did the rest. Did you remember to change the file extension to .mp4?.The PS3 is a bit picky when you come to video files :). But if thats not the problem, feel free to contact the author, I noticed that he has left his email address in the script, so users can contact him concerning about this script. 

- KDS

---

### Post by soc91 on 2007-11-20
No I did not forget to put .mp4 in the end of the file name. Is there a limit to how long the filename can be in the ps3?

---

### Post by soc91 on 2007-11-23
I know what was wrong now. I forgot to add the <protocolInfo extend="yes"/> to the ~/.mediatomb/config.xml file. Now everything works fine.

---

### Post by KaridaSerious on 2007-11-26
OK thats good news. It's a good thing to hear that the script wasn't the problem afterall :)

- KDS

---

### Post by Jugix on 2007-11-28
Alright! Finally a good app for converting my video files to PS3 supported format. My Quad Core 3600MHz just got some work to do! JIIIHAAAAAAA!! :guitar:

---

### Post by Yob on 2008-01-05
____ solved -____
In case anyone ends up in the same situation as I the solution was to add this to the end of the line in my crontab:
2>&1
so it will look like this:
  * 20  * * *  Programs/convert.sh > /home/username/convert.log 2>&1
________________________________________________________________________


Hi,

Your script works very well - first off a big thank you!

Now, I'm trying to make a cron job that runs the script once a day to convert a coupe of avi's automatically.
I've copied your example of how to convert all files in a dir and made an executable file called 'convert.sh'. When I execute this file from a terminal it works and starts converting the avi-files.
However - when I try to make cron execute the file it gives me "OMG AAC file empty". 

Any ideas?

---

### Post by KaridaSerious on 2008-01-11
Roger that. Good thing to hear that you managed to solve this problem by yourself because I've never used cron. *Starts to google about cron* :D


-KDS

---

### Post by KaridaSerious on 2008-03-01
Script Updated

---

### Post by Kadmium on 2008-06-23
Why does this script only output audio files for me? Two .wav files and one .aac file. I have all applications installed, etc. Weird.

---

### Post by graveson on 2008-06-30
is this the latest version of the script. I notice a version 2 also available on the link you attached?

[http://forum.doom9.org/showthread.php?t=127998](http://forum.doom9.org/showthread.php?t=127998)

---

### Post by KaridaSerious on 2008-07-01
Yes this is the latest version. The script located at the doom9 forums is the first version of the script, so its pretty outdated.

Kadmium, what type of file did you try to transcode? AFAIK this script doesn't handle matroska files very well so it may be the problem. I've told about this matroska problem to the author and he tries to look into it as soon as possible

-KDS

---

### Post by graveson on 2008-07-01
thanks for the update. i will try this version as i was having stuttering problems with the one on the doom9 forum.

---

