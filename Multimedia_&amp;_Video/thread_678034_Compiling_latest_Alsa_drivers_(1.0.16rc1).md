---
title: "Compiling latest Alsa drivers (1.0.16rc1)"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by proteo on 2008-01-25
Hi!

I'm trying to install the latest Alsa drivers for my sound card (Auzen X-Meridian 7.1), I have been compiling and testing earlier versions ([http://www.alsa-project.org/main/index.php/User:ClemensLadisch]("http://www.alsa-project.org/main/index.php/User:ClemensLadisch"))
 with more or less success (sound works on some programs, others don't), but i have problems compiling the most recent beta driver. I already downloaded the packages indicated on the page and when i try to compile the driver i get an error about a undeclared function. :confused:

Can anyone help me with this?

Thanks!!:)

---

### Post by Yellow Pasque on 2008-01-25
Try the scripts in this thread. Modify the first script to get '1.0.16rc1' instead of 1.0.15
[http://ubuntuforums.org/showpost.php?p=3603812&postcount=13](http://ubuntuforums.org/showpost.php?p=3603812&postcount=13)

---

### Post by proteo on 2008-01-25
Trying the first one, do I need to modify the second script?

---

### Post by Yellow Pasque on 2008-01-25
> **proteo said:**
> Trying the first one, do I need to modify the second script?
No, don't modify the second script.

---

### Post by proteo on 2008-01-25
I got this error trying to run the second script:

`/lib/modules/2.6.22-14-386/kernel/sound/pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
cp: no se puede efectuar `stat' sobre `/usr/src/alsa/alsa-driver*/modules/*': No existe el fichero ó directorio
cp: se omite el directorio `/lib/modules/2.6.22-14-386/kernel/sound/'

And i don't have any sound device listed anymore :(

---

### Post by Yellow Pasque on 2008-01-25
Are you running the 64-bit version of Ubuntu by chance?

---

### Post by proteo on 2008-01-25
No, 32 bit version on this machine, i wanted to install the other version, but was to lazy to reinstall and configure everything again :)

---

### Post by Yellow Pasque on 2008-01-25
My apologies. I didn't realize that script was configured only for hda-intel. Hold on a few minutes, and I will fix it.

---

### Post by Yellow Pasque on 2008-01-25
Here's what you should run now.
```
cd /usr/src/alsa/alsa-driver
sudo make uninstall;
```

Then run the script attached to this post.

---

### Post by proteo on 2008-01-25
Still no sound, I'm starting to get a little worried, maybe i should try a slightly older driver?

---

