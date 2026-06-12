---
title: "Canon FS200 camcorder compatibility"
date: 2009-10-25
forum: Multimedia Software
---

### Post by H504 on 2009-10-25
I am pretty new to Ubuntu, and want to get a digital camcorder that will be compatible.  Has anyone used the Canon FS200 with Ubuntu?  Thanks for any tips or any other makes/models recommended for home video recording.  I'm looking in the "under $500" range.

---

### Post by dmelliot on 2009-11-17
Hi,
I'm also looking at this camera and will need it to work with either Ubuntu or Debian.

From the small amount of research I've done so far, it should be ok, but there may be some problems with the camera setting the image aspect ratio flag incorrectly.  This would probably be fixed with the bundled software on Windows, but may need a more manual work around on Linux :(

That said, I think VLC (or similar) should be able to play the files with no conversion etc.

Will keep looking.......

---

### Post by ZachElmblad on 2010-03-08
I own a Canon FS200, and operate just fine with both Lucid and Karmic.  I just use a card reader to take the files directly off the card, in *.MOD format.  Simply rename the file to *.MOV and open with your preferred application.  I use OpenShot Video Editor inside Ubuntu on my laptops, and I find it roughly similar to Sony Vegas which I used in the past on Windows.  I've just started messing with Cinelerra on my homebrew Studio Box, but I can't offer much advice yet.   After renaming files, they will open just fine with Totem and VLC.  The camera works very well for the price, and the microphone is surprisingly sensitive.

---

### Post by ThomasNovin on 2010-03-11
I have the Canon Legria FS36 (movies stored on on-board flash). I will probably return it because A) Movies are named in some strange fashion, not just MOV028 MOV029 MOV030 etc. but MOV028 MOV02A MOV02B MOV02C MOV030. Don't really see the logic behind the filenames.

Also, the cameras filesystem is mounted read-only and I cannot change that (AFAIK). So I have to erase the downloaded movies from the camera from the camera menu.

---

### Post by no2498 on 2010-03-11
ThomasNovin hope you get this in an email
read only is good the computer can not over write the card it can only read it take things off it 
now come back reread what ZachElmblad said
you need to rename them
and you need a card reader

---

### Post by ThomasNovin on 2010-03-12
> **no2498 said:**
> ThomasNovin hope you get this in an email
read only is good the computer can not over write the card it can only read it take things off it 
now come back reread what ZachElmblad said
you need to rename them
and you need a card reader

I don't have a problem with the extension, renaming from .MOD to .MOV isn't a hassle. I do have a problem with the part that is BEFORE .MOD, MOV02A MOV2C MOV030..

Getting a card reader isn't a very good idea for me, I don't have any removable storage card :) The FS 36 used built-in flash memory.

---

### Post by yuvilio on 2010-06-07
I have a Canon FS200 and plugged it in to the power and also to a laptop running Ubuntu Lucid (64 bit). On the camera screen, the usual "DVD Burner" or "PC/Printer" choice comes up and I chose "PC/Printer". A few moments later,  it auto mounted as "Canon"  in Nautilus ("/media/CANON/" in the file system). No card reader was needed. It even showed up as a link named "Canon" with a USB pictured icon in the Desktop. In there, I found the videos (as *.MOD files) in subdirectories of the SD_VIDEO directory. I simply copied them over, renamed them to .mov files and vlc played them.  

I set the .MOV file permissions to be write as well as read and am looking into Openshot and Pitivi for video editing (Cropping, fade outs...).

---

