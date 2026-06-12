---
title: "alsa wrapper stopped working for Chrome too..."
date: 2010-09-05
forum: Multimedia Software
---

### Post by Truckerpunk on 2010-09-05
I'm running strickty ALSA on my Ubuntu 10.04, and everything was working except for using alsa-wrapper with firefox. But it didn't reallt matter as it worked fine with chrome (launching chorme with "aoss chromium-browser"). But now that stopped working too, which means multiple audio playback from browser and other applications doesn't work. Alsa-wrapper still works with Opera, but I'm not really fond of Opera. 

Any suppestions?

---

### Post by Truckerpunk on 2010-09-05
Turns out it was only java-applications that stole the entire sound. I got this sovled now, by running all java applications through the alsa-wrapper. 
I did this by renaming the javalauncher to java.bin, creating a new java file, making it executable, and adding the script below. here are codes for the terminal:

cd /usr/lib/jvm/java-6-sun/jre/bin
sudo mv java java.bin
sudo touch java
sudo chmod +x java
sudo nano java

And then making the script:

#!/bin/bash
aoss /usr/lib/jvm/java-6-sun/jre/bin/java.bin "$@"

This will also work with pulseaudio, just change the aoss in the script to padsp instead. This might not work after an upgrade of java, unless you make another of these small scripts. And the folder in which you modify should match your current version of java.

---

