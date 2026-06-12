---
title: "NVIDIA Drivers not working"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by JNowka on 2006-09-24
I Updated my machine an hour ago and now I can't get my Geforce4 MX 440 card to work under 2.6.15-27.  I was able to get into Gnome with working Nvidia drivers under 2.6.15-26.  I did go through the NVIDIA Drivers Guide by tselliot and made sure all setting were correct even step 7 under Problem Solving.  Yet still it refuse to load up under the new kernel.  Any idea what I can do?

---

### Post by JNowka on 2006-09-24
Ok, Noticed that the restricted modules for 2.6.15-27 didn't get installed trying that now.

---

### Post by tseliot on 2006-09-24
Read this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

---

### Post by JNowka on 2006-09-24
Thank you, Installing the restricted modules worked like a charm.  My problem was that i downloaded the nvidia-glx update.  When I updated the kernel it didn't even download the updated restricted modules.  So I had to download the restricted modules in order to get nvidia working.  Thank you for the article, I am reading it right now.

---

