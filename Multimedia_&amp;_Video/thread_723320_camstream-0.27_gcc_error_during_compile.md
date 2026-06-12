---
title: "camstream-0.27 gcc error during compile"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by shankscomp on 2008-03-13
I have been getting a gcc error while trying to install camstream.  I have checked and verified I have the correct gcc compiler installed.  What's next?

Here is the error I'm getting...
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check


I have attached the config.log as a zip file for your reviews.

I appreciate any assistance with this.
Thanks
Tim

---

### Post by mc4man on 2008-03-13
The first question would be do you have build-essential installed? Assuming yes check for g++ and g++ for the version(s) of gcc installed

edit: a quick ck. shows you will get a response from ```
sudo apt-get build-dep camstream
```  so run that also

---

