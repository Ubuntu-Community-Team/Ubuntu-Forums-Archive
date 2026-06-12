---
title: "Microphone - &quot;Failed to construct test pipeline&quot;"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by Benthe1st on 2007-12-07
Hi everyone!

I had feisty before, and everything worked fine. I've changed to gutsy, and now my mic doesn"t work. At System->Settings->Sound when I try to make record test i get the message:
```
"Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'"
```
Any ideas what should i do?

---

### Post by android6011 on 2007-12-08
bump same problem

---

### Post by carambolos on 2007-12-08
I have the same problem...

---

### Post by bhencetotozo on 2007-12-09
I have the same problem

---

### Post by Benthe1st on 2007-12-10
Ok, I'm not alone, but does anyone have any solution?

---

### Post by android6011 on 2007-12-13
this is kinda weak, no one can help in any way? having mic/line in ports and pretty important for some users

---

### Post by beauman on 2007-12-13
@ android6011  

> this is kinda weak, no one can help in any way? having mic/line in ports and pretty important for some users

Yeah. I posted a problem with an usb mic about everywhere, but no one did even answer...
see 
[http://ubuntuforums.org/showthread.php?p=3933077#post3933077](http://ubuntuforums.org/showthread.php?p=3933077#post3933077)
[http://forum.ubuntuusers.de/topic/137812/](http://forum.ubuntuusers.de/topic/137812/)

The mic I have (rode podcaster) is one of the best for speech recording. Next to the 
se electronics usb2200a. Which seems to work
[http://lalists.stanford.edu/lau/2006/12/0609.html](http://lalists.stanford.edu/lau/2006/12/0609.html)
But this one is way too expencive for me.

Can maybe somebody recommend a good usb mic for speech recording?

I wonder why usb mics are so poorly supported, if they don't come with any
special win drivers and work under windows just out of the box...

:guitar:
-jc-

---

### Post by zyg0t3 on 2007-12-15
Same problem here. This seems like its a gnome problem not ubuntu. might be time to try kubuntu? or get E17.

[http://lists.opensuse.org/opensuse-bugs/2007-11/msg03402.html]("http://lists.opensuse.org/opensuse-bugs/2007-11/msg03402.html")

[http://forums.fedoraforum.org/showthread.php?t=174341]("http://forums.fedoraforum.org/showthread.php?t=174341")

---

### Post by Benthe1st on 2007-12-18
Ok, but it worked in feisty...i hope they will fix it soon

---

### Post by alienpilgrim on 2007-12-18
I had, the same problem with my new vostro 1500. Here are the steps I went through to get the microphone working, even though the "Failed to construct test pipeline" error still persists with the Sound Preferences application.

1) Right click the speaker on panel, choose "Open Volume Control"
2) Click "Options" tab.  If you don't see the options tab, edit preferences and enable "Digital input source", this will make it appear.
3) Change the "Digital Input Source" to "Digital Mic 1" from "Analog Inputs".

To set the mic volume, edit the preferences and enable "digital". A "Recording" tab appears.  Move the slider up for the Digital setting. Use the sound recorder to test your sound levels.

---

### Post by Benthe1st on 2007-12-21
Thx! You were right, i changed my settings, and now my microphone works, but the error message as you said still exists. So its ok this way, i can use it.

---

### Post by Najmudin on 2007-12-21
> **Benthe1st said:**
> Thx! You were right, i changed my settings, and now my microphone works, but the error message as you said still exists. So its ok this way, i can use it.

Yes , thanks for him , after two months of waiting i can record what i hear .:guitar:
Many thanks .:)

---

### Post by Braytok on 2007-12-31
I had none of those options in my options tab :( still no mic.

---

### Post by Braytok on 2007-12-31
Fixed my problem...untill reboot anyway...

I just opened "edit > preferences" and checked all switches out of desperation. Working now.:confused:

---

### Post by bosstweed on 2008-01-09
Bump same problem. Two different computers both running Gutsy- exact same problem! Have tried advice from above with no success.

---

### Post by ScottKidder on 2008-01-15
Same problems here, using a Sound Blaster Audigy LS, and looking to use my mic only for CS 1.6 through Steam/Wine, any solutions, that have worked other than what has been posted, these have not worked for me e.g All settings are checked in alsamixer, and volume control, and sound recorder records no sound no matter the settings

---

### Post by elamd on 2008-01-15
Same problem here.  Ironically, I'm Ubuntu Studio 64.  Kinda hard to edit music when you can't make any.

Anyway, got it working by doing what Braytok did.

But every application almost always requires you to select a audio driver(oss, alsa, jack) etc.  Is there an explanation for any of this, particularly how JACK fits in?

---

### Post by macabro22 on 2008-01-29
bump!

---

### Post by dbclinton on 2008-03-03
alienpilgrim's workaround solution is a great start, but it still doesn't get alsamixer going.
David

---

### Post by jaredssix on 2008-03-05
My mic worked yesterday and for the last three months, and today it doesn't!

bump.

---

### Post by mnfiddledragon on 2008-03-06
I'm also having an issue with microphone unresponsiveness. However - this is with a simple regular mic - not with an USB mic. Could this be the same thing?

I'll check for the error this evening, but I'm not at the computer that is having this issue right now.

Said computer is running Gutsy. The issue with noted with both an onboard intel sound chip as well as with a SoundBlaster Audigy SE.

---

### Post by punong_bisyonaryo on 2008-03-07
I have a built-in mic in my Gutsy on a Kohjinsha SH6 and I tried checking all the checkboxes I can find in Volume Control and turning up all the recording levels. However, I only get hissing sounds.

I'm not sure what this means. Does it mean that my mic is detected but not properly configured? My mic can't be detected properly? My mic is broken?

---

### Post by jKeats3 on 2008-03-08
The only place I can get my mic working is in "Sound Preferences" under the "System->Preferences" menu.  Even then there's an intermediate clicking sound overlaying the mic input.  Any time I try to record in a recording program, the program complains, saying that my multimedia settings are invalid.  Yet it works during the test.

This is highly annoying.  I hope Canonical comes up with a better way to manage change; it looks like right now that the knowledge that the current distro has a given capability is no indication of confidence that the same capability will be available in the next distro.  Or that the same programs will work with it.  Bit of a crapshoot, no?

Bump.

---

### Post by jaredssix on 2008-03-09
An update: Remember my mic was working one day (three months, actually), and the next is wasn't. I ended up re-installing, and now everything is a go once again.

Punong, you say you clicked all the boxes you can find. Some "checkable" aren't automatically listed; they are accessible through first clicking on parameters in Preferences, and then checking the tabs in the GUI for the recently clicked parameters, were you may have to check them again. You may be better off performing this exercise through alsamixer (enter alsamixer into the terminal). Make sure you have all the 'capture' bits enabled, and mic boost as well.  

Navigate through alsamixer with the arrow keys. Adjust volumes with the arrow keys. Go page to page with the tab key. Unmute with the "m" key (mute is indicated by to "m"s). And enact a parameter with the space bar.

---

### Post by Mazrick on 2008-03-18
Gutsy 7.10 Install
AMD 3000+ EForce 3 250 chipset
Epox board with AC 97 sound
NVidia CK8S

Yes, I've had these same issues and have been able to resolve most of them by setting up my capture settings minimally as follows. (Note: if your hardware is different than mine, the names of devices etc. may be different. In these cases, you should follow the spirit of these instructions more than the letter, when determining which settings to make.)

I first went to the menu item "System/Preferences/Sounds". Goto the "Devices" tab, then select the "ALSA" options for all of the selection boxes.
Now go to the "Sounds" tab: Uncheck "Enable software sound mixing (ESD)"
Close the Sound Preferences window.

Then right click on the Sound Volume speaker in the upper right of the screen and select "Open Volume Control". In the "Volume Control" window that should now be open,  I went to the menu item "Edit/Preferences", and selected ALL the options in that list.

Now, select the "Recording" tab: unmute "Capture"
Now, select the "Switches" tab: select only "Microphone Capture" and "Mic Boost" boxes, uncheck all other boxes.
Now, select the "Playback" tab, and unmute "Master", "Master Mono", "PCM", "PC Speaker". Mute all other options on the Playback tab.

Now reboot and test.

All my sound works including the mic for Skype, etc, BUT I do still get the error message 
> Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat' when I try to run the Capture Test in the "System/Preferences/Sound" window.

---

### Post by macabro22 on 2008-03-19
weird...

---

### Post by jimifelony on 2008-03-19
I managed to partially solve my issue with help from a workaround i found [here]("http://samjordan.co.uk/?p=25")

First I had to install gstreamer-tools:

```
sudo apt-get install gstreamer-tools
```

then i ran:

```

LC_ALL=C gst-launch gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat
```

after ensuring nothing was muted and mic capture was on I could use skype and audacity, to stop hearing myself through the speakers i pulled the mic volume slider under playback to minimum (not muted) on the volume control.

It still gives errors in the gnome sound test, but hey, it works.

To keep it working after rebooting I added the fix to System>Prefrences>Sessions

---

### Post by MaindotC on 2008-05-12
alienpilgrim your solution worked for me.  I can't seem to star you...

---

