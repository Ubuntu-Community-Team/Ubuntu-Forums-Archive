---
title: "Quickcam Messenger"
date: 2005-10-28
forum: Multimedia &amp; Video
---

### Post by Yoriko on 2005-10-28
Hey, 
I am probably what one may call a "Noob" at linux, And I am trying to install the quickcam messenger driver on breezy.

I downloaded the driver from:
[http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/)

And the patch from there too, Patched the driver using

sudo patch -p1 < qc-messenger-0.8-fix

But when i try to "sudo make install"

I get this error (First line only because it makes 1000s, literally):

awk: cannot open /lib/modules/2.6.12-9-386/build/include/linux/version.h (No such file or directory)

This is maybe because i don't have kernal sources?
Which dev/kernal/whatever package would be best for me to get?
If it is because i don't have kernal source will this fix my other compile errors too?
Has anyone else successfully installed this driver, or should i give up and buy a linux compatable webcam?

Thanks in advance~



EDIT:
Running the ./quickcam.sh I get;

[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc


What should that be for ubuntu -.-?

---

### Post by hugelmopf on 2005-10-30
You might find the answers to your problem in a reply to another thread, that I just posted:
[http://ubuntuforums.org/showthread.php?t=81057](http://ubuntuforums.org/showthread.php?t=81057)
If it is not clear enough there, just ask there and I will try to help.

---

