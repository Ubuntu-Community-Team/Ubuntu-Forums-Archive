---
title: "[SOLVED] Trouble w/ nvidia proprieatary driver"
date: 2008-07-28
forum: Mythbuntu
---

### Post by boon2 on 2008-07-28
Hello,

I'm having trouble getting the proper nvidia restricted driver installed on my new installation of mythbuntu.  Here's what's happening:

1.  from the desktop I go to  System->Mythbuntu Control Centre.
2.  click on "proprietary drivers" button.
3.  click on "launch restricted drivers manager"

4.  A popup appears with NVIDIA accelerated graphics driver (latest cards) listed under Component.  The checkbox under the "Enabled" column is unchecked.  When I check it, it pops up a dialog telling me about the driver and offers an "enable" button.

5.  When I hit the "enable" button, it attempts to begin the download of the driver.  It immediately returns the error:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

When I go to the cited URL, The requested file is indeed not there.  However there is one called:  

nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb

i.e. ends in "45_i386.deb" instead of "44_i386.deb".  I'm assuming that this is just an update of the driver and that it is probably okay to use it?  If so, how does one go about telling apt to use a different file?

Thanks for the help.

---

### Post by laga on 2008-07-28
You need to update your packaging listings. It's as simple as running "sudo aptitude update" in a terminal window or clicking the appropriate button in whatever graphical package management tool you use.

---

### Post by boon2 on 2008-07-30
Excellent!  Thanks!

---

### Post by CoNMaN on 2008-07-31
Thanks for this.  Hope this helps me as well. I am experiencing similar issues trying to install the NVIDIA driver.

---

