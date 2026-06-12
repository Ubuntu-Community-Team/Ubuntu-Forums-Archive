---
title: "How do I know which NVidia driver package is for me?"
date: 2013-02-22
forum: Multimedia Software
---

### Post by Webnet on 2013-02-22
First thing I did was go to NVidia's web site and download the drivers.  Once these were in place I booted up to a black screen - never could login.  I had to login to command line and revert by enabling *nvidia-current*.

Here's what I've currently got configured: 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231784&stc=1&d=1361577045[/IMG]

Here's the results of using the various drivers in the screenshot:
[LIST=1]
[*]**nvidia-current** - TF2 is choppy, desktop is fine
[*]**nvidia-experimental-310** - Same results as above
[*]**Nouveau display driver** - Appears to be fine, but on bootup my top/left bar are off the screen, as if it's zoomed in just enough to not see though.
[*]**nvidia-current-updates** - Says something about updating OpenGL
[*]**nvidia-experimental-304** - Says something about updating OpenGL
[/LIST]

I've been trying to find documentation on which driver I should be using.  I found the wiki page for [Ubuntu NVidia drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and did some reading there.  But I don't see any video card models listed next to the packages.  Are video card models/drivers documented somewhere?

I hope some day Ubuntu will recognize the video card I have to intelligently pick the right driver.

---

