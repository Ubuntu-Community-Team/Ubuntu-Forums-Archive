---
title: "Amarok: changing capitalization in artist names"
date: 2009-12-15
forum: Multimedia Software
---

### Post by Bödvar on 2009-12-15
Is there a way to change the capitalization in artist names in Amarok? Currently I have Ramones displaying as RAMONES. I prefer it to be Ramones, but when I edit it to Ramones, and I click edit again, it's back at RAMONES.

Is there a workaround for this?

---

### Post by warfacegod on 2009-12-15
Try hitting Enter instead of clicking Edit.

I've had fine luck with editing in the library itself. Highlight all the entries you wish to change, right click, select edit tag artist, do typing, hit enter.

---

### Post by Bödvar on 2009-12-15
I've noticed it says the writing to the file fails because I need to check permissions.

This may be the problem rather. Thanks for your input though.

EDIT: I have isolated the problem. Sorry for thinking it was Amarok. I do not have permissions over the files and I cannot get permissions because when I type

```
sudo nautilus /media/160/Musiek/R/RAMONES/
```

or

```
gksudo nautilus /media/160/Musiek/R/RAMONES/
```

And I try to modify the permission by rightclicking on the files, the permission slips back to "root" about a second after I have selected it otherwise... this is really weird.

---

### Post by warfacegod on 2009-12-17
It looks like your music is on an external hard drive. If so then you can use this command in the terminal and you will own the external not root (usually).


sudo chown -R username:username /media/drive name


Just replace username:username with whatever name you use to login to your computer and drive name with the name of your external which probably isn't what's displayed under the icon on your desktop. Look in the media folder, it's probably some long series of letters and numbers.

---

### Post by warfacegod on 2009-12-17
If it's not an external, try chowning your home folder.


sudo chown -R username:username /home


Alhthough you should already be the owner not root.

---

