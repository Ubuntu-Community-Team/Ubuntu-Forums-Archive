---
title: "Can't hear line input"
date: 2009-10-31
forum: Multimedia Software
---

### Post by ScottLij on 2009-10-31
The line input seems to be working on my Ubuntu 9.10 box, I can go to audacity or sound recorder and record the audio coming in through the line input port but I can't figure out how to I just listen to it?  In Sound Preferences the input volume is not muted and the input level has activity.

---

### Post by ScottLij on 2009-11-01
bump?

---

### Post by jsampaio57 on 2009-11-07
> **ScottLij said:**
> The line input seems to be working on my Ubuntu 9.10 box, I can go to audacity or sound recorder and record the audio coming in through the line input port but I can't figure out how to I just listen to it?  In Sound Preferences the input volume is not muted and the input level has activity.

I have the same problem. It was as easy as un-checking the speaker's "mute" in the previous version of gnome-volume-control. Aparently this current version is great, but I can get no direct sound from the line input to the output. I can record using the Sound Recorder, but... In fact all I want is to connect my new digital radio (with only one speaker) to the PC so that I can listen the stereo through the PC speakers!

Cheers...
Jorge

---

### Post by Kenneth D. Gladden on 2009-11-07
Had the same problem.
Solved by going to Synatic and installing aumix then 
running amux from menu and increasing volume on line.:D

---

### Post by ScottLij on 2009-11-08
Hmm, when I run aumix I only have three volume controls for Volume, IGain, and PhoneOut.  Tried increasing the line in volume from the command line using aumix but it didn't work.  Any other suggestions?

---

### Post by mxc1090 on 2009-11-08
> **Kenneth D. Gladden said:**
> Had the same problem.
Solved by going to Synatic and installing aumix then 
running amux from menu and increasing volume on line.:D

Thank you. I actually googled "line in ubuntu 9.10" and found this thread. That was all I needed. Now I can use my xbox 360 on my monitor and sound through the speakers.

Timely search too...this thread is pretty recent.

---

### Post by mxc1090 on 2009-11-09
.

---

### Post by Drumber on 2009-11-09
I am having the exact same problem.  I am very new to ubuntu and Linux in general, could someone tell me what Synatic/aumix are and how to obtain them?

---

### Post by JCK-longhair on 2009-11-12
> **Drumber said:**
> I am having the exact same problem.  I am very new to ubuntu and Linux in general, could someone tell me what Synatic/aumix are and how to obtain them?

Hi, I'm new here too :)

Use the Synaptic Package Manager, which is in System menu --> Administration, to find and install aumix. (There are other threads describing in detail how to use Synaptic Package Manager). I typed "aumix" into the search box then chose to install  "aumix-gtk", because it has the graphical interface. (Click in the check box and "Mark for Installation", then hit the "apply" button and follow through. Once it's installed it magically appears in the Applications --> Sound & Video menu.)

Hope that helps!

---

### Post by Drumber on 2009-11-12
Thanks for the info. Though moving the sliders around didn't cause the line in to be played though the speakers. I can see the level in sound prefrences and record from it, same as ScottLij.[URL="http://ubuntuforums.org/member.php?u=317723"]
[/URL]

---

### Post by k7k0 on 2009-11-20
Try this [http://ubuntuforums.org/showpost.php?p=8308073&postcount=3](http://ubuntuforums.org/showpost.php?p=8308073&postcount=3)
That solved my problems with STAC9227 card

---

