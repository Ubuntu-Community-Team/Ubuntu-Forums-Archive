---
title: "[SOLVED] How to change player (Gnash) in firefox 3.03"
date: 2008-11-11
forum: Multimedia Software
---

### Post by bricksen on 2008-11-11
I upgraded to 8.04 and seem to be unable to play movies in youtube?
It runs on Gnash wich wont load the movies. But I find no gnash under :firefox/preferences/applications
And I am able to download the movies with::Fast Video Download and watch them with Movie Player so I shouldnt miss any program.
I installed: ubuntu restricted-extras and that took care of any flash problems but how do I change what player firefox uses??
usr/lib/firefox/plugins contain only :flashplugin-alternative.so and libjavaplugin.so

Anyone who sees what I'm missing?

---

### Post by gandaran on 2008-11-11
installing ubuntu-restricted-extras also installs adobe flash, it's better you remove gnash or any other flash (swfdec) installed.
look in synaptic for mozilla-gnash-plugin and swfdec-mozilla and remove them

and you should try adobe flash 10, you can download the .deb  package from adobe [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) remove the flashplugin-nonfree in synaptic first

---

### Post by bricksen on 2008-11-11
I removed the mozilla-gnash.plugin with synaptic and it works fine 

Thanks alot :-)

---

