---
title: "pam_mount invert deprecated"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by Dretkal on 2010-06-04
Hey everyone,

I am somewhat new to the whole pam_mount file and its whole workings. I am currently getting an error 

that the "invert" attribute is deprecated, support will be removed in the next version.

I get this error when I try to log in as root. 

Here is the line in the pam_mount.conf.xml:

<volume sgrp="nomount" invert="1" fstype="cifs" server="mine" path="home mountountpoint="/home/%(USER) options="domain=mine" />

Any help you could give would be great. 

Thanks

---

