---
title: "I broke my audio drivers"
date: 2011-04-12
forum: Multimedia Software
---

### Post by slackr007 on 2011-04-12
I was messing around trying to get drivers for a usb guitar amp a couple days ago and, in the process, did something to make the sound stop working.  I was trying to install OSS, but I don't think I couldn't get it to work, so I tried to go back to alsa.  

I'm using a Dell inspiron 1520 with Ubuntu 10.10 64-bit.  When I looked up my sound card on alsa's website I didn't find the exact chipset (mine is ICH8 family, alsa only lists up to ICH7) so I went with what was similar (snd-hda-intel) since my sound worked when I first installed ubuntu.

I followed LordRaiden's Comprehensive sound guide sticky thingy and got close to the end.  I ran the module-assistant and it made it to 49% and then quit.  Here's the last page of the log file with the errors:

```
In file included from include/linux/pci.h:58,                               
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,   
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:      
/usr/src/modules/alsa-driver/include/linux/pci_ids.h:2: fatal error:        
@CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory   
compilation terminated.                                                     
make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1        
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                   
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                 
make[3]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'       
make[2]: *** [compile] Error 2                                              
make[2]: Leaving directory `/usr/src/modules/alsa-driver'                   
make[1]: *** [build-stamp] Error 2                                          
make[1]: Leaving directory `/usr/src/modules/alsa-driver'                   
make: *** [kdist_image] Error 2
```

A couple other details that may or may not be useful:
[LIST]
[*]When I open sound preferences, there are no devices listed in the hardware tab and there is only a 'Dummy Output' listed in the output tab.  
[*]When I open the alsa-mixer, it's just a blank window.  If I click on edit>Sound Card Properties the whole window closes. 
[*]According to lspci, the kernel driver in use for my sound card is oss_hdaudio.
[/LIST]

Thanks in advance!

---

### Post by lidex on 2011-04-12
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by slackr007 on 2011-04-12
Here you go!

[http://www.alsa-project.org/db/?f=503ee7505d9aefb2d09e81ffa287710d6b440f31](http://www.alsa-project.org/db/?f=503ee7505d9aefb2d09e81ffa287710d6b440f31)

---

### Post by lidex on 2011-04-13
I would suggest going into synaptic and removing any OSS packages. Next reboot then re-install alsa.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Now rerun the info script.

---

### Post by slackr007 on 2011-04-13
Wow, that was easy.  Sound was muted on reboot, so no login ding had me scared!  Thanks a ton, lidex!

---

