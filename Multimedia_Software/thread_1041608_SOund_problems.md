---
title: "SOund problems"
date: 2009-01-16
forum: Multimedia Software
---

### Post by Doulpe on 2009-01-16
How come my sound doesn't work? When I go to Preferences>Sound there are no drivers listed for the device and I'm wondering why is this? I have tried a couple solutions like Reinstalling ALSA when I try sudo ./alsa_1.sh it works but when I do ./a;sa_1.sh I get this:


 sudo ./alsa_2.sh 
`/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
cp: cannot create regular file `/lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver*/modules/*': No such file or directory
cp: omitting directory `/lib/modules/2.6.27-7-generic/kernel/sound

How can I fix my sound??

---

### Post by markbuntu on 2009-01-16
Go to System/Administration/Users and Groups and add your user to the group "audio".
Then log out and log in and see if that works.

---

### Post by Doulpe on 2009-01-17
When I go there all I see is Manage groups... so I'm not quite sure how to do what you said.

---

### Post by Doulpe on 2009-01-17
*Double Post*
I Don't think thats the problem.

---

