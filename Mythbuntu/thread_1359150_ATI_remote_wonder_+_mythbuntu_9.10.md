---
title: "ATI remote wonder + mythbuntu 9.10"
date: 2009-12-19
forum: Mythbuntu
---

### Post by tfwarlord on 2009-12-19
Hey, i have resently installed mythbuntu 9.10, and during the install where i can select my ATI RF 1 (remote wonder), it worked just fine, but when the install has completed only the "arrows" work, so i go to check out the setup, and it is gayed out (under IR option); so i try and reselect it and i cant.
Everytime i try and reselect, the combo gays out and returns to the default none selected status. after i have enteret my password.. The arrows only works some time, and NEVER after the pc has been woken form sleep. The wonder drivers is always gayed out though.... Does anyone have a fix for this?


ps. i have tried to reinstall the entire os several of times, and i always get the same result. plz help

---

### Post by tfwarlord on 2009-12-20
Come on i cant be the only that have this problem??

---

### Post by blackoper on 2009-12-20
I'll let you know. I didn't have problem with the remote wonder in 9.04 but I recently upgraded my sister's box and have not tried getting the ati remote wonder working yet. I believe last time i just added the ati remote module in /etc/modules to have the driver load on startup

---

### Post by tfwarlord on 2009-12-21
> **blackoper said:**
> I'll let you know. I didn't have problem with the remote wonder in 9.04 but I recently upgraded my sister's box and have not tried getting the ati remote wonder working yet. I believe last time i just added the ati remote module in /etc/modules to have the driver load on startup
and how do you do that? i am a total linyx noooob.. I only checked it in Mythbuntu Control Center under IR (and it keep graying out there)


UPDATE:

I discovered the error..
When i do Hybernate while in S3 it go save to disk (sleep goes save to ram). When i go to Save do disc, for some reason i got promted by login (locked out), after i have logged in, even though i am in frontend mythtv, the remote dosent read it like "In mythtv application" (proberly due to the lock out)... How can i avoide the loggout while going to save to disk?


and btw how do i bind poweroff / hypernate to the power button... I have found the location of the config, but i cant get it to work.
i use this 
begin
    remote = ati_remote_wonder_rf
    prog = mythtv
    button = power
    config = echo disk >/sys/power/state
    repeat = 0
    delay = 0
end

ps. When i execute this commands in terminal, it can never be reawoken (and it dosent matter if i raite mem instead of disk), but if i do a hybernate or standby otherwise i have no problem??

---

