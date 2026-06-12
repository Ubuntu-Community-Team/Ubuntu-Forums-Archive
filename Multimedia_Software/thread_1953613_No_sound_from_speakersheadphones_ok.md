---
title: "No sound from speakers/headphones ok"
date: 2012-04-06
forum: Multimedia Software
---

### Post by ForrestBrandt on 2012-04-06
Hey all,
Been having this persistent problem where sound plays ok from my headphones but not from my onboard speakers.   
I've searched around on the web and tried various things but to no avail. 
I Even updated to 12.04 but it didn't solve the issue either.  

Here is the link from my output from SOUNDTROUBLESHOOTING ([https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)) step 4:

[http://www.alsa-project.org/db/?f=71a089123d2be85724a5dc78cda899237548e6f1](http://www.alsa-project.org/db/?f=71a089123d2be85724a5dc78cda899237548e6f1)

I noticed that ALSA driver didnt match, maybe thats the problem.

!!ALSA Version !!------------  Driver version:     1.0.24 Library version:    1.0.25 Utilities version:  1.0.25 

but i am not sure about how to correct this.  

Help is greatly appreciated.

---

### Post by Yellow Pasque on 2012-04-06
> I noticed that ALSA driver didnt match, maybe thats the problem.

That's not inherently problematic, but if you want to try latest kernel module:
```
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkms
```

If that doesn't work, play with hda analyzer: [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

EDIT: Also, you have multiple snd-hda-intel model= lines in alsa-base.conf. Use one at a time.

---

### Post by ForrestBrandt on 2012-04-07
Updating the kernals didnt work.    
I am playing around with the hda link you sent, nd will let you know.


"EDIT: Also, you have multiple snd-hda-intel model= lines in alsa-base.conf. Use one at a time. 	"

Can let me know how access this and set it to use one at a time.

thanks

---

### Post by Yellow Pasque on 2012-04-07
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Delete one or both of those lines.

---

### Post by ForrestBrandt on 2012-04-07
Hey ,so i got rid of those lines in gedit, then rebooted, but still no sound from speakers, 

As far as using the HDA analyzer, I messed around for a while, but I must admit that I am not to sure what I am looking for.  saw that some of the sliders on the various Aud-out were set to s low volume, so i tried to slide them up.  but that didnt do much.

Anytips on what to look for, thasnks for you help

Forrest

---

