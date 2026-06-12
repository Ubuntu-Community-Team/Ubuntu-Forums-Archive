---
title: "Jaunty &amp; Logitech USB Headset"
date: 2009-04-24
forum: Multimedia Software
---

### Post by spikoley on 2009-04-24
I cannot get my [Logitech ClearChat Comfort USB headset]("http://www.newegg.com/Product/Product.aspx?Item=N82E16826104214") to work in Jaunty.  Has anybody got this model or any other Logitech USB Headset to work?  Usually [this thread]("http://ubuntuforums.org/showthread.php?t=509598&highlight=headset") would do the trick.

When I go into Sounds and click test I get the following error:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

---

### Post by gnimsh on 2009-05-05
This happens to me as well.  In Skype I can set the default device to pulse, in which case the sound is sent to my headset AND my speakers.  When I choose the actual USB headset setting, it doesn't work.  When I try to make calls with twinkle by using the headset, it tells me that the device is busy despite the fact that it is not being used by any other devices.

---

### Post by Vihura on 2009-05-05
I have Logitech USB Headset and i think where is the problem, if i go to (Gnome)System>Preference>Sound I can choice ' Logitech USB Headset USB audio (OSS)' in all tabs exept last one 'Defaul Mixer Tracks' ' Logitech USB Headset USB audio (OSS)' is not on the option list. I have sound in totem, and skype but not in Firefox, (youtube), no system sound and no VLC. Any sugestion ?

---

### Post by LonelyAppleHater on 2009-05-11
I was having a problem getting my Logitech USB 350 Headset working also.  But, I came across this post:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I pretty much did the Part A section of it, logged out, logged back in, and Twinkle and other apps were able to see it again.  Also, make sure you do the sudo apt-get autoremove or go to System -> Administration -> Cleanup Janitor in order to get rid of some of old and obsolete packages if you haven't done so already.  

Hope this helps!

---

### Post by jschodde on 2009-09-22
The headset I own is this one:
[http://www.logitech.com/index.cfm/webcam_communications/internet_headsets_phones/devices/223&cl=us,en]("http://www.logitech.com/index.cfm/webcam_communications/internet_headsets_phones/devices/223&cl=us,en")

I'm on Jaunty and I couldn't get it to work, nor could I find any mention of "Logitech" in the System > Preferences > Sounds settings. What I did was the following:

[LIST]
[*]Plugged in the headset (USB)
[*]Run System > Administration > Computer Janitor
[*]Log out
[*]Log in
[*]System > Preferences > Sounds, under "Music and Movies" I selected "Logitech Logitech USB Headset USB Audio (OSS)" and clicked the Test button and it worked. Note that "(ALSA)" option did not work.
[/LIST]

I don't think the Janitor had much to do with it because it just removed several .deb packages laying around.

Oh, and I have not tried to get the microphone working yet. I just wanted to hear some music!

---

### Post by Crimson Kaze on 2009-09-28
I've got the same headset as AppleHater but I can't seem to get it working

---

