---
title: "No volume control GStreamer plugins and/or devices found."
date: 2008-11-07
forum: Multimedia Software
---

### Post by linux_beginner on 2008-11-07
Hi!
i've just upgraded my ubuntu 8.04 to 8.10 and when it has finished ,now there s no sound, or card sound device detected too.
when i  click on volume control from panel it says:
> No volume control GStreamer plugins and/or devices found.
  
so please any help?
thnx

---

### Post by AmandaKerik on 2008-11-08
In some ways I'm glad to not be alone in this, in other ways... it sucks.

I've tried this: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Including "Getting the ALSA drivers from a *fresh* kernel" and just beyond. 

I don't think I'm quite up to compiling my own drivers. It worked fine before I upgraded to Intrepid.

Ubuntu sees my audio card in the device listing, but doesn't (now) have drivers for it.

Thanks for your time and patience,
Amanda

---

### Post by Arger Wüterich on 2008-11-08
I encountered a similiar problem after updating my newly installed Intrepid Ibex system.

I would suggest that you look up if your user is in the group "audio",
```
groups
```
should give something like that:
```
audio adm dialout cdrom plugdev lpadmin admin sambashare

```

If the audio group is missing, try a simple: 
```
usermod -g audio YOURUSERNAME
```

This fixed the issue for me. Maybe a bug while performing new updates.

Greetings from Germany,
Arger Wüterich.

/edit: Don't forget to relogin/restart.

---

### Post by mahuyar on 2008-11-09
Thanks, Arger's solution fixed it for me.  Instead of using
```
 usermod -g audio YOURUSERNAME 
```
I had to
```
 sudo gedit /etc/group 
```
and add my username to the audio group.

Other thoughts:  I'm not sure why my username is not in the audio group.  Perhaps, pulseaudio should take care of that?  I'm not using pulseaudio atm, because I need to use WINE, and WINE's audio wouldn't play nice with pulseaudio.

---

### Post by user11 on 2008-11-25
usermod -g audio YOURUSERNAME doesn't work for me. All I get is "unable to lock password file"

---

### Post by hollowhead on 2008-11-26
Same as above same error message as above The group thing doesn't work for me as I have no dev/snd.  Any suggestions anyone?  My sound has always worked fine until ibex.....

---

### Post by Johari on 2009-03-19
> Hi!
i've just upgraded my ubuntu 8.04 to 8.10 and when it has finished ,now there s no sound, or card sound device detected too.
when i click on volume control from panel it says:
Quote:
No volume control GStreamer plugins and/or devices found.
so please any help?
thnx 

I had same problem....on dual boot win xp and Ubuntu 8.10. Sound card works in windows but not Ubuntu.   Same indications as above.

Solved by:
1.  downloading linux driver for Creative SB XFi from Creative web site to my /documents/downloads folder.
2. Select places menu and find the file in the downloads folder, right click file and select "extract here".
3. open terminal window and cd to the downloads folder.
4. type make (files are checked for correct parameters)
5 If make finishes ok then type make install and the driver is installed into Ubuntu.
6. I heard a light thump from my speakers as it installed.
7. Tested okay for playback but I havent tested with mike.....i believe that is still broke att

Dont ask too many complicated questions as I'm still just poking around linux trying to learn.  Hope this helps.

---

### Post by Akusai on 2009-04-12
Hi, I'm new to the forums and new to Ubuntu, and I'm having the same problem except it's been doing that since install. I'm dual-booting with Vista Ultimate and the sound is Creative X-fi on-board the MB. It works fine in Vista but not Ubuntu.

I added my username to the "audio" group, I installed the Linux driver from the Creative website, and the volume control still says the same thing.

Anyone else have another option? Thanks.

---

