---
title: "Having problems with sound"
date: 2009-01-14
forum: Multimedia Software
---

### Post by Doulpe on 2009-01-14
Ok, so I finished upgrading to ubuntu 8.10 and I notice that *Nothing* has sound. Everytime i try and change my sound devices etc. it says i need to configure my soundcard properly etc. I tried to reinstall Alsa because it's the one that seems to work the best. The first command sudo sh ./alsa_1.sh works no problem so I restart then try the second one:sudo sh ./alsa_2.sh I get this:



~/Desktop$ sudo ./alsa_2.sh 
`/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
cp: cannot create regular file `/lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver*/modules/*': No such file or directory
cp: omitting directory `/lib/modules/2.6.27-7-generic/kernel/sound/'

Any solutions that might able me to Have my sound back because i miss it :'( P.S. I already tried restarting ALSA

---

### Post by fluxbuntu_user on 2009-02-19
Having the exact same problem as described above. Was any solution ever found?

---

