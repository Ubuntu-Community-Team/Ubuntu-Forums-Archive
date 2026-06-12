---
title: "Problems with OSS to Alsa/Pulseaudio"
date: 2014-08-15
forum: Multimedia Software
---

### Post by satan3 on 2014-08-15
Hi there everyone, 

hope this is the right place to post this...

I'm trying to get a sound trigger written in python and using OSS to work on my Dell Inspiron 7537 laptop using Xubuntu 14.04.  The software is here [http://sourceforge.net/projects/audiotrigger/](http://sourceforge.net/projects/audiotrigger/), and im using gphoto2 for the actual taking of the photos.

I tried using padsp but this didnt help.

Using aoss, i can get the code which uses OSS to deal with the ALSA/Pulse audio on my system.  
When the GUI is running it has a horizontal bar representing mic or line-in.  When 'Capture' is enabled and the mic is 'listening' the bar should bounce around depending on sound detected on the mic.  instead however, the bar goes  up to 100% and remains there, as if the mic is turned up far too much.  Using PulseAudio Volume control while this mic is open and listening, I can see the is an OSS proxy entry in the Recording tab which has the expected bouncing bar reacting as expected to increases and decreases in volume.  

When i compare this PulseAudio instance of the open mic to the GUI instance of the open mic there seems to be no similarity.  Playing around with the  the PulseAudio recoring and input sliders, so the mic is super sensitive, the GUI bar in the Audiotrigger program drops down to 40-50% and bounces around there, but seems to bounce from right to left (if you know what i mean) not the other way around as is expected.

I can imagine this doesnt sound very clear since im describing some random program taken from the internet.  So i suppose my basic question is: does anyone know if there are similar problems with aoss that jumbles up the Input, or confuses sensitivities etc. when trying to link up OSS and Pulse/ALSA.  Im about to let this one go and find something else but i've been trying and retrying  aoss, padsp, osspd etc. etc. to get this little thing to work, because everything else seems to work fine and i'm just at the finishing line.  I'm not looking for someone to open up Audiotrigger and try solve the problem for me, rather point me in the right direction with dealing with programs that use OSS.

Thanks for reading all this in advance

---

