---
title: "iPod Touch 8GB 3rd Gen not recognized in banshee or rhythmbox"
date: 2010-04-04
forum: Multimedia Software
---

### Post by jhoek95 on 2010-04-04
Hey guys, I just recently installed Ubuntu 9.10 through wubi in Windows 7. I would like to sync my ipod music and videos with banshee. When I plug my iPod touch in, the ipod charges, but banshee isn't recognizing a new device. I checked the plugins, and the iPod support is checked. Anyways, thanks and I hope you can help! This is my first thread :D

---

### Post by `GooZ´ on 2010-04-13
Hi jhoek,

It might be possible that this won't work since you're running Ubuntu inside Wubi. Could you try checking if your ipod shows up in the file manager, or in rhythmbox?

---

### Post by WinterRain on 2010-04-13
Try Gtkpod.

---

### Post by temporos on 2010-04-25
> **WinterRain said:**
> Try Gtkpod.
I installed gtkpod, and my iPod Touch won't show up in the iPod Manager.  It doesn't need to be jailbroken, does it?  I am hesitant to jailbreak it, because I have some purchased apps on it that I want to continue to use and update.

I guess I don't really need to say that my iPod (Touch, 8 GB, Gen3) isn't showing up in Rhythmbox, either...

**Edit:  **Oh yeah, and my iPod shows up as a camera named "iPod" in the file manager (karmic netbook remix).  What's up with that?

---

### Post by jaminthorns on 2010-05-02
Try upgrading to Lucid Lynx 10.04. It has full iPod Touch, iPhone support. :D

---

### Post by temporos on 2010-05-02
> **jaminthorns said:**
> Try upgrading to Lucid Lynx 10.04. It has full iPod Touch, iPhone support. :D
But those koalas are just so darn *cute*!  :biggrin:

---

### Post by Zappanale on 2010-05-02
I'm having ipod troubles too...
In 10.04, when I connect my ipod touch (I think it's 2nd gen), although it appears on the desktop, and can be seen in rhythm box, AND I can transfer files, the music still doesn't appear on my ipod. Any suggestions?

---

### Post by GrumpyBob on 2010-05-03
> **Zappanale said:**
> I'm having ipod troubles too...
In 10.04, when I connect my ipod touch (I think it's 2nd gen), although it appears on the desktop, and can be seen in rhythm box, AND I can transfer files, the music still doesn't appear on my ipod. Any suggestions?

I have the same issue, 32Gb iPod, 2G, version 3.1.3.  Computer recently upgraded from 9.10 to 10.04.

Rhythmbox seems to transfer the mp3 files, but they can't be seen on the iPod.

Robert

---

### Post by GrumpyBob on 2010-05-03
OK, I installed ifuse via synaptic, and now I can upload music to the iPod Touch, and can see and play said music on the iPod.  Unfortunately about 25% of the album artwork is now associated with the wrong album!

Robert

---

### Post by MartinFernando1993 on 2010-05-15
I have a 2nd gen ipod touch with 3.0 firmware and on 10.04, it syncs fine. Just look for them from your ipod be cause it updates the main music library :) . Also it may take some time for it to sync so be patient.

---

### Post by temporos on 2010-05-15
Sounds as if I'll have to abandon the poor Koala in favour of the Lynx. :P

---

### Post by vkcaspervk on 2010-05-15
I am running 10.04, I plug in my iPhone 3G 16 gig 3.1.3 OS, I can see, add, and delete files via Nautilus, but Rhythmbox doesn't see it.

Verified the ipod plugin is active.
Tried reinstall RB.

Any other Idea's?

---

### Post by didibanner on 2010-09-06
OK guys, here's what I have been able to get so far vis-a-vis the ipod touch 3rd Gen:

1) If you have a security lock code, you have to enter the code before you plug your ipod touch in otherwise it will not be recognized

2) After dragging and dropping music from rhythmbox into the ipod touch, you have to wait a while for the music to actually sync. Even though rhythmbox has finished transferring the files, it takes some time for this to actually register with the ipod.

3) If you are using gtkpod, you have to first go to Edit > Repository/iPod Options. When there, you click on the Add new Repository tab on the upper left. In the space for iPod Mount Point, write /home/{your username}/.gvfs/iPod. Then select the model where it says Model:

Hope this helps ;)

---

