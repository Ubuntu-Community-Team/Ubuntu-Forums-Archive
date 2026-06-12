---
title: "NDISwrapper &quot;module could not be loaded&quot;"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Tarkan640 on 2011-02-13
I am trying to set up wireless on my desktop. It has no internet whatsoever, I could hook up ethernet but I would have to transfer the whole computer across the house. I installed ndiswrapper from the installation CD. 

I also installed NDISGTK which is some GUI with the ndiswrapper. I clicked Install New Driver, I am pretty sure I have all the other necessary files along with the mn710.inf, but I get the error:

"Module could not be loaded. Error was:

FATAL: Could not read '/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory"

After clicking ok, it shows the driver there, but my card is still not working, no lights or anything. Does anyone know what that error is and how I can get it working?

thanks,
jonny

(SOME ADDITIONAL INFORMATION:

ndiswrapper -l shows driver installed and device present
)

---

### Post by dmizer on 2011-02-14
Most cards do not need ndiswrapper these days. What chipset do you have?
```
lshw -C network
```

---

