---
title: "I ruined my sound trying to install OSS - Help!"
date: 2009-07-21
forum: Multimedia Software
---

### Post by ubiedubie on 2009-07-21
I have previously compiled and installed the X-Fi Drivers for my sound card.

I then followed [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

After uninstalling Pulse and disabling ALSA I tried to install OSS and then it just gave me a load of error messages saying things are in use by ctxfi and things.




```
(Reading database ... 133841 files and directories currently installed.)
Preparing to replace oss-linux 4.1-1052 (using oss-linux-4.1-1052_amd64.deb) ...
OSS not loaded.
 * Shutting down ALSA...                                                 [ OK ] 
Unpacking replacement oss-linux ...
Upgrading OSS - will not purge /usr/lib/oss.
Setting up oss-linux (4.1-1052) ...
Building OSS Modules for Linux-unknown 2.6.28-13-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Building module lynxone
Building module lynxtwo
Building module oss_ali5455
Building module oss_allegro
Building module oss_atiaudio
Building module oss_audigyls
Building module oss_audioloop
Building module oss_audiopci
Building module oss_cmi878x
Building module oss_cmpci
Building module oss_cs4281
Building module oss_cs461x
Building module oss_digi96
Building module oss_emu10k1x
Building module oss_envy24
Building module oss_envy24ht
Building module oss_fmedia
Building module oss_geode
Building module oss_hdaudio
Building module oss_ich
Building module oss_imux
Building module oss_midiloop
Building module oss_midimix
Building module oss_sblive
Building module oss_sbpci
Building module oss_sbxfi
Building module oss_solo
Building module oss_trident
Building module oss_usb
Building module oss_userdev
Building module oss_via823x
Building module oss_via97
Building module oss_ymf7xx
depmod -a
Forcing re-detection of installed soundcards
Starting Open Sound System
mv: cannot move `/dev/snd' to `/dev/snd.osssave/snd': Directory not empty
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctxfi
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
Failed to disable conflicting sound drivers
Reboot and try running soundon again

Also check that you have not compiled sound support statically
into the kernel.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...

```

---

### Post by igorzwx on 2009-07-21
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
QUOTE:
**Troubleshooting**

 If you run into problems, follow these steps first: 
 
**Recovering From a Failed .deb Install**

 If you use the .deb package and it fails to install completely, [use this procedure]("http://ubuntuforums.org/showpost.php?p=5055305&postcount=105") to remove it. 
 
**Consult the OSS wiki**

 The wiki's [Troubleshooting page]("http://www.opensound.com/wiki/index.php/Troubleshooting") may already have an answer to the problems you have. 
 
**Additional Support**

 If you have OSS installed properly, but still have issues, the OpenSound project has free user support forums and an IRC channel. Be sure to include the output from these commands so the experts don't have to prompt you for them 
ossmix
ossinfo -v3Also, you'll want to note if the osstest command works and plays sound. 
 
**Forums**

 You can make a thread on [the OpenSound user forums]("http://www.4front-tech.com/forum/index.php").  
 
**IRC**

 [Freenode]("http://freenode.net/irc_servers.shtml") hosts the OSS support channel (#oss). You can paste your support information from the aforementioned commands [here]("http://oss.pastebin.com/") 
 
**Reverting to ALSA**

 NOTE: I've tested this procedure (on an Intrepid install) and was successful, but some people are complaining that it does not work. If you see any errors, please respond to the forum post. Some users wish to revert back to ALSA to try Creative's X-fi drivers or maintain complete Ubuntu compatibility. [Click here]("http://ubuntuforums.org/showpost.php?p=5539687&postcount=331") for the procedure.

---

