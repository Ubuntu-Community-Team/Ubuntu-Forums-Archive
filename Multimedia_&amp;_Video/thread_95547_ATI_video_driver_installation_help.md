---
title: "ATI video driver installation help"
date: 2005-11-26
forum: Multimedia &amp; Video
---

### Post by jlaine on 2005-11-26
Hi,

I was following the instructions in the sticky on how to install the ATI video driver, using ubuntu 5.10.  I was doing the first part about removing the driver and everything went ok on that part then I started to do the part where you Reinstall the driver and I get the following error:

john@ubuntu:~$ sudo apt-get install xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-driver-fglrx
john@ubuntu:~$

What should I do?  I am new to linux, and this was a fresh install.  My graphics card is a Radeon 9000 series not really sure about the number though.

Thanks, 

John

---

### Post by Zimmer on 2005-11-26
Quite possibly you have not added the necessary repositories for this package to Synaptic. (or you were not connected to the net?)
Look here..
[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28CategoryDocumentation%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28CategoryDocumentation%29)
and for setting up the ATI Drivers try to follow this:

[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

I found this EasyUbuntu helped me with some of the other useful stuff you may wish to acquire, but I used the wiki manual instructions to load the ATI drivers..
[http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23](http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23)

Regards
Zimmer

---

