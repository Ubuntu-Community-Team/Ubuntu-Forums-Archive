---
title: "AVIDEMUX producing washed out mpg from avi. HELP!"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by aonegodman on 2008-01-08
I've been trying out avidemux and I've just about got it figured out.

I used it to convert an avi to DVD mpg. Followed several online tutorials and waited the 4 hours or more for it to do its "thang". DONE!

Upon checking the output file "mpg" by double clicking, Totem opens up and loads the mpg.

Sound quality is good and sync is good, but the video looks "washed out" almost white.  :confused:

What adjustments do I need?  Have you experienced this problem?

All help and comments appreciated on this.  Thanks.

---

### Post by aonegodman on 2008-01-08
):P   Ok I found the problem.

But I don't know what caused it. The driver for my Nvidia MX440 had evidently shut down or was turned off by Avidemux during the conversion process.

I found this by deciding to d/l another small size .avi  file and check it.  Upon loading into Media Player I had the same "washed out" playback.

Coming from Windows I said ok lets reboot and see if that don't reset some issues.

Upon reboot my start up screen was ok but I was unable to reset appearance preferences.

Ubuntu came up and told me I had to reinstall driver for my Nvidia card before changes could be made and asked me if I wanted to do that. I said yes, it said you will have to reboot for changes to take effect.

I rebooted. Correct screen config came back up.

I went back to video file I had previously converted from avi to DVD mpg in Avidemux. Clicked it up.

Loaded into MPlayer and all is well.  Now onto DVDauthor for menu setup and the burn.


Before I close this post, perhaps others may wish to comment on this experience.

Is this a bug in Ubuntu?  A bug in Avidemux?  or an Nvidia driver problem?

Thanks!

---

### Post by yabbies on 2008-01-08
just to let you know tovid can transcode in a 1/4 of the time, plus make your own menus with todisc and burn.

---

### Post by aonegodman on 2008-01-10
I DO want to know since I failed to produce a playable DVD for the third time in a row.

Avidemux seemed to have done the transcode correctly and sound was in sync.

I went ahead and used DVDstyler to create basic menu and make an ISO file.

Next I used K3d to burn the ISO to a DVD-R.

Placed it in my home  DVD Player and " Disk appears to be damaged or unplayable!"

Took it back to my computer and stuck it in DVD-Rom and it started up ok, but I didn't play all the way and as I tried to fast forward it seemed to loose sync.

So I haven't got this figured out yet. Needless to say coming from Windows XP and having used all the endless " copy and burn" and "crack" software out there down to an art, I am a little frustrated. :confused:

I will try tovid next.

---

### Post by yabbies on 2008-01-10
good luck with tovid, I've never had a problem with it
 don't hesitate to ask if you need any help.

---

### Post by aonegodman on 2008-01-11
Update . . .    Ok I finally found tovid and after creating a "broken pipe" in my Package Manager and figuring out I had to go in there and individually remove some stubborn library files I got it installed.

Note: Package Manager requires the removal of several other programs prior to installation of tovid, at least on my Gutsy 7.10 destro( i.e avidemux, lives). I wanted to try "lives" to.

Anyway, the file I found and got to install was  "tovid_0.31-1~getdab1_all.deb" located at  [http://www.getdeb.net/](http://www.getdeb.net/)  look for it under the Fiesty files. I could not find one for Gutsy.

I opened tovid and followed several online guides to load my avi movie file. It ran and transcoded the file. It failed at the very end due to the inability to execute a "makexml" command. Working on this - however it did make an mpg file at /tmp/filename.mpg.

I went ahead and ran todiskGUI to add menus and chapters and prep for DVD burn.

todiskGUI made a new folder with AUDIO_TS and VIDEO_TS.

Next I used K3D to create a new DVD project. Dropped both above files in the project and burned my DVD.  It played in my home DVD player.

Now I had a few problems with the finished DVD. 1) audio was not in sync with video.
It lagged by about 10 to 15 sec.

2) Few spots depixilized in the video.

3) I didn't find that it worked in 1/4 the time as avidemux, perhaps a little faster.

That's my progress so far. Thanks!

---

