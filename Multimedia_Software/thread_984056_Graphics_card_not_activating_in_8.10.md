---
title: "Graphics card not activating in 8.10"
date: 2008-11-16
forum: Multimedia Software
---

### Post by iamlost on 2008-11-16
Hi
I have just updated my new Dell Inspiron 530 pre-installed with Hardy Heron to Intrepid Ibex. I have done nothing but as soon as it was plugged updated it. 

It's done everything ok apart from now the graphics card does activate. I go to System>Administration>Hardware Drivers, it shows me that there is a graphics card driver to activate and i click activate but it shows a loading bar that stay at 0% and then goes back to the Hardware Drivers and the card remains unactivated.  

The card  is a ATI Radeon HD 2400 PRO if that helps. 

Please can someone help as I'm drawing blanks everywhere i look.

---

### Post by binbash on 2008-11-16
sudo apt-get install build-essential xorg-driver-fglrx

sudo aticonfig --initial

---

### Post by iamlost on 2008-11-16
Thanks for the fast reply but after doing that the same problem still occurs.

---

### Post by iamlost on 2008-11-16
On a strange but possibly related note, my ubuntu doesn't tell me it's release number or name in 'about ubuntu' in system

---

### Post by eternalnewbee on 2008-11-16
> On a strange but possibly related note, my ubuntu doesn't tell me it's release number or name in 'about ubuntu' in system
You can find more information in: **Main Menu > System > Administration > System Monitor**
You can also install an application called **Sysinfo**, that will give you more detailed info about your hard- and software. To install Sysinfo, go to **Main Menu > Add/Remove Applications**, and in the search bar type: Sysinfo, select it and apply. After installation is complete, you can find it under: **Main Menu > System Tools.**
Good luck.

---

### Post by binbash on 2008-11-16
paste the output of glxinfo | grep render

---

### Post by pesz1 on 2008-12-02
I am having the same problem but with 8.04 (Dell 530n machine) and the card is the second one I installed to use dual monitors.  The system doesn't recognize the Radeon card at all.  I have tried Envy, other drivers, no luck... 

Any advice would be appreciated.  

Output from glxinfo | grep render:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by wpg9210 on 2008-12-04
Im having the exact same problem and output from glxinfo

---

### Post by TANGO! on 2009-01-07
Hi, I'm having this same problem;  I thought I'd bump the thread.  Also, the ATI drivers download page seems to be down at the moment, so I'm wondering if there's any relationship with the problem.

---

### Post by Afisamuleal on 2009-01-11
Hey, I had this problem, but it's very simple to solve:

System-->Synaptic Package Manager-->Settings-->Repositories-->Third Party Software-->Check the boxes-->Close-->reload button on synaptic

Then try the proprietary drivers activation again.

It needs to have somewhere to download the non-open-source packages from to install them.

---

