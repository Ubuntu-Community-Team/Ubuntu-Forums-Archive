---
title: "Multimedia keys"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by bward1 on 2007-01-03
I have a microsoft wireless desktop elite keyboard and mouse (the only good stuff microsoft makes) and I would like to use the media keys.  I have already set things up in System -> Preferences -> Keyboard Shortcuts but that appears to be only half of the problem.  I think that the next step is to get the commands (play pause stop etc. ) interface with my media player, amarok.  As of right now play pause and stop do not work.  I wouldn't be surprised if those keys worked in rhythmbox, but rhythmbox has a very bad tendancy to crash on me so I can't really test it.

The mute button is also something that I would like to be able to use.  As of right now the volume up and down buttons work but the mute button doesn't.  The X comes up ontop of the speaker in the panel as if it were muted, but it actually isn't.  When I double click on that to bring up the volume control (Alsa mixer) it appears that the keyboard effects the headphone volume, which effects the overall volume, but to mute, the PCM (w/e that is) volume needs to be muted.  Is there a way that I could easily accomplish this?  btw I have a 5.1 surround sound system, I dont know if that makes a difference in anything.

the last issue which isn't as important to me, is the keyboard scroll wheel.  It is physically the same thing as the mouse scroll wheel, but it doesn't seem to work in ubuntu.  Any advice here?

Thanks in advance for any help.

---

### Post by haiku99 on 2007-01-03
see LadyDoors posts on multimedia keyboards in this thread, good info ....
[http://ubuntuforums.org/showthread.php?t=237408](http://ubuntuforums.org/showthread.php?t=237408)

reading that info enabled me to get multimedia buttons on my USB speakers working (including PCM mute), so I wrote a short howto 
that might also be helpful

[http://ubuntuforums.org/showthread.php?p=1482074](http://ubuntuforums.org/showthread.php?p=1482074)

---

### Post by bward1 on 2007-01-04
Thanks for that information, I know have a much better conceptual understanding of what I need to do, I just need a few things clarified first.

first the xev stuff

I was able to get the keycodes for play/pause, stop, next, and previous, but for some reason there aren't keycodes for the volume up, volume down, and mute buttons.  Also I saved the output to a txt file. 

```
rev > out.txt
```

 and then I proceeded by doing 

```
cat out.txt | grep keycode
```

 and it didn't return anything, so I know it isn't just me missing it.  That method worked for the other keys.  These keys both do things with the gnome settings, but I dont know how to find their keycodes.  Under the gnome keyboard settings thing, it says that volume up is XF86AudioRaiseVolume and the other keys have the proper names too.  Is there a way to find where the config files are to get at the keycodes that gnome is seeing that xev isn't.

Also, I dont have an .Xmodmap file.  I get the feeling that this file should have all the key binds for all the keys on the keyboard, so i dont want to make a new one and than have only media keys work.  Is there a default .Xmodmap that I should copy and then add as needed for the media keys, or should i just make a new one and only add entries for the keys that I want to configure?

Where should I go from here?

---

### Post by haiku99 on 2007-01-05
wish I could help, but I don't know nearly enough, am fairly new to Linux.......

---

### Post by ViRMiN on 2007-02-15
I've also got the Desktop Elite and on FC6 I used KeyTouch - [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

---

### Post by ViRMiN on 2007-02-15
Ace!  It's even packaged for Ubuntu :)  Guess what I'm installing right now!?

---

### Post by bward1 on 2007-04-15
I just tried keytouch and I think that it is imperative that I share my experiences.  I first installed the software (apt-get install keytouch) and then ran it.  I will admit that the software looks nice, and it even had a profile for my keyboard.  I looked through the different features but _DID_NOT_CHANGE_ANYTHING_ and some weird stuff started to happen.  First, about every five or ten keystrokes - didn't matter which ones - it turned the screensaver on, which of course was just annoying and obnoxious.  I decided I would just uninstall keytouch and just forget about it.  Now this is where things go really bad.  Somehow uninstalling keytouch uninstalled the keyboard itself (I don't even know how) and the keyboard stopped working.  Fortunately I was already logged into the system on a neighboring computer via ssh, so I tried to see what was going on, and heres what I got:```
ls
bash: /bin/ls: No such file or directory
```
I logged out and tried to ssh again and received this error message ```
Read from socket failed: Connection reset by peer
```
So now things aren't looking up.  I restarted the system and it wouldn't boot.  I then selected recovery mode, but that kernel paniced.  I then put in a live cd so that I could manually mount the partitions to see what was going on:  /bin/ and /etc/ were deleted entirely!  So as far as I can tell, my ubuntu installation is toast.  Fortunately all of /home is still good, so all my personal files are still ok.

All I can say is, I'm never using keytouch again!

---

