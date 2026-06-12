---
title: "trying to fix nvidia and now can't use most recent kernel"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by ralphhughes on 2007-10-21
I've been messing about trying to get Nvidia's drivers for my Geforce2 MX/MX400 for a while. I tried downloading the .run package from nvidia's web site and using the program envy on fiesty fawn, however being the first time I'd used linux back then (august 07) I couldn't get it to work and just used the 'nv' drivers which gave me higher screen res but no opengl.
   Upgraded to gutsy gibbon the other day and thought I'd have another go. I used envy but got the message that my kernel headers were not found and couldn't be downloaded by the package manager because they were obsolete or not found.
    I realised then that I'd booted accidentally, and for the first time in a while, into the old kernel on my boot menu (2.6.20-16) and that I had the new kernel (2.6.22-14) with headers that probably would have worked.
    Tried to boot into the newer kernel and the computer stays for about 5 minutes on the graphical ubuntu loading bar without it moving at about 1% then drops into a text mode with  several errors that I can't remember exactly that say fatal and have what look like hex codes to the righ of them. Then I'm dropped into a minimal shell type thing called 'Ash'.
   Older kernel works fine, but won't install the nvidia drivers. Newer kernel seems to have been broken by me trying to get the graphics card working. Whats my next step in fixing this?

---

