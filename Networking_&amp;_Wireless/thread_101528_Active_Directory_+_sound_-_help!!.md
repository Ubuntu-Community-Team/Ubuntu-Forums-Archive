---
title: "Active Directory + sound - help!!"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by zluka on 2005-12-10
i'm a power user in windows, but a newbie in linux. gone through many troubles and did manage to join my ubuntu box into the AD at work. i can log in and "sudo" with my AD user, so i thought everything is fine. :KS 

but i later realised this: "No volume control elements and/or devices found." everything is ok with my local user, so i guess i have a permission issue.. 

as far as i've figured, i should add my domain user into the "audio group", but i can't find it to add to the local groups.

or am i totally wrong? does anyone know any solution to this? "google"ing didn't help. :confused: 

any kind of help is appriciated.

thanx..

---

### Post by nesman89 on 2005-12-12
Bump!

same problem here.  local user sound is fine.  however when i log into windows domain my user has no sound.  i'm sure it's a permssion issue.  changed permission on /dev/dsp no luck yet. 

anyone?

---

### Post by nesman89 on 2005-12-12
alright found the solution. at this thread

[http://www.ubuntuforums.org/showthread.php?t=77469&highlight=sound+active+directory](http://www.ubuntuforums.org/showthread.php?t=77469&highlight=sound+active+directory)

but mine was slightly different than what was proposed.

i did

sudo adduser "username" audio

notice their is no DOMAIN or +(winbind seperator)

hope this helps.

---

### Post by zluka on 2005-12-13
thanx everyone for replies. i didn't guess it was that easy. :razz:

---

