---
title: "How do I shrink video in ubuntu?"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by whitefort on 2007-06-25
What I mean is, suppose I have a vid clip that's about 5 Mb in size.  But I want to post it to a website that only allows clips of 1.5 megs or less.

In the past I could easily set the output size and run it through Windows Media Maker to shrink it from 5 Megs to 1.5,

But now I don't use Windows any more, and I'm not sure what program I need to do the same thing in Linux.  Any advice would be much appreciated!

Thanks.

---

### Post by aussiedini on 2007-06-25
You could try avidemux. Just change the calculated size to what you want.

---

### Post by whitefort on 2007-06-25
Many thanks - it took me a while to work out how to do it, but it works great!

Thanks again!

---

### Post by bionnaki on 2007-09-11
I have the same problem. avidemux is installed, so how do I shrink my video (.mpg)?

---

### Post by rsambuca on 2007-09-11
If I recall correctly, it is under "Tools -> Calculator"

---

### Post by bionnaki on 2007-09-12
thanks.
but what should I do?

---

### Post by orange2k on 2007-09-12
Calculator is just a *calculator*...
You have to choose the format (or codec) you wish to encode it to, the desired bitrate (this is where the calculator comes in) etc. After you have made your desired changes, select save and the encoding begins...

---

### Post by bionnaki on 2007-09-12
ok. still not clear on what steps I should take...is there a guide anywhere? not looking to learn video editing - just compress a few videos for youtube. .mpg files thare 900 mb that need to get down to about 300 mb.

---

### Post by rsambuca on 2007-09-12
Here is the avidemux wiki, which looks to be fairly easy to follow.  You have heard of the search function on your web browser, haven't you? :)

[http://www.avidemux.org/admWiki/index.php?title=Main_Page](http://www.avidemux.org/admWiki/index.php?title=Main_Page)

---

### Post by bionnaki on 2007-09-12
right...I've been over that wiki/guide and still havent seen anything related to compressing file size. There is a resize option, but that only shrinks the size of the video, not the file size itself.

---

### Post by rsambuca on 2007-09-12
It is under the configure option underneath the video codec choice.  Select your codec, and then configure to choose the bitrate you want.

---

### Post by netgooroo on 2008-03-22
Hey, 
I just got avidemux installed myself and I'm looking to shrink some vids so I can up them to my page. Problem with current size is that it does not fit within the "regulatory" size limits of my video hosting site so, if anyone can help a brotha out with this, that would be awesome! I'm very much pleased with the editor thus far so, if I can figure out how to shrink the vids..  that would be perfect. 
Thanks!
net:cool:

---

### Post by rsambuca on 2008-03-22
> **netgooroo said:**
> Hey, 
I just got avidemux installed myself and I'm looking to shrink some vids so I can up them to my page. Problem with current size is that it does not fit within the "regulatory" size limits of my video hosting site so, if anyone can help a brotha out with this, that would be awesome! I'm very much pleased with the editor thus far so, if I can figure out how to shrink the vids..  that would be perfect. 
Thanks!
net:cool:
You can use the [calculator and 2 pass encoding]("http://www.avidemux.org/admWiki/index.php?title=FAQ#I_use_2-pass_encoding_and_the_output_file_size_is_bigger_than_I_wanted_.28e.g._1300.C2.A0MB_instead_of_1200.C2.A0MB.29") to get the exact video size you want.

---

