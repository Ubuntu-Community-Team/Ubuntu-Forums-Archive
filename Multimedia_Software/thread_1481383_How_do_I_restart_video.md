---
title: "How do I restart video"
date: 2010-05-12
forum: Multimedia Software
---

### Post by AVH on 2010-05-12
My computer resumes from hibernate with a blank screen. How do I restart the video from the command line, with out being able to see it?

---

### Post by themusicalduck on 2010-05-12
To restart the desktop manager, you can press ctrl+alt+f1, login and use this command ```
sudo service gdm restart
``` (this will close any open applications though)

With the hibernation problem, I'm not sure if this is obvious but have you tried moving the mouse around once it has booted? On my netbook, I have to move the mouse around for a few seconds to disable the screensaver and bring up the login prompt, otherwise it just shows a blank screen.

---

### Post by AVH on 2010-05-13
This machine has never come back properly from hibernation in Ubuntu from back beore feisty.

The box fires up ok and the led on the monitor goes from amber to green but nothing comes up on the screen, not even a command line.

 I think I also need to be sure I'm in a terminal first without being able to see it

---

### Post by themusicalduck on 2010-05-13
So if you press ctrl+alt+f1, you don't get a prompt to login to a terminal on the screen?

Why do you use hibernate anyway if it boots up like this?

Here's another good tip for if your only resort is to hard reset - press the combination ctrl+alt+REISUB with a second between each letter. That will stop any processes and reboot the machine safely.

---

### Post by llawwehttam on 2010-05-13
> **themusicalduck said:**
> So if you press ctrl+alt+f1, you don't get a prompt to login to a terminal on the screen?

Why do you use hibernate anyway if it boots up like this?

Here's another good tip for if your only resort is to hard reset - press the combination ctrl+alt+REISUB with a second between each letter. That will stop any processes and reboot the machine safely.

On most machines its still Alt + Sysrq + REISUB

---

### Post by themusicalduck on 2010-05-13
> **llawwehttam said:**
> On most machines its still Alt + Sysrq + REISUB

That's the correct one.. my bad.

---

### Post by AVH on 2010-05-19
Alt + Sysrq + REISUB worked. Ctrl+alt+f1 didn't, screen stayed blank.  I usually do do a hard boot because of this very problem. Every once in a while I'll try to get hibernate to work to avoid the delays of a hard boot. So far no luck

---

### Post by AVH on 2010-05-19
Alt + Sysrq + REISUB worked. Igat a statement the the system was entering sleep mode and the it rebooted.  Ctrl+alt+f1 didn't work, screen stayed blank.  I usually do do a hard boot because of this very problem. Every once in a while I'll try to get hibernate to work to avoid the delays of a hard boot. So far no luck

---

