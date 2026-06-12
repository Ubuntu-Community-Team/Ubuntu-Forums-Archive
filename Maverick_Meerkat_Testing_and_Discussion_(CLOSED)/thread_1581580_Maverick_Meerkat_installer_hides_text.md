---
title: "Maverick Meerkat installer hides text"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mp035 on 2010-09-25
Hello all, I have tried to report this (minor) bug in the installer, but it seems impossible to report bugs with the installer (which is the first thing a new user sees) using the ubuntu-bugs application.  

The problem is that during install the text does not wrap correctly to the install window so half of each line is unreadable.

The install was on a toshiba laptop with 1280x800 resolution.

How do I report this?

---

### Post by kansasnoob on 2010-09-25
I filed this during iso-testing for the Beta:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

Does it apply? If so you could comment there.

If not, and if you've begun the installation from the Live Desktop rather than choosing "Install Ubuntu" when the try or install options appear, then you should be able to just change desktops and follow these instructions:

[https://help.ubuntu.com/community/ReportingBugs#Collecting%20information%20from%20a%20specific%20package](https://help.ubuntu.com/community/ReportingBugs#Collecting%20information%20from%20a%20specific%20package)

> Collecting information from a specific package

Press Alt+F2 to open the "Run Application" window, pictured above. Type ubuntu-bug <package name> and click Run. If you're not sure which package has the problem, refer to the instructions for finding the right package. 

In this case "ubuntu-bug ubiquity".

---

### Post by mp035 on 2010-09-25
Thanks Kansasnoob, I have posted a comment on your bug report, I think it's the same problem.   Thanks for the explanation of the ubuntu-bug application.  I was not putting the package name after the command and it mentioned that it couldn't find a PID, which confused me.  Your example was perfect.  Thanks again.

---

### Post by efflandt on 2010-09-25
I have same issue with text slideshow during install chopped off on right on 1080p HDTV (1920x1080), so I added a comment to that bug report.  I always have trouble searching or finding my way around launchpad on my own without a specific link to an issue.

---

