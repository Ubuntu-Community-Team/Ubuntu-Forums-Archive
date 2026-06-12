---
title: "Missing xorg.conf file"
date: 2010-08-29
forum: Multimedia Software
---

### Post by Steelkilt on 2010-08-29
I am running Ubuntu 10.04.  I have a dual-head Matrox G450 and I wanted to edit the xorg.conf file that was located (in prior versions) in etc/X11.  I don't have an xorg.conf file in that location (or any where else).  My question is should I have that file, or has it been re-shuffled in this latest release?

If it has been moved, can anyone tell me where it now resides and what it is called?

If I should have that file, can anyone tell me how to get it back?  

I installed OSS for audio.  Would that have affected the xorg.conf file?

Thank you.

---

### Post by squaregoldfish on 2010-08-29
It's not unusual to not have an xorg.conf file any more - Xorg is pretty good at figuring out the required settings for itself these days, so it's often not needed.

If you do want to create one, it will live in /etc/X11 as before.
Steve.

---

### Post by Steelkilt on 2010-08-29
And if I create an xorg.conf file, the system will read it?

Cab I put just the pieces I need for the dual head card in the xorg.conf file?

Thank you.

---

### Post by squaregoldfish on 2010-08-30
Yes, the xorg.conf will be read automatically if you create it. Not sure about just putting in the bits you need - give it a try and see what happens!

Incidentally, I seem to recall that there's a command somewhere that can dump an xorg.conf file from a current X session. Unfortunately I can't remember the command, but it may help you out if you can find it....

Steve.

---

### Post by Steelkilt on 2010-08-30
Cool.  I am checking my Linux Phrasebook.

---

### Post by dino99 on 2010-08-30
you might find help there: 

[http://ubuntuforums.org/tags.php?tag=dual+head](http://ubuntuforums.org/tags.php?tag=dual+head)

---

### Post by Steelkilt on 2010-09-01
I believe the command is "getconfig" but I have not been able to get this command to work.  The system does not recognize it.  I searched for it and tried an "apropos" command, but got nothing.  Perhaps it has been replaced or I am just not using the command properly.  Among other things, I have tried running it from the etc/X11 file.  

From the description on the Xorg site, "getconfig" should provide a dump of the current Xsession.

I continue to noodle.

---

### Post by squaregoldfish on 2010-09-01
Try this:

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

Steve

---

### Post by Steelkilt on 2010-09-02
Steve,

That link was key.  Awesomely helpful.  I have an edited Xorg.conf file in my X11 directory now.  I still have not been able to get the monitors out of mirror mode, but that is probably a defect in my edits to the Xorg.conf file.  My edits are based on guessing, based on other posts and old information from the Matrox site. I am hoping that the system is actually reading that Xorg.conf file.  This is a process, but getting the xsession dumb was a major step.  Thank you.

JG

---

### Post by squaregoldfish on 2010-09-02
No worries.

If you want to be sure that your xorg.conf file is being read, make it invalid in some way - Xorg will complain/refuse to start!

Probably can't help you any more from here. Good luck!

Steve.

---

