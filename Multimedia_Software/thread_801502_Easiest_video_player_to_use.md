---
title: "Easiest video player to use"
date: 2008-05-20
forum: Multimedia Software
---

### Post by Fidelio1st on 2008-05-20
Ubuntu version: 8.04 Hardy Heron
Firefox version: 3.0b5

**Very new to Ubuntu/Linux, used to Windows/MAC environment



What is the easiest video player to install, so that videos will run properly on Firefox?  

For instance, whatever I have now will play Youtube videos, but not myspacetv videos on my myspace page.  Also I've noticed whatever I have will play certain videos, but the time bar (to move to a certain point in the video) does not work.

I downloaded VLC, but not sure if I installed properly into firefox (if that is possible) as it made no difference.

I'm very new to Ubuntu/Linux (not real comfortable with commands, etc), so I get overwhelmed with a lot of choices....I just want the simplest set of instructions to view videos properly... thanks.

---

### Post by cozmicharlie on 2008-05-21
> **Fidelio1st said:**
> Ubuntu version: 8.04 Hardy Heron
Firefox version: 3.0b5

**Very new to Ubuntu/Linux, used to Windows/MAC environment



What is the easiest video player to install, so that videos will run properly on Firefox?  

For instance, whatever I have now will play Youtube videos, but not myspacetv videos on my myspace page.  Also I've noticed whatever I have will play certain videos, but the time bar (to move to a certain point in the video) does not work.

I downloaded VLC, but not sure if I installed properly into firefox (if that is possible) as it made no difference.

I'm very new to Ubuntu/Linux (not real comfortable with commands, etc), so I get overwhelmed with a lot of choices....I just want the simplest set of instructions to view videos properly... thanks.

I think mplayer is the best to use in Firefox - this should help you to get it set up properly "http://ubuntuforums.org/showthread.php?t=766683".

---

### Post by Alan Coleman on 2008-05-21
Im using one called miro. seems worth a look.
sudo apt-get install miro  is the code ithink.

---

### Post by Fidelio1st on 2008-05-27
I'm following the directions here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Last thing I did was this command:
sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss compizconfig-settings-manager faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin pulseaudio-utils unrar w32codecs

And now I'm stuck on the sun-java6-bin license page that reads at top "Operating System Distributor License for Java v1.1 (DLJ)"

At the bottom of the page, it reads "<Ok>"  I scroll all the way down, press ENTER, try to click Ok, try typing Ok, and nothing happens, and there is no other button to accept the agreement or move past this page.

How do I proceed?

---

### Post by Fidelio1st on 2008-05-27
Found the answer here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/186071](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/186071)

So stupid, you have to press the tab key.  Like where does it tell you that.

Why is stuff on ubuntu so complicated?  This had me stuck for like an hour (I posted on here after being stuck for a bit).

Very frustrated ubuntu user here.  Why doesn't Ubuntu come with all of this already installed.  You have all this other stuff installed, why not set up video to work correctly.

VERY FRUSTRATED!!!!!!!!!!

---

### Post by digish778 on 2008-05-27
Please install Mplayer browser extension. You could find that in the Synaptic. You dont have to move to the commandline.

Open the Synaptic and in the Search area give the serach for mplayer.

you will find the mplayer browser extension. Please install the browser extension file.

This will help in the viewing of the videos.

Some of the videos in the internet requires the Windows Media Player 11, which cannot be player in the Linux, I feel. there might be a mthod to play that also.

---

