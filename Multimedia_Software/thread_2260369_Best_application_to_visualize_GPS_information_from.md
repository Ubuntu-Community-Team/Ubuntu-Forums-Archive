---
title: "Best application to visualize GPS information from photos"
date: 2015-01-11
forum: Multimedia Software
---

### Post by oz1cz on 2015-01-11
I have just replaced my old digital camera with a new one that includes a GPS. So now I'm looking for a program that can visualize GPS information from the camera.

It's easy to extract the longitude and lattitude from the EXIF information in the image, but is there an Ubuntu program that I can use to easily see where my photos were taken?

---

### Post by Benjamin_Eunice on 2015-01-11
I did some research and found a program called GPS Correlate. I haven't run it but it supposedly does something similar to what you want.

To install, go to terminal and type the following command:

```
sudo apt-get update
```

Next, type this command:

```
sudo apt-get install gpscorrelate
```

This command can be used for any program if you know the package name.

The terminal is the most reliable way to get programs installed but you can just go to the Ubuntu Software Center and search "GPS Correlate".

---

### Post by oz1cz on 2015-01-12
> **Benjamin_Eunice said:**
> I did some research and found a program called GPS Correlate. I haven't run it but it supposedly does something similar to what you want.

I'm sorry, but it doesn't.

GPS Correlate adds GPS information to an image file. That's not what I want. The GPS information is already in my image files. I want a program that visualizes the information already in the file. something like this: [http://piwigo.org/ext/extension_view.php?eid=122](http://piwigo.org/ext/extension_view.php?eid=122), but not as a web service but as a standalone Ubuntu program.

---

### Post by mc4man on 2015-01-12
Maybe digikam

---

### Post by oz1cz on 2015-01-12
Yes, digikam does the trick, thank you.

---

