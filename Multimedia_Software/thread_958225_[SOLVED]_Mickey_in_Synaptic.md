---
title: "[SOLVED] Mickey in Synaptic"
date: 2008-10-25
forum: Multimedia Software
---

### Post by ububaba on 2008-10-25
I have been using Ubuntu/Kubuntu 8.04 without any sound problems.
Recently when I switched over to 8.04.1, cannot get microphone 
to work. 

Tried to update
alsa-base
alsa-utils
alsa-lib

Synaptic won't do it. It simply gets frozen. Several repeats have
not helped at all. I would like help in getting the sound back on
the mike and Synaptic working. Thanks

---

### Post by ajgreeny on 2008-10-25
If you have any broken packages showing in the system tray of synaptic, use the **Edit->Fix broken packages** from synaptic menus and see if that helps.

---

### Post by gandaran on 2008-10-25
is the microphone enabled or muted in volume control?

---

### Post by ububaba on 2008-10-25
Apparently the number of broken packages is ZERO.
I have fiddled around with the microphone. It is 
neither muted nor off. I have even installed a 
brand new one. :(

Freezing of Synaptic must be the nucleus of the problem.

---

### Post by ububaba on 2008-10-25
Following the methods shown on this thread:
[http://ubuntuforums.org/showthread.php?t=475013](http://ubuntuforums.org/showthread.php?t=475013)
downloaded the latest version of alsa > 
alsa-driver-1.0.17.tar.bz2
alsa-lib-1.0.17a.tar.bz2
alsa-utils-1.0.17.tar.bz2

from Alsa project to a directory.

All went well except when going through these steps  

```
cd alsa-driver-1.0.17
sudo ./configure
sudo make
sudo make install

```
[COLOR="Red"]
sudo make
sudo make install[/COLOR] 

both produced error. And the microphone is still dead. Thanks for you suggestions.

---

### Post by gandaran on 2008-10-26
have you tried changing sound capture driver in system » preferences » sound to alsa or any other driver?

---

### Post by ububaba on 2008-10-26
> **gandaran said:**
> have you tried changing sound capture driver in system » preferences » sound to alsa or any other driver?

Thanks **gandaran**. I have done that too. Synaptic is working alright now.
My conclusion is that "sound capture driver" somehow does not "unlock" or hindrance is still in place. Visually the mike is on full volume.

---

### Post by ububaba on 2008-10-26
Quite stupid or unbelievable. Switching the mike from the
back to the front did the trick. I have had it plugged
in the back for years. Thanks every one.:KS

---

