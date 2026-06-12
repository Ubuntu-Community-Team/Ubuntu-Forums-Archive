---
title: "Which version of Mythbuntu"
date: 2009-08-09
forum: Mythbuntu
---

### Post by HW_Hack on 2009-08-09
So I should be building my system this week - my one constraint for several reasons is using a Hauppage 1600.

Fairly new Asus mobo and Nvidia graphics card

So is there strong reason to go with 8.10 or 9.04 ?

From a technical point (with the 1600) I want the latest drivers / best detection of HW. This will be a single purpose machine solely handling front-end and back-end Myth services. So fancy ubuntu GUI features ect. are not important. Just want a fairly simple install and solid operation.

THANKS IN ADVANCE

---

### Post by dano1 on 2009-08-10
had no probs with the 1600, after the learning curve(new ubuntu/linux user) with 9.04. am using jya,s repositories. Not sure if it's needed but updated v4l just for sure, also firmware update per myth wiki.

msi mobo, nvidia 9400 card.

hth, danny

---

### Post by klc5555 on 2009-08-10
> **HW_Hack said:**
> So I should be building my system this week - my one constraint for several reasons is using a Hauppage 1600.

Fairly new Asus mobo and Nvidia graphics card

So is there strong reason to go with 8.10 or 9.04 ?

From a technical point (with the 1600) I want the latest drivers / best detection of HW. This will be a single purpose machine solely handling front-end and back-end Myth services. So fancy ubuntu GUI features ect. are not important. Just want a fairly simple install and solid operation.

THANKS IN ADVANCE

As most of the tech magazine reviewers noted for plain-vanilla Ubuntu 9.04, it was basically a bug-fixed 8.10 with updated kernel and driver support. This extends to Mythbuntu also. A 1600 will work out-of-the-box, including a newer cx18 driver that fixes the "first analog capture" bug.

Since you use an NVidia card, you likely will have to do the simple "vmalloc" edit in Grub after installation to get the NVidia proprietary driver to load simultaneously with the cx18 driver for the 1600. This would affect both 8.10 and 9.04 (and 8.04, and 7.10, and ...)

You don't have an ATI Radeon card, so you won't have to worry about the Radeon bug that affects 9.04, but not 8.10.

So the short answer: certainly go with 9.04. It's a more solid, bug-fixed 8.10. The same features, only better.

---

### Post by HW_Hack on 2009-08-10
**Thanks for the info ! ** Looking forward to doing a fresh install ASAP. I'm sure there will be a few pot holes but glad to see the 1600 supported

---

