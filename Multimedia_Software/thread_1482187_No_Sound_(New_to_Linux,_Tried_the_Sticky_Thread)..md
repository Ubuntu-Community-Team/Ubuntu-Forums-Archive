---
title: "No Sound (New to Linux, Tried the Sticky Thread)."
date: 2010-05-13
forum: Multimedia Software
---

### Post by 456chris on 2010-05-13
Hello, I have been using Xubuntu for the past 2 days and haven't figured out how to fix my sound problem through searching page after page of threads, google searches, etc.
I have a Sony VAIO e series with an Intel sound card I think.
I'm Dual Booting with Windows 7 Home Premium (I have tried unmuting in W7 then rebooting).
I am using Xubuntu 10.04? I think.
Thanks.

EDIT: Would it be better for me to switch to using Ubuntu rather than Xubuntu? If so, how would I make the switch?

---

### Post by 456chris on 2010-05-13
So messing around and I get volume when I have my earphones plugged in although it is REALLY quiet.

---

### Post by XubuRoxMySox on 2010-05-13
It's strange how so many have no problem at all while for others of us it's a big headache.

I got sound working in mine by completely removing PulseAudio:

You can use Synaptic to remove pulseaudio and gstreamer0.10-pulseaudio.

Then install (if not already installed) alsa-base, slsa-tools-gui, alsa-utils, linux-sound-base, alsamixergui, and libesd-alsa0. You can also add gnome-alsamizer, esound, esound-clients, and esound-common.

Use Menu > Multimedia and choose the mixers (alsamixer, mixer, etc) to graphically set levels. You may have to add controls to be displayed and use them to adjust the levels.

For me, pulseaudio was the problem I think. I understand that when it works, it offers some nice advantages. But when it doesn't work, it's a hassle even for experienced users. Grub2 has been the same way: Great when it works (for most people), and a major pain in the backside when it doesn't (for some of us).

Pulseaudio-free and enjoying sound again,
Robin

---

### Post by 456chris on 2010-05-13
Thanks for the help but it seems like I still cannot hear sound from my laptop's speakers :(

---

### Post by 456chris on 2010-05-13
Bump. Does anyone have an idea where I can check for errors or anything?
Thank you.

---

### Post by 456chris on 2010-05-13
Sorry for continuous bumping, I've just tried so many solutions and I don't really know much about linux to try find the problem myself.
Again, thanks for any help...

---

### Post by 456chris on 2010-05-14
Sorry bumped again, could a moderator please delete my previous bumps so I'm not getting cheap post counts? Thanks.

---

