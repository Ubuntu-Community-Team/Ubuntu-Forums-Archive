---
title: "Photos load, videos don't"
date: 2011-01-05
forum: Multimedia Software
---

### Post by mmcl on 2011-01-05
(Not too tech savvy here.) With Ubuntu 10.04.1, I'm trying to download a mix of photos and videos from my little Panasonic camera.  When I download, F spot comes on and downloads, but I can't play the videos; can only look at the photos.  Should I look for some other software? If so, please tell me how to go about it.  

Thanks,

Martha

---

### Post by dodo3773 on 2011-01-05
> **mmcl said:**
> (Not too tech savvy here.) With Ubuntu 10.04.1, I'm trying to download a mix of photos and videos from my little Panasonic camera.  When I download, F spot comes on and downloads, but I can't play the videos; can only look at the photos.  Should I look for some other software? If so, please tell me how to go about it.  

Thanks,

Martha
 
Are you sure you have all the proper codecs installed? That would be my first guess since you can view pictures and not videos. Do you know what kind of file it is? For example you may have a video called 
  
myvideo.mp4    

or something like 

myvideo.avi

Well the mp4 after the dot is the type of file it is. So  "myvideo.mp4"  is an mp4 file. Also, myvideo.avi is what is called an avi file. It is that simple. The ".mp4" is what is called a file extension. So what is the file extension of the file you are trying to open?

---

### Post by no2498 on 2011-01-05
close f spot
click open the icon/cam
find the video's you can click to play or drag 1 to the folder you like
or load them to the desk top

---

### Post by mmcl on 2011-01-06
Thanks much.  I don't have time tonight; will try again and use your suggestions tomorrow.

Martha

---

### Post by azertyh on 2011-01-06
hello,
i have the same problem. xubuntu 10.10, shotwell, and a canon camera.
shotwell loaded the photos, but the videos can't be imported.
and the camera can't be mounted.

---

### Post by mmcl on 2011-01-07
That's a bit comforting that azertyh has the same issue.  Weirdly, when I first updated to 10.4.01, about 12 weeks ago, I was able to view the videos. However, I had done something wrong and there was no more memory left on my computer. So, I re-installed the operating system.  Since then, everything has been hunky dory, except that now the videos won't play.

Back to the matter at hand: 

In answer to dodo 3773, I've no idea about codecs. However, it is clear that all the photos, whether connected to videos or not, have a jpg file extension. Even I know that that's not a video. I'm not sure how to go about finding and loading codecs.

In answer to no2498, I don't understand the instruction, "click on the icon/cam."

Suggestions, please?

Martha

---

### Post by BicyclerBoy on 2011-01-08
The newer video format on digital cameras is commonly AVCHD or MP4.

Basically just mpeg-2-ts container with MPEG-4/10 H264 video & AAC audio.

VLC plays this no problem.

---

### Post by azertyh on 2011-01-08
> **BicyclerBoy said:**
> The newer video format on digital cameras is commonly AVCHD or MP4.

Basically just mpeg-2-ts container with MPEG-4/10 H264 video & AAC audio.

VLC plays this no problem.

the problem is not playing these videos but loading/importing them from the camera to the hard disk.
i think it's detecting and mounting issue.

---

### Post by BicyclerBoy on 2011-01-08
Yes you may be right..

My digital photo camera very occasionally does not mount on the netbook 10.10 .

I think the auto action may stuff up the mounting..

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Configuring auto-mount section & gconf-editor may be a fix..

---

