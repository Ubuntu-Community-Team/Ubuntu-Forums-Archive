---
title: "Amarok 2.0 Beta 3 (amarok-kde4) can't play audio"
date: 2008-11-07
forum: Multimedia Software
---

### Post by QuacoreZX on 2008-11-07
Hey all,

Everytime I try to start up Amarok's new beta, I get a popup message saying "HDA Intel (ALC883 Analogue) does not work.  Falling back to default" and I can't hear any sound.  If I use amarok-nightly, I can hear sound, but it crashes when scanning my library.  Any ideas?

---

### Post by slugicide on 2008-11-09
> **QuacoreZX said:**
> Hey all,

Everytime I try to start up Amarok's new beta, I get a popup message saying "HDA Intel (ALC883 Analogue) does not work.  Falling back to default" and I can't hear any sound.  If I use amarok-nightly, I can hear sound, but it crashes when scanning my library.  Any ideas?

I get this, too.  Sucks that no one's responded...

---

### Post by grotto on 2008-11-09
I had this issue as well. I installed phonon-backend-gstreamer and set gstreamer as prefered from xine under Backend in Sound System Configuration in System Settings. 

I'm using KDE-nightly, kubuntu-members-kde4 launchpad and Unsupported repositories so I am not sure if it'll be applicable.

---

### Post by r_avital on 2009-09-15
Ten months later I'm dealing for the first time with the same problem (just upgraded to Jaunty).  Installing phonon-backed-gstreamer did NOT solve the problem for me, but installing phonon-backend-xine did - After I made sure the xine is set as preferred, following the steps in grotto's reply above.  Specifically, in KDE4 at the prompt, you can run "kdesudo systemsettings" and click on the "backend" tab.

[Actually I'm running under gnome, and this still worked after running "gksudo systemsettings" - and of course KDE4 is installed, but since that "preferred" setting is for KDE4 I don't know if it is pertinent under gnome.  Some pages I've read, people said they've had to uninstall phonon-backend-gstreamer and keep the xine equivalent to make it work]

---

### Post by markbuntu on 2009-09-16
If you are using gnome on a 64 bit system you may need to get the xine-ui and set xine to use pulseaudio to get Amarok to work. At least that's what I had to do

---

### Post by noremacyug on 2009-10-10
> **markbuntu said:**
> If you are using gnome on a 64 bit system you may need to get the xine-ui and set xine to use pulseaudio to get Amarok to work. At least that's what I had to do

i just wanted to thank you.  i couldn't get audio out of amarok on my aspire one aoa150.  i have netbook remix installed.  i installed the xine-ui, changed it to pulseaudio and viola!  thanks again.

out of curiousity though, is there any other way to change that setting without have the ui installed?

---

