---
title: "Getting sound to work in online scrabble (isc.ro) and ubuntu"
date: 2010-12-16
forum: Multimedia Software
---

### Post by Essence Lumin on 2010-12-16
I love online scrabble. And the place for it is the site at [www.isc.ro](www.isc.ro). They have an application to download for windows or linux. The windows application has always been no problem. The linux one was no problem either except there was no sound. Sound is important especially to hear when the other player has made a move. Otherwise I have to stare at the screen and see when the tiles or timers have changed.

Anyway, I have spent a lot of time getting the sound to work with this application. I hope this message will help others via a google search to solve this problem. Wordbiz doesn't have a message board and hasn't updated the linux application since 2005 so here goes here. This is a little rough since I tried so many things I might be missing some things.

First of all, the sun and openjdk packages must be installed. 
You should look at /etc/alternatives/java

This link should point to something like

/usr/lib/jvm/java-6-sun/bin/java

and not something that has openjdk in the link.

openjdk's version of pulseaudio consistently crashed the program after a sound file played twice with this:

~/WordBiz$ java -jar wordbiz.jar
Exception in thread "PulseAudio Eventloop Thread" java.lang.IllegalStateException: drain failed
	at org.classpath.icedtea.pulseaudio.EventLoop.native_iterate(Native Method)
	at org.classpath.icedtea.pulseaudio.EventLoop.run(EventLoop.java:141)
	at java.lang.Thread.run(Thread.java:636)

To see if java sound is working at all try this:

[http://java.sun.com/products/java-media/sound/samples/JavaSoundDemo/](http://java.sun.com/products/java-media/sound/samples/JavaSoundDemo/)

It didn't for me at first. Then I installed mplayer which apparently brought in some necessary libraries.

Then after cd'ing to the wordbiz directory, the command line

paspd java -jar wordbiz.jar

worked for me. I am probably forgetting things but hopefully that will help you.

---

