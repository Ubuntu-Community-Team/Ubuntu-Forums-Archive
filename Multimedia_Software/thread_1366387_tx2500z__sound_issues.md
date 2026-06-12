---
title: "tx2500z  sound issues"
date: 2009-12-28
forum: Multimedia Software
---

### Post by callummacdonald on 2009-12-28
hey there this is my first post on the Ubuntu forums that i can remember i used to use mint but i gave up because i had issues with my sound driver. yesterday i thought id install Ubuntu and see if it was any better ( i realize they are very similar os'). however i have spent the last 5 hours installing or trying to install drivers:(. i finished with most of my drivers about two hours ago and now i only have to work out why there is no sound at all coming from anywhere its worse than when i used mint because when i open the sound option there is not even a device listed. i was looking forward to being able to leave  Microsoft behind in favor of Linux but at the moment it looks like ill be forced to go back :'(. 
 neway ne help would be appreciated i realize there a lo of people with sound issues but ive tried all the supposed solutions i could to make it work but nothings changed 

thank for looking Callum

---

### Post by Favux on 2009-12-28
Hi Callum,

For a HP TX2500 do the following.

To the bottom of the file /etc/modprobe.d/alsa-base you add the following line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1

```
To edit the file you would use:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Since you have to be root when you edit it gksudo will do that.  It will ask for your password.  Gedit is gnome-edit.

---

### Post by callummacdonald on 2009-12-29
hey thanks for i tried it but i don't think t changed anything.

btw is it normal that the file i added the line to was empty??:S

thanks

---

### Post by callummacdonald on 2009-12-29
hey thanks for i tried it but i don't think t changed anything.

btw is it normal that the file i added the line to was empty??:S

thanks

---

### Post by Favux on 2009-12-29
Hi Callum,

My apologies, I forgot the name change that started with Jaunty.  Please see the post again.

---

### Post by callummacdonald on 2009-12-30
hey sorry i still don't hear anything any there is still no hardware listed in system>preferences>sound hardware.
on the bright side gksudo gedit /etc/modprobe.d/alsa-base.conf worked as in the file opened wasn't empty :D
if theres anything else you know that might work it would be really helpful but if not thanks anyway.

i'm going to try restarting now i'll let you know if it worked

hey sorry it didn't do anything

---

### Post by Favux on 2009-12-30
You're in Karmic correct?  Check in Hardware Drivers and see if you have the softmodem driver installed.  If so unactivate it and restart.

---

### Post by callummacdonald on 2009-12-30
hey sorry whats karmic ?
i'm using the latest Ubuntu 
is the softmodem he same as the software modem?

thanks

---

### Post by callummacdonald on 2009-12-30
:D:D:D:D thank you sooooooooo much finally working

---

### Post by Favux on 2009-12-30
Hi Callum,

Great, you got it!  :)  You're welcome.

You have to have tunes after all.

---

