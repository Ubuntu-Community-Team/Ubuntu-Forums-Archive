---
title: "DVD Totem  hheellppp"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by Ex-windows on 2007-10-16
[SIZE="1"][SIZE="2"][B][COLOR="Blue"][SIZE="2"][SIZE="2"]I upgraded to Fiesty and totem would no longer play the DVDs stored on the computer.The error message reads 

Totem could not play file:///media/hdb1/home/family/DVDS/musical/MELISSA_ETHERIDGE_GH.iso

There is no plugin to handle this movie.
I have xine-xtra plugins installed. 

This is the second time I have upgraded to Fiesty and this has happened. 
As far as I can tell everything else is fine, including my nvidia setting and twinview. DVD' disc's play just fine it is only affecting the ones stored on the computer. What can I do to solve this???? 
Any
help would be greatly appreciated[/SIZE][/SIZE][/COLOR][/B][/SIZE][/SIZE]

---

### Post by yabbies on 2007-10-16
iso is not a media format. It's an image of a disc.
when you rip your dvd you need to encode it to .mpg or .avi format.
.mpg if you are going to backup a copy
and .avi is preferred if you are just going to watch it on your computer.

---

### Post by Ex-windows on 2007-10-16
Thank you very much for the quick reply.
If I right click the dvd drive it says copy disc but when I try it will only allow to copy as a "File Image" and it comes out as an iso. Is there some other program I shouls be using?????.
I am curious though why it worked in Edgy and not in Fiesty.
Thanks again and in advance

---

### Post by yabbies on 2007-10-16
you need ripping software like
dvd::rip
[https://help.ubuntu.com/community/DVD%3a%3aRip?highlight=%28%3Arip%29]("https://help.ubuntu.com/community/DVD%3a%3aRip?highlight=%28%3Arip%29")

---

### Post by Ex-windows on 2007-10-17
Thank you, Sorry for the delay.  I am trying acid rip and so far so good except that  the special features are not getting recorded.But the Movies are coming out great.... Any ideas on how to get the Special Features to record?????
Thanks again

---

### Post by mommebu on 2007-11-21
While in earlier versions of ubuntu totem-xine was able to play iso files it seems to fail now if you load the image from the menu, however from terminal it worked for me using:
totem-xine dvd://absolute/path/to/your/iso/file.iso &
This is without mounting the image.

Strange that the newer version lost the feature from the menu though...

---

