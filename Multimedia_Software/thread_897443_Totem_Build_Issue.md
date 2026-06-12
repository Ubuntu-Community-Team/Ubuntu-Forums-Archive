---
title: "Totem Build Issue"
date: 2008-08-22
forum: Multimedia Software
---

### Post by gulshan karmani on 2008-08-22
Hi All,
 
We are trying to cross compile totem 1.5.0 version for arm.
 
GST versions: gst-plugins-base - 0.10.9 ;  gst-plugins-good - 0.10.4 ;  gst-plugins-ugly - 0.10.4 ; gst-plugins-bad -0.10.3; gstreamer - 0.10.9
 
During the build i am getting /usr/lib/libgstbase-0.10.so - wrong format error. Actually GST libraries (cross compiled) are  in a seperate path. I am setting -L option for the custom lib path. Also I have set GST_LIBS also. But still we get the issue
 
Just to check, we have renamed the /usr/lib/libgstbase-0.10.so, and then the build takes the cross compiled one from the custom path!
(We are getting same problem for libgstreamer also)
 
How can we overcome this issue. Any hints will be helpful.

Rgds,
Gulshan

---

