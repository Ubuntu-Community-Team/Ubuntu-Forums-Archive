---
title: "Nvidia GPU temp from command line?"
date: 2009-04-28
forum: Mythbuntu
---

### Post by LorenzoS on 2009-04-28
How do I get the GPU temperature from nvidia-settings at the command line?  It's working fine from the Nvidia X-Server gui at the desktop.  My GPU is listed as "GeForce 8500 GT (GPU 0)".

Sorry for the novice question, but I just can't figure this out from the man pages.

---

### Post by ian dobson on 2009-04-28
Hi,

Have a look at nvclock. I think it's a package you can install with apt-get install nvclock.

Regards
Ian Dobson

---

### Post by LorenzoS on 2009-04-30
Ian, thanks very much for the reply.  You actually helped me solve the nvidia-settings question indirectly because I stumbled upon someone else who solved the problem when I Googled nvclock.

Turns out this command does work but only when run from a terminal window at the desktop. ```
nvidia-settings –q gpucoretemp
```  If running from a remote connection via SSH, you have to set the display first.```
export DISPLAY=:0.0
nvidia-settings –q gpucoretemp
```

---

### Post by novellahub on 2009-05-01
```
nvclock -T
```

---

