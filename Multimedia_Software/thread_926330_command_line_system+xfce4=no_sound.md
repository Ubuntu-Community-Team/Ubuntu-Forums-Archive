---
title: "command line system+xfce4=no sound"
date: 2008-09-21
forum: Multimedia Software
---

### Post by Athanasius on 2008-09-21
I have installed a command line system from the alternate cd then I installed xfce4 (I don't want to install Xubuntu - I want something that uses less resources on my old laptop).

I installed gxine for videos but I get no sound.  Is there a package for sound that I am missing?  I have installed pulse but I still get nothing.  Can somebody help?

---

### Post by cariboo on 2008-09-21
Have you got alsa and alsa-utils installed. I just recently did the same thing except I didn't bother with the gui. Once you have alsa installed run asoundconf in a terminal as a regular user, this will give you a list of commands. here are some examples:

```
 asoundconf
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio
asoundconf set-oss PARAMETER
asoundconf unset-oss
```

next run 

```
asoundconf list
Names of available sound cards:
NVidia
U0x46d0x8da
SAA7134
```

Next 

```
soundconf set-default-card NVidia
```

Once you have run the above commands open alsamixer in a terminal and play with the sound levels while palying a sound file

Jim

---

### Post by Athanasius on 2008-09-22
Thank you, I will give it a try.

---

### Post by Athanasius on 2008-09-22
It worked.  Thank you.

---

