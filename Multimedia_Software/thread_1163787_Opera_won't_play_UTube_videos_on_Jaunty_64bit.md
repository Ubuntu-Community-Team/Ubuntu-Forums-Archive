---
title: "Opera won't play UTube videos on Jaunty 64bit"
date: 2009-05-19
forum: Multimedia Software
---

### Post by cybrsaylr on 2009-05-19
UTube video clips played fine in both Firefox and Opera browsers in Intrepid 32bit. Did the upgrade to Jaunty 64bit and only Firefox plays UTube videos well. Opera just plays the audio with no video shown. On other sites video is also a hit or miss problem with Opera, while Firefox plays all videos very well. 
I'm using Opera 9.64 64bit version.

Anyone know how to get video to play with Opera?

---

### Post by gandaran on 2009-05-19
> **cybrsaylr said:**
> UTube video clips played fine in both Firefox and Opera browsers in Intrepid 32bit. Did the upgrade to Jaunty 64bit and only Firefox plays UTube videos well. Opera just plays the audio with no video shown. On other sites video is also a hit or miss problem with Opera, while Firefox plays all videos very well. 
I'm using Opera 9.64 64bit version.

Anyone know how to get video to play with Opera?
well the question is how did you install flash, which package and where?
somehow theres something deferent with the flash install that opera is not detecting it.

---

### Post by Arup on 2009-05-19
> **cybrsaylr said:**
> UTube video clips played fine in both Firefox and Opera browsers in Intrepid 32bit. Did the upgrade to Jaunty 64bit and only Firefox plays UTube videos well. Opera just plays the audio with no video shown. On other sites video is also a hit or miss problem with Opera, while Firefox plays all videos very well. 
I'm using Opera 9.64 64bit version.

Anyone know how to get video to play with Opera?


The problem is the x32 flash left over in your install. Go to synaptic, mark for complete uninstall the flashnonfree plugin and nsplugin. Then download Flash alpha 10x64 from adobe's side. Extract the tar, compy libflashplayer.so to /usr/lib/mozila/plugin and when you start Opera it will automatcially recognize it.

---

### Post by Heldrex on 2009-06-28
I followed that, (exact same problem) but it will not let me paste it, or extract to the location. I get the error; error moving file: permission denied.

I am moving it from my desktop to /usr/lib/mozilla/plugins

Edit: I know this is a two months old but maybe someone can help. :)

---

### Post by Heldrex on 2009-06-28
Solved the problem myself. I moved the plugin to it's own folder within home and had opera look for plugins within that folder as well. Not a perfect solution but it was easy.

---

