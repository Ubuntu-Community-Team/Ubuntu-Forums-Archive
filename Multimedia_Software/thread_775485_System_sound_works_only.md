---
title: "System sound works only"
date: 2008-04-30
forum: Multimedia Software
---

### Post by madad2005 on 2008-04-30
Hi,

I am using the ALSA drivers and using onboard sound drivers at the moment. When I start up ubuntu, close down and test the system sound options, I get sound through fine. However, if I try to play sound from a videoor mp3, nada. I downloaded all the codecs I think i need.

Any ideas?

---

### Post by Wee Aldo on 2008-04-30
I have the exact opposite problem, I can't get the system sounds to play, but I can get mp3 DVD music cd's to work. So maybe someone will post a solution for both our problems, they must be related.

---

### Post by Gunman1982 on 2008-04-30
Which program are you using to play video or music? totem? amarok? are you using the sound daemon esd?

Is your soundcard able to do hardware mixing? If not than you have to configure each program to use either a sound daemon (i.e. esd) or configure alsa to do software mixing (more work but runs better imho).

You can find out if esd is running by executing the command
ps aux | grep esd
in a shell

---

### Post by Wee Aldo on 2008-04-30
Thanks all...

got this instruction from another post...

sudo apt-get install esound...

and now I can get the login, logout and startup sounds.

---

