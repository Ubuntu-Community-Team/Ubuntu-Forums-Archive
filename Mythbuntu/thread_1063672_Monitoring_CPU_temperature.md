---
title: "Monitoring CPU temperature"
date: 2009-02-08
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-02-08
Hi

Sorry if this is an obvious newbie question, but is there any way I can check the temperature of my CPU in Mythbuntu? I can check from the BIOS screens during startup, but I was wondering if there is a more convenient way?

Thanks
NM

---

### Post by ian dobson on 2009-02-08
Hi,

Have a look at lm-sensors, it includes the core-temp module for monitoring cpu core temperatures.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2009-02-08
Thanks Ian, that seems to do the job.

However, I'm a little confused: lm sensors reports 3 different temperatures, temp1, temp2, and temp3. Theres about 15-20C between the highest (temp2) and the lowest (temp1). temp1 and temp2 report "sensor = transistor" and temp3 reports "sensor = thermal diode".

Any idea how I can find out which is my CPU temp?

Also, is there any way of getting this information into the system status in Myth front end?

Thanks
NM

---

