---
title: "[SOLVED] how to load alsa modules into kernel spaces?"
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by diplomat.x on 2008-04-15
Step 4 of this tutorial [http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install) wants me to insert alsa modules into the kernel spaces. How to do that? 


> 4. Loading the ALSA modules 

Now insert the modules into the kernel space. 
```
   modprobe snd-ens1371
   modprobe snd-pcm-oss
   modprobe snd-mixer-oss
   modprobe snd-seq-oss
```

If you get an "init_module: No such device" error when you run this modprobe command, make sure that you uninstall all the sound related modules first. Use lsmod to check the installed modules and rmmod to uninstall. Then modprobe the new modules. See Troubleshooting for other solutions. To make module loading permanent, you have to add these lines to /etc/modules.conf (for Debian users, this means you have to create a file with these lines in /etc/modutils and the do update-modules).

---

### Post by diplomat.x on 2008-04-15
AMAZING......

I was stuck at step 4. Had turned comp. off. Just restarted and sound is backkkk......YAY !!
My alsa version is new toooo 

Success screen attached...   :guitar:

---

