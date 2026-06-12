---
title: "[SOLVED] Sound dropping out on installs/updates/crashes"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by d41m40u on 2008-02-29
I have some sort of an issue where sound will occasionally stop working.  This happens most often after installing programs.  It also occurs, though infrequently, after updates to Ubuntu.  Finally it just recently happened when a program (Miro) crashed and I terminated it.  I can get sound functioning again by installing the ALSA driver from a Fresh Kernal (as per the instructions [[COLOR="Blue"]_here_[/COLOR]]("https://help.ubuntu.com/community/SoundTroubleshooting#head-d8ad2bdeea082f749845b766aa82831110042360")  followed by shutting down, removing the sound card, starting up, shutting down, reinstalling the card, booting up, and finally rebooting.  That seems to work every time, but it seems like a lot do to to fix what seems to be a sound driver crash or something.  I've looked around in the forums, and haven't seen anything similar so has anyone got any ideas?

Running Ubuntu 7.10

Looking through other posts I see that often output of some sort is requested depending on which command is run but, being a linux newb, I'm not exactly sure what would be most useful, and rather than gum up the board with extra unneeded junk, I ask that you tell me what output to post from which commands.  Thank you!
-D41m40u

---

### Post by erginemr on 2008-02-29
Please refer to my post here:
[http://ubuntuforums.org/showthread.php?t=710581](http://ubuntuforums.org/showthread.php?t=710581)

---

### Post by d41m40u on 2008-03-01
No sorry, that didn't seem to help at all.  What I did manage to do though is find a way to make it happen consistently.  I know now that I don't have to take out the card and reinstall it, etc.  All I have to do now is follow the directions I specified earlier and reboot twice.  In order to cause it to stop working, all I have to do is boot into Windows XP Pro and then back to Ubuntu.  The solution works every time and so does the break.  Any Ideas?

---

### Post by erginemr on 2008-03-01
Do you happen to have an onboard sound card as well? If so, does it work without problems when you remove the PCI sound card? Did you disable your onboard sound from BIOS? 

And what is the outcome of 
```
lspci | grep -i audio
```

---

### Post by d41m40u on 2008-03-01
I already know the integrated sound portion of my motherboard is dead, so that definitely would not work. I did check the BIOS though and it was set to auto-detect.  I switched it to Disabled and that does seem to have fixed the problem when booting between Windows and Ubuntu, time will tell if it affects the other problems.  Here I have posted to the output you have asked just in case:

00:0a.0 Multimedia audio controller: Fortemedia, Inc Xwave QS3000A [FM801] (rev b2)


I am going to mark this as Solved though as that seems to have done the trick.  Thank you for your help! :grin:

---

### Post by erginemr on 2008-03-01
Swweeeet! \\:D/

---

