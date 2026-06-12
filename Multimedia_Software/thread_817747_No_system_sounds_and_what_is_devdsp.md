---
title: "No system sounds and what is /dev/dsp?"
date: 2008-06-03
forum: Multimedia Software
---

### Post by WackyCat on 2008-06-03
Hi..completely new user here..just installed Ubuntu 2 days ago. It took a few hours, but after reading the stickies (Thanks!!), I got my AWE SB card working (I can play mp3 and signals fed into line in can be heard in the speakers). I now have two questions/problems I cannot resolve.
1. If I go to system/preferences/sound and try to play any of the 'system sounds' like login or logout, I don't hear anything.
2. I have downloaded a few programs for amateur radio which use the sound card, but they always default to /dev/dsp for the sound card location, and will not work. How do I find the 'true' location of the sound device, and should I move it to /dev/dsp, or just point the program to the newly found location?

Thanks

---

### Post by Prospero2006 on 2008-06-04
Most likely your sound device is /dev/dsp

Basic Principle: Everything in Linux can be treated like a file.

Most of your devices can be located in the /dev/ directory. 

Sound is /dev/dsp, /dev/dsp0 /dev/dsp1 etc...

Now, you said you can play mp3 files. That's good. (It's always sweet when you make Linux do something for the first time.)

Check the device settings in that media player.

You can also do sudo apt-get install audacity.
Try to load a song into that and play it. Under preferences, you'll get a clear list of available sound devices.

Hope that helps.

---

### Post by jocko on 2008-06-04
"/dev/dsp" indicates you use OSS sound. If you have not specifically set up your sound to use OSS due to some very specific hardware that is not supported by ALSA, you should be using ALSA.
In gnome-sound-properties, check that you have set everything in the "Devices" tab to use alsa (pulseaudio should also work, as it should default to using alsa).
If you don't have the option to use alsa, or if alsa doesn't work, there's something wrong with alsa on your system (in hardy, alsa is broken on my intel HD sound card, unless I rebuild the driver).

One of the symptoms of the problem on my laptop is that alsa is not available as an option (so oss becomes default). Another symptom is that running "alsamixer" in a terminal spits out an error (don't remember exactly, but it complains about a missing file or something)
The fix for my problem can be [found here]("http://ubuntuforums.org/showpost.php?p=4675505&postcount=8"), if you think you have the same problem.
It should be harmless to try, but if you don't have an intel HD audio card, it will proably not help...

---

### Post by WackyCat on 2008-06-04
Propero2006 and jocko: thanks for the replys...The problem (at least for me) is I can't seem to figure out just what is supposed to be in /dev/dsp..is /dsp a file or a folder contained within /dev? All I can find is what appears to be a file, but I don't know what it is or how to open it. I will install Audacity, and see if that gives me a better handle on things..if not I will be posting again.

---

### Post by jocko on 2008-06-04
I don't know that much about /dev/dsp or other /dev/* files, but it's not a file that YOU have to do anything to. It's a special file that lies in between your user space application (in this case any application capable of producing sound) and the actual hardware of your computer (check what [wikipedia say about device nodes]("http://en.wikipedia.org/wiki/Device_node") =/dev/* files if you have the urge to know).
If you use oss for your sound (which you probably don't unless you have actively decided that you don't wish to use alsa), your sound applications will send their signal to something called /dev/dsp, and if you use alsa they will send their signal to some other /dev/* (don't remember... right now I'm using my desktop computer which happens to have a rare sound card that is not very well supported by alsa, so I'm using oss).

---

### Post by WackyCat on 2008-06-05
jocko:  thanks for directing me to that article...cleared up what dev/dsp is.

---

