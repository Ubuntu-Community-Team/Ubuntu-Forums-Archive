---
title: "Want to capture VHS tapes to Ubuntu."
date: 2011-02-07
forum: Multimedia Software
---

### Post by Deer Hunter on 2011-02-07
Hello everyone,
I have some VHS tapes that I'd like to digitize, and I need help finding a program that can capture the video to Ubuntu (I'm running 10.04).  I have USB capture-box, which connects to the player via composite RCA, then goes to the computer.  Can anyone direct me to some Linux software that can help me with this?  The video editing programs which I've found in Ubuntu so far don't seem to support real-time capture; it seems like you have to import your digitized file into the program.  Thanks in advance.

Deer Hunter

---

### Post by korleon on 2011-02-07
Just a guess here but I think if you have video coming in via USB here's a couple of links with programs you might find useful:

[https://help.ubuntu.com/7.04/musicvideophotos/C/video-editing.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video-editing.html)

[http://alicious.com/2008/videomovie-screen-capture-programs-for-ubuntu-linux/](http://alicious.com/2008/videomovie-screen-capture-programs-for-ubuntu-linux/)

Hope they have what you need

---

### Post by oldos2er on 2011-02-07
Simplest way is to use cat, **cat /dev/video0 > foo.mpeg** for example. I've also used vlc for this.

---

### Post by Deer Hunter on 2011-02-07
I tried VLC and it couldn't detect my capture device.  Neither could Kino, Pitivi, or DeVeDe.  I wonder if that's part of the problem. But the device was seen alright in my XP virtual machine on this computer, so apparently Ubuntu could see it well enough to do that much.  Here's a link to the capture device, maybe you can tell if it is the problem: [http://www.staples.ca/ENG/Catalog/cat_sku.asp?CatIds=&webid=911628&affixedcode=WW](http://www.staples.ca/ENG/Catalog/cat_sku.asp?CatIds=&webid=911628&affixedcode=WW)

Thanks for the advice so far.

Can you elaborate on "cat," what it is and does? It sounds interesting but I'd like a little more info before I jump in blindly.  Thanks.

---

### Post by Deer Hunter on 2011-02-08
Of course, I am also able to make this work just fine in Windows, but that kind defeats the purpose, as I want to be able to do it all in Linux.

Any other ideas anyone?

---

### Post by sunnymolini on 2011-02-08
Have you checked the manufacturer of the device to see if they have some real linux drivers?

---

### Post by Deer Hunter on 2011-02-08
> **sunnymolini said:**
> Have you checked the manufacturer of the device to see if they have some real linux drivers?

Unfortunately, no they do not have linux drivers.

---

### Post by oldos2er on 2011-02-08
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

**cat** is a CLI app that captures output from a file or device and redirects it to your screen (e.g. **cat /etc/apt/sources.list**, a command you see frequently in the forums) or to a file.

---

### Post by Perkins on 2011-03-01
I am trying to do exactly this.  I have found that streamer can capture the audio and video from my device.  In my case the command is:

 streamer -C /dev/dsp1 -c /dev/video1 -iComposite1 -s 720x480 -n ntsc -t 9:00:00 -f jpeg -j 100 -F stereo -o Video.avi

Here's where I run into issues:

1)  The *only* modes listed in the (extremely sparse) documentation that works are jpeg avi, and raw.  This means I have a choice between huge files, and even more huge files.  Which means that none of the video editors I can find can process them.  The best is Openshot, which will load the first 15 minutes before dying.  Pitivi is at least kind enough to tell me that it's timing out on processing the file, but there's no way to tell it that it's ok to try longer.

2)  The A/V sync is off by approximately .25 seconds.  It annoyingly doesn't stay completely constant and bobbles around between .19 and .30.  XawTV can record just fine, with only between .06 and .09 offset, but its resolution maxes out at 384x288, which makes things awfully fuzzy.  And no, kicking streamer down to that resolution doesn't get rid of its audio lag.

So, it looks like I'm down to ffmpeg for trimming, which is fine, I've done that before, but I need a way to resync the audio (and preferably a trick to make streamer try to keep the audio offset more constant, even if it's larger.)  The documentation on these things is awfully sparse.

---

### Post by FakeOutdoorsman on 2011-03-01
Have you tried using FFmpeg directly?
[FFmpeg Documentation: 7.7 video4linux and video4linux2](http://www.ffmpeg.org/ffmpeg-doc.html#SEC27)

You can then output to a more suitable output format.

---

### Post by Perkins on 2011-03-01
I can get ffmpeg to capture the video, but the audio is getting lost.  Also every encoder I try does horrible things to the video quality...

I guess I'll try the windows software that came with the thing and see how it does...  The reviews mostly said it was junk, but I don't care if the editor and DVD creator work so long as it captures the video properly.

---

### Post by skullmunky on 2011-03-02
Here's a method I've been using for capturing VHS using a Hollywood Dazzle Firewire interface: 

[http://ubuntuforums.org/showthread.php?p=10511306#post10511306]("http://ubuntuforums.org/showthread.php?p=10511306#post10511306")

But the main issue you're facing is probably the basic hardware support for the capture device you have.  the link to Staples gave me an odd page asking for my zip code to ship one to me ;)  I don't want one because it obviously doesn't work so good, but what's the model?  With that it's possible to figure out if it even has good linux driver support at all.

---

### Post by Perkins on 2011-03-03
I think it's the USB version of the Dazzle.  The hardware support seems fine.  It can capture audio or video flawlessly.  I just can't seem to find a combination of settings that will stitch the two together in a reasonable manner.  The Windows software seems to work about perfectly for capturing, it just really sucks at creating DVDs.  So, I will plug it into my gaming machine, which has a nice, large, NTFS partition, and do it that way to save the headache.

---

### Post by Perkins on 2011-03-08
Grahhh!  The Windows capture software did one tape, now it makes my machine crash...  The linux software works, but I need a way to resync the audio and the video...  Can anyone give me a hint about how to do it?

---

### Post by skullmunky on 2011-03-14
What are the settings you're using with ffmpeg?  I don't have a USB capture device so can't test it but if it didn't work (you mentioned no sound...?) I have some thoughts.  The examples I see in the documentation for ffmpeg seem to have something like "-f oss -i /dev/dsp" to set the sound input.  That may not work so good because OSS is a pretty old and venerable sound system for linux.  Currently you usually have ALSA and probably PulseAudio running to manage sound, and this can cause silent failure of programs that are still using OSS.  (For example, in OSS only one application can have access to the sound hardware.  Newer sound systems don't have that limitation, but it may mean that old programs trying to access the hardware via OSS won't be able to and you just get silence.) 

Also with ffmpeg what video codec and quality flags did you use?  The default bitrate is extremely low and looks quite bad, so you have to crank the settings way up.  

ffmpeg also seems to have some flags to control sync, not sure if those will help.  if the sync problem is constant you could timestretch the audio in Audacity or possibly just within kdenlive, but obviously it's better to get it right initially!  

You might have tried these already but if not, give them a shot:

Transcode : [http://www.transcoding.org/transcode?Video4linux_Examples]("http://www.transcoding.org/transcode?Video4linux_Examples")

GStreamer (Not the same as streamer ;): [http://www.linuxtv.org/wiki/index.php/GStreamer]("http://www.linuxtv.org/wiki/index.php/GStreamer")

gst-launch is also pretty cryptic but super powerful and effective once you get what's going on with it.

---

### Post by rob22941 on 2011-03-24
> **Perkins said:**
> Grahhh!  The Windows capture software did one tape, now it makes my machine crash...  The linux software works, but I need a way to resync the audio and the video...  Can anyone give me a hint about how to do it?

May I ask what software you were using in Windows?

---

### Post by Perkins on 2011-03-24
And the post I made (or thought I made) with the settings I used has disappeared into never-never land somehow...  I'll have to dig through my notes again.

I'm using the Dazzle software that came with my capture device.  I'm fairly certain that the machine crash it causes is due to some kind of overheat issue that seems to have cropped up on my pushing-five-years old desktop. (No idea why, I clean the heatsinks regularly, and all the fans are spinning...)  It doesn't crash my laptop, but I don't have enough disk space there to store the 1.5 hour video segments I'm working on, and I have discovered that my nifty little PCMCIA SATA controller card doesn't support Vista.  :(  

But, I think I've ripped enough non-essential stuff off the drive to have enough space for it to work.  Of course, if someone were to point me at a tutorial for Transcode and/or FFMpeg that doesn't assume the reader already knows all the ins and outs of how video encoding works, I would definitely be interested.  :)

---

### Post by dnguyen1963 on 2011-03-25
This is the exact reason why I still have XP on my computer.  Video capturing in Linux is a real pain.  I am using Windows Movie Maker and it recognizes my Dazzle right away.  Dazzle software (Pinnacle)also works very well, but it is limited to only 104 min of capturing (some of my VHS is 6 h long).  I have been searching for a Windows Movie Maker equivalence in Linux for a few years now and still not found one.

---

### Post by Brandel Valico on 2011-03-25
I use a nice program called XawTV to yank the video feeds to my hard drives. Works like a champ pretty much every time I use it. Once it's on my drive I use Mandvd to convert the .avi to video format and burn it to a dvd if thats my goal. (ManDVD has a setting that allows me to adjust and preview the adjustment of audio synch on the very few occasions I have needed to do so built right in.)

Both should be able to be installed from the software centre.

---

### Post by Perkins on 2011-03-25
I used XawTV to figure out the properties of my capture card.  It doesn't work for capturing in my case because its only available resolution is 320x240, and its only available codec turns the image into one cut above swirling mud.  Also it crashes when I stop recording, but that's relatively minor.

Worst case is I'm going to buy one of the laptop hard drive deals I'm seeing going past and put that in my laptop.  That will likely solve the issue.

---

### Post by Brandel Valico on 2011-03-25
Yeah, sorry about that I missed that you had tried XawTV the first time I read through this.

A command you can try out

> NTSC HIGH ('DVD' QUALITY) RES CAPTURE

mencoder -tv norm=NTSC:driver=v4l2:width=720:height=576:input=1: fps=25 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=80 00:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192 :aspect=4/3 -o capture.mpg

As soon as you push enter the capture process will begin, to end it push CTRL+C.

You may also want to try Xdtv it's an older program that is a souped up version of Xawtv. Harder to get running now-a-days but works at a higher frame resolution then standard Xawtv does.

---

### Post by BuntuNooob on 2011-07-01
Found a youtube tutorial that might help.
 
[SIZE=2]http://www.youtube.com/user/luckyglasspig#grid/user/2B7CB4BF57D76F2C
[/SIZE]

---

### Post by Perkins on 2011-07-02
I figured out a couple of days ago that the overheat issue was with my video card.  So I removed it and went back to using the onboard one.  Now I can't see the video it's capturing, but it seems to work anyway.

I'll take a look at the tutorials and see if they'll work for what I'm doing.

---

### Post by movieplayer on 2011-09-22
where is there a list of ubuntu/linux compatible usb video capture devices?

---

### Post by Perkins on 2011-09-22
Anything that's compatible with V4L.  A list of currently available drivers is available at [http://www.exploits.org/v4l/](http://www.exploits.org/v4l/)

Some of them map to specific products, while the rest are for particular chipsets.  The manufacturer's specs usually include which chipset a particular device uses if you dig far enough.  Most consumer devices I've seen have been either 3com or Bt8x8, but it's a good idea to double-check before you buy one.

---

### Post by MeKino on 2011-09-25
Hi,

I have been using vlc for capturing video successfully...

But, if all you are experiencing is audio sync problems then these can be corrected using avidemux (yes, works with mpeg files).

Kino

---

### Post by meiradarocha on 2012-02-26
My best result in video capture is with mencoder, using an old Pixelview PlayTV Pro card (composite and S-Video inputs):


[FONT=Courier New]mencoder \
tv:///1 \
-tv norm=NTSC-M\
:device=/dev/video1\
:alsa:adevice=hw.0,0\
:audioid=0\
:amode=1\
:driver=v4l2\
:outfmt=i420\
:width=720:height=480\
:fps=29.97\
:brightness=10:contrast=-25\
:buffersize=300 \
-ffourcc divx \
-oac mp3lame \
-lameopts cbr:preset=128 \
-ovc lavc \
-lavcopts vcodec=mpeg4\
:threads=2\
:vbitrate=1500\
:autoaspect\
:keyint=30:sc_threshold=-50000:vb_strategy=2 \
-vf dsize=4/3,kerndeint=20:0:0:1:1 \
-vf-add softskip,harddup \
-endpos 02:10:00 \
-o ~/videos/tv-composite-mpeg4-mp3-$$.avi[/FONT]

ffmpeg works, too:

[FONT=Courier New]ffmpeg -threads 2 \
 -f alsa -i hw:0 -aq 1 \
 -f video4linux2 -channel 1 \
 -i /dev/video1 \
 -acodec pcm_s16le \
 -ar 44100 \
 -vcodec mjpeg \
 -qscale:v 1 \
 -pix_fmt yuvj420p \
 -r 29.97 \
 -s 768x480 \
 -aspect 4:3 \
 -filter:v yadif=0:0:0 \
 ./Vídeos/ffmpeg-capture.mjpeg.$$.avi[/FONT]

I use no-compression audio and deinterlace on-the-fly. The result is better than in Windows.

---

### Post by Perkins on 2012-02-27
I will give that a try at some point.  The major difficulty I was having stems from the capture device I am using introducing a variable offset between audio and video.  mencoder detects this offset, and reports it, but I couldn't find any options to correct it.  It's been long enough I should probably fire it up again and see if it does any better.

---

### Post by chickenPie4breakfast on 2012-02-27
I had trouble capturing form my device on Windows XP until I used Virutual Dub - fortunately the program seems to work fine under WINE - although I have only tried editing video not capturing as I no longer have a capture device.

---

