---
title: "Rhythmbox - In The Mood plugin"
date: 2010-09-16
forum: Multimedia Software
---

### Post by nosh276 on 2010-09-16
Okay, I'm trying to install the "in the mood" plugin in rhythmbox.

I downloaded the tar.gz and extracted it and attempted to do a > ./configure 
make install but I don't really know what I'm doing and it always responds that it doesn't know a ./configure command. 

So, I looked around and installed build-essentials, which I thought would make it work, but I keep getting the same response.

I then read somewhere, that I just have to copy the "in the mood" folder to the rhythmbox plugins folder. I did, and the plugin appears in the list of plugins, but when I click on it, it says "Unable to Activate Plugin".

My last attempt took me to code.google for the plugin, where it said I needed to install libmad and marsyas. Libmad was easy, since it's a dev package, but after I downloaded marsyas, and extracted it through > tar xzvf marsyas-0.4.0.tar.gz but I ran into the same problem with ./configure and make install

I really hate asking for help, since there's so much information out there already, but I just can't seem to figure out how to get the plugin to work.

---

### Post by abcsds on 2010-12-04
I've ran into the same problem with the plugin, but I did manage to install marsyas. for this u have to use Cmake. The user manual is very detailed about installation, i'm a total noob and i got to install it. This is the link[ http://marsyas.info/docs/manual/marsyas-user/index.html]("http://marsyas.info/docs/manual/marsyas-user/index.html") 
still, if you get any advances with in the mood pluging, i'd thank you for telling me :D

---

