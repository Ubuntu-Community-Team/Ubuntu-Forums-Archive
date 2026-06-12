---
title: "Distributed Environment"
date: 2008-06-06
forum: Mythbuntu
---

### Post by cburling on 2008-06-06
I am setting up a new Mythbuntu environment and want to break it down into several components.  I have a frontend/master backend which will be installed inmy viewing area.  This device is working great and has my PVR150 in it attached to a directTV satellite receiver.  That part works great as I said.  

I have brought up a secondary backend/frontend which only has Mythmusic installed on it.  I use the frontend just for burning cds to its 300GB hard disk.  The secondarty backend connects to themaster fine and when I use Mythweb off of the master, I can see the music.  But on the front, when I look at the media library for music, there is none.  I am hoping someone has run into this before and can comment on it.  I have searched the forums and can't seem to find an answer.

Once this is working, my plans are to build another secondary baclend server which will have a lot of disk and start buring my dvds to it.

Thanks in advance for any pointers or assistance.

---

### Post by tgm4883 on 2008-06-06
> **cburling said:**
> I am setting up a new Mythbuntu environment and want to break it down into several components.  I have a frontend/master backend which will be installed inmy viewing area.  This device is working great and has my PVR150 in it attached to a directTV satellite receiver.  That part works great as I said.  

I have brought up a secondary backend/frontend which only has Mythmusic installed on it.  I use the frontend just for burning cds to its 300GB hard disk.  The secondarty backend connects to themaster fine and when I use Mythweb off of the master, I can see the music.  But on the front, when I look at the media library for music, there is none.  I am hoping someone has run into this before and can comment on it.  I have searched the forums and can't seem to find an answer.

Once this is working, my plans are to build another secondary baclend server which will have a lot of disk and start buring my dvds to it.

Thanks in advance for any pointers or assistance.

Currenty Media (Music, Videos, Pictures) are not shared via the MythTV protocol.  You will need to manually share them via NFS or CIFS.  Be sure to mount them in the same location on each computer

---

### Post by uopjohnson on 2008-06-06
> **tgm4883 said:**
> Currenty Media (Music, Videos, Pictures) are not shared via the MythTV protocol.  You will need to manually share them via NFS or CIFS.  Be sure to mount them in the same location on each computer
Yes.  Myth gets very confused it you mount things in differnt places on ddifferent frontends.  I have my multisytem setup so that each frontend has 
/stroage
/stroage/music
/stroage/video

I actually have music and videos on a an nas so they have to get mounted on every machine.

---

### Post by cburling on 2008-06-06
Ok.  Thanks for the input.  My guess is that I will share just the /storage/music onthe music server and mount it to /staroage/music on the frontend/master backend.  Thinking that through then, I will not need to actually have the slave backend be a Mythbuntu box, since it is only going to be a disk server.  I can just go with my standard ubuntu distro for that server.

Thanks again for the help.

---

