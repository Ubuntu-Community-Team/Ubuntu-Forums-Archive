---
title: "Equivalent for mstsc?"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by fekioh on 2011-09-13
Hello,

I am trying to use SonicWALL SSL-VPN NetExtender to connect to my PC at work. I have already installed netExtender to my ubuntu laptop. 

Under widows, I would run netExtender, enter user name, password, domain etc. and then , when connected I would go Run>mstsc and a new window would open connected to the remote PC.

Now, I can successfully connect to netExtender (by running it through the terminal) but then how can I actually open the window with the connected PC desktop? i.e. what is the equivalent of mstsc?

Thanks

---

### Post by SlugSlug on 2011-09-13
[http://ubuntuforums.org/showthread.php?t=1542306](http://ubuntuforums.org/showthread.php?t=1542306)

---

### Post by fekioh on 2011-09-13
Thanks,

rdesktop -0 -f hostname

... worked. -f is for fullscreen

---

