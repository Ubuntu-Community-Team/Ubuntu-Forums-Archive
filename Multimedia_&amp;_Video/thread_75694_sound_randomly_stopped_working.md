---
title: "sound randomly stopped working"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by shelbydz on 2005-10-14
Hey guys, I'd been having trouble with my computer the last few days. Well it all boiled down to a burnt out DVD-RW. 

However, when I rebooted (after taking out the drive) my sound stopped working. The strange thing is, I didn't get any errors on boot up, all my games and stuff still work (they'd usually show if there a problem w/ the sound card). And Rhythm Box would open and run like it was playing mp3s. I checked the volume control to make sure that nothing was turned down or muted. Made sure the amp was on and the speakers plugged in, etc. In short, everything is how it should be, but no sound. 

I have the output of amixer posted here:
[http://paste.ubuntulinux.nl/3044](http://paste.ubuntulinux.nl/3044)
can someone please help me! this is a built in sound card on my Abit IC7 motherboard. Please lmk if you need more info.

---

### Post by deckard on 2005-10-29
Did you ever figure this out?? The same thing happened to me this week and I'm totally stumped! As far as I can remember, no major changes were made to the system or anything but after I booted up a few days ago the sound no longer worked. No errors or anything. I dual boot Windows and the sound still works fine on there.

The only other thing is that Synaptic is now giving me the following message when I load the package information:

> 
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatures were invalid: Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


---

### Post by Flame0001 on 2005-10-29
Same thing happened to me last night. I was listening to my music, went to sleep, woke up and rebooted my computer... then all of a sudden no sound. No errors that I can see anywhere...

Although my problem is most similar to Shelby's. I temporarily mounted a second harddrive last night, and it's not mounted anymore. And no sound now...

---

### Post by Flame0001 on 2005-10-29
This is the solution that worked for me, taken from the Hoary wiki:

Audigy 2 & ALSA

If you have ALSA set up with an Audigy 2 and everything "should" be working according to the manual, there is a chance that the following will fix it:

    *

      Run 'alsamixer'. If you have multiple cards, run it for the appropriate card, like in my case 'alsamixer -c 1'
    *

      Browse the channels until you find the "Analog/Digital Output Jack" and press 'M' to enable it if it's disabled

---

### Post by tom.vanlaere on 2005-11-20
Running the alsamixer worked for me too. I didn't found "Analog/Digital Output Jack" though, but I (re)enabled some channels made sense to me, and sound was instantly back.

thanks for the info.

Tom

---

### Post by fobitt on 2007-01-07
I had the same problem when using 6.06 and 6.10. After running automatix to install some software everything worked fine until I rebooted, then no sound. My sound card was not even being seen. It looks like some of the software I have installed required gstreamer-0.8.0 and that was conflicting with the default of gstreamer-0.10.  In order to fix it I simple deleted the $HOME/.gstreamer-0.8.0 folder. That seemed to keep gstreamer-0.8.0 from loading and stopped to conflict. Everything seems to be working great now.

---

### Post by obbimi on 2008-01-02
I had the same problem with 7.10 on my Dell Vostro 1700.
I was able to fix it to 'increase' the volume on the PCM 'entry' available when running 'alsamixer'.
Thx for the solution

---

### Post by VvWolverinevV on 2008-02-05
Does anyone know what causes this?  Increasing the PCM entry in alsamix only recovers sound in my left and right front speakers, not in my other speakers or my subwoofer.

*Edit*
I just needed to enable the side, center, and subwoofer channels by pressing 'M'.  It would still be nice to know why this happened so randomly.

---

### Post by VvWolverinevV on 2008-02-21
*Bump*

This happened to me again.  It seems like it might be related to the installation/configuration of WINE.  Anyone have any ideas?

---

