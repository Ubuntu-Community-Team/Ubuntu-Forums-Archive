---
title: "Installed the wrong ALSA driver"
date: 2009-09-18
forum: Multimedia Software
---

### Post by DnjS on 2009-09-18
Ok, so I've been trying to get Skype up and running but have had problems with the audio playback. Somewhere I got the tip to update my ALSA driver and everything would work out. When googled on, I found a script that proposed to do that very thing. Problem is, when I rebooted all of my sound was gone! I've only been using Ubuntu for approximately a year so I still do silly mistakes like this. Could anyone please tell me how to atone my sins and revert my error? The script is from this page: [http://www.stchman.com/alsa_update.html]("http://www.stchman.com/alsa_update.html") I'm on a standard Samsung NC10


:KS

---

### Post by scrooge_74 on 2009-09-18
I wonder if you read what was in the file, it starts by saying is a script from 2007, do you have the same board or similar? Anyway

start by removing what ever you installed, go to synaptics and remove alsa and remove what you downloaded. I think you should have a section title local or obsolete, I think you should have something there to remove.

Then after you take out everything that has to do with alsa, reboot, then reinstall alsa using synaptics dont go downloading stuff like that, no need.

Then post back

Edit: I just checked again even the drivers that the script downloads (from this guys website) are outdate, those are ver 1.0.16, even my Lenny system is using newer drivers.

---

### Post by DnjS on 2009-09-18
alsa-util and alsa-base has been completely removed, then I rebooted the system and installed them again. unfortunately no change.

So if I got old drivers, shouldn't there be a way to update them fairly easily?

---

### Post by scrooge_74 on 2009-09-18
Not necesarly cause you manually installed them not using synaptic.

Now that you have your system back in order, lets get a few things first since skype is tricky sometimes.

Can you have any sounds coming from music, a video, etc? If you say yes to that then we can continue on to solve your skype issues

---

### Post by DnjS on 2009-09-18
unfortunately, I have no sound what so ever except the tiny pc-speaker that just goes beep. :P

I don't think the reinstallation of those packages really did the trick sadly.

---

### Post by scrooge_74 on 2009-09-18
Next step would be for you to check this:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

There is also something here [http://ubuntulinuxtipstricks.blogspot.com/2009/01/jaunty-no-sound-outputs.html](http://ubuntulinuxtipstricks.blogspot.com/2009/01/jaunty-no-sound-outputs.html)


You could be having problems with pulse audio, you could try desabling or removing it and let alsa manage sound at present

---

### Post by DnjS on 2009-09-18
ok, so I think I just had a minor breakthrough, when I started fiddeling with the sound troubleshooting I spotted that I have no driver for ALSA installed or even a loaded alsa module! Take a look at this which I got from a command from the troubleshooting site: [http://www.alsa-project.org/db/?f=91619ee33cae283bdee6b4db3e552b14c180a5cc]("http://www.alsa-project.org/db/?f=91619ee33cae283bdee6b4db3e552b14c180a5cc")

---

### Post by DnjS on 2009-09-18
Ok, got it working by entering the command "*sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2*" which basically re-installed the whole alsa deal.

Thank you very much for your quick support! :D

---

### Post by scrooge_74 on 2009-09-18
Nice to hear you made it, in future try to stick to repositories and to synaptic, 99% of solutions and applications you need are there.

---

