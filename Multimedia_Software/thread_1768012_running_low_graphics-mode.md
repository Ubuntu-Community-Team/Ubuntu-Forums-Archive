---
title: "running low graphics-mode"
date: 2011-05-26
forum: Multimedia Software
---

### Post by tony van on 2011-05-26
I have a dual boot xp -ubuntu - AGP ati 2600 series radeon. intel
8300 dell .
 
the message comes up after login "ubuntu is running in low-graphics mode".
I hit ok and i get 5 choices and none of them work.
1) run ubuntu in low-graphics mode.
2) reconfigure graphics.
3) troubleshoot the error.
4) exit to console login.
5) restart X.
:D
should i just use the re-installation disc and redue everything ?
I'm clueless.

---

### Post by wolfen69 on 2011-05-26
Did you install the ATI graphics driver?

---

### Post by aeronutt on 2011-05-26
At grub menu, hit 'e' to edit the boot options, and add "radeon.modeset=0" to end of the line that starts with 'linux..'.

If that lets you boot, check out :
[http://ubuntuforums.org/showthread.php?t=1747996](http://ubuntuforums.org/showthread.php?t=1747996)
and
[http://ubuntuforums.org/showthread.php?t=1739199](http://ubuntuforums.org/showthread.php?t=1739199)


EDIT: and good question, did you install proprietary ATI driver?

---

### Post by tony van on 2011-05-26
i added radeon.modest=0 and a new screen popup.  message is "gnome power manager installed problem.
there is a screen anthony-desktop asks for password. tried password did not work.
it got me a little further in.
 
i was running ubuntu for about a year and half now with no problems.
think i need to reinstall drivers ?
 
thanks for response.

---

### Post by aeronutt on 2011-05-26
I'm at a loss for your next step now. Hopefully, others will pop in to help.

Although, I should ask, can you boot from liveCD?

And if you have installed the proprietary ATI drivers, you should uninstall them.

---

### Post by tony van on 2011-05-27
I can boot from cd-live. takes me into a screen gives me 2 choices .
at the top right was a icon for drivers installation and i activated and it gave me an error.
I'll probably try and install 11.04 later.
 
thanks for reply and help.
tony

---

