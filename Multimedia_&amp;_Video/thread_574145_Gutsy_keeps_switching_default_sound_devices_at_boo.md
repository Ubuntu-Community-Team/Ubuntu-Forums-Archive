---
title: "Gutsy keeps switching default sound devices at bootup"
date: 2007-10-12
forum: Multimedia &amp; Video
---

### Post by frefactory on 2007-10-12
Hello,

I have a strange kind of problem, each time Ubuntu 7.10 boots up, it scans automatically for sound devices. I love this feature, but the only problem is, that each time, a different sound device (soundcard, VOIP USB Phone, USB Cam) becomes device nr. 0 in the list. It is quite nerving, because each time I use skype, for instance, I have to manually set what device it should use. 

Does anyone know a solution? (Apart from never rebooting again)

Cheers!

---

### Post by frefactory on 2007-10-19
Hi everyone,

I have found an easy workaround, so that I did not have to mess around with many conf files. I have installed the package " asoundconf-gtk ", which allows you to set the default ALSA device. Up till now, it seems to be working fine. 

This is what I did :

1. open a terminal
2. install the package by typing :** sudo apt-get install asoundconf-gtk**
3. start the app by typing :** asoundconf-gtk**
4. select your default soundcard from the drop down menu
5. quit the app and close the terminal window
6. reboot a couple of times and test. But it should work fine like this.

cheers!

---

### Post by Simoo on 2007-10-19
Great post, thanks. 

I have an Audigy and an on board VIA. Disabling the VIA in the BIOS had little effect and I was getting quite frustrated with the lack of sound, your solution sorted it!

The only issue is, asoundconf-gtk only has an effect when run as a user not root, so it has to be run for every user individually. And so no Ba dum on the login screen.

Aside from this issue I am more impressed with Gutsy than I have been with any operating system in a long time, fantastic work! In particular the integration of Firefox & Xine etc. with Apt.   

Simon

---

### Post by daxm on 2007-10-19
> **frefactory said:**
> Hi everyone,

I have found an easy workaround, so that I did not have to mess around with many conf files. I have installed the package " asoundconf-gtk ", which allows you to set the default ALSA device. Up till now, it seems to be working fine. 

This is what I did :

1. open a terminal
2. install the package by typing :** sudo apt-get install asoundconf-gtk**
3. start the app by typing :** asoundconf-gtk**
4. select your default soundcard from the drop down menu
5. quit the app and close the terminal window
6. reboot a couple of times and test. But it should work fine like this.

cheers!

Thanks!  Even though my c-media sound card is the only one in my system (and it is labeled the default) I had to use your steps here to get sound.

---

### Post by zx80user on 2007-10-22
Thanks, seems to be a complete solution

---

### Post by CulleyS on 2007-10-22
I'm trying to troubleshoot another problem, when I run these two commands, it shows I already have asoundconf-gtk installed.  But, when I type "asoundconf-gtk" into a terminal, I get this message:

asoundconf-gtk
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

I opened ~/.asoundrc and it's completely empty.  I'm not sure how to include "~/.asoundrc.asoundconf" in it?  When I open ~/.asoundrc.asoundconf, all it has in it is the following:

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file

I added this to the ".asoundrc" file - "<~/.asoundrc.asoundconf>" - but that didn't do anything for me.

I've also run "asoundconf is-active" and "asoundconf-gtk is-active" from the terminal a few times, but it doesn't seem to do anything.  Doesn't give me any error messages, but doesn't really say whether it's done anything either.

Thanks.

---

### Post by CulleyS on 2007-10-22
Figured it out, alsa base package wasn't installed. :)

---

### Post by FSWolf on 2007-10-22
hi im having some issies as well iv tryed all these things but some resion it keeps thinking i no longer have a sound card this is totaly puzzling to me. 


PLEASE HELP 
its a Dell dell dimention 4100

the sound card did work!!! 
but then after reboot showed there was no sound card

!!!!

Please this ia a friends comptuer help

---

### Post by Simoo on 2007-11-07
Try typing 'dmesg' into a terminal after a restart and look for clues. You could also try running 'alsamixer' from a terminal, see if Alsa has found and setup the card

---

