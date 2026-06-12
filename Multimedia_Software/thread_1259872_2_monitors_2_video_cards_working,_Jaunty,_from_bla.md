---
title: "2 monitors/ 2 video cards working, Jaunty, from blank screen"
date: 2009-09-06
forum: Multimedia Software
---

### Post by jmiter on 2009-09-06
Just wanted to share how I was able to get both of my monitors working, each on its own graphics card.  I had days of trouble getting both to work, read (what felt like) every post on how to get these working, and had no luck until now.  Hope this can help someone.

Original symptom: only one monitor working (nv driver).  Second monitor (nvidia driver) was not powering up, then was powering, but was blank with only the mouse cursor

The setup
Jaunty 64bit
Video card 1= Nvidia TNT/TNT2. PCI slot. VGA out to Samsung LCD TV.  Using driver "nv" in xorg.conf

Video card 2= GeForce fx 5200, AGP 8x slot .  VGA out to Sharp HD LCD TV.  Also has S video Out, Got it to work too.  Using driver "nvidia" in xorg.conf

Ultimately, I enabled Xinerama.  Xinerama was the only fix that worked. 
The actual steps that worked for me:
- correct xorg.conf so that there are no errors in Xorg.0.log
- uninstall / purge all nvidia drivers.  reboot
- install the nvidia driver i needed using the ubuntu installer.
- enabled Xinerama using nvidia-settings.

Here are some details below.
I upgraded from Hardy to Jaunty in Adept.  After the upgrade, the xorg.conf file didn't seem to be correct any longer since only one monitor worked - the PCI connected one - TNT/TNT2, Samsung).

After addressing all the errors in Xorg.0.log, and getting my xorg.conf corrected to not have errors, the second monitor (nvidia fx 5200 on the AGP) still did not power up.  It was, however, recognized and noted in the xorg log.

Uninstalling all the nvidia drivers and then reinstalling the Nvidia driver 173.14.16 using the installer in ubuntu allowed the second monitor to power up.  No picture, just a mouse cursor if I moved the mouse to that screen.

Using nvidia-setting - I enabled Xinerama and restarted X.  Twinview did not work for me.

There are still a few problems, but so minor I probably will not fix them....
- System Settings -> Display crashes when I try to run it.  I noticed this has been reported by others when Xinerama is enabled.

- nvidia-settings now claims that I do not have an nvidia driver on the system.  However. Xorg.0.log clearly states that I am using this driver for the fx 5200 card - as I have specified in xorg.conf.

(edited, additional) When I booted up this morning, the second monitor did not work, was not powering on.  For some reason, my xorg.conf file had been rewritten at boot time.  I copied a backup I had made once I got both monitors working yesterday, then crtl-alt-backspace to shutdown the x-server, startx , and everything worked fine again.

good luck

---

