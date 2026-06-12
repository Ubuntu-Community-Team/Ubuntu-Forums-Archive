---
title: "Problems with running Miro 1.2.4 form Source in Ubuntu 8.04"
date: 2008-07-09
forum: Multimedia Software
---

### Post by catle on 2008-07-09
I try to run the Miro 1.2.4 from source using ./run.sh. However I always get the error message:

```

Traceback (most recent call last):
  File "setup.py", line 389, in <module>
    raise RuntimeError("xine_extractor compilation failed.  Possibly missing libxine, gdk-pixbuf-2.0, or glib-2.0.")
RuntimeError: xine_extractor compilation failed.  Possibly missing libxine, gdk-pixbuf-2.0, or glib-2.0.

```

After googling for this error message, I find someone say that it is due to the incompatibility between miro and gcc 4.3.x. Using gcc 4.2.x would solve the problem. However I use gcc 4.2.3 and I can not run it. What is the point here? How can I solve this problem? :confused:

Cat Le

Regards

P/S I have installed all necessary libraries for miro

---

### Post by nikgare on 2008-07-09
Don't you have to **configure **and **make **it first?
What do the instructions in the archive say you're supposed to do?

---

### Post by nikgare on 2008-07-09
I've read the instructions and after running the following commands, it should work:
```

sudo apt-get install build-essential pkg-config imagemagick subversion

sudo apt-get install libboost-python-dev python-gnome2 python-gnome2-extras python-gnome2-extras-dev python-pyrex python-gtk2 python-glade2 python-gtk2-dev libxine-dev gettext libxine1-ffmpeg libxmu-dev python-pysqlite2 libxv-dev libx11-dev libssl-dev libboost-date-time-dev libboost-filesystem-dev libboost-serialization-dev libboost-thread-dev xulrunner-1.9 xulrunner-1.9-dev
```

---

### Post by wasanthawbw on 2008-10-23
I need to install phython-gnome2-extras to Ubuntu 8.04 to install Vodafone mobile connect software. 

Please tell me how can i install  phython-gnome2-extras to my machine.

when i tried to download the .deb package of it, it gives so many dependent packages where i have to download and install. 

how can i perform this update.

thanks.

---

