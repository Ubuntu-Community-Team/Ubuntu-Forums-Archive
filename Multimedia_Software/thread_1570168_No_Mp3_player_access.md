---
title: "No Mp3 player access"
date: 2010-09-07
forum: Multimedia Software
---

### Post by AcademiaX on 2010-09-07
I'm really new to Ubuntu (and to Linux in general), so this may be a dumb problem. Basically speaking, I have read-only access to my mp3 player. It doesn't show up in Rythymbox, and I'm not able to transfer anything new to it manually in /media. In /media it shows up as two entities, one with the name of the device and an mp3-player like icon (which does nothing) and it shows up as a usb0 filesystem. I'm not able to paste anything into it.

I've followed the instructions I've found, I've installed [COLOR=Black]the mtpfs and the mtp-tools pack[/COLOR]ages and enabled the plugin for it in Rythymbox. Any time I try to mount or unmount either of the devices showing, I get "umount: /media/usb1 is not in the fstab (and you are not root)."

Not sure where to go from here, any help would be greatly appreciated

---

### Post by tommcd on 2010-09-07
What brand and model name or number is your mp3 player?
On my Sandisk Sansa Fuze you have to set it the usb mode to msc (the default is mtp = Microsoft Transfer Protocol). After setting the Fuze to msc the player automounts on every linux distro I use.

And welcome to the Ubuntu forums!

---

### Post by AcademiaX on 2010-09-08
Thank you for your time, tommcd. I was able to change the usb mode to msc, but had the same results as before. The mp3 player is an RCA H125A

---

### Post by AcademiaX on 2010-09-08
*bump*
Any other suggestions? :[

---

### Post by tommcd on 2010-09-08
Try mounting and unmounting the device using sudo. See if you have write access to the mp3 player with sudo.

Sorry, but I have not found a better solution. Googling your <RCA H125A + Ubuntu> did not turn up much at all. If I find something more helpful I will post back.

---

