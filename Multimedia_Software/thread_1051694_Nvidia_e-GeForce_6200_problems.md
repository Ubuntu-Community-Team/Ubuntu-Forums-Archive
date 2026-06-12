---
title: "Nvidia e-GeForce 6200 problems"
date: 2009-01-27
forum: Multimedia Software
---

### Post by AmunRa on 2009-01-27
I recently bought a e-GeForce 6200 pci video card.  I've installed the Nvidia 177 drivers, kernel, etc. via the synaptic package manager.  However when I go to System > Administration > Hardware Drivers, I find no drivers to activate.  Even after restart.  However both the package manager and software add/remove say that the drivers are installed.

I've tried installing the card and starting it up connected to the monitor.  It goes through the dell/intel splash screen, and then to the ubuntu splash screen. . . and then after a few seconds of blank screen I'm left with a blinking cursor prompt. The only thing I can do is press the power button, up pops "*Stopping Gnome Display Manager*" the closing ubuntu splash screen, then off.  The vga port on the mobo puts out nothing.  Take out the video card, and it's back to normal.

I did notice the appearance of System > Administration > Nvidia X Server Settings.  When I open it it says 'You do not appear to be using Nvidia X Driver.  Please edit your X configuration file (just run nvidia xconfig as root), and restart the X server."  Hmmm. . . not sure.  lol.

I'm using Intrepid 8.10

Suggestions?

---

### Post by AmunRa on 2009-01-27
. . . any suggestions? :\

---

### Post by themrfreeze on 2009-01-27
I'm having a very similar problem.  

I'm in the process of building a media center PC using Mythbuntu 8.10, a Tyan S2875 motherboard (two single-core 2.0GHz Opteron processors), 2GB RAM, pcHDTV 5500 tuner card, and a brand new XFX GeForce 6200 video card.  I'm a sysadmin by trade, but my knowledge of Linux's inner workings is fairly minimal.

Installing Mythbuntu from CD goes fine.  However, I found the video while watching high-def TV choppy, and thought that maybe the video drivers were the issue.  I then tried to install the proprietary NVidia drivers (177 I think...whatever was recommended).  Upon reboot, the screen goes black after the Mythbuntu splash screen, and the computer is basically frozen.  I have to power cycle the machine to get it working again, and replacing the xorg.conf file gets me back to the desktop (albeit with minimal video settings).  Weird thing is that after this happens, I can't use my wireless keyboard to get into the BIOS or the GRUB menu...I have to power the computer down completely and remove the USB dongle to get it back again.

I've tried using Envy to install the drivers, as well as the installer from NVidia's website, and the installer that comes with Mythbuntu, and all three result in the same black screen weirdness.

At this point, I'm going to try installing 8.04 instead and see it has the same problem.  If anybody has any suggestions for getting 8.10 working, I'm all ears.

---

### Post by themrfreeze on 2009-01-27
Update:  Mythbuntu 8.04 does exactly the same thing has 8.10...as soon as you load the NVidia drivers and reboot, it boots to a black screen.  Sometimes if you let it sit, you'll get a green screen with black lines running vertically.  Computer has to be powered off after this.  I really wish I knew what was causing it...I wonder if it's something specific with this XFX video card I bought.

---

### Post by themrfreeze on 2009-01-28
Just a follow-up:

I replaced the GeForce 6200 card with an older Quadro FX500 card, installed the NVidia drivers, and it works perfectly.  Not sure if the issue is with this particular 6200 card, or some bug in Ubuntu, or whatnot, but if you have the black screen problem, trying another card may do the trick.

---

