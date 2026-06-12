---
title: "SB Audigy 2 ZS Plat no sound at all! Please help!"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by MrSpiffdifilous on 2007-07-19
I've been tring to get my soundcard to work for 2 days now to no avail. I was following the page > [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)  instructions when I got this error message:

>  &#9474; In file included from /usr/src/modules/alsa-driver/include/adriver.h:858,  &#9618; 
 &#9474;                  from                                                      &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/sound/driver.h:46,                    &#9618; 
 &#9474;                  from /usr/src/modules/alsa-driver/acore/hwdep.c:22:       &#9618; 
 &#9474; include/linux/pci.h:541: error: expected identifier or ‘(’ before          &#9618; 
 &#9474; numeric constant                                                           &#9618; 
 &#9474; In file included from                                                      &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/sound/driver.h:46,                    &#9618; 
 &#9474;                  from /usr/src/modules/alsa-driver/acore/hwdep.c:22:       &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h: In function                &#9646; 
 &#9474; ‘snd_pci_orig_save_state’:                                                 &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many  
arguments to function ‘pci_save_state’                                     &#8593; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h: In function                &#9618; 
 &#9474; ‘snd_pci_orig_restore_state’:                                              &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many       &#9618; 
 &#9474; arguments to function ‘pci_restore_state’                                  &#9618; SUBDIRS=/usr/src/modules/alsa-driver                                       &#8593; 
 &#9474; O=/lib/modules/2.6.20-16-generic/build CPP="gcc-4.1 -E" CC="gcc-4.1"       &#9618; 
 &#9474; modules                                                                    &#9618; 
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'     &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/hwdep.o                       &#9618; 
 &#9474; In file included from                                                      &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/sound/driver.h:46,                    &#9618; 
 &#9474;                  from /usr/src/modules/alsa-driver/acore/hwdep.c:22:       &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition    &#9618; 
 &#9474; of ‘jiffies_to_msecs’                                                      &#9618; 
 &#9474; include/linux/jiffies.h:268: error: previous definition of                 &#9618; 
 &#9474; ‘jiffies_to_msecs’ was here                                                &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition    &#9646; 
 &#9474; of ‘msecs_to_jiffies’                                                      &#9618; 
 &#9474; include/linux/jiffies.h:290: error: previous definition of 
of ‘msecs_to_jiffies’                                                      &#8593; 
 &#9474; include/linux/jiffies.h:290: error: previous definition of                 &#9618; 
 &#9474; ‘msecs_to_jiffies’ was here                                                &#9618; 
 &#9474; make[6]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1          &#9618; 
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  &#9618; 
 &#9474; make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618; 
 &#9474; make[3]: *** [modules] Error 2                                             &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'      &#9618; 
 &#9474; make[2]: *** [compile] Error 2                                             &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618; 
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646; 
 &#9474; make: *** [kdist_image] Error 2      

i have no idea what to do. before I followed these instructions my card was showing up, just not working. Now I sees that the device is there when I use >  lspci -l   But thats it. When I go into Sound Settings there are no devices listed. What do I do?

---

### Post by fredj on 2007-07-19
I have a soundblaster audigy 2 ZS (not the platinum) model and it was detected under Feisty and worked
fine with some tweaking of the alsa mixer. Perhaps by trying to install software you have made things worse.
My card and yours use the same driver although you may have to do some extra tweaking to get the front
panel to work.

---

### Post by MrSpiffdifilous on 2007-07-20
which code are you using? I've been trying "emu10k1" and it hasnt worked. I only started tweaking because it didnt work in the first place. like I said, it was recognized but not actually working for some reason.

---

### Post by fredj on 2007-07-21
Forget about lspci that only detects the physical device. Try opening a terminal and type
sudo lshw -class sound
Then look for your sound card and look for the word driver=. If you find the word UNCLAIMED then it means
that a driver is no longer being loaded for your soundcard. Post the output from that here
The trick to getting most soundcards to work is opening the Alsa mixer (double click on the speaker icon in
the taskbar) go to the Edit->Preferences menu and add all the playback and record volume controls (and
switches) make sure they are unmuted and suitable volume level are set (around 70%).

---

