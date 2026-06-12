---
title: "Permanently mount shared network drive"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by trendal.toews on 2009-05-07
Okay, I'm frustrated.

It seems like every time you search Google or Ubuntu Forums on how to mount a network drive you get a whole new and different way to do it than last time.  And no matter which one I try I haven't got it to work yet.

I am using Jaunty.

On my old Hardy box I had it working for a while then I killed the entire network trying to do something else and just installed Jaunty to fix it.

Could someone please tell me what I am missing.?

It is a shared storage drive on our office network.  If i type findsmb in terminal it shows up.  It gives me the IP address and netbios name and is showing Samba 3.0.10.

What do I need?

Thanks

---

### Post by trendal.toews on 2009-05-07
IT WORKS IT WORKS IT WORKS...............! oops read the next post

Thanks to [this]("http://ubuntuforums.org/showthread.php?t=288534") post I got it working perfect!  O:)O:)O:)O:)O:):lol::lol:8)

---

### Post by trendal.toews on 2009-05-07
solved 

Edit:  ummmm.. Partially solved that is.  I can read the drive fine but seem to have problems with write permission.  I transfered a folder containing several subfolders and data and it seems to have copied some of them but not all.  It kicked out some with a denied permissions error.  Why does it allow some and not others?

---

### Post by trendal.toews on 2009-05-07
I guess I don't quit have it yet.....

---

### Post by Iowan on 2009-05-07
Well, you already found the How-To I'd have pointed you to... 
The next step will require some detective work.  Check the directories to see if they have spaces or other special characters in the names.

---

### Post by trendal.toews on 2009-05-07
> **Iowan said:**
> Well, you already found the How-To I'd have pointed you to... 
The next step will require some detective work.  Check the **directories** to see if they have spaces or other special characters in the names.

you mean the directories i am trying to copy?

On that storage drive I can create a folder fine but it then shows a locked symbol by it and I can't delete it.

---

### Post by Iowan on 2009-05-07
I'm more familiar with checking permissions via CLI, but I presume you should be able to right-click the directory, select Properties, then look at Permissions. (Might need to open the directory, then go up a level to be able to check Properties>Permissions.

---

### Post by trendal.toews on 2009-05-07
will give it a shot tomorrow.  Thats at work and I'm at home now.  Thanks

---

