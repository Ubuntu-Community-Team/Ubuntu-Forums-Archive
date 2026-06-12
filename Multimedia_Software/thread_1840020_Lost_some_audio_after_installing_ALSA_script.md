---
title: "Lost some audio after installing ALSA script"
date: 2011-09-06
forum: Multimedia Software
---

### Post by His Royal Freshness on 2011-09-06
[http://ubuntuforums.org/showthread.php?t=1835172&page=2](http://ubuntuforums.org/showthread.php?t=1835172&page=2)

I followed the advice in the quoted text, and like I said, I ended up losing audio~

After some time though, I've found out that I have audio on FireFox and SNES, but not in Banshee or Movie Player, nor do I get the startup sound.


EDIT: I tried [this]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/136772") after a friend showed it to me, who knows Linux.   Unfortunately for me, he left not long afterward, and left me, a complete nub, to decipher it.  So I tried doing this:

> 
Step 2: Run the following command (copy/paste command into the Terminal and then hit <enter>)
 gksudo gedit /etc/modprobe.d/alsa-base.conf
 In the gedit editor, scroll down to the last lines of the  alsa-base.conf file and ADD these 2 lines to the end of the  /etc/modprobe.d/alsa-base.conf file (with the file open inside the gedit editor!):
 alias snd-card-0 snd-hda-intel
options snd-hda-intel model=targa-8ch-digidk if I even did it right.  What I did was I opened the gedit and pasted those last two lines at the bottom of it.  It didn't seem right, but it's all I could figure to do.  It didn't work.


EDIT 2: Looking around some more, I found [this thread]("http://ubuntuforums.org/showthread.php?t=1543267&page=1"), so I tried its first suggestion.  This popped up:

```
freshyfresh@DEATHHOUSE:~$ rm -r ~/.pulse ~/.asound* 
rm: cannot remove `/home/freshyfresh/.asound*': No such file or directory
freshyfresh@DEATHHOUSE:~$ sudo rm /etc/asound.conf
[sudo] password for freshyfresh: 
rm: cannot remove `/etc/asound.conf': No such file or directory
```

---

### Post by His Royal Freshness on 2011-09-07
Done more troubleshooting today.  Went the #ubuntu and someone did !alsa when I popped my question.  Looked at th sites and began going through the steps, found out that I can't even open Sound Preferences.

Pic related:
[img]http://img21.imageshack.us/img21/3715/screenshotbbu.png[/img]

---

### Post by .... on 2011-09-08
Your main mistake was using a really old version of the ALSA update script. Use the latest found here: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

Also, do this to make sure you don't have any corrupt pulseaudio files:
```
rm -rf ~.pulse*
```Log out and back in.

> idk if I even did it right.
That was the correct procedure for editing alsa-base.conf, assuming the targa-8ch-dig keyword was correct (which it probably wasn't unless you have the exact same mobo/laptop as the post you got it from). I recommend putting the file back to how it was.

If, after installing latest ALSA, you still have issues run the alsa-info.sh script in that link and post the link/output.

---

