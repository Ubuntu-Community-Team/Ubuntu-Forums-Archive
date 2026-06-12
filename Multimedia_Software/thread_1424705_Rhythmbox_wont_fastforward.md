---
title: "Rhythmbox wont fastforward"
date: 2010-03-08
forum: Multimedia Software
---

### Post by sevenX on 2010-03-08
For some reason my slider bar on rhythmbox or movie player wont let me scan/seek/fastforward through songs. I tried to install another music app think it was banshee but same thing couldnt scan through the song while it was playing the slider is greyed out and the bar doesnt move through the song as it plays. If I could fix this it would be so nice.. Im fairly new to linux. please help. :O

---

### Post by boombox1387 on 2010-03-20
It sounds like the decoder your using doesn't support seeking.  If I remember correctly, ffmpeg allows playing mp3 files, but it doesn't allow seeking in them.  For full mp3 support (assuming you're working with mp3 files) you'll need the gstreamer ugly plugin.

I'm not sure how package management works in the Netbook Remix, but I would assume it comes with Synaptic installed.  On a standard Ubuntu installation, you would go to System > Administration > Synaptic Package Manager.  Once Synaptic is open, search for 'gstreamer.'  Make sure the following are installed:

gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly

Hopefully that will take care of the problem.  If it doesn't - or if my instructions were inaccurate - let me know, and we'll see if we can figure it out.

---

### Post by sevenX on 2010-03-21
Hey Boombox thank you for this reply.  I went to follow your steps and I cannot even get into my synaptic package manager anymore... I have the following error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I was getting error prior to this when opening package manager but i would just click ok and it let me in and download packages still.  So here is screenshots of errors I was getting... first one i dont have copy + paste of error just screenshot but second pic is of what I am getting now.

---

### Post by boombox1387 on 2010-03-21
> **sevenX said:**
> Hey Boombox thank you for this reply.  I went to follow your steps and I cannot even get into my synaptic package manager anymore... I have the following error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I was getting error prior to this when opening package manager but i would just click ok and it let me in and download packages still.  So here is screenshots of errors I was getting... first one i dont have copy + paste of error just screenshot but second pic is of what I am getting now.

Hmm, I know quite a bit more about music/media with Ubuntu than I do Synaptic/dpkg, but I'll see what I can do.

First, from the error it popped up, it looks like you have duplicate entries in your software sources list.  Have you manually added PPAs?  If so, go to System > Administration > Software Sources and disable anything unnecessary (or anything that looks like a duplicate entry) from the 'Other Software' tab. Try running Update Manager, to see if you can check for and receive updates.

If that doesn't work, then it's probably time to fire up a Terminal.  The first thing I would do is follow the instructions from the second error.  Run:

```
sudo dpkg --configure -a
```

Enter your administrative password and follow any instructions it gives you.

After that, you'll want to check for updates:

```
sudo apt-get update
```

and install them

```
sudo apt-get upgrade
```

If, even after doing all of these things, you still can't use Synaptic, report back here, and hopefully I'll be able to help you more.  If not, I'm sure someone else who knows a lot more than me will come along... :)

---

### Post by sevenX on 2010-03-21
OK! :D I solved synaptic download manager error I had to manually edit /etc/apt/sources.list and remove the duplicate entries than update.   

So now... I followed your instructions well I could only find gstreamer0.10-plugins-bad so I installed that and TAH-DAH! :popcorn: It works now Thank you so much for your help... Thank you! Thank you! :D

---

### Post by boombox1387 on 2010-03-21
> **sevenX said:**
> OK! :D I solved synaptic download manager error I had to manually edit /etc/apt/sources.list and remove the duplicate entries than update.   

So now... I followed your instructions well I could only find gstreamer0.10-plugins-bad so I installed that and TAH-DAH! :popcorn: It works now Thank you so much for your help... Thank you! Thank you! :D

Woo!  Very glad to hear it.

---

