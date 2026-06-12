---
title: "Linux-friendly Camcorder?"
date: 2007-06-22
forum: Multimedia Production
---

### Post by jTHEn on 2007-06-22
I'm looking to buy a new camcorder. It seems likely that I will get one that records directly to DVD, but will I be able to transfer the video from the DVD to my computer for editing without too much hassle? Is there a better way?

Furthermore, is there any particular video camera that you folks recommend? (For Linux friendliness or otherwise)

Thanks :???:

---

### Post by kelvin spratt on 2007-06-22
check out the sanyo xacti records hd up to 60fps  onto SD cards i use this and although being the size of a cig packet delivers excellent results and the 10 meg pixal still cam with 35-180 lens and advanced features make it ideal its only let down is flash but anti shake makes low light shooting exceptionally natural,  we went to south America this year the results were spectacular and being so small very safe to carry in your pocket,.+ Linux supports the file format they play raw in all but totem player

---

### Post by Palmyra on 2008-02-02
> **kelvin spratt said:**
> check out the sanyo xacti records hd up to 60fps  onto SD cards i use this and although being the size of a cig packet delivers excellent results and the 10 meg pixal still cam with 35-180 lens and advanced features make it ideal its only let down is flash but anti shake makes low light shooting exceptionally natural,  we went to south America this year the results were spectacular and being so small very safe to carry in your pocket,.+ Linux supports the file format they play raw in all but totem player

Sanyo Xacti is likely good if you can afford it!  Pretty expensive, but then again, it's high definition.

---

### Post by cotcot on 2008-02-03
I do not think that the camcorder make is an issue for linux. You do not need to install any camcorder specific softare to get it on linux as long as the media it uses is readable in linux. I even have a canon camcorder connected and this supplier is not linux friendly.

---

### Post by Delkster on 2008-02-03
If you plan on connecting the camcorder itself to the computer, I believe most camcorders use a standard firewire (more technically known as IEEE 1394) connection. Pretty much any video editing software is compatible with the standard of transferring video over IEEE 1394.

I guess it's possible that some manufacturers, against all reason, insist on using some kind of a properietary protocol which only their (probably Windows-based) software is compatible with, but I'm not aware of such cases.

On the other hand, if you use some kind of an intermediate medium (a memory card, a DVD, or something else than connecting the camera itself to the computer), I don't know about that. I don't suppose there should be problems with that as long as the medium itself is some kind of a standard and you have a way of reading that kind of media with your Linux system (as is the case with SD memory cards, DVDs, etc.). Of course the files on that media might also be in some kind of a proprietary format even if you can read the media itself, but that sounds a little far-fetched.

---

### Post by linuxcompulsive on 2008-02-04
Hi all,
I have the Xacti HD1000. This cam records in FullHD over SD card. I have not problems on upload files from my ubuntu PC with the usb 2.0 cable or the SD card reader.

But, when I play the videos I can't see them well. The high resolution with the avc x264 codec of the xacti don't runs over linux. 

In windows, i can edit it with vegas or ulead without problems.

I tested all kind of codec packs, software like cinelerra, kdenlive, lives, kino... and all the players of the world... At this moment I haven't the solution.

linuxcompulsive
[http://www.moner.cat]("http://www.moner.cat")

---

### Post by Cresho on 2008-07-20
The sanyo xacti hd1000 is not a problem for ubuntu.  I am currently using xbmc to view the 720p 60fps and the 1080i30fps in ubuntu just fine.  I also am able to edit the videos and convert the videos just fine.

my 1080i files can be converted in many ways such as

1. 1080i 60fps to 1080p 120fps(and yes this produces fluid motion from choppy motion)

2. 1080i to 1080p with deinterlace using bob in 3 versions
a. blend fields together (film look)
b. dublicate first line (sharp look)
c. dublicate second line (sharp look)

I use virtualdub, MP4Cam2AVI_v2.71, xvid (for encoding) codec under wine.  These are open source or free softwares.  Virtualdub is way powerful. ffdshow_beta5_rev2033_20080705_clsid for decoding the high def content.

If you guys are interested, pm me and ill give you my current workflow.  I Found that this is the best way to convert to 1080p as well as downsizing it to dvd quality.  The DVD quality simply looks just amazing almost hd quality.  I currently downsized a few videos and they look way better than anything I have ever recorded on a regular video camera.


So ubuntu has no problems

the proprietary high definition format of the mp4 can be converted to avi xvid and mp3 audio.  these files can easily be played under totem.  You can add sharpness to increase the visual.  There are tons of filters which you can use to improve the image quality of these mp4 files.  I currently use interlieave "blend" and sharpness "max" with xvid high definition setting.  both quality and data rate maxed.

---

