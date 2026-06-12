---
title: "Wireless probems in 9.10"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by ecoulthard on 2010-03-17
Hello,

I purchased an Acer Aspire 7535-5415 and installed 9.10 on it in January. Ever since I have had no end of trouble with the wireless. I can connect to wireless but the connections usually don't last for long. About 5-10 minutes after startup my wireless is gone and I cannot reconnect without rebooting. I recently tried booting ubuntu 10.04 from a cd and all my wireless problems went away. Should I upgrade to 10.04 even though it is still in development or is there anything I can do to get wireless working properly in 9.10?

Thanks,
Eric

---

### Post by bkratz on 2010-03-17
> **ecoulthard said:**
> Hello,

I purchased an Acer Aspire 7535-5415 and installed 9.10 on it in January. Ever since I have had no end of trouble with the wireless. I can connect to wireless but the connections usually don't last for long. About 5-10 minutes after startup my wireless is gone and I cannot reconnect without rebooting. I recently tried booting ubuntu 10.04 from a cd and all my wireless problems went away. Should I upgrade to 10.04 even though it is still in development or is there anything I can do to get wireless working properly in 9.10?

Thanks,
Eric



Well, as you know risks are involved in unreleased software, it really depends on how critical your system is.  I have been running 10.04 on one of my systems and have found it to be pretty stable. However, I still run 9.04 on my critical system, since I did have problems with wireless in 9.10.  I did eventually go back to 9.10 and upgraded the kernel to one of the versions in 10.04 and it worked very well. I used this site for help on that as a third alternative, but you are only about a month or so away from release of 10.04 if you can wait.

Here is the site that helped me upgrade the kernel if interested.

[http://unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint](http://unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint)


If interested you might do a 

uname -r

in the version you feel works to find out which kernel it is

---

