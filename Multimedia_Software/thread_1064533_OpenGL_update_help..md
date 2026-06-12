---
title: "OpenGL update help."
date: 2009-02-08
forum: Multimedia Software
---

### Post by Lawly on 2009-02-08
To play a certain linux game, (-Tremulous-), i need an OpenGL update, as ive been told. I was also told to get it i needed to go to System -> Administration -> Restricted Plugin Manager

This is in Ubuntu. and i need help.

---

### Post by xc3RnbFO8P on 2009-02-09
Did you check: System -> Administration -> **Hardware drivers**?

---

### Post by Lawly on 2009-02-09
> **Ringi said:**
> Did you check: System -> Administration -> **Hardware drivers**?

Thanks, i went there, went to activate the driver and i got this system error:

> SystemError: E:Type '--2009-02-08' is not known on line 1 source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.

in /etc/apt/sources.list.d/ there was one document: Medibuntu.list

Opening that..., the Medibuntu.list file showed me this information:
> --2009-02-08 19:57:08--  [http://medibuntu.org/sources/list.d/intrepid.list](http://medibuntu.org/sources/list.d/intrepid.list)
Resolving medibuntu.org... 87.98.242.110
Connecting to medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-02-08 19:57:08 ERROR 404: Not Found.



Should i delete the Medibuntu file? Or is there something i need to do.

---

### Post by xc3RnbFO8P on 2009-02-09
Remove third-party software medibuntu in Synaptic Package manager and install it again.

---

### Post by Lawly on 2009-02-09
> **Ringi said:**
> Remove third-party software medibuntu in Synaptic Package manager and install it again.

FAWK.
I really screwed things up.
Ok. I went to System -> Administration -> Synaptic Package Manager, (Clicked of course), and got this error message:

> E: Type '--2009-02-08' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


Where is the repository dialog?

---

### Post by xc3RnbFO8P on 2009-02-09
Try > sudo aptitude reinstall

---

### Post by Lawly on 2009-02-09
> **Ringi said:**
> Try

Thanks, but this is my consol text direct copy:
> brad@ubuntu-win:~$ sudo aptitude reinstall
[sudo] password for brad: 
E: Type '--2009-02-08' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: Type '--2009-02-08' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
E: Type '--2009-02-08' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
brad@ubuntu-win:~$ 



---

