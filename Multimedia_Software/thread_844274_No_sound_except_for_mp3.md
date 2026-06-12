---
title: "No sound except for mp3"
date: 2008-06-29
forum: Multimedia Software
---

### Post by rubberduckie_uk on 2008-06-29
Hi there, I'm totally new to Linux so please bare with me.

I managed to get mp3s to play using Amarok, however I have no other sound.  I've tried playing ogg and wav and I did have web flash files working at one point but without sound.

Could somebody please help me fix this, giving easy, n00b-friendly instructions?
If it's relevant I'm on a 64-bit system, dual-booting with Vista.

Many thanks. :KS

---

### Post by cozmicharlie on 2008-06-29
I would suggest you start here ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)).  You need to install the codecs for playing different music files.  Because many of these are proprietary they are not pre-loaded.  Don't let it intimidate you - it really is easy.  I'll outline the steps (just to help make it easier for you and show you the basics - how to do this is all in the tutorial) and if you have any problems post back.

Install the medibuntu repository:  Open a terminal and type or cut and paste the following:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Install the Ubuntu Restricted extras from menu>system>administration>Synaptic

Or alternatively:

Install the various codecs  from the command line- this is done in one step from the command line  - you copy and paste all of this into the terminal:
```
sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib && sudo apt-get install alsa-oss compizconfig-settings-manager faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

If you need other codecs (say you want flac - then do a search in synaptic and install from Synaptic.  If it is not in Synaptic then search the forums - there is likely a method posted on how to do a particular codec install.

This is really all you need to play music.  If you want to add support for mplayer in firefox etc then follow the rest of the tutorial.

Enjoy

---

### Post by jualin on 2008-06-29
Also sometimes flash on firefox doesn't work that well together with Amarok, therefore when you are playing a mp3 on Amarok and try playing flash on Firefox, you will get no sound on Firefox. This is an issue with Firefox and Amarok trying to use the same driver for the audio card, it can be solve if you change the driver from Amarok (OSS or ALSA). I don't know how to do it on Amarok since I don't use it but I know it can be done. I have done it on XMMS and Audacity. Hope this helps!

---

### Post by rubberduckie_uk on 2008-06-30
Thanks for the help.  The link you posted was very helpful, as were the code snippets...which I'm glad I was just copying and pasting as they DID look intimidating! :)
 
I now have sound when playing ogg audio files, however when testing the example ogg video file (the one with Nelson Mandela on it), there is video but no sound.  I'm not too bothered about this, as I'm more likely to play avi and mpeg files (which I've not had chance to test yet).
 
I've yet to try Adobe Flash 10 and won't really get time over the next couple of days, but when I do I'll post back to let you know how it went.
 
Thanks again for your help. :KS

---

