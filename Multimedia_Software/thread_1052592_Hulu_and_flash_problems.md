---
title: "Hulu and flash problems"
date: 2009-01-27
forum: Multimedia Software
---

### Post by snipazer on 2009-01-27
So heres the situation. I have Ubuntu 8.10. To watch Hulu videos, I installed the Adobe Flash-nonfree. It works, but not quite right. It takes about a minute or 2 to start. After that, everything loads fine. I don't have this problem in Vista, I'm dual booting. And I have a virtual machine in Vista running Ubuntu and that machine doesn't have this problem. All other flash videos load fine, like youtube. But I seem to be having this strange problem with just Hulu. Any help appreciated

---

### Post by EvilPizza on 2009-01-28
I'm also having a problem with Hulu in Firefox, but for me, the video doesn't load at all. All I see is a black box. However, for other sites like youtube, videos load perfectly fine. I run Ubuntu 8.10, and I have the apt-get flashplugin nonfree thing. Could someone help?

---

### Post by dalhamir on 2009-01-30
do you guys have 8.10 amd64? if so, try the prerelease version of flash 10

you can find out more about it here:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

and here's some terminal commands to get you the alpha version:

```
sudo apt-get purge flashplugin-nonfree
cd /usr/lib/mozilla/plugins 
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
sudo tar -xzf libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz

```

That got hulu working for me. it doesn't deal well with multiple monitors, but I don't think the old flash did either.

also note, this will remove the flashplugin from your package manager, so you won't recieve automatic updates through synaptic. keep an eye out for future flash10 developments

---

### Post by mozychan on 2009-01-30
I've been using alpha since release and it works great with sites like hulu.com.  Only it is incredibly sluggish in loading pages that are heavily loaded with flash like [Anime Media]("http://anime-media.com/").

-moose

---

### Post by snipazer on 2009-02-05
I do have the 64bit version. I'll try that out. Thanks a lot

---

