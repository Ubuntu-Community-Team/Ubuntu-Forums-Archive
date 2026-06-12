---
title: "X-Fi or Graphics"
date: 2008-09-24
forum: Multimedia Software
---

### Post by dido__15 on 2008-09-24
This is a bit of a strange one. I followed the following guide ([http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)) to compile the kernel to support my X-Fi.

Compiling the kernel, worked brilliantly, it did kill the graphics as i expected, i reinstalled them no problem everything was back to normal.

Then I installed the soundcard, no errors in the installation and after restart the sound input works perfectly, but it broke my graphics card in the same way compiling the kernel did. I tried re-installing the graphics card using the latest drivers from the official site, but when it comes to compiling the new nvidia kernel (because there isn't one to match my new custom kernel) halfway through building i get an error that it cannot find the file "nvidia.ko"

Bear in mind this worked fine before installing the X-Fi.

After uninstalling the X-Fi drivers the Nvidia drivers install fine once again (still on the same custom kernel) so it looks to be the X-Fi rather than the kernel that is causing the problem.

I've been trawling forums for days and read somewhere that the X-Fi's like to steal Graphics cards IRQs but i have no idea how to identify or resolve this issue.

It's rather important as this pc forms the basis of my recording studio so i need graphics and sound not one or the other. I did try for a while just using onboard sound but the quality was far below acceptable.

Many thanks in advance for any help.

Dido

---

### Post by dido__15 on 2008-09-26
*bump*

---

