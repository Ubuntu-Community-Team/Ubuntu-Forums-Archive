---
title: "[SOLVED] Flash only plays sound through my on-board soundcard"
date: 2008-06-30
forum: Multimedia Software
---

### Post by boom2k1 on 2008-06-30
I bought and installed a soundcard (Diamond X71)
I have already configured in "Sound" (System->Preferences->Sound) the new soundcard to use C-Media PCI DAC/ADC.

It works fine for songbird, totem, etc..
However, the problem is that Flash embedded in firefox does not play sound to my new soundcard, even though I heard sound from my old old-board soundcard (connected through the front jack).

How should I fix it?

I have already tried to the instruction: 

 sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
SB
CMI8768


asoundconf set-default-card CMI8768


However, it does not fix the issue for me.


Please help!

---

### Post by Andreas1 on 2008-07-01
bump
same here: onboard sound broken, selected usb sound in system preferences, totem sound works, but firefox (flash) does not

---

### Post by markbuntu on 2008-07-01
You can disable the old sound card in your bios and everything should default to the new one but try this first.

Open PulseAudio Manager and go to devices. Play something and see if it shows up as a Sink. It will be labelled 

#something. 

You can highlight it and click properties and that will tell you which app is using it.

If nothing shows up the app is using alsa directly. If flash shows up and these others do not then we have narrowed the problem down to pulse audio using the wrong device. Open the Pulse Audio Volume Control and see if it is set to the same Output Device as you set in System/Preferences/Sound. If you see the correct one right click on it to make it the default.

You may need to reboot for these changes to take effect. 

If you are still having problems come back here.

---

### Post by boom2k1 on 2008-07-02
Thank you. It solves the problem!

I can't remember if Ubuntu 8.04 comes with the pulseaudio manager by default. To install it, I think we type:
```

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

```

according to [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

After we install the PulseAduio Manager, we type padevchooser in the Terminal.
If you want to enable change to all the users, we would probably type
```
 sudo padevchooser 
``` instead.

This fires up a pulseaudio tray icon. Left clicking it would give me an option to run the Manager.
Following the instruction above, I open some youtube flash video from Firefox, and I see that from the Device tab of Manager, there is the #1    Flash Animation line. However, what is wrong is that it is listed under my on-board sound card, which is not what I want.

To fix it, I left click the pulseaduio tray icon and select Volume Control there. This fires up the PulseAudio Volume Control program. The first tab opened is the Playback tab, and I can see Adobe Flash: Flash Animation subsection.
In there, I notice the Hint: Right Click on a playback stream to move it to another output device. 
Therefore, I right click on the bolded "Adobe Flash:" textlabel, under which I can then access the Move Stream... list to select the appropriate soundcard.
After selecting the appropriate soundcard, I can hear the Flash audio immediately!

[My first attempt was to try changing the Default Sink directly using the "Other" option. However, this wouldn't work.]

[I haven't tried rebooting it, although this change persists after re-logging into the same user.]

---

### Post by boom2k1 on 2008-07-02
also, I don't know if it is relevant, but I think I once installed a deb package that makes Adobe Flash uses the Pulseaudio layer.

---

### Post by markbuntu on 2008-07-02
Ok, glad to help out. Please mark this thread as solved in the thread tools above.

---

