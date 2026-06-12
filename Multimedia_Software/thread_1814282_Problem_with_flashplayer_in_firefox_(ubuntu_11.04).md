---
title: "Problem with flashplayer in firefox (ubuntu 11.04)"
date: 2011-07-29
forum: Multimedia Software
---

### Post by adiasd on 2011-07-29
Hi Folks,

I upgraded recently to 11.04 (using Unity) and after that noticed that flash animations don't appear right in Firefox. There are blank areas in the animations as their content changes. 

The interesting thing is that when I use Chromium to display the same pages flash animations work perfectly, no blanks, run smoothly.

Has anyone come across this problem? Any clue on how to solve it?

Thanks

---

### Post by lovinglinux on 2011-07-29
Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

If you are using a 32bit system, then the wizard will have an option to use the flash plugin bundled with Chrome. Just change to that option in the wizard installation options. However, I would recommend using flash Beta from Adobe Labs, which is selected by default.

---

### Post by adiasd on 2011-08-01
Thanks for this hint. I installed and after I chose the 64 bits beta version of Adobe flashpayer plugin the problem was solved. Using the version from the repository (32 bits) didn't work.

---

### Post by HiFlight on 2011-08-01
I had the same problem except that Flash crashed when using Chrome.  It works fine with Firefox.  I fixed it by uninstalling Chrome!

---

