---
title: "No Thumbnails for .jpg files in Nautilus"
date: 2009-11-15
forum: Multimedia Software
---

### Post by greyfox1 on 2009-11-15
EDIT: Solved. See my second reply below for the solution.

---

For some reason, I can't get thumbnails/previews for .jpg files in Nautilus. Nautilus had been generating them normally until today-- I copied some new pictures in from an SD card and the new files had no previews.  To fix it, I tried deleting ~/.thumbnails, at which time I lost ALL existing thumbnails and Nautilus is no longer generating them for .jpg files (it still does for video files). If I rename the file to.jpeg from .jpg, Nautilus generates the thumbnail like normal. Obviously this is a workaround and not a fix.

Other things I have tried in addition to deleting ~/.thumbnails/ :

- Removed.gconf/apps/nautilus/preferences/%gconf.xml ([source]("http://ubuntuforums.org/showthread.php?t=1068741"))
- Commented out the line:
         application/x-extension-jpg:*.jpg
  In ~/.local/share/mime/globs ([source]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/198154/comments/7"))

My settings in Nautilus are configured to always show previews for files under 100MB (which these files are). The files are all local, in my ~/Pictures directory.


Any other suggestions? This is driving me nuts.

---

### Post by greyfox1 on 2009-11-16
Bumping this up. Suggestions would be appreciated.

---

### Post by paultag on 2009-11-16
Hey there GreyFox!

So, here is what I have worked out:

The gconf key "/apps/nautilus/preferences/show_image_thumbnails" dictates the behaviour you have observed, I think. Quoting for posterity: 

```

Speed tradeoff for when to show an image file as a thumbnail. If set to "always" then always thumbnail, even if the folder is on a remote server. If set to "local_only" then only show thumbnails for local file systems. If set to "never" then never bother to thumbnail images, just use a generic icon. 

```

I think this is the fist behaviour you have observed. I'm not Nautilus guru, but I have a hunch that it would consider those files remote.

More to come as I work out a bit more. Something tells me this won't be everything involved in this fix...

---

### Post by greyfox1 on 2009-11-16
This is SOLVED, thanks to paultag in #ubuntu-us-oh and drubin in #ubuntu-beginners. What I had to do was rename ~/.local/share/mime/ , then log out & log in again. My precious thumbnails are back, finally!

---

### Post by Mawy on 2009-11-30
This has been bugging me since I moved my files to a home server. Setting /apps/nautilus/preferences/show_image_thumbnails to always worked instantly. Thanks guys! :KS

---

### Post by tombelcher7 on 2010-10-19
Hello Ubuntu Forums community,

I'm using Ubuntu 10.10 Maverick Meerkat 32bit and am just running updates ATM; hoping that it might just fix the problem but if not:

I was looking at the posts above and found that I do not have any /apps folder and clearly due to this; no /apps/nautilus/preferences/show_image_thumbnails file.  Is there a fix for no JPEG thumbnails in nautilus for Ubuntu 10.10?


Thanks

---

