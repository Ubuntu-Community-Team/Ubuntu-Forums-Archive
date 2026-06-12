---
title: "Cdrecord: How do i know the the layer break value? (DVD+R DL)"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by mplexus on 2007-07-07
Hello.

I have an iso file of a movie and it is 6.7 GB, and I want to burn it (using Ubuntu 6.10).
I installed cdrecord-ProDVD and was able to burn the image in DVD+R DL media, but the disc
wont play in stand-alone dvd player or xine. As I found out, this is because I didn't set the layer break value.

I suppose if I use driveropts=layerbreak=<value> then the DVD will be written correctly.
And as I found out again, I could use cdrecord -atip and compute the value of the layer break:
[http://www.nabble.com/a-question-about-cdrecord%2C-Plextor-PX-716-and-DVD-R-DL-tf2478765.html#a6913529](http://www.nabble.com/a-question-about-cdrecord%2C-Plextor-PX-716-and-DVD-R-DL-tf2478765.html#a6913529)

Also, I saw I could use growisofs instead of cdrecord :
[http://ubuntuforums.org/showthread.php?t=438656&highlight=layer+break](http://ubuntuforums.org/showthread.php?t=438656&highlight=layer+break)

In any case I need the layer break value.

-=Question=-

My question is: is there a way of knowing the layer break value based only on the iso image and _not_ the original DVD ? Is the layer break information somewhere in the iso file ..?

I tried mount -o loop (etc) and then cdrecord dev=/mount/dir  -atip with no success.

The particular iso file was created apparently with UltraIso (windows application).

Thanks for your time reading this!

------------
mplexus

---

### Post by mplexus on 2007-07-07
Hmm..  => [http://www.adobeforums.com/cgi-bin/webx/.3bbf8607](http://www.adobeforums.com/cgi-bin/webx/.3bbf8607)
                      => [http://www.gearsoftware.com/support/documentation/layerbreakcalculator.xls](http://www.gearsoftware.com/support/documentation/layerbreakcalculator.xls)

maybe I should try this calculator. I'll see if i need any windows programs help (hope not!).

---

### Post by mplexus on 2007-07-09
No lack so far. Has anyone successfully burned an iso image of a double-layer movie  with k3b?

PS. hope this is the proper forum for this thread..

---

