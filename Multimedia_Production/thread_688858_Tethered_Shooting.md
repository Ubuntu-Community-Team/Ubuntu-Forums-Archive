---
title: "Tethered Shooting"
date: 2008-02-05
forum: Multimedia Production
---

### Post by computergee on 2008-02-05
I was wondering if there way a way to be able to plug my Nikon D50 into my laptop via usb and have the images popup on the screen automatically after I take a picture? I can make the shutter go off with 
gphoto2 --capture-image, but it doesn't come up on the screen, and has to be initiated through the command line. Do you guys have any ideas?

---

### Post by G2_vincent on 2008-02-28
have a look here : [http://photodoto.com/tethered-shooting-with-linux/](http://photodoto.com/tethered-shooting-with-linux/)

---

### Post by moeFinley on 2008-03-29
This is really cool!  The scripts on that site work really well.  It's a shame that GTKam seems a bit unstable.  Does anyone know of any other projects that allow tethered shooting?

---

### Post by computergee on 2008-04-26
Sorry to revive this thread, but I just stumbled upon it again.

Thanks a lot G2_vincent, that script is awesome! The only problem I had with it is that the since the script deleted the files everytime time after it copied it, the file scheme went back to whatever_1.JPG, so it gave asked me if I wanted to overwrite instead of opening up the new file. I tweaked the tether script a bit so that it saves the files as 1.jpg, 2.jpg, 3.jpg, and so forth, so each picture is saved and pops up on your screen, without asking you if you want to overwrite. I also tweaked the view script to open up Eye of Gnome in full screen. I hope this helps someone else =).

PS: I used it with my Nikon D50.

---

