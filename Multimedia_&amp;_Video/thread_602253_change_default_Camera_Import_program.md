---
title: "change default Camera Import program?"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by maphew on 2007-11-04
Hello Everyone,

How does one change the default program used to import photos from a usb camera? I would like to use digikam instead of gthumb. So far I haven't been able to find any place to set this preference.  This blog post perfectly explains my circumstance and desired goal: [http://www.theclonchs.com/2007/05/20/semi-auto-download-pictures/](http://www.theclonchs.com/2007/05/20/semi-auto-download-pictures/)

thank you.

---

### Post by ziritrion on 2007-11-04
Bump. I'm also interested in changing gThumb as the default app, although I'd like it to be f-spot instead of digikam.

---

### Post by ermannobonifazi on 2007-11-06
Go to System -> Preferences -> Removable Drives and Media

select the Cameras TAB. Done.

I change my command to:

digikam --download-from %m

To change the viewing app, just right click on the file (b.e. jpg), select Properties, than Open With TAB, and add the apps you want, than set is as default.

---

### Post by maphew on 2007-11-07
Ahh, thank you!! That got me most of the way there. For my camera, a canon powershot s1, the needed parameter is --detect-camera since it doesn't mount as removable media.

digikam --detect-camera

The user still needs to push a button to tell digikam to actually download the images, but at least now it's one push instead of several. Oh, and for auto-creation of sub-albums using the date, press the [settings] tab on the right hand side of the digiakm camera window.

---

