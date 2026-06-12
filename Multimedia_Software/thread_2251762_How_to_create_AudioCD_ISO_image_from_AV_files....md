---
title: "How to create AudioCD ISO image from AV files..."
date: 2014-11-06
forum: Multimedia Software
---

### Post by abhayadevs on 2014-11-06
I need to create an AudioCD image from a couple of AV files. I dont have a CD recorder connected to my Linux Laptop but if I can prepare an ISO i can burn that ISO image to the CD using the recorder available in one of my friends laptop. It has ISO riter application.

I have tried Braesero, K3D etc but nothing is giving me the ISO image !

Thanks and Regards,
abhay

---

### Post by SeijiSensei on 2014-11-06
In K3b, when you click the Burn button, the dialog box has a checkbox for "Only Create Image".  If you check that, and enter a path to the ISO file in the Image tab, you'll get just the ISO image.

You'll need to be creating a "Data" CD, of course.

---

### Post by abhayadevs on 2014-11-06
I am using a AudioCD project template, and there when i do the "Create Image" It just creates the WAV files again.... !

In Data CD mode i cannot create a AudioCD right?

---

### Post by Bucky Ball on 2014-11-06
Just drag and drop the files to the CD/USB/whatever. You can plop any data file you want on there.

---

### Post by SeijiSensei on 2014-11-06
It looks like you cannot create an AudioCD image the way you can create a data CD.  Instead you can create a "TOC" file and place it in a directory with a bunch of WAV files.  With the contents of that directory, it's apparently possible to create an Audio CD with the right burning software.  See these:
[http://lists.centos.org/pipermail/centos/2009-January/070652.html](http://lists.centos.org/pipermail/centos/2009-January/070652.html)
[http://www.xbloome.com/drupal/howto/toc_cd_master](http://www.xbloome.com/drupal/howto/toc_cd_master)

---

