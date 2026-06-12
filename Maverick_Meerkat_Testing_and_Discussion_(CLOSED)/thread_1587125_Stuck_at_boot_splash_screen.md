---
title: "Stuck at boot splash screen"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by DevilInPgh on 2010-10-03
Hi, can somebody help?  I just upgraded from Lucid to the RC and now it hangs at the boot splash screen.  Nobody wants to help in the chats.  PLEASE HELP!!!!

---

### Post by kahping on 2010-10-03
Press Esc at the boot splash and post any error messages on the screen here. Also give your hardware specs. 

The more info you give the more likely someone will be able to help

---

### Post by DevilInPgh on 2010-10-03
Let me reiterate: I am COMPLETELY stuck at the splash screen.  That means no response to keystrokes.  Computer is a P4 2.8 GHz with 1.5 GB RAM and video card NVIDIA GeForce FX 5500.

---

### Post by vishalrao on 2010-10-03
i think just as boot starts if you hold down SHIFT you get the GRUB boot menu where you can press E to edit the boot entry and remove the "quiet splash" part to get kernel boot messages on screen - perhaps that will throw up a clue.

---

### Post by DevilInPgh on 2010-10-03
Shift key doesn't work, can't bring up grub-boot menu.

---

### Post by drs305 on 2010-10-03
If you can't even see the Grub boot screen and suspect it's not hanging up later in the boot, you can completely purge and reinstall Grub2 via a Live CD. Are you sure it's hanging at the Grub menu? 

You can try either reinstalling G2 from the Desktop or purging and completely reinstalling Grub2 via chroot. The chroot instructions are in a guide I wrote a few weeks ago:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by kumaryu on 2010-10-05
I note that you are using NVIDIA GeForce FX 5500.

There was an issue with Nvidia-173 (173.14.27 ) drivers for GeForce FX5x00 cards and the new Xorg Xserver 1.9 causing a screen freeze at boot.

The driver in Maverick was updated 2 days ago just AFTER the release of Maverick 10.10 RC to 173.14.28.


Have you tried booting without xorg.conf file?
In many cases, Xserver can start without xorg.conf file.

 1. Just after the bootloader, Cntrl_alt+F1 to enter the terminal.
 2. Log in and goto /etc/X11/: cd /etc/X11/
 3. Rename xorg.conf: sudo mv xorg.conf oldexorg.conf
 4. Restart: sudo shutdown -r now

This should give you a working GUI. 
Ensure that you have your network up and running.

 5. Goto System>>Administration>>Update Manager
 6. Check (for updates)
 7. Confirm the updated packages include Nvidia-173 (173.14.28 )
 8. Install updates.

---

