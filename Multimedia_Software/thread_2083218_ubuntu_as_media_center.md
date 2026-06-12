---
title: "ubuntu as media center"
date: 2012-11-11
forum: Multimedia Software
---

### Post by jdawgvh on 2012-11-11
I am trying to run ubuntu as a media center.  I want it to run with the remote that I purchased from Amazon at:

[http://www.amazon.com/gp/product/B003TECP7U/ref=oh_details_o00_s00_i00](http://www.amazon.com/gp/product/B003TECP7U/ref=oh_details_o00_s00_i00)

I was able to find in the BIOS how to disable the keyboard, and ubuntu does indeed startup normally with no keyboard attached now.  However, this device must be throwing an error to GRUB because it keeps waiting for me to select an option to finish boot.  I would like to disable any errors that my new remote is producing in GRUB so that my media center loads normally.  Can someone help?

By the way, I should mention that I have been playing with the grub header file 00_header.  Right now it is default because none of the changes I made worked but I was playing with all of the recordfail and timeout options that I could find by Googling.  I changed recordfail to 0 (and removed the if statement).  I changed the timeout from -1 to 0 to grub default.  None of them worked.

---

