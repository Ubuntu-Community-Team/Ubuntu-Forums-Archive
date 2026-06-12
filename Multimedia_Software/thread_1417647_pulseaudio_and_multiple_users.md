---
title: "pulseaudio and multiple users"
date: 2010-02-27
forum: Multimedia Software
---

### Post by me13221 on 2010-02-27
Is it intended behavior for pulseaudio (in per-user mode) to simultaneously play audio from multiple local users at the same time?  

Specifically, if there is one user logged in via X and another connected via ssh, and they both want to play audio out of the same sound card at the same time, is this supported?

This does not work for me, one user (sometimes both) gets "Connection refused" errors, even though both users have a pulseaudio server running.

using karmic on x86_64.

---

### Post by Daan on 2010-03-04
In Debian I used to

$ pulseaudio -kill

as normal user and do

# pulsaudio -system -D

as root. Then I was able to have programs run as different users play sound simultaneously through pulseaudio.

Now I have Ubuntu and it doesn't work. Things are very different with pulseaudio in Ubuntu. None of my users are members of any of the pulsaudio groups, although they can play sound when they are logged into gnome and their session is the one up on the screen. When I switch users in gnome, any sound that is playing stops. Not what I would expect.

---

### Post by SolipsistX on 2010-03-06
There is a solution over [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654/comments/47").  It boils down to: under System->User Settings->Advanced->User Priviledges, uncheck the 'Use audio device' option for all your users.  A reboot after than might be needed (logging out and back in for all users at least is needed).

---

### Post by Daan on 2010-04-11
> **SolipsistX said:**
> There is a solution over [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654/comments/47").  It boils down to: under System->User Settings->Advanced->User Priviledges, uncheck the 'Use audio device' option for all your users.  A reboot after than might be needed (logging out and back in for all users at least is needed).

The solution to which you link isn't a solution to our problem. We want two or more users to play sound simultaneously. Unchecking "Use audio devices" makes sound stop when you switch users in Gnome. Checking it makes the first user to start pulseaudio lock it (or something). Neither option makes it possible for two users to play sound simultaneously (whether they are logged in through Gnome, ssh or wether they are simply playing an mp3 from the command line in somebody else's Gnome session.

---

### Post by me13221 on 2010-04-11
I've concluded that PulseAudio in [system mode]("http://pulseaudio.org/wiki/SystemWideInstance") is supposed to give the intended behavior, but it is not well-supported (and they [recommend against]("http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode") using it).

But it seems like that is the way to go.  Just make sure all users are members of the 'pulse-access' group, and enable system mode in /etc/default/pulseaudio and reboot.

pulse developers: please support system mode! it seems like pulseaudio is here to stay (and honestly, by karmic it seems to be working pretty well).  system mode should be brought to the point where users don't need to be warned against using it.

---

### Post by Daan on 2010-04-11
> **me13221 said:**
> make sure all users are members of the 'pulse-access' group, and enable system mode in /etc/default/pulseaudio and reboot

That works very well. Thanks!

---

### Post by markbuntu on 2010-04-11
The reason why the pulse devs recomend against system mode is that it is a real security vulnerability. In system mode anyone on the network can control the local sound devices and the devs are not so keen on allowing that by default.

The reason that system mode is still available is because they realize that people want use it for just that purpose anyway so they kept it easy to do but not really obvious.

It seems a reasonable approach to me.

You will find that pulseaudio can do a lot of neat stuff once you dig into it.

---

### Post by Daan on 2010-04-12
Hmm..

Yesterday, everything worked fine, but today there was only "Dummy output" in the pulseaudio Volume Control and no sound. After some googling, I did

```
# fuser /dev/snd/*
/dev/snd/controlC0:   2831
/dev/snd/controlC1:   2831
/dev/snd/pcmC0D0c:    2831m
/dev/snd/pcmC0D0p:    2831m
```

and killed the processes that used sound with

```
# kill -9 2831
```

Now it works again, but it would be nicer if it would work straight after booting.

---

### Post by me13221 on 2010-04-12
> **markbuntu said:**
> The reason why the pulse devs recomend against system mode is that it is a real security vulnerability. In system mode anyone on the network can control the local sound devices and the devs are not so keen on allowing that by default.

The reason that system mode is still available is because they realize that people want use it for just that purpose anyway so they kept it easy to do but not really obvious.


Wait- anyone on the *network*? that doesn't seem good.  I don't see why anything would have to be exposed on the network.

This is what I mean by begging the developers to 'support' it, rather than just leave a jumbled mess.  It's a very desirable feature.  

plus it is not without its bugs (see above).  bugs get fixed through official support channels.

I guess if I'm complaining, I should learn to code and fix things myself.

---

### Post by Daan on 2010-04-12
> **me13221 said:**
> Wait- anyone on the *network*? that doesn't seem good.  I don't see why anything would have to be exposed on the network.

I have an option "Enable network access to local sound server" under "Configure local sound server" which is unchecked by default I think.

---

### Post by Daan on 2010-04-12
> **Daan said:**
> only "Dummy output" in the pulseaudio Volume Control and no sound

I unchecked "Use audio device" under "User Privileges" and now I don't have this problem anymore.

What are these "User Privileges". Are they just a confusing way of managing groups?

---

### Post by wgandhi on 2010-11-27
Opened up a terminal and typed padevchooser.
It put an applet in the system tray
In the applet, I clicked the option which got the padevchooser module started per session.
Dont have problem with multi-users and pulse audio anymore.
Cannot explain why that fixed it... just thought I would share in case anyone knows why this works.

---

