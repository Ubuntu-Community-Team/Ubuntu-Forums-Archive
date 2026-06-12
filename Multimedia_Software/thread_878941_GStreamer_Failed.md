---
title: "GStreamer Failed"
date: 2008-08-03
forum: Multimedia Software
---

### Post by Kevin Chen on 2008-08-03
I am using Ubuntu 8.04 86_64x.
My soundcards works very well, and I can use command "alsamixer" to adjust the sound volume.
My video works also well.
But the GStreamer doesn't work:
When I double click the volume control, error: "No volume control GStreamer plugins and/or devices found."
When I open totem, error: "Failed to create a GStreamer play object. Please check your GStreamer installation."
Everything related to GStreamer doesn't work.
Please help me

---

### Post by Dyffo on 2008-08-03
I have the same problem Please help me too !!!!

---

### Post by hansdown on 2008-08-03
If you go to system> administration> synaptic package manager you can type gsteamer into the search bar to get a look at all the plugins. Be sure to click upgrade all packages to give you the newest versions of your selected packages. Hope this helps.

---

### Post by Dyffo on 2008-08-03
Done this but sadly no it doesnt solve the problem

---

### Post by hansdown on 2008-08-03
This is one of the most comprehesive guides here. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 
It is one of the first things I go to when I do a clean install.

---

### Post by Dyffo on 2008-08-05
THIS SOLVED MY PROBLEM !!!!!!!!!!!!!!!!!!!!


Please open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-ubuntu-modules-$(uname -r

---

### Post by tetrafuran on 2008-08-07
I think that in my case the new kernel caused the problem. Therefore upgrading is not possible. What should I do to fix the sound issue?

---

### Post by justiceandfreedom on 2009-05-30
I have exactly the same problem (volume control, Totem), not only in Ubuntu 9.04 , but also with Zenwalk 6.0 Xfce and Archlinux Gnome/Xfce, so with different kernels. FreeBSD is OK with Gnome 2.22. I have an Intel DQ963FX MB with Sigmatel STAC 9227 codec. Alsamixer and other volume controls (KDE, LXDE, Puppy) work well.
Update 25 June, 2009: With the new kernel in Arch it is now quite OK, just some warnings at boot (unknown device, using the guessing method)

---

### Post by Mecasickle on 2010-03-21
> **Dyffo said:**
> THIS SOLVED MY PROBLEM !!!!!!!!!!!!!!!!!!!!


Please open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-ubuntu-modules-$(uname -r

the last command:

sudo apt-get install linux-ubuntu-modules-$(uname -r

doesnt give me anything....

---

### Post by Yellow Pasque on 2010-03-22
> **Mecasickle said:**
> the last command:

sudo apt-get install linux-ubuntu-modules-$(uname -r

doesnt give me anything....
```
sudo apt-get install linux-ubuntu-modules-`uname -r`
```

---

### Post by ubuntubrian on 2011-01-22
I know that it's been many months since the last post on this problem but I ran into it upgrading to Maverick. I finally found that if all the gstreamer libraries in /usr/local/lib were removed a la:

```
rm -R -f *gst*
```

Totem and Rhythmbox work fine. Have no idea why though.....:popcorn:

---

