---
title: "Looking for an amarok command"
date: 2008-05-17
forum: Multimedia Software
---

### Post by Cresho on 2008-05-17
I am looking for a command that launches amarok with project M

I will post the one I use for double clicking and launching an mp3 file through amarok and auto play.  I add this command to the right clicking of an mp3.  Now my amarok auto plays the mp3 when I double click an mp3.

amarok %q -p


Now I need to know what to add to the top launch projectM

---

### Post by denham2010 on 2008-05-17
Your post intrigued me, as I have previously tried ProjectM, but this was with Jack, and I had major issues just getting Jack to play nicely let alone getting ProjectM to run.

Now from the Sourceforge page, I have managed to flawlessly install ProjectM-pulseaudio, as I am now running Hardy, with Pulse working fantastically.....

.....anyway, I digress.....to the question at hand:

Now I myself am unfamiliar with setting up my own context menu items, but if it is simply a command you need to launch both Amarok and ProjectM, just add the following to your above command so it looks like this:

```
amarok %q -p & projectM-pulseaudio
```

This is assuming you have the pulseaudio version installed, if not, just change the projectM command as appropriate.

Cheers.

---

### Post by Cresho on 2008-05-17
thanks!  I was unable to execute it because I dont use pulseaudio.

I use alsa and tried various combinations on trying to execute it.  I tried various combinations like

amarokapp %q -p & amarok_libvisual & projectM

and to no effect, does not work.

any help please?

---

### Post by mc4man on 2008-05-17
here's an active thread of some users (more about compiling but they seem open to use ?'s)
[http://ubuntuforums.org/showthread.php?t=749793&page=7](http://ubuntuforums.org/showthread.php?t=749793&page=7)
i'm curious though why you set a specific command to set amarok as default for mp3's. At least here with gutsy and hardy just picking amarok from r. click, properties, open with, was sufficient

---

### Post by Cresho on 2008-05-17
when I use to double click on the mp3 file, It would put it into the playlist.  NOw when I double click, it plays it streight. so no need to use the playlist manager.  i can double click on next and next mp3 and it will autoplay it.  Of course, nautilus can play mp3 when you hover over an mp3 file but I preffered this method for some odd reason.

---

### Post by denham2010 on 2008-05-19
Hi Cresho,

You just need to use the command to start the 'flavour' of ProjectM you have installed. From what I understand, the command varies depending on the version installed, ie: one for pulseaudio, one for alsa, one for libvusual etc.

To find out the command you need to use, just open a terminal and type projectM then press TAB twice. This will give you a list of all commands that start with projectM.

Cheers.

---

### Post by Cresho on 2008-05-22
trying the projectM with tabbing it twice does nothing.  although typing amarok_libvisual in the terminal gives me an output of projectM.

Still looking for command.

---

### Post by struktured on 2008-05-22
There is no "command". projectM should show up in the list of libvisual plugins when amarok is running. If it doesn't, then you have an installation problem or there is a bug with projectM.

The only time a command is applicable is when you run projectM in a standalone fashion, such as pulse audio, jack, or projectM-test.

- struk

---

### Post by Cresho on 2008-05-22
ohh well, then Ill need to try projectM pulse audio

thanks!

here is the projectM-pulseaudio install tutorial  [http://ubuntuforums.org/showthread.php?t=749793](http://ubuntuforums.org/showthread.php?t=749793)

---

### Post by Cresho on 2008-05-22
Here is an update!  I installed pulse audio and no it will not detect beats with alsa as the primary output plugin for amarok.  If I change this to pulseaudio and restart it, It works in detecting beats but pulseaudio does not output in 5.1 audio.  It sounds terrible-well if i was using 2.0 it be great but 5.1 audio on a THX system is like cherries and ****!.:popcorn:

Any Help in configuring the pulseaudio 5.1 would be appreciated.  I found a few sites but I actually ran out of time looking further and ill try later.  But would be glad of a help of a quicky tutorial.

---

### Post by Cresho on 2008-05-22
Nevermind!  I found it

sudo gedit /etc/pulse/daemon.conf

Uncomment the line containing:

    default-sample-channels = 2 

and replace &#8216;2&#8242; with &#8216;6&#8242;.


thanks all for pointing me in the right direction!  I placed thank yous' to everybody who helped.

reboot

---

### Post by Cresho on 2008-05-22
HMMM!

Still looking for a command.  If i do a amarok & projectM-pulseaudio in the terminal will run fine but amarok %q -p & projectM-pulseaudio will not launch projectM-pulseaudio at all but amarok does play.

Anymore help will be appreciated.  Now at least i have projectM launching when I launch amarok :) :( :confused:

---

