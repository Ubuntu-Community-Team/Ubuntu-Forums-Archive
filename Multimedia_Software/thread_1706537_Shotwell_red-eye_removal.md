---
title: "Shotwell red-eye removal"
date: 2011-03-14
forum: Multimedia Software
---

### Post by gofurygo on 2011-03-14
Hello

I have a small problem with shotwell. When I open a picture for red-eye removal, Im zooming in to get a better view to set the red-eye removal "circle". So I zoom in, click the red-eye removal button...then shotwell zooms back out and and does fit to screen/fit to window. So I have no chance to place the red-eye removal correctly because its always zooming out again which makes it very hard circle those red eye balls :-(
Also, zooming-in is locked after clicking "remove red-eye".

Anybody can confirm this and how can I "fix" it...? I mean, fix it other than using eg. Gimp ;)

Is this a bug? I use Ubuntu 10.10 and shotwell version is 0.8.1

Thanks

---

### Post by gofurygo on 2011-03-14
Anybody can confirm this by following these steps:

1) open a picture in the standard picture viewer
2) click "edit picture" --> new window opens
3) zoom into the picture
4) click red-eye removal

In my case, shotwell un-dos the zoom and fits the picture to window/screen
Zooming while red-eye removal is active is not possible. Closing the red-eye removal dialoge will apply the previous zoom actions afterwards.

Like said, its impossible to place the red-eye removal circle with pictures fit to screen/window and not being able to zoom...

Thanks in advance guys ;-)

---

### Post by NightwishFan on 2011-03-14
I am unable to do this as well. Clicking zoom-in under the menu has no effect either. There is a bug report for it here:
[https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/652158](https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/652158)

Edit: Upstream bug here: [http://trac.yorba.org/ticket/2369](http://trac.yorba.org/ticket/2369)

Edit edit: Workaround:
[QUOTE=Gustaf Thorslund]I found out Crop can be used as a workaround for this.

1) Crop out the area with the red eyes
2) Now use the redeye function on the limited picture
3) Use crop again and move the box to an other area of red eyes.
4) When done. Crop the picture again to the full size (or any other desired size).

Hope this can help.
[/QUOTE]

---

### Post by eric-yorba on 2011-03-14
> **NightwishFan said:**
> Edit: Upstream bug here: [http://trac.yorba.org/ticket/2369](http://trac.yorba.org/ticket/2369)

Yup, that's the ticket for this bug.  Unfortunately the fix won't make it into Shotwell 0.9. :-(

---

### Post by gofurygo on 2011-03-14
Thanks for the quick confirmation guys...really too bad a fix wont make it to version 0.9... although the bug was first mentioned 7 months ago...:rolleyes:

---

### Post by gofurygo on 2011-06-06
Hello there

A few days ago I installed Natty on a new computer - painless.

I ran in to another "problem" with shotwell. I resized a picture to 1920 width (height was different due to the original aspect ration of the photo). I opened the cropped picture again in order to crop it according to my screen resolution (1920x1080). I selected crop-->specific and entered 1920x1080. But all shotwell gave me is a smaller rectangle (with the "right" ration) but not stretched to the full width of the photo. In other words, it didnt create a crop mask as specified. Can anybody confirm this?

Here: [http://shotwell.3510.www.nabble.com/Shotwell-desired-crop-ratio-not-accepted-td37531.html](http://shotwell.3510.www.nabble.com/Shotwell-desired-crop-ratio-not-accepted-td37531.html)  I read that this is supposed to be like this :( very strange, really...

BTW, the redeye removal thingy still aint working...

Cheers

---

### Post by gofurygo on 2012-01-13
Shotwell has to go...seriously... 

It lost its simplicity and straight forward usage with the latest versions.

Now its not even possible to rotate the picture with the click of a button. Its only possible with keyboards shortcuts or choosing from the menu. No toolbar can be displayed having the rotate left/right button.

Almost 1 year later, the red-eye removal bug is still not fixed.

And, worst of all, everytime you rotate a picture and go to the next one, it asks you to save the changes or not - for every picture individually... like some windows apps. This is what I liked best, rotate many pictures in a folder, then close shotwell and save everything with 1 click...but now...

Im moving to eye of gnome and gthumb.... sorry...that killed it for me

---

