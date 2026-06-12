---
title: "Hear line in through speakers"
date: 2008-10-13
forum: Multimedia Software
---

### Post by matthewbpt on 2008-10-13
This should be simple enough. Is there a way to play line in sound through the speakers in real time? I want to plug in my guitar into the line in and play it through my speakers.
:guitar:

---

### Post by markbuntu on 2008-10-13
There should be a line-in in your sound mixer. Just unmute it and turn it up. But, some sound cards can switch the line in to Rear or Bass or other surround sound speaker outputs so be sure to check in your sound mixer or volume control that this option is not selected if you are using line-in for line-in

---

### Post by Zenzan007 on 2008-12-08
I hit a similar problem on my dell lattitude D830 (using a USB harddrive to hold the OS). Anyway the way I got it to work (finally) was right click on the volume control. Select "**Open Volume Control**" On the device tab, select each device and then click on "**Preferences**" for each device, Everytime enable all the options (This might be overkill but it's what I did), Un-mute these and turn the volume up. 

Then under "**HDA Intel (Alsa Mixer)**" *(Specific to my machine perhaps) *and then Click on the "**Options**" Tab. Change the "**Input Source**" to "**Mic**" and the second one *(in my case)* to "**Front Mic**".

Then the most important part. Select the "**switches**" Tab and Tick "**Analog Loopback**" If you get a high pitched squeal, change your "**Input Source**" on the "**Options**" Tab.

This is by no means a definitive solution! This is how I got my to work and I hope it might shed some light for others with a similar problem.

Good Luck! 
Z

---

### Post by bobbysmith007 on 2010-09-15
An easy way I found:
   * go the terminal
   * Type "alsamixer" and hit enter
   * go right a bunch till you find the input you are looking for ( you may have to go past the end of the screen)
   * make sure you turn the volume up and press m to unmute (if necessary)
   * you should hear your guitar / tv / game console etc (with no lag)

---

### Post by lalawawa on 2010-12-05
When I run 'alsamixer', I get this colored character interface that takes over the terminal window I run it from.  I can't see how I can do any input to the alsamixer.  I've used alsa stuff on linux on a previous computer (it was Suse 9.0, I'm now on Ubuntu 10.04 Lucid Lynx) and it was a graphical interface.

---

### Post by lalawawa on 2010-12-05
Why can't I just use "System" -> "Preferences" -> "Sound" to configure it to play "line in" through to output.

When I play something to line in and bring up the System -> Preferences -> Sound widget and select the "Input" tab, and watch the "Input level", I can see that what I'm playing in is registering.  But the sound doesn't make it through to "Output".

If I play a flash video within firefox, the sound from THAT makes it through to "Output".

---

### Post by lalawawa on 2010-12-05
I figured out how to use the character graphics alsamixer.  Used the left and right arrow keys to select what I was adjusting, then the up and down arrow keys to set the level.  Adjusting the "line in" and "master" levels set the volume to whatever I wanted.

---

### Post by lalawawa on 2010-12-05
Further information: you have to adjust "front" as well.  Also, the levels set by alsamixer seem to persist after you exit the alsamixer program.

---

