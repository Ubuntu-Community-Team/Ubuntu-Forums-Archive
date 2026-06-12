---
title: "Flash Update Problem..."
date: 2010-02-12
forum: Multimedia Software
---

### Post by Coda_ on 2010-02-12
...I have 9.04, and when I try to watch a video on youtube, it gives me this...

>             				 					 						Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/"). 						Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/"). 					
 				



...I followed the link, and installed the version it suggested for 9.04, but it doesnt work...I close out Mozilla, open it again, and still get the same message...am I  missing something?...

---

### Post by HappyFeet on 2010-02-12
Go [here]("http://get.adobe.com/flashplayer/") and download the tar.gz flash file. Right click it and **extract here**. Put the resulting **libflashplayer.so** file into /usr/lib/mozilla/plugins. Restart firefox.

---

### Post by lovinglinux on 2010-02-12
For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by Coda_ on 2010-02-12
> **lovinglinux said:**
> For 32bit see [this]("http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2").

For 64bit see [this]("http://ubuntuforums.org/showthread.php?t=1358591").

...got it...thanks...

---

