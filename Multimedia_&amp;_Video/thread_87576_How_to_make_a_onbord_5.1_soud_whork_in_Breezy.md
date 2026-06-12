---
title: "How to make a onbord 5.1 soud whork in Breezy?"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by fmasi on 2005-11-08
Helo i have a onbord sound  nVidia Corporation nForce2 AC97 Audio Controler.
 I just got a creative 5.1 speekers and i like to know how to make them whork as 5.12 in breezy. My sound bord have only 3 plugs at the back 1 is the normal out plugin that i use as front speekers i have an aux in that i pluged the rear speekers and i have the mic plugin that i use as the center and subwofer.

I figure out thet selecting Duplicate font switch in volume controle make my rear speekers duplicate the front peekers sound. My sub seem to be whorking so i went chek on that and i figure out that if i take all the pluins from the back of my soud bord and just leav the center and sub speekers i have no soud at all so i ges the sub is geting to whork by ether the front cable or the rear one. but it is supose tu use the 3 cable conected to the microfone plug as well as the center but nether of them whork the center dont work at all.

I like to know how to make it realy whork in 5.1 so i could watch some nice dvd in 5.1.  Please help me slove that.

If you have enny program that test each speeker individualy i will be hapy to thx.

---

### Post by 0okami on 2005-11-15
looks like me and you are in this together ;) 

try issuing this command in the terminal.. 
speaker-test -c6 -D plug:surround5
(i have no idea what -c6 -D parameters are) 

When I did that, it sent static noise to each speaker, however, there were a few speakers that didnt work. So, im currently looking into that. 

If i find out anything new, i'll keep you posted. 
Do so as well for me ok?

*I just re-read your post... seems you already know this ;) sorry. *

---

