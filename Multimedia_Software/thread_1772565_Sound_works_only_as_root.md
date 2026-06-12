---
title: "Sound works only as root"
date: 2011-05-31
forum: Multimedia Software
---

### Post by wyhog on 2011-05-31
I have sound if I use aplay or start totem using sudo but neither have sound if I try aplay or totem as ordinary user. The groups command shows my user name is a member of the audio and video groups. If I look at the /etc/group file it also shows pulse as a member of audio group.

This is a command line install from the 10.04 Alternate CD to which I installed xorg, icewm, gdm, nautilus, synaptic, totem, firefox, gstreamer, alsa, pulse, and others. Every thing works except the user audio. Totem will show videos but no sound. Totem will play MP3 music files (show the cover art and the progress) but no sound. But it all works ok, good sound,  if I start Totem as root.

What am I missing? 
I don't expect in depth help with this installation but thought maybe something would just pop out at someone??

Wyhog

---

### Post by NoBugs! on 2011-05-31
Did you make sure you are part of "audio" group in Users and Groups settings?

---

### Post by wyhog on 2011-05-31
> **NoBugs! said:**
> Did you make sure you are part of "audio" group in Users and Groups settings? This is not a full Ubuntu install therefore AFAIK there is no "Users and Groups settings"? But as I stated above, I am a member of the audio group as determined by typing "groups" on a terminal and also by looking at the file /etc/group with a text editor.
Since the sound system works perfectly if I launch the various sound using programs via sudo it seems my problem HAS to be a permissions type problem somewhere. But where? Where else does a user name or ID need to be listed for an ordinary user to use the sound system?

Wyhog

---

### Post by wyhog on 2011-06-01
Well this is just great. I used synaptic to "completely remove" all alsa, pulse, and totem stuff then used it to install all that back. Now my user sound system works.... sorta. If as a normal user I use aplay to play one of the test sounds or if I use Totem to play an mp3 the sound plays at about 4 times normal speed. But if I do those two things using sudo aplay or sudo totem then the test sound and the mp3 play just fine at the correct speed.
I'm at a total dead end here.

Wyhog

---

### Post by sea7kenp on 2012-11-02
Note:  I'm having trouble with this also.   But this (works on root only) is a major improvement over my prior complaint, where sound worked find under Ubuntu 6, but not 12.  (I had to temporarily explore Arch Linux to figure out what was wrong.  It's great for troubleshooting hardware issues, by the way).

Note:  I got partway, by adding group "audio" to my username (yes, sea7kenp!)  I got alsamixer work, but speaker-test (as well as mpg123, a text mpg player) still only works on Root.  

Note:  I have not tried the "remove, and re-install" methods, mentioned above.

What am I missing, here?

Thank you and best regards,

Kenneth Parker, Seattle, WA

---

