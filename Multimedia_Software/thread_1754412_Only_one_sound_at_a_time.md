---
title: "Only one sound at a time"
date: 2011-05-10
forum: Multimedia Software
---

### Post by Bobscrachy on 2011-05-10
I can't seem to get more than one thing to use to sound card at a time. If I'm watching a video, I can't listen to music. 

I'm new to ubuntu, so if you know the answer, please be specific.

---

### Post by Bobscrachy on 2011-05-10
bump

---

### Post by lidex on 2011-05-11
24 hours between bumps please.

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by coljohnhannibalsmith on 2011-05-11
[COLOR=Red]*If you're really still on Lucid **you've got problems.*[/COLOR]  This issue was ***not*** resolved in Lucid.  In order to get multiple inputs to ALSA to work, I had to purge Pulse-Audio.  This was compounded by the fact that when I purged Pulse-Audio, the volume control indicator applet disappeared.  I had to install ***gnome-alsa-mixer*** and pin it to the upper gnome-panel to have a working volume control.

Here is the link to my original thread:

[http://ubuntuforums.org/showthread.php?t=1525768&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1525768&highlight=amarok)

A better solution is to completely backup all of your data files and the perform a bare-metal installation  of Maverick.  This issue was resolved in Maverick; but only with a fresh install.  Maverick is very stable and the repositories are completely populated.

[COLOR=Red]***Notice I didn't say install Natty.  Natty is quite unstable, etc., etc...*[/COLOR]




[COLOR=Blue]Hannibal[/COLOR]

---

### Post by lidex on 2011-05-11
> **coljohnhannibalsmith said:**
> [COLOR=Red]*If you're really still on Lucid **you've got problems.*[/COLOR]  This issue was ***not*** resolved in Lucid.  In order to get multiple inputs to ALSA to work, I had to purge Pulse-Audio.  This was compounded by the fact that when I purged Pulse-Audio, the volume control indicator applet disappeared.  I had to install ***gnome-alsa-mixer*** and pin it to the upper gnome-panel to have a working volume control.

Here is the link to my original thread:

[http://ubuntuforums.org/showthread.php?t=1525768&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1525768&highlight=amarok)

A better solution is to completely backup all of your data files and the perform a bare-metal installation  of Maverick.  This issue was resolved in Maverick; but only with a fresh install.  Maverick is very stable and the repositories are completely populated.

[COLOR=Red]***Notice I didn't say install Natty.  Natty is quite unstable, etc., etc...*[/COLOR]




[COLOR=Blue]Hannibal[/COLOR]

Whoa, flashy. It may not have worked for you but it worked for 98% of the rest of us.

---

### Post by Bobscrachy on 2011-05-21
> **lidex said:**
> 24 hours between bumps please.

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

[http://www.alsa-project.org/db/?f=6692e7968aef55f9e4ace2dcf639a916f8b20f87](http://www.alsa-project.org/db/?f=6692e7968aef55f9e4ace2dcf639a916f8b20f87)

---

### Post by lidex on 2011-05-21
> **Bobscrachy said:**
> [http://www.alsa-project.org/db/?f=6692e7968aef55f9e4ace2dcf639a916f8b20f87](http://www.alsa-project.org/db/?f=6692e7968aef55f9e4ace2dcf639a916f8b20f87)

I'd suggest upgrading alsa via the link in my sig.

---

