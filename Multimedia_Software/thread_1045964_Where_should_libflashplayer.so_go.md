---
title: "Where should libflashplayer.so go?"
date: 2009-01-21
forum: Multimedia Software
---

### Post by Innova on 2009-01-21
Something happened to my flash 9 installation for both konquerer and firefox.  Whenever I loaded a page with flash they would lock up for 5-10 seconds.  It got annoying so I figured I'd try flash 10, I see that there is a 64 bit version of it out now.

I downloaded the libflashplayer.so file from the firefox plugin site, but can't figure out where to put it.  I tried looking around in /usr/lib/ /usr/lib64/, and many other directories, and got into a whole bunch of symbolic links...where should this .so go?

I am running Ubuntu 8.04 64-bit.

---

### Post by omegamike3 on 2009-01-21
You'll want to put it in ~/.mozilla/plugins/ If you don't have the "plugins" directory there yet, just go ahead and make it. Start up firefox and you'll have the new flash 10. It works perfectly on my 64bit setup. :D

---

### Post by Innova on 2009-01-21
That did it, thanks for the quick response!

---

### Post by sisco311 on 2009-01-21
or /usr/lib/mozilla/plugins/

---

### Post by Innova on 2009-01-21
> **sisco311 said:**
> or /usr/lib/mozilla/plugins/

I tried that and it didn't work.  This is mostly a single user machine, so the .mozilla option will work, but if someone suggests a beter, system-wide location I'd give it a shot.

---

### Post by eshwar_andhavarapu on 2009-11-11
Thank you so much! that worked for me too! I have a shared profile between windows and ubuntu so i figured i should go ahead and put it in the .mozilla\plugins folder. There is also a plugins folder on the windows side but it wouldn't work I suppose.

---

### Post by leonbravo on 2011-06-18
I found three different locations:

/home/$user_name/.mozilla/plugins/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so


after checking files dates, I realised that the one is updated often by ubuntu (synaptic) is in adobe-flashplugin. I decided to erase the others and create hard links to the one in adobe-flashplugin. I was checking another option, but this one worked perfectly.

Cheers.

---

