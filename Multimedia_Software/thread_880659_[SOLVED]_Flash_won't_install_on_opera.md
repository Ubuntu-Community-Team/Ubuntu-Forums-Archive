---
title: "[SOLVED] Flash won't install on opera?"
date: 2008-08-05
forum: Multimedia Software
---

### Post by joshdudeha on 2008-08-05
Hello,
     I've just installed opera, because I'm fed up with firefox crashing, and bein so slow. The problem I am facing, though is that in Opera I can't get flash player installed.

I have flashplayer 10 installed on Firefox 3.
But when I try to install version 9 or 10 in opera it just won't work.
Here is what happens.

I goto the directory in my terminal where the installer for the flash is located.. and run it ./flashplayer-installer.
It then says :
  ```
Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 9 will be installed in your home directory.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.


```

So I press enter.
It then tells me to close all browsers, which I do.
I press enter again.
Then it says 
 ```

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/joshua/.mozilla

Proceed with the installation? (y/n/q): 

```
And won't let me change the installation directory to the one opera is under.

Can anyone tell me why it automatically assumes it is being installed under that directoy.

Could you please help me?

Thank you (:

---

### Post by gandaran on 2008-08-05
opera works with flash installed by synaptic or apt-get.
to get opera working with flash installed with the abobe tarball, just find where you installed it or extract the tarball and copy/paste the libflashplayer.so file to /usr/lib/opera/plugins (root permission need, use the **sudo nautilus** command). it's that simple.

---

### Post by joshdudeha on 2008-08-05
Oh, ok . . Thank you (:

---

