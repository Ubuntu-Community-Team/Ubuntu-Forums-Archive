---
title: "Sound problems with linux and M-audio"
date: 2009-02-03
forum: Multimedia Software
---

### Post by MSdefecter on 2009-02-03
I recently purchased an m-audio delta 44 with the intention of using it within linux (ubuntu 8.10) and windows. When I tried to install the linux drivers I found that I was unable to unpack them. I tried this with all versions/ rpm//deb/tar. but when trying to install them I receive the message "could not open (package name) the package may be corrupted or you are not allowed to open the file. Please check the permissions of the file." Normally you just make the file executable and log in as root but this does not work and the installation instructions are no help what so ever. The only sound I get out of the box within ubuntu is the drum roll login but no welcome sound. I get no sound within rhythmbox it crashes instead and I get no sound in firefox or anything else I have tried. I have tried using synaptic to install oss that way and various alsa plugins aswell as envy24 which is supposed to work with this card but to no avail. I did have this problem once before with a soundblaster but ubuntu seemed to update itself and the problem went away. I am not new to ubuntu but by no means an expert so it is possible that I have overlooked something somewhere. Any help will be greatly appreciated.
Thanks

---

### Post by markbuntu on 2009-02-04
If you have a sound card with the ICE1712 chip, like a M-audio Delta 44, M-Audio 2496, ST Audio Media 7.1 and others and are having trouble getting it working with pulseaudio you can try this:

[http://ubuntuforums.org/showpost.php?p=6449370&postcount=989](http://ubuntuforums.org/showpost.php?p=6449370&postcount=989)

---

