---
title: "easyCAP on Linux (Guide)"
date: 2010-06-01
forum: Multimedia Software
---

### Post by Jake007g on 2010-06-01
Hey all, I've spent the past week of my spare time trying to get my easyCAP DC60+ to work on Linux (Ubuntu 10.04 Lucid Lynx). I know that easyCAP "Doesn't Support Linux" according to the manufacturer, but as always with Linux, there was a way, and I worked it out.

It is a relatively short process to get it up and running, it just took me a while to figure out.

You will need to install the drivers for your easyCAP model first, do a quick google search for "easyCAP Linux Drivers"  and follow some tutorials on getting the drivers installed. Credit goes to the people that made those guides. After you've installed the drivers, install KMPlayer (Which includes mencoder, which is what we need) you'll find in the Ubuntu software centre or in the synaptic package manager. You'll also need to install ffmpeg which you can find in the same places.

Once the drivers are installed, create two new empty files, rename on of them to record.sh and the other to deinterlace.sh

Open up record.sh with your favourite open source text editor and paste this into it:
> 
mencoder tv:// -tv device=/dev/video0:input=1:norm=PAL-60:width=1280: height=720 -vf pp=md -o Recording -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000


Make sure you replace all of the values for whatever you need, here's a rough guideline:

input=1 (Composite input, input=0 is s-video)

norm=PAL-60 (Used in europe, change it to norm=NTSC if that's your countries television standard)

-o Recording (This means it will output the video to a file named Recording in the same folder as where the sh script is located, you could change it to /home/yourusername/Desktop/Recording and so on).

-tv device=/dev/video0 (This might be different depending which video input your easyCAP is using. Here are some of the common inputs for your easyCAP: /dev/video0 | /dev/video1 | /dev/video2 | /dev/easycap |)

width=1280: height=720 (These are the recording dimensions, I find these to be the best personally, but just play around with them)

vcodec=mpeg4 (Obviously the video codec, change it whatever you want or just leave it as mpeg4 as it is a great codec to record with)

vbitrate=8000 (Video bit rate, there isn't much reason to go above 8000 as the easyCAP quality wont get much better)

If you wanted to get audio working, you change it a bit to something like this: height=720:forceaudio:adevice=/dev/dsp (Obviously change /dev/dsp to your easyCAP audio device, common ones are /dev/dsp | /dev/dsp1 | /dev/dsp2 | /dev/easysnd |)

So once you've configured your script, save it. Now right click the record.sh script, and enable it to be run as an executable. Now all you need to do to record is double click record.sh, and run in terminal. To stop the recording simply close down the terminal. The only problem with the recording is that it is highly interlace (Lines appear on motion), here is a video of my easyCAP before I deinterlaced it:

[http://www.youtube.com/watch?v=wudyQS_ZqGU](http://www.youtube.com/watch?v=wudyQS_ZqGU)

It is a major pain, especially when running around in a game. So to deinterlace your recorded video, open up deinterlace.sh in your favourite text editor and paste in the following:
> 
ffmpeg -i Recording -target pal-dv -deinterlace -sameq DeInterlaced.avi


The isn't much configuring to be done, but here is some help understanding it:

-i Recording (This is the input file, it looks for a file named Recording in the same folder as the script, you could point it to wherever you saved your original recording by doing something like this -i /home/yourusername/Videos/youroriginalrecordingname)

-sameq DeInterlaced.avi (This is your output file, it will output to the same folder as the script, to a file called DeInterlaced.avi, it will also keep the original dimensions and aspect ratio that you recorded in)

Now, save and close your text editor. Now right click deinterlace.sh and mark it to be ran as an executable as well. Now, you just run that script when you want to deinterlace your videos, for much nicer looking gameplay. Here is an example of some deinterlaced gameplay:

[http://www.youtube.com/watch?v=H3CWb5TXQW8](http://www.youtube.com/watch?v=H3CWb5TXQW8)


Hope I helped, for future tutorials and guides subscribe to my YouTube channel: [http://www.youtube.com/FwdFx](http://www.youtube.com/FwdFx)

See you soon

-Jake

---

### Post by Kooster on 2010-06-24
On lucid easycap works straight out of the box with a bit of tweaking in tvtime, but now when recording there is a slimy green bar spoiling my recording. How do I make that green bar disappear?

---

### Post by boga on 2010-06-26
> **Kooster said:**
> On lucid easycap works straight out of the box
Could you tell me which EasyCAP version do you mean? DC60 or DC60++ or what?

---

### Post by rmt1947 on 2010-06-27
Hi Kooster,

If you have an EasyCAP of the Empia type, as determined by the procedure explained in post 109 here:

[http://swiss.ubuntuforums.org/showthread.php?t=924504&page=11](http://swiss.ubuntuforums.org/showthread.php?t=924504&page=11)

then you will using the em28xx driver in Linux.  In view of:

[http://tvtime.sourceforge.net/help.html#recording](http://tvtime.sourceforge.net/help.html#recording)

you are presumably using mencoder for recording, in which case the following might be relevant:

[http://marc.info/?l=linux-video&m=114362520916990&w=2](http://marc.info/?l=linux-video&m=114362520916990&w=2)

[http://marc.info/?l=linux-video&m=114362692413991&w=2](http://marc.info/?l=linux-video&m=114362692413991&w=2)

Mike

---

### Post by fongoo on 2010-06-27
dude, whenever i run in terminal it just flashs with a window at the top left and then goes away relly quickly, please someone help i need this for game reviews!!!!

---

### Post by kyconny on 2010-12-18
> **fongoo said:**
> dude, whenever i run in terminal it just flashs with a window at the top left and then goes away relly quickly, please someone help i need this for game reviews!!!!


*sigh* Put pause at the end of record.sh and tell me what the terminal says before press any key to continue

---

### Post by Bairdog35 on 2011-01-15
Thank you for this beautiful thread but every time I run the record.sh it just blinks then closes? Can you please help me

---

### Post by ECas123 on 2011-02-11
I'm pretty sure I did everything correctly but when I try to run the record.sh I get this error:

```
eduardo@bacon:~/Documents$ sudo ./record.sh
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: USB 2.0 Camera
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl enum input failed: Invalid argument
tv.c: norm_from_string(PAL-60): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Unable to open '/dev/dsp': No such file or directory
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```

---

### Post by notturno995 on 2011-03-25
> **ECas123 said:**
> I'm pretty sure I did everything correctly but when I try to run the record.sh I get this error:

```
eduardo@bacon:~/Documents$ sudo ./record.sh
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: USB 2.0 Camera
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl enum input failed: Invalid argument
tv.c: norm_from_string(PAL-60): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Unable to open '/dev/dsp': No such file or directory
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```
Same thing here, we need help ;/

---

### Post by Jared Oberhaus on 2012-04-29
One thing that helped me get my EasyCAP to work was to add bars=0 to the driver arguments.
See here: [http://jared-oberhaus-tech-notes.blogspot.com/2011/11/easycap-dc60-and-ubuntu-1110.html]("http://jared-oberhaus-tech-notes.blogspot.com/2011/11/easycap-dc60-and-ubuntu-1110.html")

---

