---
title: "How I Converted YouTube Video To DVD Movie"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2007-09-02
Here's how I learned from various sources to convert a YouTube video to a DVD movie. Note that I may have more steps below than you need and I'm sorry about that. You all can reply if you don't think a step is necessary.

**GET YOUR BROWSER TO SUPPORT FLASH**
First, point your browser to YouTube and when it prompts to install Flash, do
so.

**EDIT YOUR APT SOURCES LIST**
As root, using your favorite text file editor, edit /etc/apt/sources.list and 
add these lines:

```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

**ADD A GPG KEY**
```
sudo su
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key \
add -
exit
```

**UPDATE WITH NEW APT SOURCE**
```
sudo su
apt-get update
exit
```

**INSTALL EXTRA VIDEO CONVERSION STUFF**
Note that some of the following items might be things you already have and it will skip those.

```
sudo su
apt-get install libdvdcss2 w32codecs mplayer ffmpeg lame mpg123 ecasound
apt-get install mencoder dvdauthor dvd+rw-tools
exit
```
[B]
COMMENT OUT NEW ITEM IN APT SOURCES LIST[/B]
As root, using your text editor, comment out with a # those two lines for
Medibuntu that you just added in /etc/apt/sources.list. Then, do:

```
sudo su
apt-get update
exit
```

**GET THE FLV FILE**
The next step is to get the FLV flash video file. YouTube has changed this 
technique recently, and may change it again, but there are various video sites
on the web like at Tech Crunch that can help you get the FLV file. (Note to 
myself -- update my Bash script I have that permits one to download the FLV
file now that YouTube has changed their playback sequence.)

**CONVERT FLV TO MPG FORMAT**
Once you have the FLV file, you need to convert to MPG format like so:

```
sudo su
ffmpeg -i input.flv -ab 56 -ar 22050 -b 500 -s 320×240 output.mpg
exit
```

(Rename output.mpg to input.mpg because we need to convert it in the next step.)

**CHECK IF MPG FORMAT IS THE PROPER KIND FOR DVD MOVIE**
Now that you have your FLV flash video in MPG format, you might not have it in 
the proper AC3 audio format that's required by a DVD movie. Check that by doing 
the following and seeing if it reports AC3.

```
sudo su
mplayer -vo dummy -ao dummy -identify input.mpg 2>&1 | grep \
AUDIO_FORMAT | cut -d '=' -f 2
exit
```

If it doesn't return 'hwac3' and says something else EXCEPT A NUMBER, then you 
need to run something like the following. HOWEVER, if it returns a number, try
this command instead:

```
sudo su
mplayer -vo dummy -ao dummy -identify input.mpg 2>&1 | grep \
AUDIO_CODEC | cut -d '=' -f 2
exit
```

Note that if you don't have about 2 GB free on your drive, you might not have 
the drive space to run the following conversion for an hour and a half video. 
It's also going to take about 30 minutes to run this.

```
sudo su
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf \
scale=720:480,harddup -srate 48000 -af lavcresample=48000 -lavcopts \
vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:\
keyint=18:aspect=4/3:acodec=ac3:abitrate=192 -ofps 30000/1001 -o output.mpg \
input.mpg
exit
```

For the international way, it would be, instead:

```
sudo su
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:576,\
harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:\
vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:aspect=16/9:\
acodec=ac3:abitrate=192 -ofps 25 -o output.mpg input.mpg
exit
```

**CREATE YOUR MOVIE CHAPTERS FILE**
Now you have a proper MPEG-2 file with the proper AC3 audio format required for 
DVD movies. If you didn't need to do the conversion, use the file you generated
after the ffmpeg conversion.

The next step is to create your Movie Chapter File. The following is a sample 
that you can edit and save as 'dvd.xml'. In my case I made an hour long video 
and split it up into 10 minute chapters.

```
<dvdauthor>
  <vmgm />
    <titleset>
      <titles>
        <pgc>
		<vob file="output.mpg" chapters="0,10:00,20:00,30:00,40:00,50:00" />
        </pgc>
      </titles>
    </titleset>
</dvdauthor>
```

For more info on this XML file, look for the 'dvdauthor' docs on the web. It
can show you more elaborate things you can do than this.

**PROCESS YOUR MOVIE CHAPTERS FILE**
Now we're ready for processing this with this command:

```
sudo su
dvdauthor -o dvd -x dvd.xml
exit
```

It takes a few minutes to run this. This creates a directory 'dvd'.

**TEST YOUR MOVIE BEFORE BURNING TO DVD**
Your movie directory 'dvd' can now be tested before burning to DVD:

```
sudo su
mplayer dvd:// -dvd-device ./dvd
exit
```

If you see the first few seconds of video and hear sound, fantastic -- you're
almost there. You can close that window.

**BURN DVD FOLDER TO DVD**
Now you can burn your 'dvd' folder to your DVD. Just insert a real video DVD 
that's designed for video. Note it might be listed as DVDRW or something like 
that, but just make certain you see 'video' listed on it. When you insert this
DVD, if your Linux asks you to make a DVDRW or something, click Cancel and 
close any Nautilus or Konqureror windows that might be pointing to it. Now run:

```
sudo su
growisofs -dvd-compat -Z /dev/dvdrw -dvd-video ./dvd/
exit
```

Note the ending / on the './dvd/' is important.

It should take a good bit of time to run this, so be patient.

When done, if you have a DVD icon on your desktop, right-click it and choose to
eject it.

You're now ready to play your new DVD movie!

---

### Post by FRuMMaGe on 2007-09-05
A much better way to get the video from youtube is to simply wait until the video is fully loaded.  Now (before you close your browser), navigate to your "tmp" directory.  The flv file is here for you to drag onto your desktop.

It's far simpler.

---

### Post by SuperMike on 2007-09-05
> **FRuMMaGe said:**
> A much better way to get the video from youtube is to simply wait until the video is fully loaded.  Now (before you close your browser), navigate to your "tmp" directory.  The flv file is here for you to drag onto your desktop.

It's far simpler.

Okay, and then what? Run some command-line commands to convert to simulated stereo MP3? Wouldn't it be great, if you're going to run a command-line command, to run them all in one step? And, I had managed to build a XULRunner GUI that interfaced with that Bash command (so that it was prettier). The yt2mp3 project at code.google.com was all about that.

This worked, until YouTube changed the way they deliver the FLV. Now I have to refigure out that way.

---

### Post by FRuMMaGe on 2007-09-06
Cool.  I just use WinFF to convert all my videos.

---

