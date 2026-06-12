---
title: "Missing plugin, Flash is not working"
date: 2012-03-30
forum: Multimedia Software
---

### Post by Crazy K on 2012-03-30
Recently all of a sudden flash doesn't want to work for me. This has been happening for a few days now. Odd this is I can play youtube videos if I have shockwave flash disabled in the plugins on chrome, but when checked I can't view videos. 

Other flash things don't work even if it's enabled or disabled. 

I'm still somewhat of a noob with ubuntu so I need a step-by-step way of fixing the problem. 

I read a few how-to's, but they didn't help me at all. 

Please reply soon, my family needs to do some import stuff on my computer that requires flash and I need help as soon as possible. Thanks!

---

### Post by Crazy K on 2012-03-30
If it helps, I use Chromium not Google Chrome.

---

### Post by efflandt on 2012-03-30
There are other threads about problems with the most recent flash update, which I believe began yesterday (March 20), which for many of us turned everyone on YouTube videos into smurfs (blue faces) and totally messed up other colors.  Although, other videos, include ads on YouTube before user videos appeared normal.

Many people had success unchecking "hardware acceleration" in flash settings.  But some of us could not do that because the flash settings dialog would freeze along with flash controls.

I used Synaptic to totally remove flashplugin-installer and anything related and installed four-square 64-bit flash (same version) manually directly from adobe.com.  Then I was able to disable flash hardware acceleration.  Although, even that seems to stutter at times trying to watch videos on kbb.com and auto manufacturer sites.

Maybe it affects users of other types of video differently than nvidia driver users.  Basically the flash update dropped a bomb on Linux users.

---

### Post by Crazy K on 2012-03-31
I don't have the smurf problem. Just can't seem to get the flash plugin to work. Youtube works fine, which I find odd, but other sites with flash don't work or say the plugin is missing. I did see there were other threads, but I'm still somewhat noobish when it comes to these type of problems. 

I moved the libflashplayer.so file to the chromium web browser plugins folder, it shows up, but problems seem to be worse. 

Any idea when an update for this will be released? I went back to a previous version, but it seems to make my browser run slower.

---

### Post by bman on 2012-03-31
For me if I am running a flash video full screen it will freeze. I have to hit the restart button on my case to get out of it.

A solution would be nice.

---

### Post by Crazy K on 2012-03-31
It seems to be working for me now. I have flash control installed as an extension for Chromium, and all I have to do is click a box to make sure it plays. 

I also followed another topic here: [http://ubuntuforums.org/showthread.php?t=1948626](http://ubuntuforums.org/showthread.php?t=1948626) which seemed to help me out.

---

### Post by pyutaros on 2012-11-19
I got tired of manually downgrading flash on every computer I use, so i wrote this script.  Save it to a your computer and remove the ".txt".  Make sure it's sent to run as an executable and then you can run it from a terminal by typing ./Adobe_fix.  Here is the code below:

```
wget http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip
unzip fp_11.1.102.63_archive.zip
tar -xzvf fp_11.1.102.63_archive/11_1r102_63_32bit/flashplayer11_1r102_63_linux.i386.tar.gz -C fp_11.1.102.63_archive/
sudo cp -f fp_11.1.102.63_archive/libflashplayer.so /usr/lib/flashplugin-installer
```

---

