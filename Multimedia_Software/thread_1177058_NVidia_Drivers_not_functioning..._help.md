---
title: "NVidia Drivers not functioning... help?"
date: 2009-06-03
forum: Multimedia Software
---

### Post by DnDer on 2009-06-03
I'm stuck at some ungodly low resolution after installing 9.04 on my box.

I found the following commands to run from another thread here on the forum:
```
sudo apt-get install nvidia-settings
sudo nvidia-settings
```

All this does is generate an error message for me when I attempt to run it.
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

My slack-loving friend told me to try nvidia-settings as a user and not as root, to try to find the absolute path. This was the following result.
```
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-glx-173
 * nvidia-glx-180
 * nvidia-glx-96
Try: sudo apt-get install <selected package>
bash: nvidia-xconfig: command not found
```

As far as installed things, all I have is "nvidia x server settings" listed in my add/remove list. This is not the same as having an actual driver? It says it's meant to configure those drivers... 

What am I neglecting to understand, here? Something's not quite connecting in my brain...

---

### Post by DnDer on 2009-06-03
Bump for the day shift.

---

### Post by Bearly Able on 2009-06-03
Don't know if this will help; I've been having Nvidia problems with Jaunty, and I'm not sure if I've got them fixed or not.

However, if you go to Hardware Drivers, it should give you an option for installing the correct Nvidia driver.  I tried Nvidia X Server Settings first, but that just gave me the same error message you got; using Hardware Drivers seems to be the way to go.

---

### Post by DnDer on 2009-06-03
Okay... Made it back to add/remove applications, and I pulled down "NVidia binary X.Org driver ('version 173' driver)" from the  System Tools > Canonical-maintained applications portion. I chose that one since it was the highest version mentioned in the terminal dialogue I posted earlier.

I then went to the display option under System > Preferences, and it asks if I want to use the vendor's graphic's driver tool. I click "yes" and the same message pops up as before, about "You do not appear to be using the NVIDIA X driver..."

Do I just keep downloading binaries till it works?

---

### Post by David Crockett on 2009-06-03
Did you ever solve the problem?  I have the same problem on an Old Dell that I just installed Ubuntu.  I am stuck in the low resolution mode also.   I have an even older Dell with Ubuntu where the default system tools works well for adjusting the resolution.   I have yet to find a simple answer or discussion.   I am not very well schooled in Unix or Linux.


Regards,
David

---

### Post by DnDer on 2009-06-03
No, not yet.

---

### Post by Steelmourne on 2009-06-04
I've posted a step-by-step guide to installing nvidia drivers in the absolute beginners forums.

---

