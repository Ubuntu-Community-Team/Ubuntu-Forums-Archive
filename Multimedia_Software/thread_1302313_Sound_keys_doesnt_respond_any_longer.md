---
title: "Sound keys doesnt respond any longer"
date: 2009-10-26
forum: Multimedia Software
---

### Post by Dreadlock man on 2009-10-26
Hi all,

I've been trying to get  the Internal Mic to work in my HP Pavilion  dv4-1114. I've made some changes  in the alsa-base.conf file and the client.conf(/etc/pulse directory) and nothing  changed, so I rollbacked the files. But when I did this, I found that the touch-sensitive keys that managed the volume level didnt work any longer. The wierd thing, is that they actually change the level of the Icon in the gnome panel, but the "Master" slider in the volume settings of HDA ATi SB (Alsa Mixer) doesnt change at all, and I have to change the volume manually in the control panel, which is very annoying. Is there a setting to solve this? Reinstalling pulse audio maybe?. I'd like to make a clean start and install all the audio application again, but I dont know what they are and how to configure them properly. I'll be very gracefull with any comment or idea that you can give me. Thanks

PS: sorry about my english

---

### Post by Dreadlock man on 2009-10-27
I've found where the problem was. Apparently I played with the configuration settings more than I should..... In System>Preference>sound there's a dropdown menu where you select the mixer device. It should be "HD ATI SB(alsa mixer)" and it should be marked the "master" option in the list below. By mistake I changed the previous value into (capture: monitor HDA...), so thats why the keys didnt respond.  Well I'll keep messing things around until I get the Internal mic to work :D... bye

---

