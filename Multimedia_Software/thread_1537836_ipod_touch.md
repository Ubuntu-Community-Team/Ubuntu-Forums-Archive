---
title: "ipod touch"
date: 2010-07-24
forum: Multimedia Software
---

### Post by hollowhead on 2010-07-24
How do you use an ipod touch in lucid?  It doesn't work out of the box for me.  When we got it it said on the screen connect to itunes.  Not having windows I've just taken it to a neighbours with a pc with itunes.  It seems to have formatted it since now all the icons appear work on the device.  Note we did not connect to itunes or register.  Plugging it into ubuntu an icon appears, but rhythmbox still comes up with the "do you want to initialise the device?".  Songbird, amarock and gtkpod fail to see it.  My question is should we have done something else on itunes?  ipod 8g A1288 Assume this is the right forum?

---

### Post by petrus250 on 2010-07-24
Unfortunately, there is no ipod touch support via programs or out of the box. I wish there was (wine cannot handle it).

---

### Post by hollowhead on 2010-07-25
That doesn't seem to be the spin put about on the web...  Is there any way to transfer mp3s to it?

---

### Post by hollowhead on 2010-07-25
I've made a bit of progress I put ifuse on the system Amarock now offered to add an itunes.db file to the touch.  But on loading Amarock again doesn't.  Possibly I need to register with itunes?

---

### Post by nathan.osborn1 on 2010-07-25
I have an iTouch that has no problem being read by Ubuntu but I have not tried to drag and drop yet. Try this link. It is page from the community. I have not tried it myself but I am going to soon. Tell me how well it works or doesn't if you decide to give it a go.
 
Here is the link: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) 
The link didn't work right, but it is good now.

---

### Post by hollowhead on 2010-07-25
Thanks I found that.  I tried the iphone usb instructions on that page still nothing.  The system sees the pod but not the programs for transferring music.  I found this [http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html](http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html).  I'd already installed the repository software but I'm missing libgvfscommon0, however if I try to install it using the terminal I get a conflict warning and if I use synaptic I get a warning it will involve removing a huge number of apps including rhythmbox!  I might try connecting to itunes using the touch and see if that sets up .db file and maybe that will be enough...  Despite the claim made on the community page it is not supported out of the box though!

---

### Post by hollowhead on 2010-07-26
Think I need to create itunes.db and the folder it sits in using itunes on a pc.  Will try this then post back results.....

---

### Post by hollowhead on 2010-07-30
Ok it works kind of....  I don't think gtkpod is quite seeing it correctly.  

For anyone with the same problem heres the quick guide.

1) Attach touch to itunes on windows this will format the touch's drive (no escape from this?).
2) Set up account with itunes when invited, this sets up control folder and itunes.db.
3) install ifuse, gvfs and every other ipod supporting software.
4) This wasn't enough for lucid though, in the end when invited by gtkpod to set up folders on pod select mount point in home/.gfvs and type of touch and agree to allow it to do its stuff.

Following all this rhythmbox see touch allows you to rename it, play from it but not put files on it apart from album art (I find the the same problem for 3rd and 4th gen nanos too for the last versions of ubuntu).  I've got Amarock to see the pod but I cannot see the pod in Amarocks window difficult to explain but true.  Gtkpod isn't totally happy but puts playlists on as albums, but not album art.  So I put album art on with rhythmbox.  Never could work out how to use songbird and don't like Banshee although it stopped transferring a few generations ago as well.

---

