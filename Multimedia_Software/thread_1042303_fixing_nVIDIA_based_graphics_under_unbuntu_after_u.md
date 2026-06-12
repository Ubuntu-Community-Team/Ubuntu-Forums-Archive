---
title: "fixing nVIDIA based graphics under unbuntu after upgrading 8.4 to 8.10"
date: 2009-01-17
forum: Multimedia Software
---

### Post by ceci123 on 2009-01-17
Hello everyone. 

This is not a question but rather a solution (that i wanted to share with others) to the notorious 800x600 resolution problem after upgrading from Ubuntu 8.4 to 8.10. 

After upgrading my Desktop from 8.4 to 8.10..everything went just find that is until i restarted. My screen went black! So I had to start my pc on a low resolution mode. I googled everywhere looking for hints and ideas for this problem and noticed that a lot of people had run into the same problem. (here are other links talking about the same or similar problem:
[http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)
[http://ubuntuforums.org/showthread.php?t=599620](http://ubuntuforums.org/showthread.php?t=599620)
[http://ubuntuforums.org/archive/index.php/t-968305.html](http://ubuntuforums.org/archive/index.php/t-968305.html)
[http://ubuntuforums.org/showthread.php?t=1002910](http://ubuntuforums.org/showthread.php?t=1002910)... 
) 
and the list goes on. Some claim that they fixed the problem by reinstalling other by some other method. 

**Here is what I did and it worked for me. I FOUND THIS LINK [http://packages.ubuntu.com/intrepid/i386/nvidia-glx-177/download](http://packages.ubuntu.com/intrepid/i386/nvidia-glx-177/download) AND DOWNLOADED and installed this nvidia-glx-177 package.** Also checked all these downloads. See image attached. 

I am not sure but you might want to follow their suggestion... that is [B]"You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) intrepid main restricted

Replacing fr.archive.ubuntu.com/ubuntu with the mirror in question. 
[/B]

After that went to System >> Preferences >> Hardware Drivers >> double click the NVIDIA Accelerated Graphics Driver (version 177) [Recommended].

This time it went and it actually downloaded the drivers and was able to activate the "NVIDIA Accelerated Graphics Driver (version 177) [Recommended]" radio button. 

Conclusion. The trick here is to somehow activate the "NVIDIA Accelerated Graphics Driver (version 177) [Recommended]". 

Good luck.

---

