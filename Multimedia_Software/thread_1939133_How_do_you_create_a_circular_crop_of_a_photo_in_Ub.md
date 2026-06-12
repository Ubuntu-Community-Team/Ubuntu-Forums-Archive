---
title: "How do you create a circular crop of a photo in Ubuntu?"
date: 2012-03-11
forum: Multimedia Software
---

### Post by rocksockdoc on 2012-03-11
Using any of the standard photo-editing tools in Ubuntu, is there a way to draw a circle on a picture and then crop to that circle (with the area outside the circle going transparent)?

Tools currently available are shown below (but anything easily installed is fair game).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214096&stc=1&d=1331453330[/IMG]

---

### Post by papibe on 2012-03-11
Hi rocksockdoc.

You can do that with GIMP:

- Add an alpha channel to the layer that define the picture.
- Use the ellipse selection tool to draw a circle where you need it.
- Invert selection.
- Cut.

That should do it.

Hope it helps.
Regards.

---

### Post by shantiq on 2012-03-11
you may need to manipulate size of original image to make a decent circle possible    then

**1.**   use ellipse tool in **Gimp** to select area you want

**2.**   cut

**3.**   edit/paste as new image


**4.**   save as png will **automatically** keep the remaining space transparent [shows black here but is alpha channel simply click on image to verify]


[CENTER][[IMG]http://img99.imageshack.us/img99/7988/movey.th.png[/IMG]](http://img99.imageshack.us/img99/7988/movey.png)[[IMG]http://img41.imageshack.us/img41/2266/77184677.th.png[/IMG]](http://img41.imageshack.us/img41/2266/77184677.png)[[IMG]http://img703.imageshack.us/img703/5605/25069669.th.png[/IMG]](http://img703.imageshack.us/img703/5605/25069669.png)[/CENTER]



handy trick to make buttons

[[IMG]http://img692.imageshack.us/img692/3871/coloh.th.png[/IMG]](http://imageshack.us/photo/my-images/692/coloh.png/)

---

### Post by rocksockdoc on 2012-03-15
Thanks both of you for suggesting Gimp which seems to do the job nicely.

In the past, I had trouble with the complexity of using The Gimp for 'drawing' circles, but for circular cropping (which is vastly less frequent than drawing), the complexity is less problematic.

Since I didn't get this information until it was too late for the task at hand (but plenty early for the NEXT cropping effort), I should report back that I ended up inserting the picture into PowerPoint on Windoze and then using the PPT circular crop tool.

But, of course, that's NOT a Ubuntu solution that is portable. :(

---

