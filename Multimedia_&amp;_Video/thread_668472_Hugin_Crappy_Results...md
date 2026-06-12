---
title: "Hugin Crappy Results.."
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by CyberAngel on 2008-01-15
Why am I having so crappy results when trying to create a panorama using hugin??

It seems like hugin is not using enblend at all and also it cannot create automatically control points...
I have to do it on my own or by running the autopanog program....

I am on gutsy and I have installed hugin using apt-get from the official repositories.

Check the following file that has the original pictures and the final hugin output.
I tried many different combinations but no success at all....
I had about 400 control points for this panoramic picture and hugin was saying also "Good Fit" before press stitch :(

[http://filebeam.com/41866cdf254f645ed9f8aa5c9dd8478a](http://filebeam.com/41866cdf254f645ed9f8aa5c9dd8478a)

---

### Post by roketa on 2008-01-16
In preferences I have checked "use alternative enblend program" end I have written "enblend" in text box. Also I think enblend only works if you set output format to tif in stitching tab and click on checkbox "use enblend".  

I use newer compiled from source version though.

---

### Post by CyberAngel on 2008-01-16
> **roketa said:**
> In preferences I have checked "use alternative enblend program" end I have written "enblend" in text box. Also I think enblend only works if you set output format to tif in stitching tab and click on checkbox "use enblend".  

I use newer compiled from source version though.

Maybe it is that....
I am always using high quality jpeg output!
I will try it and keep this thread informed.

Anyway even if I solve my problem, still I have the issue with the control points.

---

### Post by CyberAngel on 2008-01-18
I think that I found the reason of why Hugin can`t create automatically control points!!!
Maybe it is the ntfs partition that I am keeping my images! If I copy my images on my Desktop (reiserfs partition) then it works fine.
This is weird of course because autopanog can create them successfully...

As for the enblend yes it is working only on tiff output....
It has a check box that says that...

Now my problem is that the tif output is not working!!! :|
It is creating the separate tif files but not the final output!!

---

