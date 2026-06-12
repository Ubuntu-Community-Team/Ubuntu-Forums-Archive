---
title: "No Sound On Feisty"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by BlueBamboo on 2007-05-03
Ok, I think I had sound earlier, but I rebooted once and the sound was gone. Then I started tinkering around with the sound settings and haven't been able to get the sound back. I don't believe I had this problem at all on Edgy Eft. Also my sound card is an Creative Labs Soundblaster Audigy 2 ZS. 
I followed every single instruction on the "comprehensive sound problem" guide. Here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) 
Up until the point I started to type in and execute the line 
"sudo module-assistant a-i   alsa-source" 
in the alsa driver compilation section did things not work.  
It said building alsa-source step 1 and completed up to around 50 % before I got an error message. 
At the end of the log file, here is what it looked like: 
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function 'pci_restore_state'
make[6]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1 
make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: *** [modules] Error 2
make[3]: Leaving directory '/usr/src/linux-headers-2.6.20-15-generic' 
make[2]: *** [compile] Error 2
make[2]: Leaving directory '/usr/src/modules/alsa-driver' 
make[1]: *** [build-stamp] Error 2 
make[1]: Leaving directory '/usr/src/modules/alsa-driver' 
make: *** [kdist_image] Error 2 

Please help :confused:

---

### Post by Cigar Jack on 2007-05-04
The the following it got my sound working.

```
sudo apt-get install asoundconf-gtk
```

Then run asoundconf-gtk and select your sound card.

---

### Post by BlueBamboo on 2007-05-04
I installed and ran it but it says "You need at least one ALSA sound card for this to work!":(

---

### Post by oxmyx on 2007-05-04
For me, I found that in volume control/switches the Audigy Digital/Analog Jack box was checked.

---

### Post by BlueBamboo on 2007-05-04
I can't even get into volume control anymore.

---

### Post by Timokl on 2007-05-19
I have exactly the same problem. :-(

---

