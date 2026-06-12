---
title: "HDA-Intel Audio Problem"
date: 2009-02-27
forum: Multimedia Software
---

### Post by afbase on 2009-02-27
At the moment, I have only crackly noises coming out of my speakers or headphones.  I have the HDA-Intel Audio
```
~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


~$ asoundconf list
Names of available sound cards:
Intel

```I have to use this Java Web Start (javaws) based program once a week called [Elluminate]("http://www.elluminate.com/").  I must exit all other programs in order for Elluminate's audio to work properly.  I knew this was a bit funny, but I figured to myself, "It's probably because it's a Java app." Once I'm done using Elluminate, I can close it, and open other programs again that use audio.  

This time it isn't working very well.  I looked at the sticky about [Sound Troubleshooting]("http://ubuntuforums.org/showthread.php?t=205449"). I followed the first four steps in the [U][B][SIZE=3]General Help - Start here if you have no idea why sound is not playing

[/SIZE][/B][/U][LEFT]I then thought that maybe because I have crackly sounds, I have sound, and this wasn't the approach for me.  

So does anybody have any suggestions?  thanks

by the way:
```
sudo /etc/init.d/alsa-utils restart Intel
``` does not change the crackling in anyway.
[/LEFT]

---

### Post by albandy on 2009-02-27
try loading the program this way:

aoss java -jar loadmyjarfile.jar

or 

aoss java_executable

if you don't have the command aoss install it:
sudo apt-get install alsa-oss

---

### Post by afbase on 2009-02-27
Thanks for the tip, I'll try that next time!

I found out how to solve it. Go to part C step 3 of this [tutorial](http://ubuntuforums.org/showthread.php?t=789578).  Make sure the pcm is set to something greater than zero.:popcorn:

---

### Post by afbase on 2009-02-27
> **albandy said:**
> try loading the program this way:

aoss java -jar loadmyjarfile.jar

or 

aoss java_executable

if you don't have the command aoss install it:
sudo apt-get install alsa-oss
thanks, How do i mark this thread as solved and mark a thanks to you.  It seems that i can't find those features on this forum anymore!

---

### Post by albandy on 2009-02-27
I think you've to reaname it to solved or something.

---

### Post by afbase on 2009-02-28
there used to be a button where it just modified the title for me to solve it.

I also want to find the button to thank you.  It used to be like this little medallion or something but i don't see either of these anymore.:confused:

---

### Post by afbase on 2009-02-28
[ now i know why i can't find these items any more](http://ubuntuforums.org/showthread.php?t=1039481)

---

### Post by Walkabout3 on 2009-10-03
> **albandy said:**
> try loading the program this way:

aoss java -jar loadmyjarfile.jar

or 

aoss java_executable

if you don't have the command aoss install it:
sudo apt-get install alsa-oss

To get sound working on the Elluminate Java application in Ubuntu (eeePC with KDE on Ubuntu actually) I had to do the following:
1) Install Sun Java.  Google it if you need to.  It's what I've got.  I don't know if any other flavour works or not.
2) Install the aoss package as advised above.
3) When asked by Firefox whether to run the recording.jnlp file using Java or download, select download (into  any directory).
4) In the terminal, cd to the directory in question
5) Run the following:

```
aoss javaws recording.jnlp
```in the same directory as the file.

Walkabout

---

