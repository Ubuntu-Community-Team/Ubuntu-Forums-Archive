---
title: "Mythvideo no playback"
date: 2009-03-01
forum: Mythbuntu
---

### Post by travelinman81 on 2009-03-01
I am stuck been looking for days how to solve this never had the problem before on my other myth box. Anytime I try to watch a video it goes to black screen then back to title page when I tailed the .log file it says basically cannot open file and the name and location of the file. I can watch live tv, but the videos aren't working I have set all files to use the interal player (thats what I used on the other box). It will not play any file or any music but live tv works. I am using an onboard nvidia 8200 asus board sound over HDMI working, latest alsa, and latest stable Nvidia drivers 180.29 I think. Anyone have any ideas?? Anymore information you need, let me know. I am starting to get frustrated since I had the last box working fine. It is really killing the WAF I had built up with the last myth box.

---

### Post by uMuppet on 2009-03-02
Check the permissions of the videos, and can you play them with Mplayer normally?  Might even be a codec issue.

---

### Post by travelinman81 on 2009-03-02
I thought that, I can play the videos fine with totem they are in a Samba share that my user has r,rw access too, maybe for some reason mythtv user doesn't have any I will make sure to add myself to that group and check mythtv users permissions, but the fstab mounts that file with a credential file out of my root directory which lists my credentials so anyone who logs into that box should have full read write permissions on those files. I will double check those though. About it being a codec I think mythtv uses ffmpeg so it should support anything that ffmpeg does correct? It won't play anything from AVI - MKV. Thanks for the reply

---

### Post by travelinman81 on 2009-03-02
I just reformated the partition and am reinstalling 8.10 and will just start from scratch. Could be I was using the VDPAU enable svn trunk of Myth I will rebuild the latest Nvidia drivers and alsa to get my audio and video working then dive back into mythtv it shouldn't be such a pain I don't recall having so much trouble last time a I set it up and it was working beautifully but it was on my loud overclocked desktop so I built a new quiet HTPC since I liked it so well and now poof everythign is crappy.

---

### Post by travelinman81 on 2009-03-02
It still won't work, I can play videos in /var/lib/mythtv/videos but not when I change the directory to my samba share /media/Server. I can see the videos but they will not play. The same video will play even if I change the directory to /home/*username*/videos. but not from the share any ideas anyone please this was working fine on my other setup. which uses the exact same fstab entries for the samba share.

---

### Post by travelinman81 on 2009-03-02
Well I am at a complete loss it makes no sense, why can't myth deal with any of the files from my samba share. I don't know what to do everything is the same as the other mythbox now someone please anyone give me a hand here.

---

### Post by nickrout on 2009-03-02
likely to be an ownership/permissions issue.

as the user that runs mythfrontend cd into the directory the videos are mounted in and try to play one with mplayer or mythtv (yes the player can be called with mythtv filename.avi)

Or look at the mythfrontend.log when trying to play a video.

---

### Post by travelinman81 on 2009-03-03
I will paste in the contents of mythfrontend.log when I play the file to me the only relevant part is cannot play the file
```
2009-03-03 07:15:41.877 RingBuf(/media/Server/videos/TV Shows/filename.avi): Could not open /media/Server/videos/TV Shows/filename.avi.avi
```

---

### Post by utar on 2009-03-03
Try deleting the space from "TV Shows" and have you double checked that you have the capitals right?

---

### Post by eldragon on 2009-03-03
im having the same problem with one of the frontends on a gutsy install. backend running on another computer

never thought of debugging it since i plan to format that buster when i get the time. 

other frontends work fine though.

---

### Post by travelinman81 on 2009-03-03
I can view all the files so I am pretty sure I have the syntax right in the options section. I have tried changing the directory's permission to 777 and I still can't play them. How can I change the mythtv users permissions to the same as my login user?

---

### Post by travelinman81 on 2009-03-03
this is the terminal output when I try to cd into the directory and watch the video with mythtv
```
2009-03-03 09:51:39.788 Using protocol version 40
2009-03-03 09:51:39.807 TV: Attempting to change from None to WatchingPreRecorded
2009-03-03 09:51:39.807 RingBuf(/media/Server/videos/Kids/pumpkin.avi): OpenFile(/media/Server/videos/Kids/pumpkin.avi, 12)
2009-03-03 09:51:46.309 RingBuf(/media/Server/videos/Kids/pumpkin.avi): Could not open /media/Server/videos/Kids/pumpkin.avi.
2009-03-03 09:51:46.309 RingBuf(/media/Server/videos/Kids/pumpkin.avi): CalcReadAheadThresh(1111138144 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
Mutex destroy failure: Device or resource busy

```

---

### Post by nickrout on 2009-03-03
> 2009-03-03 07:15:41.877 RingBuf(/media/Server/videos/TV Shows/filename.avi): Could not open /media/Server/videos/TV Shows/filename.avi.avi

the obvious error is filename.avi.avi , ie .avi is repeated. I am not sure why.

What is the actual filename?

What happens when you use mplayer as your video player?

when logged in as [user that runs mythfrontend] can you open the file? Try 

head filename

or

ffmpeg -i filename

seeing the filename in a listing is not enough, that involves a different permission to opening (ie playing) the file.

Also how about a ls -l of the filename and a ls -ld of the directory it is in?

---

### Post by travelinman81 on 2009-03-03
I got it figured out now I added a mythtv user to my server and to samba and mounted the share as that user now everything is fine thanks to my over the top secure samba use. Thanks for all the help.

---

