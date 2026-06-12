---
title: "Playing DVDs ???"
date: 2010-10-16
forum: Multimedia Software
---

### Post by producer on 2010-10-16
I've searched for play and DVD but there seems to be nothing useful.  I've just upgraded to Ubuntu 10.10 and I can't get a reliable libdvdcss2 to install anywhere.  It has always worked before and I don't have a standalone DVD player.  I always watch them on my computer. How do I do this in 10.10?

---

### Post by bluebyt on 2010-10-16
I installed 10.10 and to have DVD working I just did these commands in the terminal:

 sudo apt-get install libdvdread4

 sudo /usr/share/doc/libdvdread4/install-css.sh

Also I used VLC for DVD player which is really good.

---

### Post by producer on 2010-10-16
Thanks.  I thought I tried that before.  I am using Movie Player and maybe it's a problem, I don't know.  Trying this again.

---

### Post by producer on 2010-10-16
And now it works.  Many thinks!  You're terrific.

---

### Post by Nightstrike2009 on 2010-10-16
You probably need to add medibuntu repository [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") and check out the Adding the repository section for what to do next.

Then just type the text below into terminal:

> sudo apt-get install ubuntu-restricted-extras
That should install all necessary codecs including DVD playback

Hope that helps :-)

---

