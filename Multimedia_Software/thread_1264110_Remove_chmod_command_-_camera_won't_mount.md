---
title: "Remove chmod command - camera won't mount"
date: 2009-09-11
forum: Multimedia Software
---

### Post by omskates on 2009-09-11
Hi,
Got myself in trouble trying to get my Kodak Easyshare to play nice with jaunty.  I really shouldn't run commands I don't completely understand but it had seemed to work for someone.

sudo killall gvfs-gphoto2-volume-monitor  

sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor 

Now nautilus will not acknowledge the camera at all and not sure how to reverse the action.  

Some people seemed to find solutions throughout this thread (8 pages long so only scan through if this interests you)
[http://pennsylvania.ubuntuforums.com/showthread.php?t=965167](http://pennsylvania.ubuntuforums.com/showthread.php?t=965167) 

Thanks

---

### Post by purgatori on 2009-09-11
Chmod manages the 'permissions' (who is allowed to read, write, and/or execute) of particular files. By using chmod with the -x flag, you are removing the e**x**ecute permission from the gphoto2 volume manager -- so that it won't start up again after killing it. 
To reverse your actions:

```
sudo chmod +x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
```

And yes, you're right; you really shouldn't run commands without having some idea of what they do, or at least how to reverse any changes made :)

You don't say specifically what error you're getting when you try to access your camera through nautilus, so that's as much help as I can provide at this time. Good luck.

---

### Post by HappyFeet on 2009-09-11
Try gthumb for importing photos. After camera is plugged in close window that pops up. Then open gthumb and file>import photos.

---

### Post by mcduck on 2009-09-12
..and of course the best way to get the pictures from digital cameras is to just use a memory card reader. They work always, regardless of your camera, you don't need to keep the camera connected or powered, and the transfer speeds are usually about twice the speeds you'd get from camera.. ;)

For some reason or other the USB connections in digital cameras are always amazingly crappy. Even on cameras built for professional use, and as you might have guessed cheaper consumer cameras are even worse.

---

### Post by omskates on 2009-09-12
Thankyou, I know just enough to be dangerous but I'm learning:)


#Initial Rror when connecting:
Error initializing camera: -60: Could not lock the device

#Error when using "Image Viewer":
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

#Error when opening with Gthumb:
Error initializing camera: -105: Unknown model

#Gthumb does not detect a camera & I can't seem to mount it, I don't havethis issue with any oter externals.  I may need to get the SD card reader. 

 Thanks guys!

---

