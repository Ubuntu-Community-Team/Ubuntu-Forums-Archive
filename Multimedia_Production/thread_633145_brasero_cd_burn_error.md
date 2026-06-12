---
title: "brasero cd burn error"
date: 2007-12-06
forum: Multimedia Production
---

### Post by eotakos on 2007-12-06
Hi! i've just burned a cd from .iso file in brasero.  everything seemed to be going well, untill the error message at the end.  actually i'm not sure if the burn was completed or not. -by the way is there any tool to check the cd for errors? - because the cd seems to be working fine... and if the cd is fine, then why the error message?...    anyone had this problem before?   you think i should switch to k3b or something else?

thanks for you time

---

### Post by disturbed1 on 2007-12-07
Depends on what the error message was :)

Could of just been something simple. Like Brasero ejected the CD at the same time Gnome was attempting to mount it. So you'd get a could not mount the volume error.

To check the quality of a cd you should install cdrecord
```
sudo apt-get install cdrecord
```
Or use Synaptic if you don't like the CLI.

Once cdrecord is installed, it comes with a utility called readcd. This is a CLI program (runs in the terminal) as root only. Use ***sudo readcd -c2scan*** to perform a C2 error scan.

Readcd is also able to do pif and pisum8 scans on DVDs.

---

