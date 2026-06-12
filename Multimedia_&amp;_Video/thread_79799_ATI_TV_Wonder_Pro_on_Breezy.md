---
title: "ATI TV Wonder Pro on Breezy"
date: 2005-10-20
forum: Multimedia &amp; Video
---

### Post by *nix_noob on 2005-10-20
Anyone know how to get and set up dirvers for ATI TV Wonder Pro on Breezy.? I'm new to linux drivers so i need a step-by-step guide.

---

### Post by dust0r on 2005-10-30
I'm looking for the same question.  Im not sure that the ATI PCI card is even supported.

---

### Post by techflat on 2005-11-03
Hi, I have that problem too.. just wanted to receive e-mail notifications if there's an answer here...

I'm using All-in-wonder x600 pro though

---

### Post by techflat on 2005-11-04
I went to the [http://gatos.sourceforge.net/]("http://gatos.sourceforge.net/") site and tried to understand things there... there isn't a lot of explaining there...

I tried setting up the drivers, even if they're supposed to be for XFree and we're using Xorg here. Not shure about compatibility. Not shure if the drivers are installed and working.

I downloaded the drivers from ati too, seems to work.

I downloaded tv-time, apparently it's a very good program (wouldn't know... yet) but it doesn't seem to work, my device right now is /dev/video0 but it's not working.


I haven't found too much information on this subjet, so it would be great if someone could give a place to begin or a guide on what to do.

thanx

---

### Post by *nix_noob on 2005-11-04
try sudo apt-get install gatos and sudo apt-get install tvtime i got it to work :)

---

### Post by jecos on 2005-11-04
Just install tvtime and your tuner should be working already if your using a standalone tuner card like tv-wonder. 

Gatos is only for ALL-IN-WONDER cards.  Almost every tv tuner card has kernel drivers already. So get rid of Gatos unless you actually have an ALL-IN-WONDER.

Xorg 7.0 will have Gatos integrated into it.

---

### Post by techflat on 2005-11-04
Thanx.

I'm using gatos because I have an All-in-wonder x600 Pro.

The only thing I'm missing right now is tv 
(under ubuntu, haven't get rid of windows...)

I've tried a couple of versions of linux, this one works very good. The package management is beautyfull...

About Xorg 7.0, I read about Gatos being integrated into it, will be very good and easy to do...

But right now I want my tv working under Ubuntu :D  Any ideas. Gatos is already installed and tvtime too.

When I run tvtime I get a blue screen and with a no dev found error (/dev/video0).

---

### Post by techflat on 2005-11-04
Something else.

I run the Multimedia System Selector and when I run a test, apparently the image I get is a small tv window.

Plus, I took a screenshot (print screen button) and the place where the little window is is black in the screenshot.

---

### Post by Ubuntu Warrior on 2005-12-04
Yep, have the same problem. Have been driving myself dilly trying to get my ATI AIW Pro 128 working. My display is perfect so the default Breezy drivers seem to handle that ok but I just cannot get TV-in working. For some or other reason I don't have any /dev/video0 device (not even sure if I should but tvtime seems to look for one).

Have tried installing the drivers from the ATI site (version 8.19.10) but these don't seem to support the AIW Pro I have.

Would really like to get TV working on my system for viewing/recording etc. Can anyone help?

---

### Post by NittanyLionTX on 2006-01-13
Sorry to jump in, but I'm having a problem with the sound on my TV tuner.   I am using a ATI TV-wonder 2000 XP, and have installed tvtime, which gets a rather nice picture, but no sound.

I have an audio cable that runs from the audio out of the card to my microphone slot on my soundcard.

I'm not really sure what the problem is... T.T

---

### Post by Zyphrexi on 2006-02-04
I had that card... I took it back and got an ATI AIW 9600 2006 edition instead.
it can be funny sometimes, check to see if it's muted.

---

### Post by techflat on 2006-02-04
What do you mean by muted??

---

### Post by Ubuntu Warrior on 2006-02-08
Sorry can't help on that one. Did you do anything tricky to get the ATI TV to work. Apps like tvtime, etc. just complain on my system that they cannot find the card. Do I need to mount the device specifically?

---

### Post by ranman on 2006-02-21
[QUOTE=NittanyLionTX]Sorry to jump in, but I'm having a problem with the sound on my TV tuner.   I am using a ATI TV-wonder 2000 XP, and have installed tvtime, which gets a rather nice picture, but no sound.

I have an audio cable that runs from the audio out of the card to my microphone slot on my soundcard.

I'm not really sure what the problem is... T.T[/QUOTE]


Put it in the line in not the michrophone jack... or re-map mic to line in...  Line in is normally the blue one... and for all the other people...  i think i can get the AIW 2006 working with some persuasion because i had it working in debian... =) *gets out C manual and pitchfork*

---

