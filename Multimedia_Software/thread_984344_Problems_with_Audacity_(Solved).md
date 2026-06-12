---
title: "Problems with Audacity? (Solved)"
date: 2008-11-16
forum: Multimedia Software
---

### Post by drbongo on 2008-11-16
I had been having problems with Audacity, it was refusing to play any sounds and coming up with an error message: 

**Error while opening sound device. Please check the output device settings and the project sample rate.**

At first I thought it was a bug in the beta version, but after a lot of fiddling around I discovered that the problem was caused by the installation of jackd!

Basically if jackd is installed Audacity starts it up and then ALSA and OSS cannot get access to the sound card. There are a variety of simple solutions:

1. The simplest solution is to uninstall jackd if you don't need it.

2. If you need jackd you can simply open Audacity Preferences and choose the jackd server as the input and output devices. (Audacity will now work, but I found the the sound quality was very poor)

2. Another solution is - after starting audacity, open a terminal and type "killall jackd", close the terminal and Audacity will then work. ( you could also use Jack Control to do this if you have installed it.)

3. You can launch Audacity by opening a terminal and typing "audacity | killall jackd". Audacity takes about 30 seconds to appear but works fine.

4. Finally you can create a launcher - Create a new blank document, type:

#! /bin/bash
audacity | killall jackd

Save the file as 'audacity', open System>Preferences>Main Menu, open the Sound and Video sub-menu and right click on the Audacity Launcher and select properties. You can then browse to and choose your newly created launcher. (Remember to make the file executable using properties and permissions etc):guitar:

---

