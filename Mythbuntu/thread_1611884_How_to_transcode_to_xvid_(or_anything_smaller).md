---
title: "How to transcode to xvid (or anything smaller)"
date: 2010-11-02
forum: Mythbuntu
---

### Post by Quadari on 2010-11-02
Hi All,

I have a couple of recorded shows that I'd like to save.  So, to take a specific example, I have one show that is currently taking about 8GB of space.  I'd like to transcode it to something much smaller (say to xvid) so that I can save it on the computer (and potentially burn it to a disc).  I don't care THAT much about video quality, and I know that a 90 minute show (which is what this is) can be compressed down to the order of a couple hundred MBs.

There's a ton of info on the web about MythExport and nuvexport, etc.  But I can't tell if any of it is current as a lot of the sites talk about the fact that nuvexport will be built in to mythtv 0.21, etc.  (I'm on 10.04.1, and mythtv 0.23.)

I tried just going to the recording and choosing "Transcode", but I can't tell if that actually did anything.

Some help or direction to the most recent instructions would be much appreciated.

Thanks!

---

### Post by sanderj on 2010-11-02
You could try "handbrake"...

---

### Post by chuckrp on 2012-05-15
I would like to do the same thing. Did you ever get an answer to this?

---

### Post by klc5555 on 2012-05-16
For just handling an occasional recording, as the OP wanted to do, either of the solutions presented from 2 years ago are still valid.

nuvexport (if correctly installed) will handle a variety of output formats using the default ffmpeg or mencoder (transcode too, if you're still running myth 0.23) See: [http://www.mythtv.org/wiki/Nuvexport](http://www.mythtv.org/wiki/Nuvexport)

Handbrake will work well also, within the two or three output formats it supports. The gui will be user-friendlier to most, but you'll need to have found the actual recording file you want to work with, since Handbrake doesn't interact with the mythconverg database.

Also, if you just want to transcode the recording, make an iso, burn it onto a dvd and be done with it, the program Devede works very well and simply for cranking out an iso for burning with k3b, brasero, or whatever you're using.

Mencoder or ffmpeg run from a prompt can get you a transcoded and smaller recording. Since ffmpeg has to be the most annoying command-line utility ever devised, a much easier-to-use gui has been developed for it: [http://winff.org/html_new/](http://winff.org/html_new/)

In theory, even Mytharchive can work. [http://www.mythtv.org/wiki/Mytharchive](http://www.mythtv.org/wiki/Mytharchive)

And there are likely a half dozen or more other solutions out there as well.

---

### Post by Zorbitz on 2012-05-16
I agree that Handbrake may be the easier choice if working directly on the recorded file. The file should be easy to locate as you most likely know the date and time the recording was done, and the fact that the filenames used by recordings will be <channel_id>_<datestamp>.mpg

As an example, a recording I did on April 5th 2012 at 9:00PM (21:00) from channel 1020 has the filename 1020_20120405210000.mpg (so syntax would be chanid_yyyymmddhhmmnn.mpg) I don't think the last two digits represent seconds, rather a unique ID. Not sure though, but they tend to be zeros.

Despite ffmpeg's rather heavy use of command line parameters (and frequent changes to them), it is my personal choice when transcoding. I like to compile from source to get the latest version, excellent guide for doing this this at [https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) Remember to add *--enable-libxvid* to the ./configure line if you want xvid support (will require libxvidcore-dev package).

I typically make cutlists to trim recordings, and then use mythtranscode with the *--honorcutlist* parameter and write to a FIFO for ffmpeg to read from.

Note: Compiling the latest version of ffmpeg will break streaming recordings from mythweb because the *-deinterlace* parameter has become deprecated (can be fixed by modifying the ffmpeg command line parameters used in mythweb code. I found them in **/usr/share/mythtv/mythweb/modules/stream/stream_flv.pl**).

---

### Post by nickrout on 2012-05-17
OTOH disk space is really cheap, buy another disk!

---

### Post by chuckrp on 2012-05-22
I am using mythbuntu on my computer and can not get handbrake to install. Do i need to change over to ubuntu and mythtv?

---

### Post by nickrout on 2012-05-23
mythbuntu uses the same respositories as ubuntu so if it won't install on mythbuntu it won't install on ubuntu.

You have to install handbrake via a ppa:

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

However there doesn't seem to be a 12.04 build there. This page seems to suggest you can install it from the oneric package on that ppa:

[https://answers.launchpad.net/ubuntu/+source/software-center/+question/194730](https://answers.launchpad.net/ubuntu/+source/software-center/+question/194730) - I would try that first.

There is one here by the look of it: [https://launchpad.net/~marcusls/+ppa-packages](https://launchpad.net/~marcusls/+ppa-packages) - but they are labelled "unstable" - ie unreleased code by the look of it.

---

### Post by perspectoff on 2012-05-23
Handbrake doesn't transcode to .AVI any longer; only to MKV. Since my DVD player only plays .AVI (with XVID) this made me stop using handbrake.

I only use mencoder for transcoding nowadays.

Here's a very good guide to video conversion, from Ubuntuguide/Kubuntuguide:

[http://ubuntuguide.org/wiki/Video_Conversion](http://ubuntuguide.org/wiki/Video_Conversion)

---

### Post by nickrout on 2012-05-23
> **perspectoff said:**
> Handbrake doesn't transcode to .AVI any longer; only to MKV. Since my DVD player only plays .AVI (with XVID) this made me stop using handbrake.

I only use mencoder for transcoding nowadays.

Here's a very good guide to video conversion, from Ubuntuguide/Kubuntuguide:

[http://ubuntuguide.org/wiki/Video_Conversion](http://ubuntuguide.org/wiki/Video_Conversion)

Why are you using a DVD player when you have mythfrontend?

---

### Post by nickrout on 2012-05-23
> **nickrout said:**
> mythbuntu uses the same respositories as ubuntu so if it won't install on mythbuntu it won't install on ubuntu.

You have to install handbrake via a ppa:

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

However there doesn't seem to be a 12.04 build there. This page seems to suggest you can install it from the oneric package on that ppa:

[https://answers.launchpad.net/ubuntu/+source/software-center/+question/194730](https://answers.launchpad.net/ubuntu/+source/software-center/+question/194730) - I would try that first.

There is one here by the look of it: [https://launchpad.net/~marcusls/+ppa-packages](https://launchpad.net/~marcusls/+ppa-packages) - but they are labelled "unstable" - ie unreleased code by the look of it.

PS looks like there is another ppa for the development version of handbrake, here [https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

EDIT: Just to add, I successfully installed both handbrake-gtk and handbrake-cli on precise using the oneiric packages from the handbrake-releases ppa.

I did ```
sudo add-apt-repository ppa:stebbins/handbrake-releases
``` and then edited /etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list and changed precise to oneiric in each line. after sudo apt-get update I could install.

---

### Post by chuckrp on 2012-05-23
Can this be done when I initially set up a tv show to record in Mythtv? In the user jobs?

---

### Post by nickrout on 2012-05-24
> **chuckrp said:**
> Can this be done when I initially set up a tv show to record in Mythtv? In the user jobs?

You can run any script as a userjob, there are lots of examples in the wiki and in the mailing list archives. If you ask on the mailing list, you will get lots of ideas and suggestions.

There is also this stub script which will allow you to use your own  transcoding to meet your requirements:

[http://www.mythtv.org/wiki/Transcode_wrapper_stub](http://www.mythtv.org/wiki/Transcode_wrapper_stub)

---

### Post by chuckrp on 2012-05-28
I went to the WIKI site as recommended. My question is now do I copy all of that script into USERJOB1 or do I need to enter it into SQL. I thought I was starting to understand this but now not sure. I have gotten Mythtv .25 working. 64 bit loaded. Can watch TV and record. I've upgraded the computer I was using with a 250 GB Sata drive and a Nvidea 6xx series card. HDMI connection is working. So if I could get it setup to delete commercials and transcode to XVID that would be great. Then I will figure out how to copy the transcoded files over to a DVD.
Could someone tell me the answers?

---

### Post by nickrout on 2012-05-28
> **chuckrp said:**
> I went to the WIKI site as recommended. My question is now do I copy all of that script into USERJOB1 or do I need to enter it into SQL. I thought I was starting to understand this but now not sure. I have gotten Mythtv .25 working. 64 bit loaded. Can watch TV and record. I've upgraded the computer I was using with a 250 GB Sata drive and a Nvidea 6xx series card. HDMI connection is working. So if I could get it setup to delete commercials and transcode to XVID that would be great. Then I will figure out how to copy the transcoded files over to a DVD.
Could someone tell me the answers?

[LIST=1]
[*]That script is a wrapper, you need to add your own transcoding bits. Copy the script into an editor, add your transcoding bits and save it as, say, /usr/local/bin/mytranscodescript.py
[*]use mytranscodescript.py as userjob1
[*]can't figure why you want to go to xvid and then to DVD, DVD's are mpeg2. Or are you simply wanting to store the files on a DVD rather than try to make it DVD format
[/LIST]

---

### Post by dodle on 2012-05-29
Xvid with FFmpeg:
```
ffmpeg -i <video_file> -sameq -vcodec libxvid -acodec libmp3lame <new_video>.avi
```
or
```
ffmpeg -i <video_file> -sameq -vcodec mpeg4 -vtag xvid <new_video>.avi
```

h264 with FFmpeg:
```
ffmpeg -i <video_file> -sameq -vcodec libx264 -acodec libmp3lame <new_video>.avi
```

I recommend h264 as it has better compression. And, as another user said there is a good front-end for FFmpeg called WinFF.

If you want to specify the target bitrate you can do this:
```
ffmpeg -i <video_file> -b 1400k -vcodec mpeg4 -vtag xvid -acodec libmp3lame <new_video>.avi
```

---

### Post by andrew.46 on 2012-05-29
If using x264/h.264 you might be be best to also use a preset....

---

### Post by FakeOutdoorsman on 2012-05-29
> **dodle said:**
> Xvid with FFmpeg:
```
... -sameq ...
```

The *-sameq* option should not be used in this case. It does not mean "same quality" as the documentation unfortunately used to imply. The docs now say, "use same quantizer as source (implies VBR)", but using the same quantizer isn't always a good idea and it wasn't designed to be used between inputs and outputs that do not share the same quantizer scale such as encoding from flv1/h263/h263+/mpeg1/mpeg2/mpeg4/msmpeg* to H.264.

> **dodle said:**
> 
h264 with FFmpeg:
```
ffmpeg -i <video_file> -sameq -vcodec libx264 -acodec libmp3lame <new_video>.avi
```

H.264 and AVI are a bad mix (unless your encoding in lossless mode with x264 due to the lack of b-frames).

> **andrew.46 said:**
> If using x264/h.264 you might be be best to also use a preset....

Agreed. Example:
```
ffmpeg -i input -vcodec libx264 -preset medium -crf 24 -acodec copy output.mkv
```
General usage is to use the highest crf value that still gives you an acceptable quality and the slowest preset you have patience for (ignore the *placebo* preset as it is a complete waste of time). The presets can be seen with:
```
x264 --fullhelp
```

---

### Post by chuckrp on 2012-05-29
I am wanting to save the files as xvid on a data DVD. Then I can send them to my son in Germany to watch there. He is using a media player.

---

### Post by chuckrp on 2012-05-31
thx

---

### Post by dewmanstl on 2012-07-19
Is there any how to's on dropping these into user jobs? I have searched google and havent really found much. Burning to a dvd is a much better option then just "buying a bigger disk"

---

### Post by nickrout on 2012-07-19
> **dewmanstl said:**
> Is there any how to's on dropping these into user jobs? I have searched google and havent really found much. Burning to a dvd is a much better option then just "buying a bigger disk"Not in MHO

---

