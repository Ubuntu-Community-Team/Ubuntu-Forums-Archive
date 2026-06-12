---
title: "Problems with sound - Not recongnize sound card anymore"
date: 2012-01-11
forum: Multimedia Software
---

### Post by luciano_sabenca on 2012-01-11
Hello, everybody.
I'm having a big problem with sound in my Ubuntu 11.04.
The sound output was working fine, but  the microphone didn't.
So, I tried to reinstall all drives, but now nothing is working.
The Ubuntu doesn't recognize my sound card anymore.
The log from alsa is in this link:
[http://www.alsa-project.org/db/?f=58fbdb55678f98ccdf638d5405b22ebf45ba6c11](http://www.alsa-project.org/db/?f=58fbdb55678f98ccdf638d5405b22ebf45ba6c11)


I already tried this tutorial, but this didn't resolve my problem:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Thanks 
:D

---

### Post by MoreOrLess on 2012-01-11
There's a problem with the kernel module:
```
Driver version: 
     Library version:    1.0.24.1
Utilities version:  1.0.24.2
```

Reinstall the linux-image package, which contains the sound kernel module
```
sudo apt-get install linux-image-`uname -r`
```

---

### Post by luciano_sabenca on 2012-01-11
I tried to run this command in the terminal, but there was no effect.
The message says that linux image already is the newest version.
Thank you

---

### Post by MoreOrLess on 2012-01-12
Oops. Command should have been:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```

---

### Post by luciano_sabenca on 2012-01-13
I tried that, but didn't work...
I still have no sound...

---

### Post by MoreOrLess on 2012-01-13
> So, I tried to reinstall all drives, but now nothing is working.
Can you explain exactly what you did to reinstall drivers? It might help to undo it..

---

