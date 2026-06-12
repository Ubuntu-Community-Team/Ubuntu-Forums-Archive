---
title: "intricate sound conflict -- skype, flash and rhythmbox"
date: 2008-07-31
forum: Multimedia Software
---

### Post by ingrid_ozikem on 2008-07-31
Not the usual one, so please read.. I've already reinstalled Ubuntu for some improvement. 

  Firefox Flash + Rhythmbox = works in any order or together.
  Firefox Flash followed by Skype = works only if Firefox is closed.
  Skype + Rhythmbox = works in any order or together.
  Skype followed by Flash = doesn't work until I start Rhythmbox which works and then Flash starts working.

Using Hardy Heron with PulseAudio and ALSA and OSS. Installed the flashsupport plugin that helps flash use pulseaudio. Don't want to the 'perfect Pulse Audio' set up -- been there, done that, really messed up Skype, esp. recording. Had to reinstall Ubuntu.. 

So if anyone has any ideas about this particular conflict, it'd be very helpful!

---

### Post by Lilszamora on 2008-08-03
I really want to know also, this is a bothersome problem for me, I had it all working once now it doesn't

---

### Post by ingrid_ozikem on 2008-08-04
I fixed my problem by reinstalling Ubuntu :(

After that, I set everything to use ALSA alone. DO NOT install libflash support or whatever it is that helps flash play pulseaudio. Without that plugin and on a fresh install of Ubuntu, everything set to ALSA works. 

I can now use Skype, Rhythmbox, Flash ... everything at once if I wish! No conflicts.. the mic works, everything works. (For the mic, you do have to start gnome-volume-control and unmute the mic after finding it first.)

I did not uninstall PulseAudio .. fear breaking something.. but I dont think any program uses Pulseaudio at the moment.

Put another way, Skype is the real problem.. I think it only likes ALSA and doesn't like Pulseaudio anyway.

But yes, Ubuntu's sound is probably the worst it can be. What a mess. Pick a sound system and get rid of everything else! (Though to be honest, they can't force 3rd party software like Skype to get with the program..)

but still, sound sucks in Ubuntu!

---

### Post by kokonobs on 2010-02-26
Had the same problem as. 

I unistalled libflashsupport and it all works now.

---

### Post by abelandlinux on 2010-11-28
Hello,

would you please explain how to uninstall libflashsupport?
I am having this problem too, and I am extremely new to linux.

I appreciate your help.

---

