---
title: "GIMP can not save some images as jpeg"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by geek_sandy on 2008-02-15
I have this weird problem: GIMP fails to save some images as jpeg saying "JPEG image plug-in could not save image". And in .xsession-errors i see the following:

** Message: Failed to close thumbnail pixbuf loader for /home/sandy/Pictures/p2135168s.jpg: Unrecognized image file format

This happens only with some images, and it always fails to save them no matter how many times I tried. Other images work just fine. Scenario: I copy photos from my camera, select some photo, open it with GIMP, resize and rotate, then do 'save as', and here it can either work or break. Seems like some combination of attributes of some particular photos make it break. As I said, trying again the same picture does not help at all. And it does not depend on the resizing ratio or rotation - it just does not like some photos. Saving the same photos as png works fine.

---

### Post by geek_sandy on 2008-02-15
I forgot to mention it was Ubuntu 7.10 with all the latest updates installed.

By the way, I have just found that it behaves the same way in Fedora 7 with all the updates. The same images can not be saved. So it must be something fundamental like jpeg library. I can provide a sample image to reproduce the problem.

---

### Post by Wobblybob on 2008-02-17
I have the same problem, several jpg images from one batch of photos will open but after rotating them they will not save and now some that would not save will not load either in gimp. I'm using Gusty with GIMP 2.4.2. One image that refused to save as jpg then saved ok as png and I then opened that and saved it as jpg with no problem.

edit:
any image works ok when I open them with "image viewer" then save them as png then edit in gimp and resave the png to jpg [confused]. I have re installed gimp with no luck

---

