---
title: "iriverter on Ubuntu LTS 10.4"
date: 2010-06-05
forum: Multimedia Software
---

### Post by bloozguy on 2010-06-05
ireverter will not launch due to a java problem:

"Could not find the main class: org.thestaticvoid.iriverter.ConverterUI"

In the past a solution was to add:

"export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jni"

before the java line in the script.
This does not correct my problem.:(

---

### Post by mh2ack on 2010-06-09
I had the same problem. I read and searched then tried going to their website ([http://iriverter.thestaticvoid.com/](http://iriverter.thestaticvoid.com/)). There is also a link to their website in the Ubuntu Software Center...  I uninstalled the version of Iriverter from the Ubuntu Software Center and then clicked the link to install the version 17.1 from their website and it works. Ubuntu needs to update the version of Iriverter in the Software center, or something. The problem probably has to do with that the current version contains nonfree binary codecs. I suppose they would need to do something similar to what they do for Adobe products.

Given what I was trying to do and following the lead of another thread I installed Avidemux. So now I will see which I like better.

---

