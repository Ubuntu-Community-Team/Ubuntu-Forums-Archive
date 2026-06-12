---
title: "Howto increase refresh rate in feisty with nvida drivers?"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by Irwin J. Finster on 2007-04-24
Hi I just installed feisty and have enabled the nvidia drivers and set up my dual monitor system. All works fine so far, but the refresh rate at my second monitor is stuck at a measly 60 hz. I know for fact that the monitor will support more (has in Suse). I tried to increase the refresh rate with the nvidia-settings manager, but it won't let me. So I fear I will have to edit the xorg.conf by hand.

Unfortunately I have no real cue on what to change there. I have attached a copy of my current xorg.conf to this post if anyone cares to have a look.

Thanks,

Irwin

---

### Post by mansoniaberlin on 2007-04-24
I had the same problem, but after installing the Kubuntu-desktop I got a new entry in the panel (Zubehör) and it was possible to change resolution and refresh rate with that kde panel.
Installing the driver was quite tricky. I installed the nvidia-glex-legacy driver. Than I had to change the xorg.conf. Under devices I added Option         "AllowGLXWithComposite" "true" to enable 3D-abilities (you can find it under etc/x117xorg.conf). 
After that procedure I opened etc/default and edited linux-restricted-modules-common at the end of the page : Disabled module ="nv"     to Disabled modules="".
I am now running my Gforce mx400 with 85 Hertz.
Good luck!
Andreas

(Lots of hours to figure it out...)

---

### Post by Irwin J. Finster on 2007-04-24
Do you have multiple monitors running? I do, for I fear if not this tool you mentioned won't configure the two monitors independantly. Is there not just a way to enter a higher refresh rate in the xorg.conf manually?

---

### Post by mansoniaberlin on 2007-04-25
Quit x-session with alt/strg/F2 and stop gdm with "sudo /etc/init.d/gdm stop. Type "sudo dpkg-reconfigure xserver-xorg. this will open the editor and you can change the configuration. Restart gdm with "sudo /etc/init.d/gdm restart".
You can edit the conf. manually by changing it from root to user ( sudo chown xy xorg.conf). After changing set root rights again (sudo chown root xorg.conf).

Also I am running only one monitor.
Andreas

---

