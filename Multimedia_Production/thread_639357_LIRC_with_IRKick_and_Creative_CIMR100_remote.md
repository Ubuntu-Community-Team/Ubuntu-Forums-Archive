---
title: "LIRC with IRKick and Creative CIMR100 remote"
date: 2007-12-13
forum: Multimedia Production
---

### Post by Araj on 2007-12-13
I'm not very experienced with Ubuntu/Linux and LIRC is slowly driving me insane.

I'm trying to get a Creative CIMR100 (serial port) remote to work in (K)ubuntu Gutsy.

LIRC is installed and seems to run if I tell it where the remote is

lircd -d /dev/ttyS0

when I say "it seems to run" I mean I don't get any error messages and if I start IRKick it starts a client and the device is listed in the IRKick config panel, I can setup buttons etc.

However, nothing happens when I press buttons on the Creative controller.

If i enter irw, the prompt hangs waiting for input, which doesn't come. In IRKick, if I try to configure by using the "press a button on the remote" method, nothing happens either.

I have tried 2 different lirc.conf files from folk who seem to have the CIMR working, no joy. I have found several howtos and numerous threads on forums, with a wide range of solutions to problems with LIRC, and tried everything I thought might help.

With no error messages, it's kind of difficult to figure out what's wrong. Before you ask, yes the controller does have a battery and the receiver does work in XP ;-)

Very grateful to anyone with more experience who can help me in the right direction.

---

### Post by CyberCod on 2008-04-12
I know this sounds simple, but make sure you have a good battery in the remote. 

A friend of mine bought one of these and we spent 3 hours trying to get it to work, only to eventually find out that the battery was dead.

If you put it on your tongue and it tastes a little funny, it still has power.  If not, it is dead.  

In a related topic, always check to be sure the mower has gas before you pull the cord.  I had to learn that one the hard way too.

---

