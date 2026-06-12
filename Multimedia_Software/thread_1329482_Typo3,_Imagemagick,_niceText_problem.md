---
title: "Typo3, Imagemagick, niceText problem"
date: 2009-11-17
forum: Multimedia Software
---

### Post by Statik on 2009-11-17
Hi all,

New Karmic AMD64 install with LAMP tasksel installed. Installed Typo3 and almost everything is working as expected. The only thing that doesn't work is the niceText option for creating graphics. This relies on imageMagick and libGD (libgd2-xpm installed). Using the Typo3 install tool I can see that all tests pass except for the two niceText items. I cannot seem to find a reason for this.

Does anyone have any ideas on how to tackle this? Google hasn't given me any joy.

Thanks!

Statik

---

### Post by benvantende on 2009-11-18
Hi,

It is very difficult to explain the settings for ImageMagick as it depends on a lot of things. I would suggest to use GraphicsMagick that is also in the repositories. Then all your problems will be over ;-)

Enjoy TYPO3! Currently I am at [http://t3uxw09.typo3.org](http://t3uxw09.typo3.org)

gRTz

ben

---

### Post by benvantende on 2009-11-18
> **Statik said:**
> 
New Karmic AMD64 install with LAMP tasksel installed. Installed Typo3 and almost everything is working as expected. .................

Statik

Hey Statik,

If you install TYPO3 from the repositories GraphicsMagick will be installed automagically as there is a dependency ([http://packages.ubuntu.com/karmic/typo3](http://packages.ubuntu.com/karmic/typo3)). I guess you did not install it from the Ubuntu repositories. Did you?

gRTz

ben

---

### Post by Statik on 2009-11-18
You are correct, I didn't install it from the repositories as I didn't even know it was there. I may have to try that.

Thanks

Rod

---

