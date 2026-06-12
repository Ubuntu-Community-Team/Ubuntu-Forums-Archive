---
title: "Problems with video playback over NFS/CIFS and VOB files"
date: 2008-05-28
forum: Mythbuntu
---

### Post by jakev383 on 2008-05-28
I've ripped some of our DVDs to VOBs on a NFS share. I have a master backend with 3 tuners in it, and 2 separate front end machines.  All the Myth machines are running Mythbuntu 7.10 now, and the NFS/Samba backend is running RHEL5 with the share being on a RAID5 array.  I have the same share set up for both NFS and CIFS/SMBFS so it should hit with anything.

I have tried to mount the front ends with both of these in my fstab:

```

192.168.76.1:/videos    /media/videos   nfs     rsize=8192,wsize=8192,hard,intr,nfsvers=3,actimeo=0
//192.168.76.1/Videos   /media/videos           cifs    guest,auto,user,rw,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

``` 
(no, not both at the same time.... I tried each one separately)
Biggest problem I'm getting is when I select a video to watch (all VOB files remember) the video starts and everything looks great, but the timer will only show the video as 15 minutes long or so, even though it's actually 50 minutes long. Rewinding, fast forwarding, skipping, jumping, etc. all give horrible results - I can fast forward at up to 3X, but if I try and jump to 10X or more sometimes the video will lock up completely or it will be very jerky as it fast forwards and play audio snips during the fast forward process.  Once it reaches the timer's "end point" (15:38 on one video, different for different videos) it will jump to the last couple seconds of the show (the credits) and then end.  Rewinding is hit or miss - if we're past the display's "end point" then it will exit from the video.

This is all on a 100M network. The NFS/CIFS share is a 3G Intel with 2G of RAM and the share is a RAID5 array so spooling the video out shouldn't be a problem.  The front ends are wither a 1.2G VIA board with 1G of RAM (20G HD if it matters) or a 2.2G Celeron with 512M and a 60G HD.  The Via machine is on a 87 foot CAT5e run and the 2.2G Celeron is on a 54g wireless connecton that is about 15 feet from the access point (I get 145 feet of range from the access point, tested).

Am I mounting the drives wrong, or should I recode the videos into a more friendly format? I don't need DVD quality since they're all SD content anyway so I could recode but I don't want to get TOO horrible with the quality - as long as it looks like what I record off of my PVR150 I would be fine, no matter the format. 
I attempted to recode one of the VOB files into xvid format using the following (on the RHEL machbine):
```

nice -n 19 mencoder Pretender.vob -ovc xvid -oac mp3lame -xvidencopts bitrate=1000 -o Pretender-xvid-1000.avi

```
But the quality was pretty bad. File size dropped a LOT (which would be nice to do anyway - 2G VOB files eat a share up quickly) but the quality drove the wife up the wall.

Thanks for any suggestions or hints!

---

### Post by jakev383 on 2008-05-28
Well I tried recoding again today and got a good quality out of the xvid version - it just used the wrong audio track when it re-encoded the file. Here's the command I used:
```

nice -n 19 mencoder Episode\ 6\ -\ Past\ Sim.vob -ovc xvid -oac mp3lame -xvidencopts bitrate=2000 -o xvid-2000.avi

```
Made a nice file that was 75% smaller than the original which makes me happy. Now to just figure out the audio.... Really don't want to do a 2-pass method since if this works I would like to script a conversion script to process a whole directory.....

---

