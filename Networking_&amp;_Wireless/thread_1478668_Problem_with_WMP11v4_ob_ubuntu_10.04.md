---
title: "Problem with WMP11v4 ob ubuntu 10.04"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by diesel7186 on 2010-05-10
I am trying to hook up my Wireless card WMP11v4 and for some reason I cannot get it to work. I had a friend of mine try to do it with me and he cant get it to work. 

I download ndiswrapper as well as the .inf file needed for it in the old ubuntu versions.

I am wondering if anyone knows how to get the problem resolved where I am able to get the wireless connection fixed.

Thanks, 

Donkey

---

### Post by pdc on 2010-05-10
here is a diagnostic script that analyses your wireless setup

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

download it; run it; read it; it should offer solutions;

you can post the full results back here for folks to see and help

---

### Post by IndyGunFreak on 2010-05-12
> **pdc said:**
> here is a diagnostic script that analyses your wireless setup

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

download it; run it; read it; it should offer solutions;

you can post the full results back here for folks to see and help

I'm not really sure how that would have helped.... Looking at the data it gives, all it would have really shown it was not connected, which he knew.

Anyway, for anyone else using this device w/ NDISwrapper.  Go to Linksys' site and download the "Setup Wizard"... It has a newer lsipnds.inf file than just the "driver" download.  You will not need wine or anything to run the setup wizard to get the inf file, it's inside the zip file.  Install the lsipnds.inf file in ndiswrapper, and you should be golden.

IGF

---

### Post by dwpbike on 2012-07-19
tanks, indy, still valid advice.  ended a multi-year absence on nephew's dell.  now to amazon to replace antenna he broke.

---

### Post by wildmanne39 on 2012-07-19
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

