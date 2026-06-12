---
title: "Audacity not recording internal sound"
date: 2012-02-24
forum: Multimedia Software
---

### Post by dkolars on 2012-02-24
Recently upgraded from 10.10 to 11.04...  Also have a new system that is working just fine... 
A buddy sent me a link to his SoundCloud page so I could get a song of his...   So, today I opened Audacity for the first time on the new system/OS and found that I cannot record what is playing on my system speakers.  I have dic**d around with Audacity since day one with Linux, and can honestly say that I'm far from being a fan of the program!!  

In Windoze, I used CoolEdit2000 with a few plugins and LOVED it... very intuitive, easy to run, etc.  Not so Audacity, in my experience, at least.  I've attempted to run CoolEdit under Wine, but it fails miserably... I've installed Virtual Box, but have not had time to mess with it running my old programs.  

So, in Audacity, I have for recording input choices the following:

HDA ATI SB: ALC892 Analog (hw:0,0)
pulse: Rear Mic:0
pulse: Front Mic:0
pulse: Line:0
pulse: Rear Mic:1
pulse: Front Mic:1
pulse: Line:1
default: Rear Mic:0
default: Front Mic:0
default: Line:0
default: Rear Mic:1
default: Front Mic:1
default: Line:1

I plug in the front mic, and it works under "pulse: Front Mic:0".  I have not tried a rear mic (I got better things to do than check the mic in the rear since I never use it!!)...  

NONE of the Line settings work.  

So, if I want to record whatever is playing on my system, I need to hold the mic up to the system speakers.  Duh...  I think not.

So, any gurus have a fix for this?  Or a better program (my 1st choice!)...

Would a separate sound card, rather than the MB soundchip be a good investment?  Frustrating, to say the least...  Grrrr...  :mad:

TIA!!  DK

---

### Post by Bobhuber on 2012-02-24
> **dkolars said:**
> Recently upgraded from 10.10 to 11.04...  Also have a new system that is working just fine... 
A buddy sent me a link to his SoundCloud page so I could get a song of his...   So, today I opened Audacity for the first time on the new system/OS and found that I cannot record what is playing on my system speakers.  I have dic**d around with Audacity since day one with Linux, and can honestly say that I'm far from being a fan of the program!!  

In Windoze, I used CoolEdit2000 with a few plugins and LOVED it... very intuitive, easy to run, etc.  Not so Audacity, in my experience, at least.  I've attempted to run CoolEdit under Wine, but it fails miserably... I've installed Virtual Box, but have not had time to mess with it running my old programs.  

So, in Audacity, I have for recording input choices the following:

HDA ATI SB: ALC892 Analog (hw:0,0)
pulse: Rear Mic:0
pulse: Front Mic:0
pulse: Line:0
pulse: Rear Mic:1
pulse: Front Mic:1
pulse: Line:1
default: Rear Mic:0
default: Front Mic:0
default: Line:0
default: Rear Mic:1
default: Front Mic:1
default: Line:1

I plug in the front mic, and it works under "pulse: Front Mic:0".  I have not tried a rear mic (I got better things to do than check the mic in the rear since I never use it!!)...  

NONE of the Line settings work.  

So, if I want to record whatever is playing on my system, I need to hold the mic up to the system speakers.  Duh...  I think not.

So, any gurus have a fix for this?  Or a better program (my 1st choice!)...

Would a separate sound card, rather than the MB soundchip be a good investment?  Frustrating, to say the least...  Grrrr...  :mad:

TIA!!  DK
outRec > [http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)

---

### Post by ajgreeny on 2012-02-24
Run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture" where you can move to the line slider and hit spacebar to activate line in capture. See screenshot.
Esc will save and exit.  That may do the trick.

---

### Post by calande on 2012-02-24
I have a similar problem. When I record anything, I only get a white noise. I use either Audacity or the Sound Recorder that comes with Ubuntu. I tried just about every input devices from the list. I ran alsamixer and all levers are up. I'm trying to record an Internet radio from a Flash applet. Any idea?

---

### Post by Hylas de Niall on 2012-02-24
Loopback cable from headphone to mic?

---

### Post by calande on 2012-02-24
Do you suggest to add a cable? But I have only one output (to the speaker)...

---

### Post by Hylas de Niall on 2012-02-24
I believe it's possible with a male/male lead from speaker/headphone jack to mic/line in jack, but be careful with the levels.

In Windows7 it's a case of enabling non-default sound settings for stereo mix recording, but (i think) that's do-able due to funcions of the proprietry drivers. Sadly i have no idea how to do the same thing with foss drivers other than what has already been suggested.

I'd be interested to see how it's done too, as i have to boot my Win7 machine to record streaming audio right now.

---

### Post by calande on 2012-02-24
Me too, I need to reboot into Windows to record my radio, it's a pain in the a## :(

---

### Post by dkolars on 2012-02-24
Bob Huber!  Thanks... works like a champ, once I got it installed...  kinda coughed and sputtered for a minute, but eventually it "took"...  GREAT recording quality, too!!  Then, can edit in Audacity... see, it's good for something!!

> outRec > [http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)  -- I recommend this if you're having problems... my AlsaMixer settings were fine, the sound controls were all fine, etc. etc. etc.  

DK

---

### Post by calande on 2012-02-25
while installing outrec, I face this bug: [https://bugs.launchpad.net/ubuntu/+source/gambas/+bug/672859](https://bugs.launchpad.net/ubuntu/+source/gambas/+bug/672859)

---

### Post by dkolars on 2012-02-25
I think I saw that as well... It took me 3 tries to get it installed, but it worked...

---

### Post by Baldrick_NZ on 2012-02-26
> **dkolars said:**
> Bob Huber!  Thanks... works like a champ, once I got it installed...  kinda coughed and sputtered for a minute, but eventually it "took"...  GREAT recording quality, too!!  Then, can edit in Audacity... see, it's good for something!!

  -- I recommend this if you're having problems... my AlsaMixer settings were fine, the sound controls were all fine, etc. etc. etc.  

DK

Outrec works awesomely! How do you change settings, like increase the recorded bit rate? I find 112kbps vorbis is a bit low...

Any ideas?

Cheers.

---

### Post by calande on 2012-02-26
After 3 tries I still get this error message:

```
$ sudo dpkg -i outrec_0.0.3-1_all.deb
(Lecture de la base de données... 215112 fichiers et répertoires déjà installés.)
Préparation du remplacement de outrec 0.0.3-1 (en utilisant outrec_0.0.3-1_all.deb) ...
Dépaquetage de la mise à jour de outrec ...
Paramétrage de outrec (0.0.3-1) ...
Traitement des actions différées («*triggers*») pour «*menu*»...
Dans le fichier «*/usr/share/menu/outrec*» à (ou dans la définition qui se termine à) la ligne 4*:
?package(outrec):needs="X11" section "Applications/Sound" title="outRec" command="/usr/bin/outrec.gambas" icon="/usr/share/pixmaps/outrec.png"
                                     ^
Attendu*: «*=*»
Traitement du fichier abandonné en raison d'erreurs...
Traitement des actions différées («*triggers*») pour «*desktop-file-utils*»...
Traitement des actions différées («*triggers*») pour «*bamfdaemon*»...
Rebuilding /usr/share/applications/bamf.index...
Traitement des actions différées («*triggers*») pour «*gnome-menus*»...
```

---

