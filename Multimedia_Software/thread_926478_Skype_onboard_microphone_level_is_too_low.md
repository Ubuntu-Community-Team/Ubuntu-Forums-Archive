---
title: "Skype onboard microphone level is too low"
date: 2008-09-22
forum: Multimedia Software
---

### Post by grikdog on 2008-09-22
Skype works fine on Mac or Windows, but not Ubuntu??!  Everything seems to be working ok, except the Dell Inspiron 1525's onboard microphone (default sound in).  The level is unacceptably muted.  Is there a solution that won't break other apps?  I see lots of breezy "solutions" (remove pulseaudio, install esound) that don't discuss ramifications of decisions Ubuntu *didn't* make, for some reason.

Thanks,
d

---

### Post by squaregoldfish on 2008-09-22
Are you allowing Skype to auto-adjust the volumes (Options -> Sound Devices -> Allow Skype to automatically adjust my mixer levels)?

I always find I have to disable this and set the volumes manually to get anything useful.

Steve.

---

### Post by mexicanbob on 2008-09-22
Hi Steve
I have been through all options to try to get sound on Skype using my microphone but no luck.   what cheeses me off it works on the other mobs OP :) so its not the mike. Learning to use and loving Ubuntu
Would appreciate any clues that you can give.

Bob

---

### Post by grikdog on 2008-09-22
> **squaregoldfish said:**
> Are you allowing Skype to auto-adjust the volumes (Options -> Sound Devices -> Allow Skype to automatically adjust my mixer levels)?

I always find I have to disable this and set the volumes manually to get anything useful.

Steve.

Hmmmm...  Yes.  Which manual volumes do you set?  Just capture?  I'll try this! Thanks.

---

### Post by squaregoldfish on 2008-09-22
> **grikdog said:**
> Hmmmm...  Yes.  Which manual volumes do you set?  Just capture?  I'll try this! Thanks.

Mic or Line In are the two obvious ones to try, assuming your mixer has channels with these labels. Otherwise, just experiment and see which ones make a difference. The echo123 service is handy for this!

Steve.

---

### Post by grikdog on 2008-09-22
> **squaregoldfish said:**
> Mic or Line In are the two obvious ones to try, assuming your mixer has channels with these labels. Otherwise, just experiment and see which ones make a difference. The echo123 service is handy for this!

Steve.


Ok, I'm obviously more of a newbie than I thought.  Where does Ubuntu hide its internal microphone volume control?  What "mixer" are we talking about?
I installed (and am about to uninstall!) something called the Gnome ALSA Mixer, which allowed me to MUNG settings to the point that now I have NO INPUT VOLUME AT ALL!  Putting mixer settings back where they were doesn't get my microphone volume back either.

Grrr... ](*,)

---

### Post by squaregoldfish on 2008-09-22
OK, you should have a mixer by the name of gnome-volume-control (type it into a terminal to get it up).

This should have three tabs - Playback, Recording and Switches. The Recording tab will have your microphone input slider on it, together with a little microphone icon at the bottom right, which will enable the microphone as an audio input (or disable it if it's got a socking great red cross through it).

Make sure it's enabled, and turn the slider up a bit - hopefully that'll get you some input volume.

Steve.

---

### Post by yogitoad on 2009-01-06
Enter this code...then if your voice sounds faint..go into the sound setting for skype and set them to microphone on the in and outgoing, try another test call you will get an error message reset both in and out back to default...problem solved.

killall pulseaudio
sudo aptitude remove pulseaudio
sudo aptitude install esound
sudo aptitude remove /etc/X11/Xsession.d/70pulseaudio

dont know why

---

### Post by rfurno on 2009-10-18
I had a similar problem with Skype running on Ubuntu 9.04. I had even trying different headsets for no avail.
What worked for me was to launch the volume control and check all available devices and ensure that none had the mic muted.

---

### Post by snuggs on 2009-11-19
me as well.. my mic seems to have been turned down by default.. sound preferences > input and adjusting the input volume worked for me.

---

### Post by Deerfoot on 2009-12-21
I was tying myself in knots yesterday, reading ideas from others in forums as I tried to get input sound when using Skype.
Today, another try - success!
I am using Ubuntu 9.10 - no problems before with Skype.
This proved the simple answer for me: right click on loudspeaker (top panel of computer). Choose Sound Preferences. Input/Input Volume - move the slider to about halfway (it may be set on Unamplified - as mine was). Make sure Mute is not ticked. 
With your microphone/headphone **turned on**, test Input Level by speaking. If no reaction, choose another option from Connector. (I needed to change from the default Line-In to Microphone 2).
What a great relief! 
I hope this is a help to someone.
Happy Christmas and New Year.

---

### Post by mircea.postolache on 2009-12-23
> **squaregoldfish said:**
> Are you allowing Skype to auto-adjust the volumes (Options -> Sound Devices -> Allow Skype to automatically adjust my mixer levels)?

I always find I have to disable this and set the volumes manually to get anything useful.

Steve.

This worked for me. Thanks!

---

