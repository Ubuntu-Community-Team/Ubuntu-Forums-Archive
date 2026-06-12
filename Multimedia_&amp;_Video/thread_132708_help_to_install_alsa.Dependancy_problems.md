---
title: "help to install alsa.Dependancy problems"
date: 2006-02-18
forum: Multimedia &amp; Video
---

### Post by alexal on 2006-02-18
i have a audigy 4 (non pro) and i am trying to do what here says: [https://wiki.ubuntu.com/HowToSetupSoundBlasterAudigyInBreezy?highlight=%28audigy%29](https://wiki.ubuntu.com/HowToSetupSoundBlasterAudigyInBreezy?highlight=%28audigy%29)
in order to have sound. But when in the second step i type: sudo dpkg -i alsa-source_1.0.10+1.0.11rc2-2_all.deb
it says:
 (Reading database ... 79677 files and directories currently installed.)
Preparing to replace alsa-source 1.0.10+1.0.11rc2-2 (using alsa-source_1.0.10+1.0.11rc2-2_all.deb) ...
Unpacking replacement alsa-source ...
dpkg: dependency problems prevent configuration of alsa-source:
 alsa-source depends on gcc | c-compiler; however:
  Package gcc is not installed.
  Package c-compiler is not installed.
dpkg: error processing alsa-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alsa-source

i searced a little at the package manager and some gcc are installed. Which filles exactly i have to download to make it work?

---

### Post by alexal on 2006-02-18
I think i posted too early.The drivers insalled(i had some updates to do).
BUT when i type; sudo module-assistant auto-install alsa-source 
the terminal says:sudo: module-assistant: command not found
this was the last step of the guide but does not work. do you know what is wrong?

---

