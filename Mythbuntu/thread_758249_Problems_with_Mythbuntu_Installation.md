---
title: "Problems with Mythbuntu Installation"
date: 2008-04-17
forum: Mythbuntu
---

### Post by rbrown3 on 2008-04-17
I have followed the instructions in the Mythbuntu Installation manual, and have performed the first stage of the Mythbuntu installation.

(Please note: the docs people might want to update the manual. There hava apparently been several changes in the installation that are not reflected in the current manual)

In any event, I have attempted to set up the MythTV Setup, and I am having several problems.

Right now, the main problem that I seem to be having is that the remote control doesn't seem to be working. I am using a Streamzap PC remote which, when I first started up, worked without problems. Now, however, despite the fact that I have checked the configuration several times, the system seems to be ignoring the commands sent by the remote.

I say "ignore" because the remote receiver has an LED which lights up whenever I hit a button on the transmitter. I know that the receiver is receiving commands, yet MythTV does not respond to them at all.

Can someone give some idea how to get this thing working???

---

### Post by tgm4883 on 2008-04-17
What do you mean there are several changes that are not in the manual.  The manual was written for 7.10, and to my knowledge, the Mythbuntu 7.10 ISO has not changed since release.  8.04 is different, however, it is not released yet and neither is the documentation for that.

---

### Post by majoridiot on 2008-04-17
> **rbrown3 said:**
> I say "ignore" because the remote receiver has an LED which lights up whenever I hit a button on the transmitter. I know that the receiver is receiving commands, yet MythTV does not respond to them at all.

Can someone give some idea how to get this thing working???

the light on the receiver only means that it is seeing an ir data pulse... not that it is getting good data,
or data that it can interpret.

if you run **irw** from a terminal and press remote buttons, do the correct- or any- buttons
report as being pressed?

---

### Post by rbrown3 on 2008-04-22
Greetings:

   Sorry for the late reply. I was figuring out the solutions to some of my other installation problems.

   Actually, this Mythbuntu is really cool!

   Anyway: one of the things I did was a re- install of the system.  The first time it came up, the Streamzap remote worked. Not all the buttons on it seemed to be correct (for example, the channel up button caused what I was watching to go back five minutes, the channel down button caused it to try to go forward) but there were responses to my remote.

   I shut down the system and went to work. When I got home, I restarted it.

   The remote stopped working.

   I restarted the system. It worked again. I used it for a time, shut down, and restarted. The remote stopped working.

   This went on for a time. Sometimes I used the Control Centre to reconfigure the remote, and that caused it to work for a time. Other times nothing I did made it work.

   Now, of course, it doesn't work at all.

   I finally read the message to test the remote with irw. I began the test. The result is that no matter what button I hit on the remote, there is no response on the terminal. None whatsoever.

   Aside from having krappy reception of channels, this remote problem is the main problem I am having. Any suggestions on how to solve it?

---

### Post by laga on 2008-04-22
When you don't get any output with irw, does the remote still work in mythfrontend?

It'd be interesting to see the output of "dmesg", the output of "lsmod", the contents of /etc/lirc/hardware.conf and maybe /etc/lirc/lircd.conf.

It would be even better if we could two copies of everything:

One when it doesn't work and one when it works (maybe after reconfiguring using the control centre?).

Sounds like a lot of work, but we should be able to figure out what's wrong with that information.

---

### Post by rbrown3 on 2008-04-22
Greetings again:

   I found the problem with my remote.

   It turns out it wasn't my remote at all.

   I had a real problem believing that a system this good at configuring everything else would have such difficulties with the remote. My first thought, of course, was to look at my hardware. 

   After establishing that the remote and its receiver weren't at fault, I did some inquiry about the case I was using.

   I had purchased the case and CPU board secondhand from a friend, who had "forgotten" to tell me that the case had a built- in IR system. He didn't tell me about the IR system because he had lost its remote and couldn't tell me what kind of system it was.

  The system, apparently, was a USB system which, incidentally, was hooked into one of my USB ports. I just shut down the system, removed the connection, and restarted.

   My remote has worked ever since.

   Actually, I am rather embarrassed. I usually make it a habit to insure I know everything about hardware I buy.

   Oh, well...

   In any event, it appears that the last thing I need to fix with my remote is the fact that several of my buttons do not work as they should. Checking around I discover that there are some "keyboard mappings" that I should be able to change and set up. Unfortunately, every document that tells me I should edit such mappings gives no idea how to do so!

   Does anyone know how to do this? As an alternative, could someone please steer me to some documentation that describes how to do this?

---

### Post by majoridiot on 2008-04-23
> **rbrown3 said:**
> Greetings again:

   I found the problem with my remote.

   It turns out it wasn't my remote at all.

   I had a real problem believing that a system this good at configuring everything else would have such difficulties with the remote. My first thought, of course, was to look at my hardware. 

   After establishing that the remote and its receiver weren't at fault, I did some inquiry about the case I was using.

   I had purchased the case and CPU board secondhand from a friend, who had "forgotten" to tell me that the case had a built- in IR system. He didn't tell me about the IR system because he had lost its remote and couldn't tell me what kind of system it was.

  The system, apparently, was a USB system which, incidentally, was hooked into one of my USB ports. I just shut down the system, removed the connection, and restarted.

   My remote has worked ever since.

   Actually, I am rather embarrassed. I usually make it a habit to insure I know everything about hardware I buy.

   Oh, well...

   In any event, it appears that the last thing I need to fix with my remote is the fact that several of my buttons do not work as they should. Checking around I discover that there are some "keyboard mappings" that I should be able to change and set up. Unfortunately, every document that tells me I should edit such mappings gives no idea how to do so!

   Does anyone know how to do this? As an alternative, could someone please steer me to some documentation that describes how to do this?

glad you got things working!  don't be too hard on yourself for the oversight... we *all* make silly
mistakes... especiually idiots. ;)

you can find basic info on .lircrc syntax, etc. here:

[http://www.mythtv.org/wiki/index.php/LIRC#LIRCRC](http://www.mythtv.org/wiki/index.php/LIRC#LIRCRC)

here is a list of all keybindings, for configuring mythtv:

[http://www.mythtv.org/wiki/index.php/Keybindings](http://www.mythtv.org/wiki/index.php/Keybindings)

to get a list of all mplayer keys and commands that can bound to remote buttons, from a terminal:

```
$ mplayer -input keylist
$ mplayer -input cmdlist
```

you can config vlc and xine, etc. but i don't use them, so i don't have that info at hand.

---

