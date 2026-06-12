---
title: "Sound output low after different OS install alongside"
date: 2011-08-22
forum: Multimedia Software
---

### Post by victor.cighir on 2011-08-22
Hello Community!

I've had a problem that freaks me out. It's the 5th time this happens to me.

A couple of days ago I created a squashfs image of my up to date Pinguy OS 11.04 root. I booted it from Ram successfully. SOUND had no problems on either of them.

I then proceeded and installed Fedora 15. This affected both systems above mentioned, i.e. SOUND has very low output volume. For instance if I play a movie on youtube, an avi, or an online radio station I have to max both speakers and mixer. This way I have close to normal output levels.

My system looks like this now:
[LIST=1]
[*]hd0,1 - Pinguy OS 11.04  + squashfs image in root fs; HOME folder for these OS's is on hd0,5
[*]hd0,2 Fedora 5 with home folder on the same partition
[/LIST]

I must say I had this problem before this winter when I had Ubuntu 10.10. I wanted to check out development versions of Ubuntu 11.04. I installed it alongside, same setup as now (home folder on separate partition for Ubuntu 10.10) and sound was low... Tried back then different setups, reconfiguring etc without success. Only reinstalling could help.


I just tried creating a new user account on my Pinguy OS. Sound is the same.

When I boot off a LiveCD or Ubuntu 11.04 installed on a USB stick I do not have this issue. Also on Fedora sound is okay.

Thank you before hand for helping.

---

### Post by victor.cighir on 2011-08-24
Today I had some time to work on this problem.

[LIST=1]
[*]Reinstalled PinguyOS and kept my home folder. Result was that sound was still low... Created a new user it also had low sound.
[*]Installed PinguyOS to another partition with separate home folder and different user name. This time sound worked great.

[*]Tried after all this to copy some folders like .pulse, .config, .gconf, .cache etc. whatever seemed related to configuration. All this without result.

[*] In the end I had to reinstall pinguy again with separate home partition and different username. Everything worked good so I copied back my important folders: .mozilla, Documents, Desktop etc.
[/LIST]

Once again the only to recover seems to be reinstalling the system :(
Will try on my second PinguyOS install to copy the broken home folder which I carefully backed up :))
Any other ideas of how to break or repair my system?

---

### Post by victor.cighir on 2011-09-01
One more thing I forgot to mention in previous posts. The following thing happened to me before and remembered just now.

While messing around with skype volume levels decided to install pavucontrol. After doing so, I successfully switched standard input in form of monitor which was quite annoying (I could hear myself in the speakers) to Analogue input. Everything was fine now with input, except output levels are low again.

I understand that some people here find that not using vanilla Ubuntu might be reason enough no to answer, I have to remind you that Pinguy OS is essentially UBUNTU Linux. Still! 

Anyway I have the idea that this is all about configuration. And since pulseaudio is configured per-user basis I think something could be solved by removing config files in the home folder. Just don't know which one yet.

If this is the case, then why creating a new user does not fix this issue? If it is a global problem, then why reconfiguring pulseaudio does not fix the problem?

Hope to get an answer to this one soon cuz' I got tired reinstalling. Or maybe I'll just do a reinstall for fun on Ubuntu 11.10 beta 1 and see if it breaks...

---

### Post by victor.cighir on 2011-09-27
If anybody ever finds this... This is unbelievable!!

So> finished my exams and installed Linux Mint Katya kernel 2.6.38-8 up 2 date. I was editing some subtitles with *gnome-subtitles* , suddenly heard a loud squeaky sound and my sound setup went dead! I can only play sound with volume set to almost 0 and speakers set to max, though output seems normal.

Tried to start ```

$alsamixer
cannot open mixer: No such file or directory
```

Stopped pulseaudio (also disabled autospan), tried to start alsa. But alsamixer still doesn't load.

Every time something different happens with my sound I remember it happened to me before... That time also had to reinstall. 


There is one thing though I cannot understand: how can it go so wrong that I cannot undo? Or how come nobody has a clue about this? Maybe the post is in the wrong place?

---

### Post by lidex on 2011-09-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

You mentioned skype. Make sure to disable the option to allow skype to control levels. 

To reset pulse config:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by victor.cighir on 2011-09-28
Thank you for your reply! I have hope again :)

I ran the utility and the results are attached. At first sight, it looks like my pci card is recognised as usb.

Anyway back to my last problem: pulseaudio related config was deleted; I had no alsa files. Reboot and the problem is the same: if I start bashee, vlc or smplayer, even youtube I get this insane noise (white noise?), like with the old TV's when scanning for signal. Putting the volume to almost minimal somewhat solves the problem and I get almost normal levels.

I remember reading something about this, I think it was alsa related, but I'm not sure: all mixer levels were too high.

Actually amazing is that it happened while working on something ( not while editing config files, messing with packages etc. )

Thanks again!

---

### Post by victor.cighir on 2011-10-06
This looks like a lost cause... Anyway I switched to 11.10. Until now everything works fine or better. Messing with settings doesn't screw things up.
Also for the very first time after a couple of releases (10.04? was maybe the last one to work?) tvtime works with a patch cable: from tvcard output to soundcard mic plug. It get's detected automatically and sound is redirected to the speakers. Altough only the >>mic<< plug works and there is a small 0.1s delay between sound and video. It's better than nothing. In 11.04 I had to manually switch my speakers when I wanted to watch TV.

---

### Post by lidex on 2011-10-11
Sorry to not get back in time. Looks like your alsa install was borked and loading usb module instead of the correct one. A re-install should have fixed it.

---

### Post by victor.cighir on 2011-10-11
Reinstalled Pinguy again. Sound is working good so far. Haven't tried messing with it again, but if you want me to do it and collect some info I will be glad to.

This is the alsa-info script output in working state.

I was thinking of making some kind of full back-up, mess with the system and do a diff and see what went actually wrong, what files changed? Could you point me in that direction?

---

