---
title: "flash and java can't share audio in Karmic. No ALSA wrapper..."
date: 2009-11-07
forum: Multimedia Software
---

### Post by Truckerpunk on 2009-11-07
Hey. Whenever I play a Flash video or start a Java-application, while having a musicplayer running, I will not be able to hear the sound from the flash or java-application. Pulse audio just doesn't support multiple audioplaybacks. This is why I used ALSA-wrapper("aoss firefox") in Jaunty, which worked flawlessly, but in Karmic the command("aoss firefox) doesn't work. Does anyone know how to get multiple audioplayback in Karmic?

---

### Post by Potted Meat on 2009-11-11
Mine is broken too.  I had been using "padsp firefox" in Jaunty.  Now that doesn't work.  When Java uses the audio system it does not even show up in the PA volume control app.  If I go to YouTube and watch a video it will show up.  

Also, when Java is using the audio system nothing else will play at the same time.

I'm getting really frustrated with sound and Ubuntu. 

PM

---

### Post by thedaylights on 2009-11-19
I recently did a fresh 9.10 install and flash video worked immediately. I installed Amarok, then a while later youtube stopped producing sound. I followed a fix by uninstalling and reinstalling flash support. It worked again. I rebooted and ran Amarok, again, no sound for Youtube. 

All other flash video players I have tried fail to play video as well as sound (they stop after 2 or 3 seconds) while youtube plays only video, no sound.

EDIT ***
I uninstalled flash player via Ubuntu Software Centre (which is where I installed it) and reinstalled it via Synaptic. Youtube and other flash video works for now, with sound. Not sure why this happened??

---

### Post by thedaylights on 2009-11-22
It went back to not working. Youtube: no sound. Every other flash player: video for 2 seconds, then freezes. Help!?

---

### Post by VertexPusher on 2009-11-23
> **Potted Meat said:**
> Also, when Java is using the audio system nothing else will play at the same time.

I'm getting really frustrated with sound and Ubuntu.
Install the following packages:

gstreamer0.10-alsa
gnome-alsamixer
alsa-oss

Remove the following packages:

pulseaudio
gstreamer0.10-pulseaudio
vlc-plugin-pulse

Restart the computer, log in and run
```
speaker-test
```
If you hear the test sound, you're done. Your system is using ALSA now instead of PulseAudio. Start your Java applications with aoss as usual. Use gnome-alsamixer to control volume levels. Use asoundconf to select your default soundcard if there is more than one soundcard in your computer.

---

### Post by NoonienSoong97 on 2009-11-24
> **VertexPusher said:**
> Install the following packages:

gstreamer0.10-alsa
gnome-alsamixer
alsa-oss

Remove the following packages:

pulseaudio
gstreamer0.10-pulseaudio
vlc-plugin-pulse

Restart the computer, log in and run
```
speaker-test
```
If you hear the test sound, you're done. Your system is using ALSA now instead of PulseAudio. Start your Java applications with aoss as usual. Use gnome-alsamixer to control volume levels. Use asoundconf to select your default soundcard if there is more than one soundcard in your computer.

Well can't remove pulseaudio, or gstreamer0.10-pulse audio unless I also remove ubuntu-desktop which I think is a bad idea. Or do I have to redirect my audio to another program before uninstalling those packages?

---

### Post by thedaylights on 2009-11-24
I may have found a solution:

> Removing Conflicting Plugins

Ubuntu comes with swfdec plug-in, but it doesn't work on several sites. Installing the version from Adobe might solve this problem and improve performance.

To remove other flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

Code:

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree



From [Firefox Optimization Thread]("http://ubuntuforums.org/showthread.php?t=1193567").

---

### Post by Truckerpunk on 2009-11-26
I found a work-around, to solve my problem with Java and multiple audio playback... Here's what I did:

1. This step might not be necessary!!!
   I completely removed Pluseaudio with: 
    
   $ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio

   and then;

   $ sudo apt-get autoremove

2. Install Google chrome Ddevelopment version for linux from          
   here:
   
   [http://www.google.com/chrome/intl/en/eula_dev.html?](http://www.google.com/chrome/intl/en/eula_dev.html?)      
   dl=unstable_i386_deb

   or

    [http://www.google.com/chrome/intl/en/eula_dev.html?](http://www.google.com/chrome/intl/en/eula_dev.html?)
    dl=unstable_amd64_deb

3: Add "aoss" (without the ") to the launcher for Google chrome. 
   This might not be necessary, but it works for me.      
   Start Google chrome, and let it synchronize your plugins, and     
   settings from firefox. (I use Sun Java).

4: Enjoy your Java applications with multiple audioplayback.

It's strange that the native linux browser firefox can't handle this, but a development version of Google Chrome can. I even tried it with Opera for linux, and this works as well. So it seems like it a problem with Firefox.

---

### Post by Potted Meat on 2009-11-29
Yes, Opera works with padsp but seems a bit unstable with the Java apps that I'm running.

I might give Chrome a try.

It's such a shame that after all these years, audio is still so difficult to get right.

---

### Post by Mr_Bumpy on 2010-06-22
I had the problem under Ubuntu Lucid where the sound output from Java apps would conflict with the sound output from other programs.  In other words, I couldn't play an MP3 and get sound output from the Runescape login screen simultaneously.  I did it by following these steps:

1. First, you will need to rename the java executable, and put another command in its place.  Enter the following commands using the terminal:
```
cd /usr/lib/jvm/java-6-sun/jre/bin
sudo mv java java.bin
sudo touch java
sudo chmod +x java
sudo nano java
```
2. Now, copy and paste the following into the nano editor window, then press CTRL-X to exit and Y to save changes:
```
#!/bin/bash
padsp /usr/lib/jvm/java-6-sun/jre/bin/java.bin "$@"
```
3. Restart Firefox if it is open, then test the sound.  An easy way is to visit this page: [http://javaboutique.internet.com/Guitar/]("http://javaboutique.internet.com/Guitar/").  Play around with the sounds, and then try to play an MP3 or something on your computer.  While the MP3 is playing, see if you can still hear the guitar sounds when you click on the buttons.

If it works, you may want to lock all of the sun-java6* packages at their current version in Synaptic, otherwise a future Java update may break this hack, and you'll have to do it all over again.

---

