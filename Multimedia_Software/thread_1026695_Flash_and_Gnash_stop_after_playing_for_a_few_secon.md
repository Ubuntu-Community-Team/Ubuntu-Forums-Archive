---
title: "Flash and Gnash stop after playing for a few second"
date: 2008-12-31
forum: Multimedia Software
---

### Post by ruddha on 2008-12-31
I'm running the latest ubuntu (8.10). It worked fine until suddenly flash stopped working. Video's play for a few second and stop. I tried completely removing flash, installing gnash, using opera and deleting the .mozilla folder. Unfortunately nothing worked. Who knows a solution?

---

### Post by homemadejam on 2008-12-31
> **ruddha said:**
> I'm running the latest ubuntu (8.10). It worked fine until suddenly flash stopped working. Video's play for a few second and stop. I tried completely removing flash, installing gnash, using opera and deleting the .mozilla folder. Unfortunately nothing worked. Who knows a solution?

You could try the following:
```
sudo apt-get install libflashsupport
```

Jam

---

### Post by wolfen69 on 2008-12-31
completely remove any flash or gnash. then open terminal and: 
```
sudo apt-get clean && sudo apt-get autoremove
``` then go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu. click to install. restart firefox if open. then, for opera, go back to the flash site and download the .tar.gz flash file. right click and extract here. open folder and copy the libflashplayer.so file. open your home folder and do Ctrl-h. look for your .opera folder and open it. navigate to the plugin folder and paste.

---

### Post by ruddha on 2008-12-31
> **homemadejam said:**
> You could try the following:
```
sudo apt-get install libflashsupport
```

Jam

Unfortunately I don't have libflashsupport:

```
$ sudo aptitude install libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for libflashsupport
No candidate version found for libflashsupport
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

---

### Post by ruddha on 2008-12-31
> **wolfen69 said:**
> completely remove any flash or gnash. then open terminal and: 
```
sudo apt-get clean && sudo apt-get autoremove
``` then go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu. click to install. restart firefox if open. then, for opera, go back to the flash site and download the .tar.gz flash file. right click and extract here. open folder and copy the libflashplayer.so file. open your home folder and do Ctrl-h. look for your .opera folder and open it. navigate to the plugin folder and paste.

I tried everything, unfortunately flash still isn't working.

---

