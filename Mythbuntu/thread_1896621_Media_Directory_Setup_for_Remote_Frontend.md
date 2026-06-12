---
title: "Media Directory Setup for Remote Frontend"
date: 2011-12-17
forum: Mythbuntu
---

### Post by MickSulley on 2011-12-17
I now have my Myth box (front and back ends in one box) up and running and I have also installed the front end on my desktop and I can watch and record TV from there, that works fine. 

How do I setup the media library directories so that I can access then on my desktop?  Currently it just looks at the local directories rather that the backend.

I have SSH setup so I can see the backend box for normal Nautilus file operations but cannot figure out the correct format for the setup in Myth.

Thanks
Mick

---

### Post by williammanda on 2011-12-17
If you are referring to accessing your media files via some other media program ie vlc, then I can tell you how I do it. If this is correct then post and i will give details. If not and you are trying to access the media files in Mythtv, then you need to make sure that storage group is setup.

---

### Post by MickSulley on 2011-12-17
Sorry, let me clarify.  I have MythTV front and back ends setup on one box with pictures, music etc on that box, that all works fine.

I have installed MythTV frontend on my desktop.  That works fine for watching and recording TV but for pictures and music it looks at its own local disks not at the backend on the other box as I expected.  I have tried to alter the directory in Setup > Media Setup > Music Settings, but I cannot find a way to point it to anything other than local directories.

After the earlier reply I did look at Storage Groups and created one for music, but I don't see how that can help.  Am I missing something here?

Thanks 
Mick

---

### Post by williammanda on 2011-12-17
OK thanks for the clearer picture of your problem. Concerning pictures and music, I'm almost sure that storage groups doesn't support them. I currently use NFS to enable pictures and music stored on my backend to be used on a remote frontend. You can use the following post to enable:

[http://ubuntuforums.org/showpost.php?p=10173776&postcount=8]("http://ubuntuforums.org/showpost.php?p=10173776&postcount=8")

This post was before storage groups was available / worked correctly so just disregard the "video" and use it for "music and pictures". I currently still do this.

---

