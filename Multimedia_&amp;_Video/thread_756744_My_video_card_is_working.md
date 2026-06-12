---
title: "My video card is working???"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by kjman83 on 2008-04-16
I used to use VISTA. At the moment, video quality was fairly good and didn't buffed but now I can see low qualityscreen. 
Where can I find my video card information in ubuntu?
Should I install my video card(ATI Radeon X1250) driver??

---

### Post by Existentialist on 2008-04-18
You should be able to see your graphics card with:

lspci | grep VGA

And you may have to go to system > administration > hardware drivers (restricted drivers), and enable the ati driver if you have not done so already.

---

