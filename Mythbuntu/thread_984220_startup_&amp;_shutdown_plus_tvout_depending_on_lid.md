---
title: "startup &amp; shutdown plus tvout depending on lid (hp tx1000)"
date: 2008-11-16
forum: Mythbuntu
---

### Post by Cuppa-Chino on 2008-11-16
Hi,

I have a hp tx1000 laptop that I use as myth-tv front/backend (both).

the machine has a nvidia 6150 chipset igp. currently I do not automatically start the frontend,

Most things work if I operate the machine manually but the following are still problematic:

a) shutdown & wakeup:
i have followed the instructions here [http://www.mythtv.org/wiki/index.php/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm]("http://www.mythtv.org/wiki/index.php/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm")
and the manual test for setting the sys/class/rtc/... time works fine

I cannot get mythtv to operate automatically for me though - I have all   the scripts etc but am unsure how to do a nice test run to check the time is set correctly or how to fix this

it neither shutdown nor seems to set the start time

settings as per wiki:
```
 Integrate into mythTV

mythtv-setup settings for your script

Block shutdown: (checked, if you run frontend and backend on 1 machine)

Idle Timeout (seconds): 1200 (if you set this to 0, it will disable auto shutdown)

Max wait (minutes): 120

Startup before rec. (seconds): 600

Wakeup time format: time_t

Set wakeuptime command: sudo /usr/bin/setwakeup.sh $time

Server halt command: sudo mythshutdown --shutdown

Pre-shutdown command: sudo mythshutdown --check 
```

b) ideally I would like the laptop to check at bootup if the lid is open or not, if the lid is closed I would like tv-out to be activated and the resolution  set to 1024x768 (instead of display native 1280x800)

any idea how I do that? any help appreciated

having a macro that changes the setting with one click would be an alternative


PS : need to google this more but; 
c) sound does not work after resume suspend

---

### Post by Cuppa-Chino on 2008-11-23
bump especially how do I make a macro to set nvidia settings? I would at least like to set the nvidia screen res by click of one button shortcut

---

