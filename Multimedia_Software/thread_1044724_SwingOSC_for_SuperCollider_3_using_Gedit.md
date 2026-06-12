---
title: "SwingOSC for SuperCollider 3 using Gedit"
date: 2009-01-19
forum: Multimedia Software
---

### Post by thaumato on 2009-01-19
Hello,

SC3 startup error messages at bottom.

I'm still a Linux newbie.  Trying to get SwingOSC for SuperCollider installed.  I have tried directions on these websites:

[http://artfwo.blogspot.com/2008/05/supercollider-for-human-beings.html](http://artfwo.blogspot.com/2008/05/supercollider-for-human-beings.html)

[http://www.sciss.de/swingOSC/](http://www.sciss.de/swingOSC/)

Experimented by installing SuperCollider in various locations, copying SwingOSC and SwingOSC.jar into logical subdirectories.  I couldn't find the configuration file called ~/.sclang.sc as mentioned on artfwo's blog, though I did find numerous sclang files without that extension by searching my hard-drive.

Thanks for any suggestions, and let me know if you need more specifics!

> init_OSC
compiling class library..
	NumPrimitives = 529
	compiling dir: '/usr/share/SuperCollider/SCClassLibrary'
	compiling dir: '/usr/share/SuperCollider/Extensions'
	pass 1 done
ERROR: Class extension for nonexistent class 'SCDragView'
     In file:'/usr/share/SuperCollider/Extensions/SCClassLibrary/SwingOSC/extCocoaCompat.sc'
ERROR: Class extension for nonexistent class 'SCEnvelopeView'
     In file:'/usr/share/SuperCollider/Extensions/SCClassLibrary/SwingOSC/extCocoaCompat.sc'
ERROR: Class extension for nonexistent class 'SCMovieView'
     In file:'/usr/share/SuperCollider/Extensions/SCClassLibrary/SwingOSC/extCocoaCompat.sc'
ERROR: Class extension for nonexistent class 'SCNumberBox'
     In file:'/usr/share/SuperCollider/Extensions/SCClassLibrary/SwingOSC/extCocoaCompat.sc'
ERROR: Class extension for nonexistent class 'SCPopUpMenu'
     In file:'/usr/share/SuperCollider/Extensions/SCClassLibrary/SwingOSC/extCocoaCompat.sc'
ERROR: Class extension for nonexistent class 'SCSoundFileView'
     In file:'/usr/share/SuperCollider/Extensions/SCClassLibrary/SwingOSC/extCocoaCompat.sc'
ERROR: Class extension for nonexistent class 'SCTextView'
     In file:'/usr/share/SuperCollider/Extensions/SCClassLibrary/SwingOSC/extCocoaCompat.sc'
ERROR: Class extension for nonexistent class 'SCUserView'
     In file:'/usr/share/SuperCollider/Extensions/SCClassLibrary/SwingOSC/extCocoaCompat.sc'
ERROR: Class extension for nonexistent class 'SCWindow'
     In file:'/usr/share/SuperCollider/Extensions/SCClassLibrary/SwingOSC/extCocoaCompat.sc'
numentries = 881079 / 12041772 = 0.073
	4911 method selectors, 2452 classes
	method table size 6722216 bytes, big table size 48167088
	Number of Symbols 11663
	Byte Code Size 372559
	compiled 392 files in 1.45 seconds
compile done

---

### Post by PelleK on 2011-05-30
get swingosc from [http://sourceforge.net/projects/swingosc/](http://sourceforge.net/projects/swingosc/)
extract the .zip, open a terminal in there and run these
sudo apt-get sun-java6-jre
sh install_linux_local.sh

---

