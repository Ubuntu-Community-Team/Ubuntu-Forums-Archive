---
title: "Gutsy doesn't install 3gp"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by leetcharmer on 2007-10-21
Typically, when you open a video format Ubuntu doesn't know with Totem Movie Player, it searches for the appropriate codecs to fix this.  Sadly, this is not the case with .3gp files (these are typically recorded with cell phones).

Anyone know how to fix?

---

### Post by darigaz625 on 2007-10-21
i can play them with totem, but there is no sound.

vlc just crashes when i try to play .3gp files.

any suggestions?

---

### Post by auraithx on 2007-10-23
I have the same problem.

I also can't install vlc from synaptic or the command line (can't find it in either)

---

### Post by robinlennox on 2007-10-25
Just wondering if anyone managed to find a fix?

---

### Post by KCPokes on 2007-10-25
I could always play them, but they had no sound.  I had to resort to using Quicktime Pro to convert them to something usable, which is really not the course I wanted to have to take.

---

### Post by insanish1 on 2007-11-01
Hi Everyone,
                    Just go to [http://www.real.com/linux](http://www.real.com/linux) and download the Real Player. The file name would be RealPlayer10GOLD.bin. Open the terminal window and go into the folder where you downloaded the file and run the following command on the file  
chmod a+x RealPlayer10GOLD.bin and then execute the file using
sudo ./RealPlayer10GOLD.bin

Accept the defaults and you would have Real Player installed under Applications - Sound and Video

Now try opening the .3gp files. Works like a charm!

Do let me know if this option doesnt work for you.

Thanks
Anish

---

### Post by insanish1 on 2007-11-01
Hi Everyone,
Just go to [http://www.real.com/linux](http://www.real.com/linux) and download the Real Player. The file name would be RealPlayer10GOLD.bin. Open the terminal window and go into the folder where you downloaded the file and run the following command on the file
chmod a+x RealPlayer10GOLD.bin and then execute the file using
sudo ./RealPlayer10GOLD.bin

Accept the defaults and you would have Real Player installed under Applications - Sound and Video

Now try opening the .3gp files. Works like a charm!

Do let me know if this option doesnt work for you.

Thanks
Anish

:guitar:

---

