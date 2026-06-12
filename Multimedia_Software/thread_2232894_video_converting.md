---
title: "video converting"
date: 2014-07-04
forum: Multimedia Software
---

### Post by Stan% on 2014-07-04
Brothers and Sisters, 

I know little to nothing about video files. If you know of any teaching websites please list.

I have several video files on the hard drive that I`m trying to put on DVD-Rs.

The files are marked...... hdtv.x264-immerse.mkv. .......hdtv.x264-orenji.mkv ........hdtv.x264-ctu.mkv.

My DVD player plays mpeg files.

I have installed gstreamer extras and I have WinFF, VLC, and Handbreak.

How do I get these files on DVDs?

---

### Post by deadflowr on 2014-07-05
Thread moved to Multimedia and Video

---

### Post by squakie on 2014-07-05
Haven't used it in a while, but try OpenShot.  If you don't have the package manager installed, do this:

sudo apt-get install synaptic <press enter>

Enter your normal userid and password - nothing is echoed as you enter your password - and press enter after each.

Now, with the package manager installed, you can now find Synaptic Package Manager in the menus - open it.

Try adding one of your files, then set the output file type to what you want and see if it converts it for you.

---

### Post by coldraven on 2014-07-05
I'm not a video expert but VLC will convert to MP4. Go File>Convert and choose an input file and a destination file (make a new name like test01.mp4).
Click on the Covertn/Save button and then choose the Profile that ends with (MP4).
It might work but it's best to check with a DVD before you convert them all.
Handbrake will probably do similar but it is too complicated for me to explain and I have not used it for a while.
WinFF is fairly easy so give that a try as well.

Edit: I just looked at the Arista Transcoder web-site and the pre-set they show for DVDs is either DivX or MPEG2.
So maybe my advice above is no use :(
Have a look here: [http://transcoder.org/presets/index.html](http://transcoder.org/presets/index.html)

---

### Post by SeijiSensei on 2014-07-05
Many DVD players can handle DivX and its open cousin XviD.  I've played XviD-encoded files in the AVI container on such a DVD player.

MPEG2 is the standard used on DVDs.

OP, one other program you might try is [DeVeDe]("http://www.devede.org/") which can create a standard DVD from video files.  I haven't tried it for a while and had mixed success with it in the past, but it's free and in the Ubuntu repositories.  I've also used a commercial program for Windows called [Convert X to DVD](http://www.vso-software.fr/products/convert_x_to_dvd/).  It's very easy to use and handles all sorts of input files.  As a test I converted an H.264 720p video with AAC audio and subtitles to the DVD format.

---

### Post by TheFu on 2014-07-05
DVD players handles MPEG2/VOB files.  The fiels you have are likely h.264/MKV and will need to be transcoded AND likely resolution changed to 480p (max of DVD).  Further, real DVDs have a specific directory and filename layout. 
This will be a 2-stage effort.  Transcode, author.

**ffmpeg** can transcode and fix the resolution to the correct type necessary for a DVD.  I haven't authored a DVD since around 2002, but there are many tools that do it when the correct input video files are provided. Search for those in synaptic. Something like: 
> $ ffmpeg -i myfile.avi -target dvd /tmp/vcd.mpg
The man page has more examples.

Oh - if ffmpeg isn't in the repos, use **avconv**. Both are related (borhters) and have a DVD setting for the transcoding necessary.

BTW - google found this: [https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring) which is where I'd start.

Plus the captions/subtitles in an MKV container can be many different formats, while DVD subtitles are limited.

Going to DVD might be good for childrens films, but I've found that having a media player device with a USB HDD is much easier.  Going to DVD is expanding the storage needed 4x. With xvid/avi, h.264/mkv encoding, it is possible to have 4 movies per DVD. mpeg2 is much less efficient with storage.  I'd keep the mkv files and spend $50 on a player, if this were my issue.

---

### Post by SeijiSensei on 2014-07-05
> **TheFu said:**
> Further, real DVDs have a specific directory and filename layout. 
This will be a 2-stage effort.  Transcode, author.

DeVeDe and Convert X both do that.

> I'd keep the mkv files and spend $50 on a player, if this were my issue.

I just play them over the network from my NFS server on my Linux client connected to the TV with HDMI.  These days I mostly use DVDs to burn Linux distributions!

---

