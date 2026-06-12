---
title: "How to capture and convert DV to MPEG on the fly without editing"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by coolcar on 2007-12-26
Hi,

I have a firewire 1394 setup going using Kino on my Gutsy 7.10. I had to change permissions using chmod 777 of file /dev/raw1394 to get Kino connected to my Sony DCR TRV25E handycam.  I have been doing the home DVD creation on this camera on my Windows partition using ULead video studio upto now. 

Now that  I have the setup going I wish to capture the video directly to MPEG and then create a DVD.

How do I do that without having to capture the raw dv and then export to MPEG. I am hoping this will save time as my hardware is pretty basic and I am only doing home dvd !

Sorry if all this is explained in Kino guide but this is my first attempt at Kino and I have not read the user guide. Thought I will ask the question. I did a quick check of the forums and have not found a thread. 

Thanks and Regards :)

---

### Post by theacoustician on 2007-12-26
> **coolcar said:**
> Hi,

I have a firewire 1394 setup going using Kino on my Gutsy 7.10. I had to change permissions using chmod 777 of file /dev/raw1394 to get Kino connected to my Sony DCR TRV25E handycam.  I have been doing the home DVD creation on this camera on my Windows partition using ULead video studio upto now. 

Now that  I have the setup going I wish to capture the video directly to MPEG and then create a DVD.

How do I do that without having to capture the raw dv and then export to MPEG. I am hoping this will save time as my hardware is pretty basic and I am only doing home dvd !

Sorry if all this is explained in Kino guide but this is my first attempt at Kino and I have not read the user guide. Thought I will ask the question. I did a quick check of the forums and have not found a thread. 

Thanks and Regards :)There's really no way to do what you're asking within Kino in one step.  Unless the video is already edited, you'll want to capture to DV anyways, edit it, then compress to MPEG2 before burning a DVD.  Compressing first, then editing doesn't make for a  very good DVD, even if its just home movies.

If you really want to have one command line do it all, here it is.
Install dvgrab 3.1 (3.0 doesn't work for this) and pipe the output of the file to VLC.  Start streaming the video from your camcorder to the 1394 port and run something like :

dvgrab --format dv2 --timestamp  - | vlc  - :demux=rawdv --no-sub-autodetect-file ":sout=#transcode{vcodec=mp2v,vb=4096,scale=1,acodec=a52,ab=128,channels=2}:duplicate{dst=display,dst=std{access=file,mux=file,dst="/home/videocapturefolder/capturedvideo.mpg"}}"  --sout-ffmpeg-strict-rc

-Couple of notes on what you're doing here-
1. The dvgrab portion here is capturing the video from the 1394 port and writing the file to the hdd.  The files are saved in the location where you executed the command and will be sequentially tagged with timestamps.

2. You're piping the video to VLC and forcing VLC to accept the video its being given is rawdv.

3. sout is transcoding the video into MPEG2 for you.  Adjust the bitrates as desired, but those should work well.

4. At dst, you're displaying the video as its transcoding and writing the file to /home/videocapturefolder/capturedvideo.mpg simulateously.  The displayed video may not show as 29.97 fps or whatever the framerate of your camera is, but it is transcoding properly.  Obviously set the folder and file name to whatever is appropriate to you.  You can erase the dst=display if you don't want to watch the video as its captured. 

5. You need to make sure you keep --sout-ffmpeg-strict-rc on there or else the VBR of the resultant mpeg file may be outside of DVD spec.

6. If you have the basic computer as you say, there may not be enough horsepower to pull this off.  That and you're still capturing to DV first, so you'll have to delete the resultant .avi files.

---

### Post by coolcar on 2007-12-27
Oh wow thanks a lot for the detailed information :KS


 Well I have a Pentium 4 laptop with about 30 GB available on the linux partition.  I guess let me first get used to Kino to see how the system is performing before trying out the single line grab and compress command. 

I will note your tips.

Thanks Again.

---

