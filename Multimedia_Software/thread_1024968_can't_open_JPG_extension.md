---
title: "can't open JPG extension"
date: 2008-12-29
forum: Multimedia Software
---

### Post by chudder on 2008-12-29
Hi all,

I just upgraded a new computer to Intrepid from Vista, I've never had this problem before but when I try to open jpg files, (taken from a screenshot) they don't open, the image viewer says, "Could not load image ______________" and there is a retry button that doesn't help.  I've noticed it will open up PNG files just fine.  On other computers, I've never had this problem, what can I do to open the JPEG format?

Thanx

Chud

---

### Post by damis648 on 2008-12-29
Have you tried other images besides just this one? Perhaps it is corrupted.

---

### Post by chudder on 2008-12-29
> **damis648 said:**
> Have you tried other images besides just this one? Perhaps it is corrupted.

Actually, yes, I've tried about 5 different JPEGs and I tried opening them in both Image Viewer and GIMP and it seems like there is something to do with the plugin for viewing JPEGs.  GIMP and Image Viewer was able to view the PNG file.  I wonder if it's something with the screenshot utility.  this is because my computer can view files downloaded, at least I tried one but it doesn't view jpg created from the screen capture utility.  

Thanx for your help

---

### Post by Therion on 2008-12-29
> **chudder said:**
> I wonder if it's something with the screenshot utility.  this is because my computer can view files downloaded, at least I tried one but it doesn't view jpg created from the screen capture utility.
Sure sounds like it.  What app are you using to capture your screenies?

---

### Post by chudder on 2008-12-29
> **Therion said:**
> Sure sounds like it.  What app are you using to capture your screenies?

I am using the default screen shot taker (if that's the right way to put it).  The one that comes up by pressing the Print Screen key.  The other way to navigate to it is to go to 
>Applications >Accessories >Take Screenshot >Grab the Whole Desktop

I manually enter the ".jpg" extension and delete the ".png" extension which has never caused a problem before but now it does.  

Thanx

---

### Post by mc4man on 2008-12-29
The screenshot is being saved with a .jpg extension but still is a png image.
If you want to save as a jpg then leave the png extension when taking screenshots (or put back for ones you've already taken), open in gimp and 'flatten image' before saving.as a .jpg

---

### Post by chudder on 2008-12-29
> **mc4man said:**
> The screenshot is being saved with a .jpg extension but still is a png image.
If you want to save as a jpg then leave the png extension when taking screenshots (or put back for ones you've already taken), open in gimp and 'flatten image' before saving.as a .jpg

okay, that's a good solution, is there a way to get the utility to save in jpg?  I could have sworn that in Feisty it let you manually change the extension.  Was that not the case and I just didn't realize it until now?

---

### Post by chudder on 2008-12-29
> **chudder said:**
> okay, that's a good solution, is there a way to get the utility to save in jpg?  I could have sworn that in Feisty it let you manually change the extension.  Was that not the case and I just didn't realize it until now?

I have come to a new assessment of the problem but no solution.  Oddly enough, I uploaded the JPGs to Gmail and they came through and are viewable either on a windows computer or via HTML.  That makes me think that there is some missing codec or plugin to view JPGs created in Ubuntu.  The fact that I remember being able to do it on Feisty for a year makes me think that I then had the plugin but don't have it with the new distro.

---

### Post by mc4man on 2008-12-29
I can change the ext. of a screenshot and open it in anything but "image viewer". (gimp2.6, firefox, gthumb, ect.

That still doesn't change the fact it's a png image. (I don't believe you can change the format of the screenshot utility

see screen for why (maybe the diff. from feisty to now

---

### Post by dtmonterrey on 2008-12-30
I have just upgraded and got the same problem. Just do a 
```
sudo aptitude reinstall libjpeg62
```
and your problem should go out...

---

