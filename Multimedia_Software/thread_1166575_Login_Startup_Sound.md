---
title: "Login Startup Sound"
date: 2009-05-21
forum: Multimedia Software
---

### Post by bstanley on 2009-05-21
Hi!
I am having problems with the Login Startup Sounds.

The very first user (no matter who) that logs in the system after
the computer is booted up will get the familiar Ubuntu start up sound.

After logging out of this first user session, all other logins will not
get the login startup sound until the machine is rebooted.

Even if you login again as the first user id that got the startup sounds,
they will not work.

The first bird gets the sounds and that is all  :(

Does anyone know if there is a fix for this?

---

### Post by bstanley on 2009-05-21
I forgot to mention that I am using  Ubuntu  9.04.

---

### Post by bstanley on 2009-05-22
No one has any ideas on this?

If it helps,  lsmod shows that my system is using ES1371 Ensoniq for
the sound card.

It is a true SoundBlaster card from about 6 years ago or so.

I generally do not have any sound card problems with it with any
version of Linux.

---

### Post by bstanley on 2009-05-22
Well, here's another clue for you all ;)

I just found out that when I log out of my user Id (bruce) and I do a CTRL-F1
and log in as another user and execute the following command:

   ps -ef | fgrep bruce

the following process is left running:

   /usr/lib/evolution/evolution-date-server-2.26 
       --oaf-active-id=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2
       --oaf-iorfd=29

If I kill this process  (sudo kill 7188,  notice with out -9),

I can then log in again (2nd, 3rd, fourth, time etc.)  with the 
Gnome Startup sounds working again.

Anyone have a clue as to why this process is left running after the
first  login/logout  ????

---

### Post by bstanley on 2009-05-25
No body is having this problem?

After further trials and errors the temp fix of my last post was found not to always be 
a solution.  Sometimes it works, sometimes it doesn't.

Sound effects always works with the first login.

Additional logins are iffy.

---

### Post by bstanley on 2009-05-26
I still can't believe that no one is having this problem with Jaunty.

I read the Ubuntu forum how to fix Pulseaudo, and I created the following
script that I can run from a launcher after logging in:

script called:  fixaudio
    #!/bin/ksh
    #
      pulseaudio --kill
      sleep 5
      pulseaudio  --start
      echo
      echo "restarted pulseaudio <Enter> \c"
      exit 0


This does get the sounds working again after logging in.

Why should I have to kill and restart pulseaudio to get my sounds back?

Is there a configuration file somewhere that is not being set right?

---

