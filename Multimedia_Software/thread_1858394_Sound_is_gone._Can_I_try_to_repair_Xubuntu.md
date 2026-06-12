---
title: "Sound is gone. Can I try to repair Xubuntu?"
date: 2011-10-12
forum: Multimedia Software
---

### Post by woodyg on 2011-10-12
One day my Xubuntu suddenly had no sound. Nothing seems muted, so the sound should be there (Kubuntu on the same machine has sound, so no problem with the computer). I am aware that these kind of things can be tricky to sort out if I'm unlucky (e.g. took ages to sort out the microphone on another computer running Ubuntu), and I don't have time to spend on this now + I'm re-installing it all soon when 11.10 is out... so I'm thinking of simply repairing Xubuntu... if it is possible of course and if the problem simply is that something is broken, and that it isn't some kind of setting that suddenly changed itself.

So is it possible to try to repair Xubuntu? I.e. to run a process that looks into the entire OS for non-working bits and pieces?

---

### Post by WorBlux on 2011-10-12
> **woodyg said:**
> One day my Xubuntu suddenly had no sound. Nothing seems muted, so the sound should be there (Kubuntu on the same machine has sound, so no problem with the computer). I am aware that these kind of things can be tricky to sort out if I'm unlucky (e.g. took ages to sort out the microphone on another computer running Ubuntu), and I don't have time to spend on this now + I'm re-installing it all soon when 11.10 is out... so I'm thinking of simply repairing Xubuntu... if it is possible of course and if the problem simply is that something is broken, and that it isn't some kind of setting that suddenly changed itself.

So is it possible to try to repair Xubuntu? I.e. to run a process that looks into the entire OS for non-working bits and pieces?

The are ways to look for broken packages, but not for settings systemwide.

You can reinstall without formatting an it should keep your /home intact, however if it's a setting issue, the problem may just persist through the reinstall. 

Besides not being muted make sure that the default output didn't get switched on you (like the HDMI out rather than the speaker out) and that the sound modules where properly loaded. (compare the output of lsmod between your working and non-working installation)

Also you shouldn't need a different need to have to dual boot for kubuntu and xubunutu. You can just install kubuntu and then "sudo apt-get install xfce4 && apt-get install xfce4-goodies" and choose the DE at the login screen.

---

### Post by woodyg on 2011-10-12
> **WorBlux said:**
> The are ways to look for broken packages, but not for settings systemwide.

How do I look for broken packages?

> **WorBlux said:**
> Also you shouldn't need a different need to have to dual boot for  kubuntu and xubunutu. You can just install kubuntu and then "sudo  apt-get install xfce4 && apt-get install xfce4-goodies" and  choose the DE at the login screen.
If I would do this, would Kubuntu have no impact on my Xubuntu? What I mean is, I'm trying to avoid installing too much stuff, as I can't escape the feeling that it somehow slows down the system overall. Am I just imagining things or does installing more and more stuff have an impact on the responsiveness of the system? Regardless if I'm Linux or Windows I feel the need for a complete re-installation every 12 months or so, as the computer starts to feel sluggish... something I associate with my fondness for installing and trying out all sorts of applications...

---

### Post by almursi on 2011-10-12
Hi woodyg,  
Now I'm in gnome, but xubuntu uses alsa. You can try alsamixergui (and amixer) and see which card is used by default. For example, graphics cards creates many conflicts with hdmi output, which tends to take alsa first for master. With the command **amixer -c number** you can choose between cards, but now I can not tell if it will be able to fix. 
Other options may exceed a simple attempt to fix.
  Best regards.

---

