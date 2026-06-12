---
title: "Sound Choppyness issues.. workaround, or fix?...for some"
date: 2010-01-17
forum: Multimedia Software
---

### Post by opt1k on 2010-01-17
**COMMUNITY DOCS FOR OSS4 [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)**
So first of all, just about everyone knows that

$ sudo apt-get install libsdl1.2debian-oss

Will correct a lot of issues right?

It appears that the next distribution will have a package called oss4-base, which is also available in debian unstable

[http://packages.ubuntu.com/search?suite=lucid&arch=any&searchon=names&keywords=oss](http://packages.ubuntu.com/search?suite=lucid&arch=any&searchon=names&keywords=oss)
[http://packages.debian.org/sid/oss4-dkms](http://packages.debian.org/sid/oss4-dkms)

This replaces alsa with oss4.
Alsa has oss emulation, oss4 has alsa emulation...

Long story short, all of the underrun errors are now gone after installing the oss4 package.

For those of you who do not want to try to use the packages from debian unstable (which should work just fine)

You can try this, its where I started, and it worked.  
[http://www.opensound.com/release/oss-install.pdf](http://www.opensound.com/release/oss-install.pdf)
Please read their installation manual.

> 
wget [http://www.4front-tech.com/release/oss-linux-4.2-2002_i386.deb](http://www.4front-tech.com/release/oss-linux-4.2-2002_i386.deb)
### It was recommended to exit to a console before doing this
#   
# you can do it with the following command and you will have to log in 
# through the terminal after doing so
# sudo service gdm stop
#
sudo dpkg -i oss-linux-4.2-2002_i386.deb


I also have a filed called
.asoundrc  in my $HOME 

> 
 pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }


Follow up with any other confirmations of success please!

---

