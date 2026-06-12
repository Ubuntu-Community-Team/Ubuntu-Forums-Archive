---
title: "install flash player in EEEpc"
date: 2009-04-19
forum: Multimedia Software
---

### Post by rooob on 2009-04-19
hello, im new here and i need some help

i have a EEE pc (the mini laptops) and everything waas working fine until i decided to upgrade it to flash player 10. 

i have tried different ways and none have worked, now i even remoe the flash 9 that in some sites used to work fine.

here are some ways i have tried
- right click on the .deb file and “install DEB file”, and the error that i got was: cnnont install package, please check your installation and ty again

- in the Terminal, coping the libflashplayer.so to usr/lib/mozilla/plugins it seems it copies but still not recognized by firefox2

- using the “install missing plugins” function in firefox, it just download and seems to work but then after you restar firefox, still asks for the plugin

- using sudo apt-get install flashplugin-nonfree it says: 
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing sl (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.us.debian.org_debian_dists_stable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

so can you help me install flash player, please?

thank you

---

### Post by rooob on 2009-04-20
anyone? :(

---

### Post by cyclone5uk on 2009-04-21
I’ve had a few problems with Flashplayer on my eepc 901 but eventually got it working.

Firstly you’ll need to make sure you’ve completely cleaned off all traces of your previous flash installs:

```
sudo apt-get remove --purge flashplugin-nonfree
```

That should completely remove the plugin and it’s configuration files.

Grab a fresh version of the .deb package for flash 10 from the adobe site and try to install again.

---

### Post by rooob on 2009-04-22
Hello, i tried that, but i got this message:

/home/user> sudo apt-get remove --purge flashplugin-nonfree
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing sl (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.us.debian.org_debian_dists_stable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

am i doing something wrong there?
thanks

---

### Post by cyclone5uk on 2009-04-23
Hmm, I’m not an expert on this but I think you may have filled your cache.

Try doing:

```
sudo apt-get clean --purge
```

And then repeat the instructions from before.

This will completely remove files from the cache used or not. This is good to do after a large update.

---

