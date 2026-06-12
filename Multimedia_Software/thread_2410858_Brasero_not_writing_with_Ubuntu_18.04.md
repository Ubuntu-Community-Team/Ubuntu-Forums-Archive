---
title: "Brasero not writing with Ubuntu 18.04"
date: 2019-01-21
forum: Multimedia Software
---

### Post by Richard_York on 2019-01-21
Hello.
I've just tried burning CD's with Brasero on both desktop and laptop machines, both running on 18.04. (I installed this using different downloads for each machine.)

First Brasero accepted and set up the playlist, accepted the CDR, then when I pressed "Burn" the dialogue came straight back with "Ejecting" and an unwritten disc popped out.

 I copied the tracks onto the Desktop, and worked from there. It went through all the burn process, from simulation to final burn,  ejected it at the end, told me the CD had burned successfully... but it was still blank. 
The same with the laptop machine.

It's no better with making a data disc - same result exactly, it pretends to do the whole thing, but pops out a blank CD each time. I used the same CDR's which worked fine with 14.04, which I was using previously. 

Thanks for any help. 
My technical jargon understanding is extremely limited, but I can follow simple instructions!

---

### Post by Autodave on 2019-01-21
Try *xfburn.*  It is in the repositories.  I have much better luck with that than Brasero.  Just be careful to note what size disc you are using: you need to input that on the main screen.

---

### Post by Richard_York on 2019-01-22
Thanks, I'll give it a go.

---

### Post by Richard_York on 2019-01-22
I tried xfburn. While it didn't ask me about disc size, & seemed to work that out for itself, it went through the whole process, made all the right noises... and once again produced a blank disc at the end of it. 
Maybe Ubuntu 18 doesn't like the discs which 14 was quite happy with?  I could get the disc writer checked, though it seems odd that two machines should have the same fault.
Any other suggestions will be welcomed, thanks.

---

### Post by scdbackup on 2019-01-23
Hi,  if the medium is blank after a normally performed burn run then the problem is most likely a failure of the drive or the medium and not a failure of the burn software.

> it seems odd that two machines should have the same fault.
  Is it surely the same problem with both drives ?

> First [...] when I pressed "Burn" the dialogue came straight back  with "Ejecting" and an unwritten disc popped out.
This is not the same behavior which you describe with the desktop drive. It could indeed be a software problem. Regrettably the GUI programs hide much of the burn backend messages from the user.  You could try more directly by a shell command like:

 ```
 xorriso -for_backup -outdev /dev/sr0 -map /some/small/directory/tree / 
```
 where /dev/sr0 is the device file address of your first CD drive. "/some/small/directory/tree" should be a path to a directory tree which is small enough to fit on the CD. 50 to 100 MB is enough for a realistic test.

  If burning seems to have succeeded, eject the drive tray and put it back in. Then run this command for checkreading:
```
 xorriso -for_backup -indev /dev/sr0 -toc -check_media -- 2>&1 | tee -i /tmp/xorriso_msg 
```
 The messages will not only show up on screen but also be collected in file /tmp/xorriso_msg. Please attach the content of this file to your report.

  Have a nice day :)  Thomas

---

### Post by newblank25 on 2019-01-24
i switched to xfburn. it works. i heard that software dev. must make some updates to work in Ubuntu 18.04. i also had problem k3b for recording.

---

### Post by LeeU on 2019-04-13
Thanks! Works beautiful!

---

### Post by speartip on 2019-04-22
Brasero needs some permissions changing to work properly. Make sure that cdrdao, wodim & growisofs are all installed then run:
```
[COLOR=#000000][FONT=Carlito]cd /usr/bin[/FONT][/COLOR]
```
then:
```
[COLOR=#000000][FONT=Carlito]sudo chmod -v 4711 cdrdao && sudo chmod -v 4711 wodim && sudo chmod -v 0755 growisofs[/FONT][/COLOR]
```
Brasero should now work perfectly.

---

