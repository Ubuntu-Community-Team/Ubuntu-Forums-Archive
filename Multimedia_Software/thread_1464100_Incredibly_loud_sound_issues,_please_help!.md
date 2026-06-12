---
title: "Incredibly loud sound issues, please help!"
date: 2010-04-27
forum: Multimedia Software
---

### Post by opethfan89 on 2010-04-27
Hi all

I recently installed Ubuntu 9.10 on my desktop and I now remember why I didn't ever use it, and that is because the sound volumes are ear-shattering loud across reboots. I have tried doing:
```
sudo alsactl store 0
```

However it doesn't save the settings. I can set the volumes manually using alsa-mixer but that is a pain.

Can anyone suggest what I can do? I _have_ read the "comprehensive fix to audio problems" sticky but it did not alleviate my problem. And as far as I know, my alsa is up to date.

I'm sorry I don't know the relevant output of code needed to show alsa version, etc., so please inform me and I will post accordingly.

Any help is very much appreciated,
Opethfan89

---

### Post by arvevans on 2010-04-27
The simple solution is to turn the volume down before doing a shutdown.  Then when you re-boot the volume will not be so loud.

Now, to better address your problem.  The sound system can take inputs from a variety of sources (CD, Microphone, Video decoding, MP3 decoding, and so on).  Each of these has it's own volume control, and own method of adjusting the volume level.  If your only volume control were the master volume, then there would be no solution to your problem.  However, there are individual sound source volume controls.  So, leave your master volume control set to a comfortable listening level, and use the specific application controls to set their levels to where you want.  

If using Gnome, you just right-click o the volume control icon in the top bar.  Click on "Sound Preferences".  This takes you to a pop-up window that has controls for "sound Effects", "Hardware", "Input", "Output", and "Applications".  This may be all you need to set default sound levels, but if not there are more controls available.  Pay particular attention to the "Input" sub-window.  This lets you select and adjust a number of sound sources.

Hope this lets you adjust your sound system to something less frightening.

---

### Post by lidex on 2010-04-27
Work through 'Part A' on this page:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by opethfan89 on 2010-04-28
> **arvevans said:**
> The simple solution is to turn the volume down before doing a shutdown.  Then when you re-boot the volume will not be so loud.

Now, to better address your problem.  The sound system can take inputs from a variety of sources (CD, Microphone, Video decoding, MP3 decoding, and so on).  Each of these has it's own volume control, and own method of adjusting the volume level.  If your only volume control were the master volume, then there would be no solution to your problem.  However, there are individual sound source volume controls.  So, leave your master volume control set to a comfortable listening level, and use the specific application controls to set their levels to where you want.  

If using Gnome, you just right-click o the volume control icon in the top bar.  Click on "Sound Preferences".  This takes you to a pop-up window that has controls for "sound Effects", "Hardware", "Input", "Output", and "Applications".  This may be all you need to set default sound levels, but if not there are more controls available.  Pay particular attention to the "Input" sub-window.  This lets you select and adjust a number of sound sources.

Hope this lets you adjust your sound system to something less frightening.

Thanks for the input arvevans. I **do** set my system volume down between reboots, but with the login noise and anytime I play music, it is still screechingly loud on startup (login noise has been disabled now though). I have tinkered with the alsamixer volume control in the terminal, and it seems that the volume is NOT the master volume, but rather two channels called "PCM" and "Headphones". PCM is left channel, headphones is right, and a combination of both regulates the volume of my speakers. Now, if I use the volume control icon in the gnome panel, or the controls on my keyboard, the Headphones volume shoots from whatever it is set at (20, for example) all the way to 75, same with PCM. As stated in my original post I have tried setting these manually and then saving the settings but they will not save for some god-forsaken reason :(

> **lidex said:**
> Work through 'Part A' on this page:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Thanks for the thread lidex. I attempted to work through part A but was greeted with various error messages when I tried to do step #5, so I cannot say whether this method works or not.

Here are the screenshots:
[IMG]http://i40.tinypic.com/wb9rtc.png[/IMG]



[IMG]http://i41.tinypic.com/16a1ezs.png[/IMG]

---

### Post by lidex on 2010-04-28
Try this in a terminal:
```
sudo apt-get install --reinstall esound-clients esound-common pulseaudio-esound-compat gstreamer0.10-esd
```

---

### Post by opethfan89 on 2010-04-29
> **lidex said:**
> Try this in a terminal:
```
sudo apt-get install --reinstall esound-clients esound-common pulseaudio-esound-compat gstreamer0.10-esd
```

That allowed me to finish the steps on that thread, and open PulseAudio volume control. I set the volumes accordingly but it still doesn't help. Any change in volume still causes my PCM and headphone audio channels to jump to 70's+ and blast my speakers. This is both from external controls (on my keyboard) and from manually dragging the slider on the gnome panel volume control applet.

---

### Post by Moozillaaa on 2010-04-29
Does the login sound come across severely distorted, as well as loud, and sounding like speed is accelerated?

[This thread]("http://ubuntuforums.org/showthread.php?t=955129&highlight=distorted") got my LOUD, DISTORTED sound fixed, in a NEW install.

---

### Post by opethfan89 on 2010-04-29
> **Moozillaaa said:**
> Does the login sound come across severely distorted, as well as loud, and sounding like speed is accelerated?

[This thread]("http://ubuntuforums.org/showthread.php?t=955129&highlight=distorted") got my LOUD, DISTORTED sound fixed, in a NEW install.


I have the login sound disabled, but any other sound (youtube videos, pandora, etc) are loud. And no, it doesn't sound like its accelerated but I did experience that previously.

And thank you for the thread, however I have already tried numerous times to set the alsa-mixer volume, but the settings don't save across reboots, and that is where my issue comes into play. The sound is automatically reverting to max every time the volume slider is adjusted, or the volume control key on my keyboard is pressed.

Thanks,
Opethfan89

---

### Post by Moozillaaa on 2010-04-29
> write failed: Bad state

How 'bout a failed sector on your hard drive?

---

### Post by lidex on 2010-04-29
Look at this page under 'Volume Range Anomalies':
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

To save alsa mixer settings:
```
sudo alsactl store 0
```

---

### Post by opethfan89 on 2010-04-29
> **Moozillaaa said:**
> How 'bout a failed sector on your hard drive?

Its a new hard drive, I doubt that'd be an issue. I think that just means a bad write to a file or a directory, not necessarily a hard ware failure issue, at least, I hope not!

> **lidex said:**
> Look at this page under 'Volume Range Anomalies':
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

To save alsa mixer settings:
```
sudo alsactl store 0
```

If you read my original post, I stated that I used that exact code, to no avail. It does not save for me :(

And thank you for that link, I remember reading through it once before and I will do so again to see if any of my problems are solved, and post back with any success (or lack thereof)


As a side note, I am going to install 10.04 here shortly (at least in a VM) and see if that has any sound fixes. Hopefully alsa/pulse FINALLY get the message and fix some of these issues that seem to be recurring.

---

### Post by lidex on 2010-04-29
> **opethfan89 said:**
> Its a new hard drive, I doubt that'd be an issue. I think that just means a bad write to a file or a directory, not necessarily a hard ware failure issue, at least, I hope not!
If you read my original post, I stated that I used that exact code, to no avail. It does not save for me :(

Think I was working too many threads - I did actually read that in your post :confused:
There is a recent thread with a fix but I can't find it now. Try these:
[http://ubuntuforums.org/showthread.php?t=1309427&highlight=save+volume+setting]("http://ubuntuforums.org/showthread.php?t=1309427&highlight=save+volume+setting")
[http://ubuntuforums.org/showthread.php?t=1203817&highlight=save+volume+setting]("http://ubuntuforums.org/showthread.php?t=1203817&highlight=save+volume+setting")
[http://ubuntuforums.org/showthread.php?t=586905&highlight=save+volume+setting]("http://ubuntuforums.org/showthread.php?t=586905&highlight=save+volume+setting")

---

