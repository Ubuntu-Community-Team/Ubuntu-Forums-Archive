---
title: "ubuntu and mythTV"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by BikerGeek on 2007-02-16
I have few questions I hope y'all will be willing to answer and I hope they're not too long-winded, I'm a geek for a living and fully believe that the more info I have to go on the better. <g> My past experience with linux is on Slackware, Redhat and Mandrake and the latest foray was several years ago, I've even been forced to remove all linux DNS servers at work so I'm way outta the loop. But ask me something about AD or smartcard login ok?<g>

I occassionally record tv shows so I've been reading up on mythTV. I'd already completed my install when I came across the ubuntu mythTV install guides and being that this install was exploratory anyway, I let the install do the partitioning originally.

The combined frontend, backend, regular desktop guide, [**Front, back, desktop**]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop"), mentions creating a partition with the xfs file system. It also confuses me a bit in that it mentions a 10GB partition but I don't see one in their graphic and it says the xfs partition should be the biggest one, I assume since it was created last from the remaining freespace. 

Also, I mistakenly did the combined frontend backend install (minues a fresh install) so I may have permissions or something set incorrectly for the one I really want, I haven't compared the two guides yet to note any differences. But I WAS able to successfully capture and view with...ummmm...mplayer I think it was, I forgot what the guide gives as the example, but I had both audio and video.

Anyway, my questions are:

1) Is mythTV the ONLY TV watching/recording solution or just the BEST one? I'm assuming I could still use xine or mplayer to watch? It's durn complicated and if it breaks I need to be able to walk my wife through fixing it because Murphy states that it'll break when I'm working late and missing Heroes or Battlestar. Is there another, simpler, program I could use for occassional recording? Something as easy as the Hauppauge Windows software? Sometimes on a timer, sometimes not. Since I have a PVR150 and have become accustomed to using it under Windows I'd like to continue using its hardware encoder.

1a)Does the Hauppage software work under wine or vmware or anything? Never mind, I guess I could get off my duff and go look that one up myself I reckon.

2) Should I/Do I really need to backup and punt and just do a totally fresh install following the Frontend backend desktop guide? Would that be easiest and most likely to work or is there a way to undo what I may have done already and make any needed changes as it looks like I already have most if not all of the needed modules installed. I don't have data replaced yet, only thing I've really done is configure the Radeon 9500 and add support for the non-opensource formats, so I'm ok with starting over if that's the best option. 

3) This partitioning thing...I have a 120GB and a 300GB drive. In Windows the 120 is my combined boot/system drive and the 300 is just for storage, I generally install all apps to the 120 too. Do I NEED that xfs file system? If I reinstall I'll certainly add it anyway since the guide says to. How should I partition with the above mentioned drives?

Thanks for the help y'all, hope I can return the favor as time goes on.

---

### Post by pelago on 2007-02-16
MythTV is a 'big' system that takes some time to get into. There's an alternative called VDR which you might also want to look at. I'm not sure if there's a small/light program just for occasional recording.

---

### Post by majoridiot on 2007-02-17
mythtv can be a little intimidating, but the documentation is improving daily.  the one drawback
with a complicated and robust package like mythtv, is that there is a LOT of packaging and 
documentation that needs to be written for free. :D

i LOVE my myth setup and i'm new to linux.  sadly, i haven't had time to play with all of the
plugins or mythweb- but i wouldn't give it up for anything.

you point out a needed addition to the wiki- what to do if you just want it on your regular pc.

the 10GB partition is for the main "root" partition, and is so small because the wiki is currently
geared to setting up a pretty-much dedicated myth box.  if i understand what you would like-
a regular pc with desktop and frontend with video storage on a second drive, then you can 
set it up something like..

do:

```
more /etc/fstab
```

to check out the mount points of your drives

we will assume (fill in your specifics) your second drive is mounted at /media/drive2 with
correct permissions for your regular user to read/write...

make a video directory on that drive for your mythtv video storage:

```
mkdir /media/drive2/video 
```

then start at the "Setup NTP" stage of the guide and work forward.  

at step 4 of Install MythTV (" **VERY IMPORTANT** "), *before* logging out, you need
to give mythtv permission to access the video storage.  be sure to wait until now, as the
mythtv user acount is not created until the packages are installed.  the command is:

```
sudo chown mythtv:mythv /media/drive2/video
```

continue with the guide.  when you run mythtv-setup, on page 2 of "General Setup", you
want to enter the mount point of the second drive- in the example here:

```
/media/drive2/video
```

the rest goes as written.

good luck! :D

**EDIT:** i forgot to address the filesystem question.  honestly, i don't know why the guide
has video storage in an xfs file system, unless there's a speed advantage(?).  from experience,
i know that ext3 filesysems are just fine, if that's how your drive is formatted.  as long as you
can read/write to the drive normally, the filesystem shouldn't (in theory) matter, so go ahead
and try it.  at worst, you will get jittery playback and know what filesystem *not* to use. ;)

---

### Post by BikerGeek on 2007-02-17
Hey man, thanks for the help, that makes it a little clearer.

I think I have it installed correctly, I actually had a picture for about 2 seconds. <G> Do seem to be having an issue pulling down the info for the channel list, think it's an issue with the host site though, the lab.zap2it whatever it was site. Can't seem to scan for any channels either way.

But neither xawtv nor TVTime work either so I'm not sure if I have a problem with my ati driver or something else. I was originally using the fglrx driver now I'm trying the open source to see if I have better results. So far that's a big fat NO. <G>

---

### Post by majoridiot on 2007-02-17
yeah, the listings (for the US) is labs.zap2it.com-

if you were trying setup last night, it was down.  it seems to be back up and running ok now.
just make sure to go there, set up an acount and configure a channel profile beore setting up
myth, otherwise you have to go back and add channels later.

---

### Post by drifting on 2007-03-31
Whoo hooo...spent all day today working on my Myth box, apart from the odd hang the live TV and recordings work.

Sadly i have not got to the remote control part yet as I have just found out the TV card (Nova-T 500) remote is not supported, unless anyone knows different?

With the above in mind, and my quick browse of the Myth manual, it would appear that I cannot call up the program guide, I press the "m" key up pops a menu, but pressing enter does not do anything? All teh tv listing data has downloaded successfully.

Any ideas? 

Paul.

---

### Post by majoridiot on 2007-03-31
will the guide come up if you press S whilst watching livetv?

---

### Post by drifting on 2007-04-01
Yes it does, well I never, think it was just a bit slow and I was not being patient. All I have to do now is work out why it hangs going back to the menu after watching live TV.

Thanks

Paul.

---

