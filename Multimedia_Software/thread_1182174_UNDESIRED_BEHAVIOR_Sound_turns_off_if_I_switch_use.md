---
title: "UNDESIRED BEHAVIOR: Sound turns off if I switch users."
date: 2009-06-08
forum: Multimedia Software
---

### Post by wubrgamer on 2009-06-08
I am running jaunty.

If I am playing music with totem or VLC, when I switch users, or switch tty sessions (i.e. Ctrl-Alt-F1) to a session that I am not currently LOGGED INTO, it will turn off.

I wish to disable this behavior and make it such that audio will continue to play no matter which tty session is active or which user I am logged into (I believe the "switch user" functionality in GDM or GNOME switched tty sessions)

Can this be reconfigured? What do you believe may be causing this "problem"?

Is it pulseaudio? ALSA? my sound card? I do not recall this behavior (although I may just be wrong) with prior versions of *buntu, and I've been running *buntu on this machine since 5.10 or so.

---

### Post by markbuntu on 2009-06-08
It is pulseaudio. It does not run as a systemwide daemon by default for security reasons. That said, and just so you know there are security concerns with doing this, you can configure pulseaudio to run systemwide very easily by editing the etc/pulse/daemon.conf file. Uncomment and change this line like this

;system-instance = no

to

system-instance = yes

and restart pulseaudio.

---

### Post by wubrgamer on 2009-06-08
> **markbuntu said:**
> It is pulseaudio. It does not run as a systemwide daemon by default for security reasons. That said, and just so you know there are security concerns with doing this, you can configure pulseaudio to run systemwide very easily by editing the etc/pulse/daemon.conf file. Uncomment and change this line like this

;system-instance = no

to

system-instance = yes

and restart pulseaudio.

What "security concerns" are there?

I'm confused.

Shouldn't it just run in the background?

---

### Post by markbuntu on 2009-06-09
When you run pulseaudio as a system instance then all users are able to load and unload modules, control the volumes etc. This is not a big concern with single user systems but can be in multiuser systems.

---

