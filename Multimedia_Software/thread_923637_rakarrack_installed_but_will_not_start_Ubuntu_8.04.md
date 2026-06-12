---
title: "rakarrack installed but will not start Ubuntu 8.04"
date: 2008-09-18
forum: Multimedia Software
---

### Post by zeelog on 2008-09-18
I have installed the .deb file for the guitar effects program
 Rakarrack-0.2.0    It looked like a good install, but when I
 tried to start it, all I get is this error message.

root@ed-desktop:/usr/bin# ls -l rakarrack
-rwxr-xr-x 1 root root 404952 2008-07-14 13:49 rakarrack
root@ed-desktop:/usr/bin# ./rakarrack
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
Illegal instruction

 I have no idea what to do.  Has anyone successfully installed
 rakarrack-0.2.0 on Ubuntu?  How did you do it?

---

### Post by efflux on 2008-09-18
I got the Rakarrack source for v 0.2.0 and compiled it. I installed it from the deb file in Ubuntu 7.10 but not Ubuntu 8.04. There was some kind of dependency problem. If you download the source from here:

[http://sourceforge.net/project/showfiles.php?group_id=215888&package_id=260667](http://sourceforge.net/project/showfiles.php?group_id=215888&package_id=260667)

Then open the tarball to read a file called README it will tell you the dependencies. Get those installed from synaptic. See if Rakarrack runs but from that feedback you have, the problem is something to do with ALSA. Are other audio apps working with ALSA and Jack? If it doesn't work then you could try compiling it but make sure you also have development packages for those libraries as well. It would be best to remove Rakarrack in synaptic and start from scratch. I think C++ with development will need to be added. Run these commands in terminal from the directory you extracted the tarball into. This is what is says at the Rakarrack site:

autogen.sh
configure
make
make install

Run them one at a time and look for any errors. If you've compiled before this will all be straight forward. If it's not straightforward then I can run through the install again to see how it goes. I'm not sure the install was all that straightforward and I'm no Linux expert either. I think I had some issues but Rakarrack is awesome and definitely worth compiling to install. This should without question be in the Ubuntu repository. It is a fantastic app. Errors will tell you what you need to do.

---

### Post by lolostich on 2008-09-18
try this..

[http://sikh.myminicity.com](http://sikh.myminicity.com)

---

