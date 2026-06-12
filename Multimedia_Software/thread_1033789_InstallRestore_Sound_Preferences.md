---
title: "Install/Restore Sound Preferences"
date: 2009-01-07
forum: Multimedia Software
---

### Post by Lifyre on 2009-01-07
I'm trying to change some settings on a new install of Ubuntu and cannot find System -> Preferences -> Sound any longer.

Does anyone know what I need to poke, prod, or install to get it or get it back?

Thanks,
Lify

---

### Post by gettinoriginal on 2009-01-07
First thing I would do is right click the main menu, edit menu, and check under preferences to make sure it sound is checked.  :)

---

### Post by Lifyre on 2009-01-07
Just checked there, thanks for the tip but there is no sound option in there.

[edit] This may sound strange but I do like terminal commands since it seems to be easier to see when things go wrong and where.  So if there is a terminal call for that particular control panel it might lead me to where I can install it.

---

### Post by Lifyre on 2009-01-07
Here are some screen shots of the issue.  The first is of the System -> Preferences menu and the second is of the edit menus location that gettinoriginal pointed me to.

-Lify

---

### Post by gettinoriginal on 2009-01-07
Try typing "gnome-sound-properties" in terminal and see what happens, that brings mine up.  It is supposedly an application, but is not found in Synaptic, so I do not know if it is part of another installation or a stand alone.  Properties says it is an application.

Edit:  Checking further in Synaptic, it is part of "gnome-control-center"  so if you do a reinstall of that in Synaptic, then it should restore it.

---

### Post by Lifyre on 2009-01-07
Told me it wasn't installed and told me to install it using "sudo apt-get install gnome-control-center"

When I try to install it I got the already installed error.  I have tried to remove and reinstall gnome-control-center.

Unfortunately this doesn't resolve the issue.  You've given me a good lead I'm going to continue working it on my end.  If you have any other ideas I would love to hear them.

-Lify

[edit]Trying to reinstall using synaptic

[edit2] Still no joy using synaptic to reinstall.  I'm going to file a bug report.  Thank you for your help, I appreciate it very much.

---

### Post by gettinoriginal on 2009-01-07
Ok, lets try this, Main Menu, edit menus, preferences, add new item, then fill it out to look like my image.  See if that puts it back. :P

[ATTACH]99132[/ATTACH]   [ATTACH]99133[/ATTACH]

---

### Post by Lifyre on 2009-01-08
It adds the icon but it fails to load it.  "Failed to execute child process" says it doesn't exist.

Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/314957](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/314957)

I've included more information in there than here.  What version of gnome-control-center do you have?

---

### Post by gettinoriginal on 2009-01-08
Mine is 1:2.24.0.1-0ubuntu7.1, and sorry, but I am stumped from here :confused: but I will keep researching :P  I also didn't realize you were trying to run Jaunty LOL, I am still in intrepid, so it sounds like a bug report was a good idea

---

### Post by Lifyre on 2009-01-08
Probably should have mentioned that :-p  Didn't think that this was one of those things they would break between distros.  I wanted to play with ext4.  It seems that Gnome no longer uses gnome-sound-properties.  According to the response I received it uses the new gnome-media gnome-volume-control.  I'm working on figuring out where the sound console is and what commands to use.

---

### Post by gettinoriginal on 2009-01-08
Good luck to you :P  I have never been brave enough to install an Alpha, minimum for me is Beta :P

---

### Post by atentik on 2011-03-12
Has this been resolved? I am having the same problem.

---

