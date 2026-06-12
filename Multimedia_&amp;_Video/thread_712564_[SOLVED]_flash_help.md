---
title: "[SOLVED] flash help"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by Hink on 2008-03-01
Hi.

I've been trying to install a flashplayer but I can't get i to work properly.
I've tried it using Synaptics Package Manager.
With that i don't get any errors during the instalation but when i try to watch a flash movie or a movieclip on youtube the player gets all f***** up.
And when I download the tar.gz file from adobe and try to install it through the terminal I get this error:


ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.


What shall I do???
//Hink

---

### Post by Sam Lars on 2008-03-01
It looks like you're using 64-bit Ubuntu... Try this thread.
[http://ubuntuforums.org/showthread.php?t=290785](http://ubuntuforums.org/showthread.php?t=290785)

---

### Post by Hink on 2008-03-01
I follow the instructions but on the command...
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
...the terminal prints out some text with this in the end. I'm not sure if I can proceed.

WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  util-linux
0 upgraded, 2 newly installed, 3 to remove and 0 not upgraded.
Need to get 16.2kB of archives.
After unpacking 5235kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'

//Hink

---

### Post by Sam Lars on 2008-03-01
Hmmm...
Try that command one package at a time, and see which one(s) is causing that.

---

### Post by Hink on 2008-03-01
It's only "sudo apt-get install linux32" that causes the problem

//Hink

---

### Post by Sam Lars on 2008-03-01
Try installing the rest and following the guide...

---

### Post by Hink on 2008-03-02
well it's working :) 
Thanks for the help

//Hink

---

