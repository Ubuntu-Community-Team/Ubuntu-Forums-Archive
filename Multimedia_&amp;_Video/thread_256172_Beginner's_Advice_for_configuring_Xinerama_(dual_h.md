---
title: "Beginner's Advice for configuring Xinerama (dual heads)"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by bobmct on 2006-09-12
As has been posted my many a new ubuntu user alike... the task of successfully configuring dual heads is daunting to say the least!
I struggled for 2 to 3 days and required the assistance of a more seasoned professional than myself.  BUT, the bottom line turned out to be quite simple and one that was easily overlooked.  The focus was on the configuration of the xorg.conf file which seemed obvious to me and others I am sure.  However, what MY cause preventins a successful config was NOT using the manufacturer supplied graphics card driver!!!

I am using a Matrox G450 and I downloaded the most current driver(s) from their site.  But in my desparate moves to get this working I must have reactivated the ubuntu provided generic driver.

Once I realized that and copied over the manufacture's version then started X again - BOINGO!!!   dual heads just like I wanted.

So, the purpose of this post is basic:  review and repeat your steps, one by one, IN DETAIL, being sure to check dates, sizes and versions, to assure that what you have is what you THINK you have.

Good luck.  Hope this helps.

---

### Post by frodon on 2006-09-13
This thread may help you :
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

