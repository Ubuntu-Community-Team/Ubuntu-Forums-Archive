---
title: "Super easy n00b question for 7900GT"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by 94ranger on 2007-03-06
Guys,

I'm a long time Windoze user and a total n00b to Ubuntu. I have a 7900GT card with my Core 2 Duo system on a GA-965P-DQ6 motherboard. Which graphics driver do I need? I installed the Solaris x64/x86 driver - should I have used the AMD64/EMT64?

I was able to get it to display 1680x1050 for my monitor, and it looks good, but my screensavers will not work. In my config file, I changed "nvidia" to "nv" to make this work. Is this the cause?

Finally, I get numerous errors when I run nvidia-settings from terminal:

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

By boxes are grey, and my only option on the left is "nvidia-settings Configuration". I use to have a whole slew of them!

Thank you all for  your help!

---

### Post by igknighted on 2007-03-06
You need the linux display driver, not solaris.  Solaris is a completely different OS.  Frankly the fact that it works at all amazes me.  Try to use synaptic to get programs you need first.  I think that Nvidia driver is nvidia-glx.  Make sure you uninstall the old driver first, however.  As an alternative, google the "Envy script".  It automates much of the nvidia driver install.

---

### Post by r4ik on 2007-03-06
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)   ( Envy)

---

### Post by 94ranger on 2007-03-06
Guys,

Thanks for the pointers! I used Envy and it installed them fine. My screensavers work,  but they appear slow and choppy when I preview them. When I try to run Nvidia-settings (through Applications > Systems Tools or through terminal) it says "failed to execute child process user/bin/nvidia-settings." I noticed that the NVidia binary X.Org driver is not installed. When Envy ran, I told it to automatically configure my x.org file. Should this also be installed or somehow enabled? Sysinfo says my VGA controller is "a Corporation Unknown device 0291 (rev a1)". 

What can I do to correct these problems? Thank you all - I appreciate it!

---

