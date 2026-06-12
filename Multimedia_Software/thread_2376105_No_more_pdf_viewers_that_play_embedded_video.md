---
title: "No more pdf viewers that play embedded video?"
date: 2017-10-30
forum: Multimedia Software
---

### Post by vanagon on 2017-10-30
Having tried several options over the past few days, it seems there are no longer any linux pdf viewers that can play embedded video (on Ubuntu 16.04, at least).

In particular, a test file is on page 23 here:
[http://mirror.hmc.edu/ctan/macros/latex/contrib/media9/doc/media9.pdf](http://mirror.hmc.edu/ctan/macros/latex/contrib/media9/doc/media9.pdf)


I also found the pdfpc program, which has its own separate way of including video which is presumably incompatible with Adobe's windows pdf readers.  Even pdfpc failed to play the videos in the test files on the pdfpc website, however.


Has anybody found any solution to this?

For okular, I did try installing the phonon-backend-vlc package, and it still didn't work.

Thanks for any suggestions!

---

### Post by monkeybrain20122 on 2017-10-30
But embedded contents of your test file won't even play in Windows because it requires flash and a very outdated version too (according to adobe its pdf reader no longer bundled with flash player and the current version of flash won't work) Why would one create a document like that which is anything but portable,  which is a security risk and when flash is being phased out?

---

