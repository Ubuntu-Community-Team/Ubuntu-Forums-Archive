---
title: "Arista- Nothing happens when file is added to queue"
date: 2010-05-25
forum: Multimedia Software
---

### Post by frankcm3 on 2010-05-25
I just downloaded Arista to convert avi's to mpegs for DVD's and also to view on a mobile device.

I add a file "movie.avi" as the source and device as DVD and then click "add to queue" and the file appears in the queue but nothing happens.

Also I believe that I have now downloaded all of the necessary gstreamer packages including the ugly multiverse. Any help would be great. Thank You.

---

### Post by mondomunchies on 2010-06-18
I have had the same trouble.  I have installed libdvdcss2 and all the others from medibuntu... etc.

I'm using 10.04 and arista 0.9.3.

---

### Post by mondomunchies on 2010-06-19
I have a quick fix.  I went to [https://launchpad.net/arista/+download](https://launchpad.net/arista/+download) and downloaded 0.9.5 which is not the default in the Ubuntu Software Center (0.9.3).  Using any of the patent-free presets still did not work, but the "patent-full" ones did.  I'm assuming 0.9.3 using "patent-full" would work too.  

If anyone knows how to fix this for real, that would be cool.

I also read the bug at [https://bugs.launchpad.net/arista/+bug/511194](https://bugs.launchpad.net/arista/+bug/511194).  Supposedly that fixes it by setting the width in presets to 8,32.  I'm not really sure what that means.

---

