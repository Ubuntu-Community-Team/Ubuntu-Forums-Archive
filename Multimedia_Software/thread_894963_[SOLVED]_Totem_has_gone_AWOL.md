---
title: "[SOLVED] Totem has gone AWOL"
date: 2008-08-19
forum: Multimedia Software
---

### Post by matrooswolf on 2008-08-19
I tried Totem-Xine, but it gave me horrible colors, so I removed it and reinstalled totem-streamer.  

But now Totem won't start from my shortcut (file/folder does not exist), nor will it start from the applications menu (same error).
The totem plugin for firefox is also not working (missing plugin).  Totem is also not listed in about:plugins.

But strangely all the packages are installed. Totem-gstreamer is installed.  Totem-mozilla is installed.  I can see them in synaptics, and in the Add/remove menu from applications.  
And: I can start Totem-gstreamer with ALT-F2.

Anybody any ideas what happened?  
And how I can get some sanity back on my desktop?

---

### Post by matrooswolf on 2008-08-20
Problem solved.

I had both totem-gstreamer and totem-xine installed and I had used
```
sudo update-alternatives --config totem
```to switch between them.  

After removing totem-xine and running the above command again, it said: there is only one totem installed, so there is nothing to choose from, and didn't give any options.
But I guess totem-xine was still selected.

So I reinstalled totem-xine
ran ```
sudo update-alternatives --config totem
``` again, 
now had the option to choose totem-gstreamer (which I did), 
and removed totem-xine again.

Everything works as before

---

