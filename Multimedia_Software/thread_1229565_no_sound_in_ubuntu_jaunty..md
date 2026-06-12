---
title: "no sound in ubuntu jaunty."
date: 2009-08-02
forum: Multimedia Software
---

### Post by vakhilesh9892 on 2009-08-02
hey guys. i have got an HP HDX16 1140 US laptop and i installed ubuntu 9.04( jaunty jackalope) recently onto to my laptop and found that the sound is not working. i check out all my sound preferences but nothing seem to work.  could anybody out there please help me out?

---

### Post by martinbaselier on 2009-08-02
Try in a terminal:
alsamixer
to see if nothing is muted. 

If not please paste the output of 
**sudo lshw -c multimedia**

---

### Post by TMAN 1 on 2009-08-02
Try this,it worked for me.  In System/Administration/Users and Groups , make sure that your user and the root user are members of the following groups:  pulse  pulse-access  pulse-rt Then try this procedure: 1. copy-paste the following command into the Terminal: sudo gedit /etc/modprobe.d/alsa-base.conf  2. and add these lines to the end of the file: # Keep snd-pcsp from being loaded as first soundcard options snd-pcsp index=-2 alias snd-card-0 snd-hda-intel alias sound-slot-0 snd-hda-intel options snd-hda-intel model=hp-dv5 options snd-hda-intel enable_msi=1 3. Then navigate to System>Preferences>Sound and change everything to ALSA 4. reboot and retest sound 5. If sound still does not work, then replace hp-dv5 with one of the following 4 model options:  STAC92HD71B*    ref    dell-m4-1    dell-m4-2    dell-m4-3 6. You will have to reboot and retest sound after every model option change to the alsa-base.conf file

---

### Post by sandman55 on 2009-08-02
When I installed I only had a very low sound and I clicked on the speaker icon top right and the volume slider was way low also it can be muted there too.

---

### Post by igorzwx on 2009-08-02
QUOTE:
"Try this,it worked for me. In System/Administration/Users and Groups , make sure that your user and the root user are members of the following groups: pulse pulse-access pulse-rt Then try this procedure: 1. copy-paste the following command into the Terminal: sudo gedit /etc/modprobe.d/alsa-base.conf 2. and add these lines to the end of the file: # Keep snd-pcsp from being loaded as first soundcard options snd-pcsp index=-2 alias snd-card-0 snd-hda-intel alias sound-slot-0 snd-hda-intel options snd-hda-intel model=hp-dv5 options snd-hda-intel enable_msi=1 3. Then navigate to System>Preferences>Sound and change everything to ALSA 4. reboot and retest sound 5. If sound still does not work, then replace hp-dv5 with one of the following 4 model options: STAC92HD71B* ref dell-m4-1 dell-m4-2 dell-m4-3 6. You will have to reboot and retest sound after every model option change to the alsa-base.conf file"

This would certainly make you system vulnerable to remote exploits.

This info might be useful:
[http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8)
[http://ubuntuforums.org/showthread.php?t=1209361](http://ubuntuforums.org/showthread.php?t=1209361)

---

### Post by kg84 on 2009-08-02
Poor old HP lappy's seem to be having a rough trot recently when it come to sound.

I have a DV6 and have lost sound on two occasions now. Each time though the fix detailed halfway down this page has worked for me. 'Having sound issues with...'

[https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation](https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation)

---

### Post by TMAN 1 on 2009-08-02
> **igorzwx said:**
> QUOTE:
&quot;Try this,it worked for me. In System/Administration/Users and Groups , make sure that your user and the root user are members of the following groups: pulse pulse-access pulse-rt Then try this procedure: 1. copy-paste the following command into the Terminal: sudo gedit /etc/modprobe.d/alsa-base.conf 2. and add these lines to the end of the file: # Keep snd-pcsp from being loaded as first soundcard options snd-pcsp index=-2 alias snd-card-0 snd-hda-intel alias sound-slot-0 snd-hda-intel options snd-hda-intel model=hp-dv5 options snd-hda-intel enable_msi=1 3. Then navigate to System>Preferences>Sound and change everything to ALSA 4. reboot and retest sound 5. If sound still does not work, then replace hp-dv5 with one of the following 4 model options: STAC92HD71B* ref dell-m4-1 dell-m4-2 dell-m4-3 6. You will have to reboot and retest sound after every model option change to the alsa-base.conf file&quot;

This would certainly make you system vulnerable to remote exploits.

This info might be useful:
[http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8)
[http://ubuntuforums.org/showthread.php?t=1209361](http://ubuntuforums.org/showthread.php?t=1209361)

 Why?I got that from these forums when I was having problems with my laptop,and it is the same laptop.That procedure is from this person on these forums [https://answers.launchpad.net/%7Emarkrijckenberg](https://answers.launchpad.net/%7Emarkrijckenberg)

---

### Post by igorzwx on 2009-08-02
QUOTE:
Why?I got that from these forums when I was having problems with my laptop,and it is the same laptop.That procedure is from this person on these forums [https://answers.launchpad.net/%7Emarkrijckenberg](https://answers.launchpad.net/%7Emarkrijckenberg)
End of QOUTE

As I told, I had already explained this in detail here:
[http://ubuntuforums.org/showthread.php?t=1209361](http://ubuntuforums.org/showthread.php?t=1209361)

This might be interesting to read too:
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[My computer talked to me in scary voices on startup]("http://ubuntuforums.org/showthread.php?t=1229100") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1229100") [2]("http://ubuntuforums.org/showthread.php?t=1229100&page=2") [3]("http://ubuntuforums.org/showthread.php?t=1229100&page=3"))
[http://ubuntuforums.org/showthread.php?t=1229100](http://ubuntuforums.org/showthread.php?t=1229100)

---

### Post by TMAN 1 on 2009-08-02
> **igorzwx said:**
> QUOTE:
Why?I got that from these forums when I was having problems with my laptop,and it is the same laptop.That procedure is from this person on these forums [https://answers.launchpad.net/%7Emarkrijckenberg](https://answers.launchpad.net/%7Emarkrijckenberg)
End of QOUTE

As I told, I had already explained this in detail here:
[http://ubuntuforums.org/showthread.php?t=1209361](http://ubuntuforums.org/showthread.php?t=1209361)

This might be interesting to read too:
[COLOR=#980101]**[ubuntu]**[/COLOR]                          [My computer talked to me in scary voices on startup]("http://ubuntuforums.org/showthread.php?t=1229100")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1229100") [2]("http://ubuntuforums.org/showthread.php?t=1229100&page=2") [3]("http://ubuntuforums.org/showthread.php?t=1229100&page=3"))
[http://ubuntuforums.org/showthread.php?t=1229100](http://ubuntuforums.org/showthread.php?t=1229100)

 Yes,I read that,but you aren't changing anything in users and groups,you are just checking to see if those are there,then all you are doing is changing what ALSA is able to read from the chip so he has sound.

---

### Post by igorzwx on 2009-08-02
PulseAudio should not be a member of the root group, and Firefox too.

---

### Post by TMAN 1 on 2009-08-02
> **igorzwx said:**
> PulseAudio should not be a member of the root group, and Firefox too.

I am not sure I understand this.I got Ubuntu 9.04 from the Ubuntu site and it is automatically installed this way.I just finished installing it on my other laptop and haven't done anything and I am looking at it being in there as we speak on a fresh install.From what I understand,someone other than me being Admin would have to have access to change anything remotely.

---

### Post by igorzwx on 2009-08-02
ask on Security forum

[[IMG]http://ubuntuforums.org/images/misc/navbits_start.gif[/IMG]]("http://ubuntuforums.org/forumdisplay.php?f=338#") 				  				[Ubuntu Forums]("http://ubuntuforums.org/index.php")  	> [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")   			 			 				[[IMG]http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif[/IMG]]("http://ubuntuforums.org/forumdisplay.php?f=338") ** 	Security Discussions  **

---

### Post by cariboo on 2009-08-02
This thread has veered way off topic, we should be helping th op get his sound working, not discussing security opinions.

Please help the op get his sound working.

---

### Post by igorzwx on 2009-08-02
O.K. What is your personal opinion about security of that "magic solution"?

As concern the problem of sound, I would propose to follow the advice 
proposed by Martin:

QUOTE:
Try in a terminal:
alsamixer
to see if nothing is muted. 

If not please paste the output of 
**sudo lshw -c multimedia**

---

### Post by TMAN 1 on 2009-08-02
> **cariboo907 said:**
> This thread has veered way off topic, we should be helping th op get his sound working, not discussing security opinions.

Please help the op get his sound working.

 Appolagies,no intention ment to go off topic,it just happened to be apart of the problem.Apparently. He should also check preferences.

---

