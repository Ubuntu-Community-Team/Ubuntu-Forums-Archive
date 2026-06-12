---
title: "ATI drivers wont work!"
date: 2006-02-20
forum: Multimedia &amp; Video
---

### Post by timmy666 on 2006-02-20
i have a radeon 9600 xt and i downloaded and installed the drivers but when im trying to use aticonfig it says:

aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

---

### Post by MAbans on 2006-02-20
I just installed it about 20 mins ago with this guide:

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

I'm running a 9600 SE..

What I did notice was the hit video performance at full screen.. I have to see how I can fix it..

---

### Post by jakez on 2006-02-20
I have installed via this wiki: [http://wiki.serios.net/wiki?title=Ubuntu_ATI_proprietary_display_driver_installation_using_ATI%27s_installer&redirect=no](http://wiki.serios.net/wiki?title=Ubuntu_ATI_proprietary_display_driver_installation_using_ATI%27s_installer&redirect=no)
Note: I had to add 'video overlay on' in the xorg.conf file to get video performance at full screen properly.
I'm running a radeon 9600 pro

Greetz

---

### Post by MAbans on 2006-02-20
Thanks for the tip.. I'll mess with it now./

---

### Post by timmy666 on 2006-02-21
it worked. thanks !

---

### Post by ugha on 2006-03-05
Hi,
I just cannot seem to install module-assistant, seems like there is none. 
sudo apt-get install module-assistant gives me something like...
**E: Package module-assistant has no installation candidate.**

And howcome I had to uninstall all that stuff just to reinstall it again?

Btw, I am running Ubuntu 5.10...\\:D/ 

Cheers!

---

### Post by ugha on 2006-03-06
I figured out that it was a matter och changeing repositories. Now the **module-assistant** is there to be installed, and a whole bunch of other things. 

then, I went trought the installation just to be disapointed by the fact that my card is not fully supported, **Mobility 9000**. But I got a TVout. But this way, with ATi drivers installed, it is running slower than the initial X config that came with Breezy.

---

