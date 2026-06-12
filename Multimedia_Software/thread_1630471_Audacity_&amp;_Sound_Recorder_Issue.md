---
title: "Audacity &amp; Sound Recorder Issue"
date: 2010-11-25
forum: Multimedia Software
---

### Post by derricklongley on 2010-11-25
Neither Audacity or Sound Recorder are picking up my voice through my computers microphone. I have tried some fixes, but I'm lost and need some tips on what might help, thanks.

---

### Post by gordintoronto on 2010-11-25
Usually, the microphone is muted by default. Click on the speaker and select "sound preferences, then go to "input."

You might also need to crank up the volume.

---

### Post by derricklongley on 2010-11-25
Yeah, I have no device to unmute, so I think that is the problem?

---

### Post by gordintoronto on 2010-11-25
More information, please!  What computer? What sound device? lspci output? Do you have speakers or earphones?

---

### Post by derricklongley on 2010-11-26
Acer Aspire 4520 and I have sound, just no recording of voice through my integrated microphone. nVidia Corporation MCP67 High Definition Audio (rev a1)

---

### Post by gordintoronto on 2010-11-26
According to your manual, is there a way to disable the sound input? Or perhaps it's disabled in the BIOS?

---

### Post by lidex on 2010-11-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by derricklongley on 2010-11-28
[http://www.alsa-project.org/db/?f=371c6820e0a9dd4888e3edd4b26d038d365100f8](http://www.alsa-project.org/db/?f=371c6820e0a9dd4888e3edd4b26d038d365100f8)

---

### Post by lidex on 2010-11-28
You have added model=acer somewhere, probably alsa-base.conf, yet it doesn't seem to be affecting the sound module. Also your alsa components are mismatched. My suggestion is remove the alsa-base.conf entry and reboot. Next update your alsa install via the link in my sig.

---

### Post by derricklongley on 2010-11-28
I'll give it a try and get back to you, thanks.

---

### Post by derricklongley on 2010-11-28
I keep getting this message below



E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

-------------------------------------------------------------
-  Prepare for compilation and installation...
-------------------------------------------------------------

/usr/src/Alsa-1.0.20 not found

---

### Post by lidex on 2010-11-30
The first messages usually indicate another process is using dpkg, ie update manager, synaptic, etc. Make sure these are closed and try again. Are you using this script:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
alsa version should be 1.0.23 not 20

---

### Post by derricklongley on 2010-12-01
Sorry, I get a fail on listening the first time. I had like .17 upgrade? 

I did finally do exactly what you said and still not working and this is what the results of the cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Dec  1 2010 for kernel 2.6.32-26-generic (SMP).

Where is aplay because I didn't see it.

---

### Post by lidex on 2010-12-02
> **derricklongley said:**
> Sorry, I get a fail on listening the first time. I had like .17 upgrade? 

I did finally do exactly what you said and still not working and this is what the results of the cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Dec  1 2010 for kernel 2.6.32-26-generic (SMP).

Where is aplay because I didn't see it.

OK. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by derricklongley on 2010-12-02
I have lost sound from stuff like vlc, but my Internet sound plays fine.

[http://www.alsa-project.org/db/?f=ca8a9313d39596917df0e283323c1a874fbda636](http://www.alsa-project.org/db/?f=ca8a9313d39596917df0e283323c1a874fbda636)

---

### Post by lidex on 2010-12-03
What is your audio output in vlc set to?
What about gstreamer apps like rhythmbox and totem?

---

### Post by derricklongley on 2010-12-04
It started working again, and those devices you mentioned are set to default. The recording though is still not working and I have a bunch of things in my sound and video section that don't work like echomixer, envy24, redmigicontrol, and aconnectgui?

---

