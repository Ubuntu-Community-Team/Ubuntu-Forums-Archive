---
title: "Errror 2041 after mythexport ipod conversion"
date: 2010-04-28
forum: Mythbuntu
---

### Post by odror on 2010-04-28
My system is 64bit ubuntu 10.04
I converted H264 file (HDPVR output) to ipods format using the recommended setting.

When Playing with VLC No problem.

When I play with quicktime (windows 7) I get 

 error -2041: an invalid sample description was found

And I am not able to import the file to itune library.

Any Ideas how to fix this conversion.

-Thanks

---

### Post by lionsnob on 2010-05-02
I'm seeing the same thing.  I also can't import the files into iTunes (which means I can't put them in my iPhone).  This is with ATSC OTA (MPEG-2) converted to mp4 and h264.  Any ideas?

---

### Post by bb_145 on 2010-05-14
I've run into the same problem with 10.04.  I've tried various arguments for FFMPEG that are supposed to work, including the one listed here

[http://www.otherroute.net/wordpress/2010/01/mythtv-install-and-export-to-iphone/](http://www.otherroute.net/wordpress/2010/01/mythtv-install-and-export-to-iphone/)

I'm starting to wonder if something has changed with FFMPEG or quicktime...

---

### Post by bb_145 on 2010-05-16
I've pretty much given up for now.  

The MP4 files that Mythexport creates work with pretty much everything except Quicktime/iTunes. :confused: I've tried approximately a half a dozen "solutions" to the error, but the only one that I've found that works is to re-transcode the file, which defeats the purpose of Mythexport.  (Part of the problem is that the 2041 error seems to be a catch-all for several different problems, and I don't know enough about transcoding/FFMPEG to troubleshoot.)

Meanwhile, I've installed Handbrake, along with a small script as a user job so I can still export the files from my Myth box.  It doesn't have the comprehensive interface of Mythexport, but at least the exported files work in iTunes.  :)

If anyone is interested, I can share the details.

---

### Post by odror on 2010-05-16
> **bb_145 said:**
> I've pretty much given up for now.  

Meanwhile, I've installed Handbrake, along with a small script as a user job so I can still export the files from my Myth box.  It doesn't have the comprehensive interface of Mythexport, but at least the exported files work in iTunes.  :)

If anyone is interested, I can share the details.

Can you please share the detail.

Thanks

---

### Post by bb_145 on 2010-05-17
The process is fairly straightforward, and is loosely based on the instructions here:

[http://www.mythtv.org/wiki/Transcoding_into_a_3gp_Video]("http://www.mythtv.org/wiki/Transcoding_into_a_3gp_Video")

1)  Install Handbrake
- The deb doesn't currently work with 10.04, so you need to compile.  Just follow the instructions here:

[http://trac.handbrake.fr/wiki/CompileOnLinux?version=5]("http://trac.handbrake.fr/wiki/CompileOnLinux?version=5")

It takes a little time, but it is straightforward.  I didn't bother installing the user interface.

2) The build process creates the HandbrakeCLI file in a folder called "build" in the current working directory.  Copy this file to /usr/bin/

3) Create a script like the following.  (I called mine iphone.sh)

```
#!/bin/sh
# MythTV user job to transcode a video to mp4 suitable for a phone
FILE=$1
TITLE=$2
OUTDIR="/export/"  # or where you would like to save your files
nice /usr/bin/HandBrakeCLI -i $FILE -o "$OUTDIR$TITLE.MP4" --preset="iPhone & iPod Touch" 
```

4) Make it executable
```
chmod a=rx iphone.sh
```

5) Copy it to /usr/bin/

6) Open your backend configuration

7) Find where it lets you add a user job (It is under "General")

8 ) Choose one of the 4 user jobs, and put a description, and then add the following script:

```
/usr/bin/iphone.sh "%DIR%/%FILE%" "%TITLE%-%SUBTITLE%" 
```

You could potentially pass more variables if you wish.

9) Scroll back 2 pages and make sure you click to enable scripts of the user job you just added.  (VERY IMPORTANT, or any jobs you start will just stay in the queue and never execute.  I missed this the first time I tried).

10) Exit the backend setup, and allow the backend to restart.

You're done!  To transcode, you just need to start the job you just created.  Just like Mythexport, it can be done either through the menu (e.g. hit m when a show is selected, and start a job), or through mythweb, or you can even set it up to  automatically transcode after the recording is complete.

Good luck, and let me know if anything is confusing or if I've made any mistakes.

---

### Post by rileyp on 2010-07-21
bb_145 what a great post! I had it working in no time with your iphone.sh script

There is a new ppa deb released the other day that works here.
[https://launchpad.net/~stebbins/+archive/handbrake-snapshots?field.series_filter=lucid](https://launchpad.net/~stebbins/+archive/handbrake-snapshots?field.series_filter=lucid)
So I installed handbrake s per that page then used your iphone.sh script and chose a dir to output to that myth has write permission to.

Ill add the footnote that I installed handbrake initially as per your guide but didn't get any output file. I think now it was because myth didn't have write permission to the suggested dir and so I deleted /usr/bin/handbrakecli and installed the snapshot deb package. I then noticed in info centre all my selected recording had supposedly been completed and twigged onto the permissions problem. I hope this helps someone
cheers rileyp

---

### Post by rhpot1991 on 2010-07-22
Have any of you tried to enable Medibuntu and use aac instead of mp3 for the audio?  There should be a decent description on this in the wiki.

---

### Post by bb_145 on 2010-07-23
Thanks rhpot1991- that works.  

Step by step in one place: 

(Assuming Medibuntu hasn't already been installed)

1) Enable the Medibuntu repository by following [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

2)  Install the libavcodec-unstripped-52 library using Synaptic Package Manager

3) Create a Mythexport configuration using the Mythexport web tool (if you don't have one already)

4) Edit the mythexport configuration file and replace libmp3lame with libfaac. It should be right after -acodec in the ffmpegArgs variable.  (The configuration file is at /etc/mythtv/mythexport_settings.cfg)

Done!  Hopefully this helps someone.

---

### Post by rileyp on 2010-07-27
Do you have settings for ffmpeg to use on mpeg2 dvb recordings for an ipod or wil they be the same as above but changing avi to mpeg2?

---

### Post by bb_145 on 2010-07-29
Sorry- I don't know anything about dvb.  

If it helps, below is a sample FFMPEG command that Mythexport runs for me (taken out of the log file with debugging on).  It converts an MPG to an MP4 with the correct audio encoding (you can see it is now using -acodec libfaac instead of -acodec libmp3lame). 

```
ffmpeg -i /media/video/1002_20090424092300.mpg -y -acodec libfaac -ab 192kb -vcodec mpeg4 -b 600kb -mbd 2 -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -s 240x320 -aspect 4:3 '/home/greg/test/CICA-Mighty_Machines-Harvest_Time-20090424092300.mp4'
```

---

