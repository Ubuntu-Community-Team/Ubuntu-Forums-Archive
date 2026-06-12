---
title: "Getting tv tuner card to work..."
date: 2011-11-25
forum: Multimedia Software
---

### Post by nd456 on 2011-11-25
I need help getting my Happauge WinTV-HVR-1850 working on ubuntu (11.10)...
Here is a link to the manufacturers website:
[http://www.hauppauge.com/site/products/data_hvr1850.html](http://www.hauppauge.com/site/products/data_hvr1850.html)
Any help would greatly be appreciated

---

### Post by arisp on 2011-11-26
Take a look at [this post.](http://ubuntuforums.org/showthread.php?t=1648472)

---

### Post by nd456 on 2011-11-26
Forgot to mention I'm a noob...

---

### Post by Johnny Buffalkill on 2011-11-30
If I'm interpreting this link correctly . . .

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800)

 . . . then the drivers should already be included in the kernel, so it should just be a matter picking decent tuner software.

My suggestion would be to use Kaffeine, which you can install from the repositories.  To channel scan in Kaffeine, select 'Television/Configure television'.  In that box, select 'Device 1', then go to the Source dropdown to select your source.  If you want OTA broadcast, select                                    "us-ATSC-center-frequencies 8VSB".  I'm not sure which one you would want for cable, but there aren't too many choices so trial and error should work.  Once you have selected a source, click OK.   Then choose 'Television/Channels' and in there do a channel scan.  If it finds channels then its working.


If all this works and then you get some kind of demux error, paste
                                   
```
sudo apt-get install libxine1-all-plugins
```into terminal

---

### Post by MartyBuntu on 2011-11-30
I'm pretty sure the pci-e version of the HVR-1850 is unsupported in Linux, according to the Wiki.

I should know...I bought one, unfortunately.


See this...
[http://linuxtv.org/wiki/index.php/Hauppauge](http://linuxtv.org/wiki/index.php/Hauppauge)

---

### Post by MartyBuntu on 2011-11-30
> **Johnny Buffalkill said:**
> If I'm interpreting this link correctly . . .

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800)

No, that's the 1800, not the 1850.

---

### Post by Johnny Buffalkill on 2011-11-30
Hmm,  I thought the only difference was that the 1850 came with a remote.  Evidently there's more to it than that.  Drag.

---

