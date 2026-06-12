---
title: "WinTV-PVR-500 MCE-Kit Remote"
date: 2007-10-30
forum: Mythbuntu
---

### Post by derfer on 2007-10-30
I have the PVR 500 MCE with remote and I can't seem to get it working right.

[http://www.hauppauge.co.uk/images/mce_remote_w_beanbag_large.jpg]("http://www.hauppauge.co.uk/images/mce_remote_w_beanbag_large.jpg")



Some buttons work and some don't. right now  i'm using the "new MCE" setup. 

Do I just have to edit the lircd.conf file?

It kinda sucks that the channel up and down buttons don't work. The back button doesn't work I have to use the stop button 

I would really like the "My pictures" "My Music" "My Videos" buttons to work.

I tried this one but couldn't get it to work.
[http://www.hauppauge.co.uk/board/showthread.php?t=7085&highlight=remote]("http://www.hauppauge.co.uk/board/showthread.php?t=7085&highlight=remote")

Thanks 
derfer

---

### Post by superm1 on 2007-10-30
> **derfer said:**
> I have the PVR 500 MCE with remote and I can't seem to get it working right.

[http://www.hauppauge.co.uk/images/mce_remote_w_beanbag_large.jpg](http://www.hauppauge.co.uk/images/mce_remote_w_beanbag_large.jpg)



Some buttons work and some don't. right now  i'm using the "new MCE" setup. 

Do I just have to edit the lircd.conf file?

It kinda sucks that the channel up and down buttons don't work. The back button doesn't work I have to use the stop button 

I would really like the "My pictures" "My Music" "My Videos" buttons to work.

I tried this one but couldn't get it to work.
[http://www.hauppauge.co.uk/board/showthread.php?t=7085&highlight=remote](http://www.hauppauge.co.uk/board/showthread.php?t=7085&highlight=remote)

Thanks 
derfer
Modify your ~/.mythtv/lircrc to map the buttons you want how you want.  Please file a bug with your exact model number on the remote, post the original ~/.mythtv/lircrc and the newly modified ~/.mythtv/lircrc.

---

### Post by ickyb0d on 2007-10-30
> **derfer said:**
> I have the PVR 500 MCE with remote and I can't seem to get it working right.


Hrm, I have the exact same kit and everything worked right out of the box.  Did you make sure you picked "Windows Media Center (new Phillips et. all)" remote?  

However, there are a few differences I did notice between the mythbuntu setup and some lircd files i downloaded for my previous installs of MythTV for that remote.  The main being the MyTV, MyPictures, MyMusic buttons are just setup to "TV", "Pictures", "Music", etc.  But looking at the lircd files, I can't see anything wrong.

---

### Post by derfer on 2007-11-02
Well I went and reinstalled Mythbuntu. I made sure I picked the MCE phillips new. Well everything is the same as before. I found out the windows icon key works for bringing up the program guide and the recorded TV button records the show that I'm watching. I would rather the record button works for this.

I'm ready to start messing with the lirc files. Is there any good instructions on how to do this?

---

