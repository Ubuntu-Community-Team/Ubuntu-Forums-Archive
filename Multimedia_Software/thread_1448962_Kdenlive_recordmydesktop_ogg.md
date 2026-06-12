---
title: "Kdenlive recordmydesktop ogg"
date: 2010-04-07
forum: Multimedia Software
---

### Post by bonfire89 on 2010-04-07
Hello,

Has anyone had an experience with importing ogg (ogv) files created with recordmydesktop into kdenlive all I get is a distorted grey mess when I do 

:/

I'm pretty sure I have the w32codecs installed.

I'm running Ubuntu 10.04 beta.


=/


Thanks

---

### Post by oyvha6 on 2010-04-07
Hi!

I have the same problem. I even tried to convert the file into an AVI file, but problem still occurs. I can, however, play the .ogv file in my mediaplayer :S 

Weird stuff! Hope someone can fix this! :)

---

### Post by bonfire89 on 2010-04-07
well, I have converted the files to avi with [http://ubuntuswitch.wordpress.com/2007/10/05/howto-convert-ogg-to-avi-with-mencoder/](http://ubuntuswitch.wordpress.com/2007/10/05/howto-convert-ogg-to-avi-with-mencoder/) and it seems to work thus far, but that isn't the point, I thought ogg was supposed to be the opensource format of choice but open source software can't handle it? heh

---

### Post by skullmunky on 2010-04-07
Try getting the latest Kdenlive.  I ran into this problem before and was just as baffled.  I installed Kdenlive 0.7.7.1 (on Kubuntu 9.04 64 bit) from the project's launchpad repository, tried it again and it works.  I can use recordmydesktop from the command line or via gtk-recordmydesktop, save an ogv file, import into Kdenlive, and successfully edit and render wihh them.  

Kdenlive also has screengrab built in via an external call to recordmydesktop, but at the moment it doesn't seem to actually do anything...but at least this other method works now!

---

### Post by IzByFl on 2010-05-21
I have the same problem, and I have the latest kdenlive...

---

### Post by dewdrop_world on 2010-08-23
Large W. T. F.

[http://en.wikibooks.org/wiki/Kdenlive/FAQ#Does_Kdenlive_support_.ogv_from_Recordmydesktop.3F](http://en.wikibooks.org/wiki/Kdenlive/FAQ#Does_Kdenlive_support_.ogv_from_Recordmydesktop.3F)

> Does Kdenlive support .ogv from Recordmydesktop?

It's not in the list of supported files.

Well screw that. Back to synaptic, look for something else.

---

### Post by Baldrick_NZ on 2010-08-24
> **dewdrop_world said:**
> Large W. T. F.

[http://en.wikibooks.org/wiki/Kdenlive/FAQ#Does_Kdenlive_support_.ogv_from_Recordmydesktop.3F](http://en.wikibooks.org/wiki/Kdenlive/FAQ#Does_Kdenlive_support_.ogv_from_Recordmydesktop.3F)



Well screw that. Back to synaptic, look for something else.

After days of trialling different apps, I settled on RecordMyDesktop, Handbrake (to convert .ogv to MP4 H264 in high quality), then OpenShot to edit the screencast/add titles/save. I usually use the All Formats>MP4 H264>HDV 720 25p>High settings. 

Works a treat for me.

Kdenlive under gnome os rather bulky and uses way more CPU than native gnome programs.

Give that ago, might be just what you're looking for. ;)

---

### Post by andrea000 on 2010-08-25
Try using record it now it uses record my desktop but uses FFmpeg to convert the output file to what ever format you want.For a file you have already recorded use ffmpeg to convert it to whatever format you want if you don't like the terminal use winff a gui to ffmpeg.That should do it.

---

### Post by 4ebees on 2011-06-23
> **Baldrick_NZ said:**
> After days of trialling different apps, I settled on RecordMyDesktop, Handbrake (to convert .ogv to MP4 H264 in high quality), then OpenShot to edit the screencast/add titles/save. I usually use the All Formats>MP4 H264>HDV 720 25p>High settings. 

Works a treat for me.

Kdenlive under gnome os rather bulky and uses way more CPU than native gnome programs.

Give that ago, might be just what you're looking for. ;)


I know it was a while back that you posted this, but I just wanted to say a big "THANKS".

It was annoying me no end and this is a perfect solution.

Though I generally use Kdenlive, I consider all the 'nix apps as tools and so swap between them when needed :)

Openshot is coming on strong and it's nice to see a couple of really good video editing apps go head-to-head.

---

### Post by Pyrosopher on 2012-02-24
I found this thread while looking for a solution to the same problem. Here is why I have stuck with Kdenlive and my alternate solution. 

I switched away from OpenShot because Kdenlive has the feature to extract frames from the video. I am creating tutorials and I record the desktop video first and add audio or subtitles afterwards. Sometimes I need more time for the explanation and Kdenlive allows me to extract a frame and splice it in for however long I need. 

VLC player is the saviour of the day. Under the media menu there is the option for "Convert / Save..." Click that option, add your file in the next dialogue, click "Convert / Save" then choose the destination. I've been using the MP4 container and it has been 100% so far.

The only niggle with the process is that it can cut off the first few seconds. No idea why, VLC is fine when it plays the original, it is only the encoding. The simple work-around is to count to 10 after you hit record to allow for the cropping.

I render my Kdenlive files as MP4s. They always come out as large files and I have found that sending them through ffmpeg reduces  filesizes by about 90% without any visible loss of quality. If I have added an audio track I use this command (it copies the audio, I didn't like what compression did to the voice-over and it only made a handful of megs difference)

ffmpeg -i inputfile.mp4 -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec copy outputfile.mp4

If I have used subtitles I use this command which discards the audio

ffmpeg -i inputfile.mp4 -vcodec libx264 -vpre medium -crf 24 -threads 0 -an outputfile.mp4

Hope this helps :)

---

