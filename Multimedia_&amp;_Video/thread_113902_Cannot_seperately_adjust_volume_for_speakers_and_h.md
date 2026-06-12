---
title: "Cannot seperately adjust volume for speakers and headphones"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by eriksundelof on 2006-01-07
I have a freshly installed version of Breezy Badger on a Dell XPS M140. I am having problem with getting the volume control working so that I can Mute the speakers but not the headphones. Now the only control I get for adjusting output is Master.

I have updated ALSA controls to the latest ones via apt-get. I have not downloaded them directly from the ALSA-site.

Does anyone have an idea how to solve this?

---

### Post by eriksundelof on 2006-01-07
anybody who has any idea? :)

---

### Post by racin on 2006-01-08
Hello,
I think I have your fix! Hopefully ...I'm still really new to this! Ok go to applications then sound and video then go to prefs check the boxes for devices that you want to see volume controls for. OK get out of prefs now you see all the volume controls? Ok see the ones with the small chains on them? They are locked together. Unclick the chains and now you can control volumes seperately. I hope this works Good Luck and  Take Care

---

### Post by eriksundelof on 2006-01-08
Well the problem is not that easy I am afraid. I use the alsamixer to see what the available controls really are, and i can assure you that the headphones are not there. 

I spent quite a lot of time by recompiling ALSA and reading the web about the problem. It seems like there is no support for separate volume control in the driver provided by them for the soundcard hda-intel in the ALSA package.

Hopefully somebody here knows the workaround for this.

So how to deal with a hda-intel card to separate the controls for speakers and headphones?

---

### Post by Jeff250 on 2006-01-08
I have an m140 too.  You know what's interesting?  I installed the latest ALSA from cvs, and now I get sound out of *only* the headphone jack!  :confused: It's an unimpressive compromise, but I'll probably keep it like this for a week or so unless I can come up with a better idea sooner.

---

### Post by eriksundelof on 2006-01-08
It is quite strange indeed. I have worked on this for like a day and a half without any luck. Tried it all basically. :)

Soon I will just give it a rest for the time being. However it would be nice to be able to listen to music from it without having to bring another handheld or something. It seems like the problem is the ALSA driver.

---

### Post by earobinson on 2006-03-14
I have this bug on a dell inspiron 1300 :(

---

### Post by Jeff250 on 2006-03-17
Edit:  I've attached an even newer patch.  Eventually, this is going to be merged with CVS.

I've got auto-muting working properly after all of this time.  This should work for Dell XPS m140's or any system that uses hda-intel with a Sigmatel 9200 chip.

To get this working, you first have to download the lastest alsa drivers from CVS.

```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/alsa login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/alsa co alsa-driver alsa-kernel
```

I've got a patch attached to the bottom of this post that I originally downloaded here from tiwai:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1843](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1843)

Download and save it to the parent directory of alsa-driver and alsa-kernel.

Then type in:
```
patch -p0 < hda-autoconfig-fix3.diff.txt
cd alsa-driver
./cvscompile
sudo make install
```

Reboot, and auto-muting should be working.  That should be the gist of the instructions.  I may have forgotten something, but the bulk of it is there. ;)

P.S.  Just a hunch, but I think this process will have to be repeated for every kernel update.  This should get easier once Dapper goes final.

---

