---
title: "[SOLVED] Opera won't play WMV files"
date: 2008-09-09
forum: Multimedia Software
---

### Post by socngill on 2008-09-09
Hi guys.

Had Firefox running for a few months exactly as I like it, but thought i'd give Opera a go.  Have to say it is great. Seems much quicker and "easier on the eye" than Firefox - but for some reason I can't play WMV files.  At the moment I use an add-on in Firefox (Media Connectivity I think) which plays the files in VLC.  However, in Opera it asks for a plug in, but I can find no way of installing a plug-in in Opera.  There is no menu option for it and I can't find anything that will work.  Did a quick google search and found very little info of any use.  

If anybody can help it would be great as I would like to check Firefox as it hurts my eyes to use - but this is the only issue I am having with changing.

Thanks in advance.

---

### Post by gandaran on 2008-09-09
to install vlc plugin. (if thats what you want) open synaptic package manager, scroll down to **mozilla-plugin-vlc** mark for install and click the apply button.
or the command line:**sudo apt-get install mozilla-plugin-vlc**

---

### Post by JAwuku on 2008-09-09
Another alternative is to use mplayer-plugin. Install it:

```
sudo apt-get install mozilla-mplayer
```

It works well on my Kubuntu 64-bit Hardy using Opera 9.50.

---

### Post by socngill on 2008-09-10
Cheers guys. Seems to have done the trick!

---

