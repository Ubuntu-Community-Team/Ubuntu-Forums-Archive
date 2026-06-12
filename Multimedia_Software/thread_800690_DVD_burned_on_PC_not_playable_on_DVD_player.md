---
title: "DVD burned on PC not playable on DVD player"
date: 2008-05-20
forum: Multimedia Software
---

### Post by cotcot on 2008-05-20
I converted an .avi film with Devede to an .iso ready to burn the DVD video. When I burn the .iso on a DVD (tried dvd-r and dvd+rw: both supported by my Lite-on DVD player) the result plays fine on the computer but gives "datadisk" on the DVD-player. I burned it with brasero, tried also with k3b (same result). I also tried to burn a DVD by copying the VIDEO_TS folder to the disk in k3b. All same result.

Any help ?

---

### Post by luisromangz on 2008-05-20
Did you burn the image or just created a data disk containing the iso file?

---

### Post by cotcot on 2008-05-20
Thanks for replying.
Yes I burned the iso correctly. It is doing the same as if I burn the DVD with the VIDEO_TS directly.

---

### Post by cotcot on 2008-05-20
Seems to be something wrong with Devede. I made DVD's with QDVDauthor or Kdenlive (I do not remember anymore) on the same brand of media with success.

---

### Post by SWilliams on 2008-05-20
I had the same problem on devede and mandvd.  The disc was formatted for NTSC, read fine on Ubuntu 8.04, but wouldn't read on my dvd player or my windows computer.

I searched for "devede" on these forums, and some other people are having the same problems.  No solutions yet.

---

### Post by serfcx on 2008-09-10
This sounds like the problem with mencoder in Gutsy. Hardy should be OK

---

### Post by ksennin on 2008-09-16
I have had that same problem with ManDVD and I AM running Hardy.

---

### Post by serfcx on 2008-09-17
This may link to a problem with genisoimage.
There is a post, which I have lost the link to, about the genisoimage in Hardy. The solution seems to be either to downgrade to an earlier release - I "pinned" a release in apt to genisoimage 9:1.1.6-1ubuntu3 - OR to compile genisoimage version 1.1.8 from source.
This has solved the problem for other people.

---

