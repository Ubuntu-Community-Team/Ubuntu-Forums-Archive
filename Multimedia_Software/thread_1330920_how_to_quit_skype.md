---
title: "how to quit skype?"
date: 2009-11-18
forum: Multimedia Software
---

### Post by bootdoc on 2009-11-18
skype won't quit!  I tried killall skype.real and sudo killall skype.real and when I try  to start skype (LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype) I get "there may be another instance running.  Top shows skype.real and it never goes away.  I have to restart the machine to get skype to quit.

---

### Post by squaregoldfish on 2009-11-19
Is there a process called skype as well as one called skype.real? If so, try killing that instead.

Incidentally, why are you killing it? I assume it's because the quit option isn't doing what it should....

Steve.

---

### Post by timgood on 2009-11-19
I had this problem as well and solved it by downloading the static binary and using that instead. Hope this helps.

---

### Post by lisati on 2009-11-19
If there's a Skype icon on the top panel, you might want to try right-clicking on it and then "Exit"

---

### Post by timgood on 2009-11-19
> **lisati said:**
> If there's a Skype icon on the top panel, you might want to try right-clicking on it and then "Exit"

If it is the same problem I was having, that doesn't work. The only way I could quit Skype was by opening System Monitor and ending Skype and killing Skype.real

Using the static binary only one process, Skype runs (there is no Skype.real) and it seems to work well without the crashes. Skype also used to stop working when the inability to quit became apparent.

---

### Post by bootdoc on 2009-11-19
did you get the static binary from skype?

---

### Post by timgood on 2009-11-20
Yes - if you go to the Skype download page here:

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

Click on the link to the static binary. Extract the tar.gz (I change the name of the extracted folder to Skype) and put it somewhere safe (I choose the home directory). You can then double click on skype in that folder to launch it. If you want to start it on boot, you can add it to Startup Applications. Any problems, let me know.

---

