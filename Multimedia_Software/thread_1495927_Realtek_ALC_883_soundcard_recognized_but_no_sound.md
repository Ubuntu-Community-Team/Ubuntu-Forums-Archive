---
title: "Realtek ALC 883 soundcard recognized but no sound"
date: 2010-05-28
forum: Multimedia Software
---

### Post by zazkia on 2010-05-28
Hi all, 

I have an MSI S420 with a realtek alc883 onboard. 
I upgraded from ubutu 8.04 to 10.4 recently, The sound worked in  8.04 although the mic did't work and the same thing in 8.10 (i went through all upgrades) it stopped working at all in 9.04 onwards.

If i did Lspci -v it did say the name of my card, ( I unmuted all in alsamixer and got the codecs but even a test soud won't work) I also dowloaded a driver from Realtek itself, that didn't work. 

Then I edited alsabace.conf some more. I tried every one that could possily be it at 
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)
including all that said MSI. 

I then tried Lordraidens comprehensive sound guide from step 1 to step 5, I used the module-assistant and istalled a driver that was called "hda-realtek-codec" or so. It was the only appropriate one on the list. 

and he says the next step is to post a thread on the forum. 
So that I did.
 
I also run into someoe with thesame problem. 
[http://ubuntuforums.org/showthread.php?t=1287173&highlight=msi+s420](http://ubuntuforums.org/showthread.php?t=1287173&highlight=msi+s420)
 

Has anyone any idea? i think ill give up and use the 8.10 that is still on a other partition:confused:

---

### Post by Yellow Pasque on 2010-05-28
I would suggest using module-assistant to remove the "hda-realtek-codec"  driver you installed and then using the ALSA upgrade script: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
If that does not get you sound after a reboot, then run the alsa-info script and post the results: [http://ubuntuforums.org/attachment.php?attachmentid=142560&d=1262704706](http://ubuntuforums.org/attachment.php?attachmentid=142560&d=1262704706)

---

### Post by zazkia on 2010-05-30
Hi &  thanks. I &#7743; halfway down the process, but it won't work 

[INDENT]checking for ALSA... configure: error: Package requirements (alsa >= 1.0.11) were not met:

No package 'alsa' found

[/INDENT]

If it doesn't find an alsa-package is this a consequence of the modprobe action?

---

