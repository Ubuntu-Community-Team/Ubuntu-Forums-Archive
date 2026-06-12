---
title: "Problems with Shotwell 0.30.14 – “Celle”"
date: 2022-07-04
forum: Multimedia Software
---

### Post by cigtoxdoc on 2022-07-04
I moved the majority of my professional writing (scientific journal articles, presentations) over to Ubuntu from Windows over five years ago.  Such writings are not pure text, but a mixture of text and images.  I often have to convert images from one format (say BMP or GIF) to JPG for insertion into a LibreOffice Writer or LibreOffice Impress document.  First thing I found today, is that there is nothing on current version of Ubuntu 22.04 LTS that allows conversion of GIF to JPG.  Shotwell used to do that, but no more.  I had to put the GIF file in an email, send it to one of my Win 10 PCs, use Paint to do the conversion and then email it back to my laptop.  Then, I go to insert it in LibreOffice Writer 7.3.4.2 and find that the default view is to prohibit showing images.  I had already gone through each setup item, and prohibiting image visualization was not on the list.  I have long ago given up on the LibreOffice help list. 

I tried to use Gnome to report the bug with Shotwell.  I set up new login and password.  It then wanted me to set up a user profile, but when I tried to do that, I was told it was a forbidden operation.  I am a heavy user of Gnome Evolution.  Fortunately, that software has a good help service.

Apparently, all image editors think we should put our images in libraries.  I file my images by client by year along with the corresponding docx and pdf documents.

If the "gods" of Ubuntu want me out of their kingdom, why don't they tell me to get lost.  Every PC I buy (refurbished from TigerDirect) comes with Win10 Pro preloaded along with Office 365.

John

---

### Post by kurt18947 on 2022-07-04
I have gthumb installed. I opened a .png graphic and simply said save as .jpg. It did. I don't know if it would support bmp though, I don't have any of those to try. I sort of suspect it wouldn't, I don't know that bmp is common outside Microsoft land and gthumb is I believe a GTK app.

Edit: Here's a possibility: [https://superuser.com/questions/26935/convert-a-bunch-of-bmp-files-to-jpeg-on-linux](https://superuser.com/questions/26935/convert-a-bunch-of-bmp-files-to-jpeg-on-linux)

Similar solution:  [https://askubuntu.com/questions/915506/bulk-image-format-conversion-from-from-bmp-to-jpg-via-command-line](https://askubuntu.com/questions/915506/bulk-image-format-conversion-from-from-bmp-to-jpg-via-command-line)

---

### Post by Claus7 on 2022-07-05
Hello,

> **cigtoxdoc said:**
> I often have to convert images from one format (say BMP or GIF) to JPG for insertion into a LibreOffice Writer or LibreOffice Impress document.  

I downloaded a gif file, placed it on the left hand side of my screen. I opened writer on the right hand side. I dragged and dropped the gif file to writer. No issue.

> **cigtoxdoc said:**
>  First thing I found today, is that there is nothing on current version of Ubuntu 22.04 LTS that allows conversion of GIF to JPG. 

I opened a terminal and did the following:
convert gif_mentioned_earlier.gif gif_mentioned_earlier.jpg

The thing is that gif was animated, so more than one files were created. I kept only one of them, which had also the right colors, since the rest of them were green ones.

> **cigtoxdoc said:**
>  Shotwell used to do that, but no more.  
Didn't know that. Shotwell is not one of the available programs in order to open a gif file.

Regards!

---

