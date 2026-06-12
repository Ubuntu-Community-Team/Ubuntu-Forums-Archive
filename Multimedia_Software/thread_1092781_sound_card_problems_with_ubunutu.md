---
title: "sound card problems with ubunutu"
date: 2009-03-10
forum: Multimedia Software
---

### Post by Arminius on 2009-03-10
hey, not sure if this is the right forum, but anyway, I'm having trouble with my soundblaster X-FI sound card.

worked perfectly under windows but linux doesn't seem to care for it.

unlike in windows where I could restore it's original settings on the few rare occasions it messed up, I haven't found that option in linux, the only way to fix it here is to reboot, is there a quicker way to reset my soundcard here?

also, are there other sound cards that are more linux friendly?

---

### Post by Therion on 2009-03-10
What problems are you having exactly and what release of (I'm assuming) Ubuntu are you running?

---

### Post by Arminius on 2009-03-10
ubunutu 8.10, and sometimes there is no sound at all, but most of the time it's like the sound gets stuck on a loop, and this small half a second sound just gets played over and over and over, and won't stop till u reboot.

---

### Post by Arminius on 2009-03-11
also when I'm watching a video, and another sound from another program sets of, then the sound from the video goes mute and I have to close the movie player and restart the video, and if another sound sets of same thing happens again

---

### Post by Arminius on 2009-03-16
ok now I really need help, now the sound has died completely, not getting anything, and yet when I restart the comp there is a slight noise just before ubunutu shuts down, so I know the speakers are working
I tried Administration\Hardware Drivers and tried suspending the audio driver then starting it again, didn't work
so I went and to the soundblaster website, redownloaded and reinstalled the driver, still hasn't fixed it.

so what can I do? how would I completely uninstall the audio driver and start over?

---

### Post by maculata on 2009-03-16
Not sure what model of X-fi your using but, dl from here:
[http://support.creative.com/Products/Products.aspx?catid=1](http://support.creative.com/Products/Products.aspx?catid=1)

And as per the readme file (I've had success with):
====================================================================


  Sound Blaster X-Fi Linux 32/64-bit Driver Source Release Readme File

  September 2008


====================================================================


The purpose of this document is to describe how to build and install the 
X-Fi Linux device driver.






Quick install


=============

In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install



Uninstall

=========

In terminal,

1) Goto source directory

2) Execute make command as root

   make uninstall

---

### Post by Arminius on 2009-03-17
thanks maculata, the uninstall did work, but when I rebooted and reinstalled the driver, still no sound?

first time I installed ubunutu I used your technique, with the exception I didn't know u could use the same one to just uninstall it.

so any ideas as to what's gone wrong, in the hardware drivers it says this driver is working correctly and it's in the green, would it do that if there was a physical failure on the soundcard?

---

### Post by maculata on 2009-03-17
In System/Preferences/Sound try the different sound playback options.

---

### Post by Arminius on 2009-03-17
nah I already tried that before I uninstalled, all the settings produce no noise when u click on test.

---

