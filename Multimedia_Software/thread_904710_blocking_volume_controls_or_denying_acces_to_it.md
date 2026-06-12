---
title: "blocking volume controls or denying acces to it"
date: 2008-08-29
forum: Multimedia Software
---

### Post by bigdee973 on 2008-08-29
i have an annoying teenager n the house that does not know difference between being loud and being utterly obnixous with his music.  how can i block his computer from gaining access to volume control and adjusting the volume?  I have adjusted the volume for him in an approriate tone.thats suitable for this house and i have right clicked the volume control and removed it from panel.. however im afraid he will find a way to adjust and install the volume control back on and wreck havoc once again with his music.  can someone please help? is there any kind of hack that will make him get a permission denied or better yet application is not installed or something in that manner that will give him absolutely no access to the sound volume? of course i know his password because i created the system for him so installing, uninstalling or modifying his computer is no problem...can someone please help. and also how can i adjust the bass and treble? i have looked in the preference section of volume control and see nothing for bass and treble i read on forums and they said click and choose tone but there is no such option...im using ubuntu 8.04

---

### Post by bigdee973 on 2008-09-01
does anyone at least know how to mute or turn off the sound through a terminal command?

---

### Post by kpkeerthi on 2008-09-01
```
amixer set Master mute
```
```
amixer set Master 60%
```

---

### Post by bigdee973 on 2008-09-01
> **kpkeerthi said:**
> ```
amixer set Master mute
```
```
amixer set Master 60%
```

Awesome thank you so much.  HEY, do u know how i could elminate sound entirely on startup or on the system entirely?  but the info you gave me does help alot thank you

---

### Post by kpkeerthi on 2008-09-02
> **bigdee973 said:**
> Awesome thank you so much.  HEY, do u know how i could elminate sound entirely on startup or on the system entirely?  but the info you gave me does help alot thank you

**To mute sound for all users:**

1. Open /etc/rc.local
```
gksudo gedit /etc/rc.local
```
2. Add this line to the end of the file
```
amixer set Master mute
```
3. Save & Exit. Reboot.

**To mute sound for a particular user:**
1. Login to gnome
2. Go to System -> Preference -> Sessions -> Startup Programs.
3. Click Add
4. Add ```
amixer set Master mute
``` to **Command**
5. Reboot.

---

### Post by bigdee973 on 2008-09-03
> **kpkeerthi said:**
> **To mute sound for all users:**

1. Open /etc/rc.local
```
gksudo gedit /etc/rc.local
```
2. Add this line to the end of the file
```
amixer set Master mute
```
3. Save & Exit. Reboot.

**To mute sound for a particular user:**
1. Login to gnome
2. Go to System -> Preference -> Sessions -> Startup Programs.
3. Click Add
4. Add ```
amixer set Master mute
``` to **Command**
5. Reboot.

thank you this will set the volume to an apprioate tone thank you very very very much.  ALSO just to be a schmuck here how can i eliminate the VOLUME CONTROL from appearing as one of the options to install on the 'add to panel' display?

---

