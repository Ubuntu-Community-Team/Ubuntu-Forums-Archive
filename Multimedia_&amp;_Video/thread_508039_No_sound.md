---
title: "No sound"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by Onay on 2007-07-23
I followed the comprehensive sound guide and have hit a roadblock at General help step 4.

Typing in sudo modprobe snd- does not show installed sound drivers, but instead tells me that the module is not found. However, when I type in sudo modprobe snd-emu10k1, I do not receive any messages at all. 

Alsamixer is using an intel chip that is not my standard sound card, and I also do not know how to change that. I have changed my sound settings to use my sound blaster audigy card as default.

I have opened volume control, and turned up the volume full on for everything, but none prevail!

I have also attempted to rebuild alsa from the source with a compilation, but when I am building it with the module assistant I receive a bunch of errors right at the end and it never reaches 100%. When I tried to create alsa from a fresh kernel, I lost my desktop and nothing was fixed.

So a quick summary: My sound card is detected, I can select it in many programs, but it doesn't seem to output any sound, or there must not be a correct driver installed. It seems that everything that I post is too specific and nobody gives me any replies, so please ANYBODY that has any input would be much obliged. I'll be back in an hour, thanks ahead of time.

---

### Post by Onay on 2007-07-23
Here's the error I get when building alsa from the source with the module assistant
```
/usr/src/modules/alsa-driver/include/adriver.h: In function                
 ‘snd_pci_orig_restore_state’:                                             
  /usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many      
  arguments to function ‘pci_restore_state’                                 
  make[6]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1         
  make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2                 
  make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2              
  make[3]: *** [modules] Error 2                                            
  make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'     
  make[2]: *** [compile] Error 2                                            
  make[2]: Leaving directory `/usr/src/modules/alsa-driver'                 
  make[1]: *** [build-stamp] Error 2                                        
  make[1]: Leaving directory `/usr/src/modules/alsa-driver'                 
  make: *** [kdist_image] Error 2
```
That was at the very bottom of the log file. Any ideas?

---

### Post by Onay on 2007-07-23
Here's the error i get when I compile manually.

When I try to make it after configuring, heres the message...
```
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2
```
That's at the very bottom

when I make install the entire body of text is just errors. What could I be doing wrong? I'm following the comprehensive sound guide to a T!

---

### Post by dragonwings on 2007-07-23
sudo asoundconf list                         to get list of sound cards


sudo asoundconf set-default-card ( type  sound card here)


eg for mine i put                   sudo asoundconf set-default-card Audigy2

---

### Post by Onay on 2007-07-24
Thanks, after restarting my computer, my volume control icon at the top has a blocked kinda sign in front of it. When I try to open it I get a message that reads "No volume control Gstreamer plugins and/or devices found. It must have happened when I was rebuilding alsa from the source. Poop :(

aplay -l just tells me there's no device now.

---

