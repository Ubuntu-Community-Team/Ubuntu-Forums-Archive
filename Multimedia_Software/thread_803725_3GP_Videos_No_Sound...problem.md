---
title: "3GP Videos No Sound...problem"
date: 2008-05-22
forum: Multimedia Software
---

### Post by stechkov on 2008-05-22
i am having a problem when i play 3GP Format Videos There is no sound playing..why?newbie...

---

### Post by vs55 on 2008-05-25
What program you use to play 3gp?  For Mplayer some libraries from medibuntu are necessary. To install them, first add this repository in /etc/apt/sources.list, i.e. if you have ubuntu 8.04:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

Then add key to the system and update the list of repositories:
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then update manager will suggest you to install the necessary libraries.

---

### Post by OwnSurname on 2008-11-20
Hi vs55,
thank you so much for your post, it helped me quite a lot, after pages and pages about compiling the libraries.
I added the repository in Intrepid with:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

which I found here:

[http://t0x.in/medibuntu.html](http://t0x.in/medibuntu.html)

---

