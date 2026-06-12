---
title: "How to manage Color in MacBook Pro 9,2 running with Quantal"
date: 2013-02-09
forum: Multimedia Software
---

### Post by bustamanteguevara on 2013-02-09
Hi you all, 

I recently installed Quantal Quetzal 12.04 in a Macbook Pro 9,2. Everything works fine and I have been able to get around with the Mactell support 

[https://help.ubuntu.com/community/MacBookPro9-2/Quantal](https://help.ubuntu.com/community/MacBookPro9-2/Quantal)

however, there is one thing that I cannot fix: The collors in the display look wierd. It is like the computer was not using its full range of collors but a reduced one, and the collors look simplified. Here is a screenshot

[https://docs.google.com/file/d/0B_dNEZelsxheZmY2WGxoVldqWE0/edit?usp=sharing](https://docs.google.com/file/d/0B_dNEZelsxheZmY2WGxoVldqWE0/edit?usp=sharing)

So I am wondering why is this. Should I callibrate the color? Should I check for the drivers of the video card?

Any help would be valued!

---

### Post by bustamanteguevara on 2013-06-14
the issue is solved like this
One goes to where Mac stores its color profiles ( Macintosh HD/System/Library/ColorSync ) and you copy the color profiles available to an ubuntu folder. 

Then, in System Settings/ Color, you choose the profile that your computer uses, for this computer (Macbook Pro 9.2) it is Color LCD-00000610-0000-9CC3-0000-0000042730C0.icc you add it and it works after you close the display and reopen it. 

If you restart the computer the problem returns. I don't know how to solve that.

---

