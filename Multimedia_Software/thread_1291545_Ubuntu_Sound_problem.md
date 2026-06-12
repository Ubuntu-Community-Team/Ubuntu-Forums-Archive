---
title: "Ubuntu Sound problem"
date: 2009-10-14
forum: Multimedia Software
---

### Post by felixvah on 2009-10-14
I have a Ace Aspire One the sound works for for a while and now it's not working at all.  When I shut down and restart I can hear the log on and log out sound, but when I play music, youtube or video there's no sound at all.  What did i missed?  Any ideas.. please help.

---

### Post by rippin on 2009-10-14
> **felixvah said:**
> I have a Ace Aspire One the sound works for for a while and now it's not working at all.  When I shut down and restart I can hear the log on and log out sound, but when I play music, youtube or video there's no sound at all.  What did i missed?  Any ideas.. please help.

You didn't tell us about the Ubuntu release, sound system, kernel or hardware, but look at the sound problem by trying to play one from a terminal or reading .xsessions-error file after trying to play a sound event for something along the line of "device busy". If it is due to esound being busy with another device, it may be necessary, as it was for me, to release the device by adding to /etc/esound/esd.conf the following:

"=-as 1" to this line "default_options"

so it looks like this

# default options are used in spawned and non-spawned mode
default_options=-as 1

The total esd.conf looks like this with the added portion

[esd]
# autospawning is not recommended, since it can't really be done
# right.  If you want your login session to be using a sound daemon,
# you should start it from the session controller, not some random
# app inside.
auto_spawn=0
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-as 1

---

### Post by tuxxy on 2009-10-14
Check all the volumes up in alsamixer, run in terminal
```

alsamixer
```

---

### Post by felixvah on 2009-10-15
Rippin,

Ubuntu release? I have Ubuntu 9.04.  I'll try what you've suggest and see what happen.  I'll post it later if it's going to work or not.

hmmm.. I'm pretty new to ubuntu. How would I get to /etc/esound/esd.conf??

---

### Post by rippin on 2009-10-15
> **felixvah said:**
> Rippin,

Ubuntu release? I have Ubuntu 9.04.  I'll try what you've suggest and see what happen.  I'll post it later if it's going to work or not.

hmmm.. I'm pretty new to ubuntu. How would I get to /etc/esound/esd.conf??

Open a file manger and look at the folder etc, then goto folder esound and open it, then edit the esd.conf file - only root can alter it. Or, open a terminal and enter

sudo <editor of your choosing> /etc/esound/esd.conf

Examples would be 

sudo nano /etc/esound/esd.conf
[INDENT]or
[/INDENT]sudo gedit /etc/esound/esd.conf

Unless you don't use sudo - I don't have it installed. Then we'll have to go over that. Chances are, tho', you use sudo.

HTH,

---

### Post by felixvah on 2009-10-15
I've tried what've you suggested and now even the start up and log out sound didn't work.  What's next?

---

### Post by rippin on 2009-10-15
> **felixvah said:**
> I've tried what've you suggested and now even the start up and log out sound didn't work.  What's next?

You said you had sound briefly in your first post. That eliminates volume being too low, and we know that the sound server was available. It's not an unusual problem that the esound server takes control of the sound device and when another program needs "sound", YouTube for instance, it has no control since the server is owned by esound; therefore, no output. The edit releases esound ownership of the sound device after 1 second once the audio file completes.  That was my reasoning for the edit.

Please double check you did the edit **exactly** the same as posted to the same file listed as root. Also, I'd like you to confirm you edited it with one of the steps I mentioned. If all is right, you should **undo** the suggestion I made.

I need more information. Try those steps for gathering error messages I first wrote you and report here.

Thanks,

---

### Post by felixvah on 2009-10-18
Sorry I had internet connection issue an wasn't able to be here as I should be.  Here's what I have on the /etc/esound/esd.conf

[esd]
# autospawning is not recommended, since it can't really be done
# right.  If you want your login session to be using a sound daemon,
# you should start it from the session controller, not some random
# app inside.
auto_spawn=0
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-as 1

I think it's exactly as you have above.  But why I have sound when the computer restart, logout, log on and not anywhere else, such as youtube, mp3, google video and etc.. I even try to play the same sound as log out and log sound on vlc and but it didn't work once I'm on the desktop.  Any ideas.

---

