---
title: "Cannot make sound work."
date: 2009-09-02
forum: Multimedia Software
---

### Post by paulizleet on 2009-09-02
I installed ubuntu 9.04 yesterday, and the sound does not work.  I have had some experience with linux in the past, but it was very little and I can't say that i'm not a noob.
 
I have looked through these forums and all over the internet for a solution to my problem, but anything i found was either too confusing for me or didnt work after i tried it. 
 
I did lspci (these are the results [http://cl1p.net/hereyougodan](http://cl1p.net/hereyougodan)) because my friend had asked me to so he could see if there was a problem, and he said that i needed to compile alsa drivers.   I did some research on that and had no luck in fixing the problem.
 
If it helps, i have Ubuntu dual booted with Vista 64 bit.  The sound works fine on vista.
Also, i was  starting it up once, and it gives me an error when i try to log in using the Run Xclient script option. 

Here are the details from the ~/.xsession-errors file:
[FONT=System]
/etc/gdm/Xsession: Beginning session startup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/home/paul/.xsession: 2: Xgl: not found
/home/paul/.xsession: 4: gnome-window-decorator: not found[/FONT]

This problem goes away when i use the GNOME option instead of the Run Xclient Script option, and i dont think that this has very much to do with the fact that my sound doesnt work. 

 Any advice would be much appreciated to help a lowly noob.  Thank you in advance.

---

### Post by ApEkV2 on 2009-09-02
in terminal type gstreamer-properties and change the sound output to ALSA (if you have it installed) then select the output device.  
Be sure to hit "Test" button and you should here a tone.

if the tone works but still no sound for music/videos, you might have to restart the computer.
if there is no tone, be sure to redo the options back to what they were before. (so as to keep the amount of changes to a minimum)

---

### Post by paulizleet on 2009-09-02
I tried what you said, ApEkV2, but that didnt work.  I switched the output to ALSA, but didnt get a tone when i clicked test.

---

