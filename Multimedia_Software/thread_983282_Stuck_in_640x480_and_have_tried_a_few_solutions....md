---
title: "Stuck in 640x480 and have tried a few solutions...."
date: 2008-11-15
forum: Multimedia Software
---

### Post by GTdave on 2008-11-15
Hi guys,

I am completely new to Ubuntu and Linux in general.

I have an Nvidia FX5600 Graphics card installed on my PC, and have installed the Nvidia drivers using envy.

I think my problem now lays in my monitor not being supported, how can I edit this???

Any help would be much appreciated.

Thanks,

GTdave :)

---

### Post by bford16 on 2008-11-26
It makes a difference which version of ubuntu you installed.  Since Hardy (8.04), xorg is self-configuring, so long as you have the correct driver installed.

This brings me to my next point.  Envy has been known to cause problems with nVIDIA driver installations. You may have to undo whatever Envy did, and install the drivers the Ubuntu way, using Synaptic or apt.

But first, reboot and hit Escape (ESC) when you see the prompt in the GRUB startup message.  Start the computer in recovery mode. You will be running as root. Once you get to a prompt, do "dpkg-reconfigure xserver-xorg."  When that program has run its course, type 'exit' at the prompt. This will cause the computer to start normally.  You should have a properly configured display, again assuming you have the proper driver installed.

Let us know how it works out.

---

### Post by Gennn89 on 2008-11-26
I'm using updated software and hardware (ubuntu 8.10, Dell inspiron 1525) but if it's possible to get the program on that version (I'm a new user as well) you could do a synaptic (use add/remove in your applications menu for best results)and search all available applications (up in the top toolbar where it says show) for screen resolution. I don't remember what topic  I found it in but just do a quick search. Hopefully it works out for you - if not I would at least try updating my OS next to intrepid (8.10).

---

