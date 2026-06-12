---
title: "Hey video experts, MKV to smaller file, best way?"
date: 2010-06-12
forum: Multimedia Software
---

### Post by captainron042 on 2010-06-12
I was wondering, what is the best program/method for making an MKV file smaller. I'm all for good quality videos, but I have a movie that is 7.9 GB, which I think is a little excessive.

I even get errors when moving files over 4GB to my external HDD, saying that there is not enough memory (RAM, I guess?)

Anyway, what is the best way to get the file smaller and still have decent quality? =< 4 GB

Thanks in advance! :popcorn:

---

### Post by slash86 on 2010-06-13
Hi,

have you tried avidemux???

---

### Post by captainron042 on 2010-06-13
yeah, I've used that program to put several videos into one pretty easily, but lowering the filesize seems less intuitive. What do you do?

Also, I'm looking for advice as to the best way to make it smaller and retain most of the quality. I'm sure there's several ways to do that, and some ways are better than others.

---

### Post by no2498 on 2010-06-13
try tragtor make em mov file type


read and install all the page tell you to
[http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/](http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/)

---

### Post by captainron042 on 2010-06-13
eh...I don't know about .mov. I'd really just want to make it a 4 gb mkv. 

.mov seems to be less usable.?

What I'm really asking is what's the best way to make the filesize smaller and still retain the most quality. IE lower framerate by x amount, make the height and width smaller, ect., and how I would actually do this with a program. 

I've opened it with Avidemux, and looked around at the commands, but couldn't figure out how to do anything.

---

### Post by captainron042 on 2010-06-21
I tried Avidemux. I've got a 9.5 GB mkv, and I tried to get it down to under 4GB, but the best I could do is almost 6GB, even though I set the limits to 3.9 :/

Any help?

---

### Post by ron999 on 2010-06-21
Use **mediainfo** to find out what's in the mkv file.
It will show the codecs and bitrates used.

---

### Post by captainron042 on 2010-06-21
Looks like it's not available for 10.04.

[http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)

Can you explain how this would help make the filesize smaller? Is it best to match the codecs or something? Sorry, I'm at a loss, and I'm pretty new to anything but just watching downloaded videos :D

---

### Post by ron999 on 2010-06-21
Well if you know the picture size and aspect ratio you can consider reducing the picture size.
If you know what bitrate is used for the video track you can consider reducing it.
Maybe there's another source for mediainfo for Lucid Lynx.

---

### Post by ron999 on 2010-06-21
Yes, mediainfo is here:-[https://launchpad.net/~shiki/+archive/mediainfo?field.series_filter=lucid]("https://launchpad.net/~shiki/+archive/mediainfo?field.series_filter=lucid")

---

### Post by coskierken on 2010-06-22
Give Handbrake a shot ([www.handbrake.fr](www.handbrake.fr)).  You can do custom sizez and bitrates to get what you want.  I do believe you can shrink an MKV file and not just break the dvd itself.  I will look at this myself.  I have run into the problem you have with putting an mkv on a usb 16Gig stick.  It just hangs for some reason.  :confused:

---

### Post by vfiz on 2010-06-22
When making the file smaller, you're going to have to sacrifice quality in some respect.  I think the easiest way would be to resize to as small as you're comfortable, set a target size for the file (make sure to check 2-pass encoding), use x264, and set as many of the time-consuming, quality-enhancing options as possible.  It may take a long time for the file to encode, but it can potentially increase the quality noticeably.

Handbrake does a great job with encoding, and I'd recommend it.  The last stable release, however, won't work with Lucid.  You'll need to use their PPA (link on this page: [http://handbrake.fr/downloads.php]("http://handbrake.fr/downloads.php")).  I've used it on Lucid, and it's suddenly closed on occassion.  But overall it's worked perfectly fine.

If you're fine with resizing, then that's a good way to go.  You may also need to crop out black bars or junk data (extraneous pixels usually on top or bottom of TV MPEG streams).  Handbrake, at least, has an autocrop feature.  Crop out the junk stuff, and then resize.  Make sure that you preserve the aspect ratio, or things will looked distorted.  Lots of people use 624x352 pixels for 16:9 or 512x384 pixels for 4:3 because they yield pretty small files.  Of course, if you're watching this on an HDTV, they'll look blurry.

Target sizes have worked great for me in Handbrake, always coming within a couple of megabytes.  Just make sure to check 2-pass encoding.  By going through the video twice, it'll get a much more efficient (higher quality for video size) encode.

Next, use x264 to do the encode.  Of the codecs out there, it's the most efficient and will yield the highest quality video.  That said, it can be pretty slow to encode compared to older, less efficient codecs.  

You'll also want to make sure the sound is encoded in an efficient way.  That is, don't use AC3 pass-thru as this will send lots of audio data to the final encode.  Use AAC or MP3 to encode the one audio stream you want (there may or may not be multiple audio streams).

Finally, if you can spare the time, use as many quality-enhancing options as possible (8x8 Transform at least).  You may need to Google some of them to see what they actually are.  If you're using Handbrake, there are explanations when you hover over something.

The 4GB thing: Your external hard drive or flash drive is probably formatted with FAT32, which has a [filesize limit of 4GB]("http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32").

---

### Post by captainron042 on 2010-06-22
awesome help!, and good advice.

I'm not getting handbrake to install, though. I added the ppa through the sources, but it's not able to get the key. Not sure what I'm doing wrong.

---

### Post by captainron042 on 2010-06-22
$ sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo: unable to resolve host dell-desktop
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 43D3A9F60C58A7169778E6FB8771ADB0816950D8
gpg: requesting key 816950D8 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
george@dell-desktop:~$

---

### Post by captainron042 on 2010-06-22
I spoke too soon, it worked now.

So I now have the ppa, and did update for Handbrake and Mediainfo....that doesn't actually install the program, does it? (if it does, where is it?) what now?

(sorry), again, I'm learning.

---

### Post by vfiz on 2010-06-22
If you've got the PPA and key set up right (and it seems that you do), then just open up a terminal and update apt-get (to make sure that it loaded the new info from the PPA:
```
sudo apt-get update
```
And then install it.  There are actually two programs you'll need to install--the command-line interfact and the GUI:
```
sudo apt-get install handbrake-cli handbrake-gtk
```
And that should do it.  You can also install using Synaptic or Ubuntu Software Center.  If you want to use one of those, just open it up and search for "handbrake".  That should give you both the command line and GUI as results.  Install and go.  

Once it's installed, it should show up in your Applications > Sound & Video menu.

---

### Post by captainron042 on 2010-06-22
....encoding

Hey, thanks! We'll see how it turns out

---

