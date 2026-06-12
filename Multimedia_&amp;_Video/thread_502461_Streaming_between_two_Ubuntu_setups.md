---
title: "Streaming between two Ubuntu setups"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by stryker719 on 2007-07-16
First, I'm sorry if something similar has been posted before, but I have been unable to find anything along the lines I'm looking for.

I'm looking to be able to stream my video/audio from one Ubuntu machine to another over my wireless network.

My primary machine has all the video, whereas my secondary machine is hooked up to the living room TV.  My goal is to stream video from my primary to my secondary.  That way, I don't have to fill up the secondary's small harddrive with content.

How would I go about setting this up?  What software do I need?  Does anything particular need to be done so that I can share over my wireless network?

Thanks in advance for the help.

---

### Post by stryker719 on 2007-07-17
Bumpity bump bump.

---

### Post by alphane on 2007-07-17
If both machines are Ubuntu, then search these forums for "NFS Filesharing".

It's a breeze to set up, and it lets me browse my desktop's harddrive (3 floors up) from the living room on my laptop over the wireless network.  To stream the media down is to simply to execute the video/music file etc that you want

---

### Post by MCMcButtah on 2007-07-17
I use samba to share files between my two kubuntu machines, so I am not sure if this differs when using nfs but...

In order for my files to play over the network in the manner you described as streaming, I needed to mount the remote share to a local mount point. If say I don't mount, and just browse to the network share, then when I click on the file it downloads it locally to some temporary place, and then plays it. That way is sucky because if you want to play a movie it downloads for 10 minutes rather than just playing. Do a search on this forum for mounting your shares in fstab, its pretty easy.

---

### Post by stryker719 on 2007-07-17
So here's a question for you; is Alphane's way actual streaming (such as streaming video from the internet), or does it download to the local drive first?

I'm installing Ubuntu on my PS3, and while I just installed a 250gb harddrive, I'd still prefer to stream rather than download to the local harddrive.

---

### Post by alphane on 2007-07-18
I couldn't tell you, because I do mount my share folder from my desktop machine.  I can say that I've watched files over 1GB, and the playback is instant, and only when skipping forward or back the timeline in a movie has any kind of stuttering occured, probably because its streaming.

As long as you mount it would seem that either Samba or NFS are the way for you to go, although I've always had the impression from these forums that Samba is a little more complicated than NFS, but read up and see!

---

