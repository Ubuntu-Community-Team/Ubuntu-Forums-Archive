---
title: "Watch videos from pc to tv"
date: 2008-07-11
forum: Multimedia Software
---

### Post by neandert on 2008-07-11
I'm trying to get get a second screen with my nvidia geforce fx 5200 videocard but I can't get it to work

someone got an idea?

greets

---

### Post by neandert on 2008-07-11
everytime when I want to set the nvidia settings, this message pops up:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by wolfen69 on 2008-07-11
run
```
gksudo nvidia-xconfig
``` i forgot the command to restart x, but you could also reboot.

---

### Post by neandert on 2008-07-11
> **wolfen69 said:**
> run
```
gksudo nvidia-xconfig
``` i forgot the command to restart x, but you could also reboot.

joris@joris:~$ gksudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by neandert on 2008-07-11
still the same problem

---

### Post by Bakon Jarser on 2008-07-11
Go to System > Administration > Hardware Drivers.  Does it say something like NVidia accelerated graphics driver   in use?

---

### Post by neandert on 2008-07-11
> **Bakon Jarser said:**
> Go to System > Administration > Hardware Drivers.  Does it say something like NVidia accelerated graphics driver   in use?

It says: no proprietary drivers are in use of this system.

empty window

---

### Post by Bakon Jarser on 2008-07-11
okay, your nvidia driver isn't installed.  you should be able to find a good thread on how to install the nvidia driver with a quick search.

---

### Post by neandert on 2008-07-12
> **Bakon Jarser said:**
> okay, your nvidia driver isn't installed.  you should be able to find a good thread on how to install the nvidia driver with a quick search.

Didn't find anything that worked for me, something's wrong. Everytime after a restart it begins with the configuration for the nvidiacard. after the settings it just begins in the 700x600 resolution and only after that when I click on the nvidia settings I get the message: You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I'm getting tired

---

### Post by neandert on 2008-07-12
joris@joris:~$ wget [http://blogage.de/files/4359/download](http://blogage.de/files/4359/download) -O compiz-check
--11:03:00--  [http://blogage.de/files/4359/download](http://blogage.de/files/4359/download)
           => `compiz-check'
Herleiden van blogage.de... 78.46.34.206
Verbinding maken met blogage.de|78.46.34.206|:80... verbonden.
HTTP-verzoek is verzonden; wachten op antwoord... 200 OK
Lengte: 27,814 (27K) [application/force-download]

100%[====================================>] 27,814        18.55K/s             

11:03:07 (18.52 KB/s) - 'compiz-check' opgeslagen [27814/27814]

joris@joris:~$ chmod +x compiz-check
joris@joris:~$ ./compiz-check

Gathering information about your system...

Distribution:          Ubuntu 8.04
Desktop environment:   GNOME
Graphics chip:         nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
Driver in use:         nv
Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
Error: No rendering method in use (AIGLX, Xgl or Nvidia)

Would you like to know more? (Y/n) y

The nv driver is not capable of running Compiz, you need to install the
proper driver for your graphics card.

Check if there's an alternate (proprietary) driver available? (Y/n) y
joris@joris:~$ WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia failed: modinfo: could not find module nvidia

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy

joris@joris:~$ ./compiz-check

---

### Post by neandert on 2008-07-12
EnvyNG  did it for me !:)

---

### Post by Bakon Jarser on 2008-07-12
Glad to see you got it working.  Did you get your settings to save too?

---

### Post by peakshysteria on 2008-07-12
You find Envy via synaptic. It's probably the best way for you to install the correct driver for your card. Then you should be good to go :)

---

