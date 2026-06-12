---
title: "Ubuntu is not using the correct ethernet card driver"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by rre12 on 2010-09-28
I am using Realtek RTL8111/8168B[COLOR=#4040FF][COLOR=Black] and it is having trouble connecting. Occasionally it would connect. I noticed that the kernel is not using the correct driver for my card. It is using r8169 instead of r8168. I downloaded the correct driver at here [/COLOR][/COLOR][http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)[COLOR=#4040FF]

[COLOR=Black]After I successful installed the new driver, it would show up when I do [/COLOR][/COLOR]```
lsmod
```[COLOR=#4040FF], [COLOR=Black]but when I restart my computer, it would revert back to r8169.[/COLOR]
[/COLOR]

---

### Post by dineshs on 2010-09-29
Have you tried this?
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

---

### Post by rre12 on 2010-09-29
I did before posting this thread. The guide is a little out of date so I decided to create a new thread. I get some errors while doing some of the command even with root access. Also the new drivers from Realtek does not have some of the files mentioned in the guide so I am unsure.

---

### Post by jacksonz123z on 2010-10-22
I used the latest Realtek drivers and followed the instructions provided but had to run dpkg-reconfigure linux-image-`uname -r`
to complete the instillation.

OK all works well but I can only get 100Mb/sec speeds after using ethtool and unplugging power etc.

Has anyone succeeded in getting this to work at gigabit speed?

---

### Post by jacksonz123z on 2010-10-23
Right I fixed it.  The cat6 cable was the problem.  To my surprise when I swapped in a high quality cat6 cable between the computer and router I was able to use Ethtool to correctly set the speed.

Be aware of very cheap cables!

---

