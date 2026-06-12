---
title: "Flash player sound problems G930"
date: 2012-02-08
forum: Multimedia Software
---

### Post by xramses on 2012-02-08
Hello there!

I'm having a problem with the flash plugin on Firefox while using my headset, i hear nothing. Other applications like skype work perfectly but no matter of what the flash plugin do not. I'm using Xubuntu 11.10 fresh installation with all updates and the restricted content and a G930 Headset (USB-plugged).

I'm not sure if this is the right category if not I'm sorry.

I am thankful for every answer.

EDIT: I tested the same on Ubuntu there it works :|

---

### Post by xramses on 2012-02-10
/push

---

### Post by xramses on 2012-02-11
/push

---

### Post by winh8r on 2012-02-11
Hi,

Could you please post exactly which "flash plugin on Firefox" you are referring to?

---

### Post by xramses on 2012-02-12
The "real" flash plugin from the restricted content.

---

### Post by winh8r on 2012-02-12
Use this to begin with and see if it helps:


[http://ubuntuforums.org/showthread.php?t=1491268&highlight=flash+plugin]("http://ubuntuforums.org/showthread.php?t=1491268&highlight=flash+plugin")

---

### Post by xramses on 2012-02-12
Already done that but it wasn't changing anything.

Anyways I know now that it isn't the Flash Plugin which isn't working instead its something in the audio settings. Skype and vlc player are working fine but for example the default music player from xubuntu isn't. So I looked in the settings of vlc player and found out that he explicit set the output settings to alsa output Logitech G930 Headset.

I also found out that I changed the output device in my ubuntu installation and only after that it worked.

So I need to change that on xubuntu too and it will (hopefully) work but the I don't know were I can do this so I need help with that.

---

### Post by winh8r on 2012-02-12
If I understand correctly all you need to do is open vlc player
 click on Tools> Preferences

Then click on "AUDIO"

Then select the dropdown menu next to "output" type

and select whatever you want from there


close vlc

reboot 

and you should have sound


I hope!!

---

### Post by xramses on 2012-02-12
Yeah sure I already have sound on vlc but I need to change the default one from the system if I want get sound on Applications which don't have this settings for example flash player.

On ubuntu you can make this directly in the audio mixer but I don't know where I can make this in xubuntu.

BTW Reboot on Linux nearly never needed :)

---

### Post by winh8r on 2012-02-12
Ok, there is a solution posted here to Xubuntu which might work for you as there seems to be some issue with selecting soundcards and disabling others.

Give it a try and see if it works.


[http://ubuntuforums.org/showthread.php?t=1870596&highlight=sound+xubuntu]("http://ubuntuforums.org/showthread.php?t=1870596&highlight=sound+xubuntu")


I know that Ubuntu doesn't need to reboot like windows when altering settings, it is just something that I do to ensure that info about all changes gets to the right places before I complain that something "didn't work" !!!!


Hope this one works for you.


*****EDIT***** it is the solution by 4Orbs I am referring to

---

### Post by xramses on 2012-02-12
Hm still having no sound with the flash plugin but now with other applications.

Maybe I can fix this tomorrow.

---

