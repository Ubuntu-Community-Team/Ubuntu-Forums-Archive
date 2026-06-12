---
title: "laptop battery serves less than an hour!"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sallam on 2010-09-25
Greetings
My laptop used to keep working for about 2 hours in win7. But now in ubuntu it stays for about 55 minutes only. And it shuts down on me without a pre-warning of any type. Is that's how it is in ubuntu?

I also noticed that in Power Managemnt, I can dim the display with a slider in AC setting, but there is no slider in battery setting..

---

### Post by mörgæs on 2010-09-25
If you are on 10.10, you will be better off in this forum:
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by philinux on 2010-09-25
Moved to Maverick forum.

---

### Post by sallam on 2010-09-25
thanks for moving my question to the right place.

---

### Post by teh603 on 2010-09-25
Its possible that its the battery itself, and not a misconfigured power manager. Despite what hardware manufacturers in the '90s told you about LiIon batteries not needing to be deep discharged, they need it anyway.

---

### Post by FuturePilot on 2010-09-25
> **teh603 said:**
> Despite what hardware manufacturers in the '90s told you about LiIon batteries not needing to be deep discharged, they need it anyway.

[No they don't.]("http://www.batteryuniversity.com/parttwo-34.htm")

---

### Post by InphekD on 2010-09-26
what video card you have? if oss and ati - you should search the forum & internet for "ati dynpm"

---

### Post by P4man on 2010-09-26
> **InphekD said:**
> what video card you have? if oss and ati - you should search the forum & internet for "ati dynpm"

that.
Im guessing an ATI videocard using the opensource drivers which do not support powermanagement yet. Proprietary drivers for 10.10 arent out yet (but neither is ubuntu 10.10, its beta for a reason).

---

### Post by KdotJ on 2010-09-26
My laptop battery is the same... and not just with Maverick. Since I started using ubuntu, since 9.10, it never lasts more then 40mins and just shutdown with no warning. Like yours, my battery easily lasts 2 hours under windows 7. 

It's a pain, one way I've learnt to combat it a bit is to use powertop from intel

```
sudo apt-get install powertop
```

Let it install and then run it as sudo

```
sudo powertop
```

It will collect data for 5 seconds and then show you what is consuming power and CPU interrupts. It offers suggestions on what to do and disable. It has easy "press b to do this..." instructions. I got my laptop to last about 1 hour 20mins

---

### Post by teh603 on 2010-09-26
> **FuturePilot said:**
> [No they don't.]("http://www.batteryuniversity.com/parttwo-34.htm")So explain to me why iPods and other devices still show the battery memory effect after numerous partial discharges, just like the old NiCad and NiMH batteries did?

---

### Post by cyberkilla on 2010-09-28
> **teh603 said:**
> So explain to me why iPods and other devices still show the battery memory effect after numerous partial discharges, just like the old NiCad and NiMH batteries did?

It says in the link he posted (which I've read before) that they don't have a memory effect. They do need calibrated occasionally, however. There's a little circuit board that manages the battery cells, and it can become inaccurate over time.

The site he posted says you should give it a full discharge cycle every 30 normal ones...

> # Batteries with fuel gauge (laptops) should be calibrated by applying a deliberate full discharge once every 30 charges. Running the pack down in the equipment does this. If ignored, the fuel gauge will become increasingly less accurate and in some cases cut off the device prematurely.

I wonder what causes it to lose accuracy. Surely not rounding errors :P

---

### Post by HeWhoE on 2010-10-07
I have a similar issue with my Toshiba A85-S107 laptop, for which I recently started using a new 12-cell battery. It has an ATI Mobility RADEON 9000 IGP.

When I bought the battery about a month ago, I was still using 8.04. The battery lasted 4 hours. Then I upgraded to 10.04 about three weeks ago. Again, the battery consistently lasted about **4 hours**. Everything was great under 10.04 except for issues with the touchpad sporadically ceasing to function. Suspend also didn't work, but it had never worked before.

So, this weekend, I upgraded to the first RC of 10.10. It fixed the touchpad issues, and I even had Suspend working correctly for the first time ever. But I immediately noticed the battery life degrade to about **2 hours**. And, this evening, it lasted only **one hour**!

---

### Post by inportb on 2010-10-08
It's not memory effect if the "memory" can't be recovered. Quite simply, even Li-ion and Li-po batteries wear out over time, especially under conditions of unusual heat (as is common with computers). And there's the calibration thing.

---

### Post by HeWhoE on 2010-10-08
In my particular case, I suspect the dramatic drop in battery discharge time from 4 hours to 1 hour over the course of two days isn't due to wear. 

If I have time, I'll reinstall 10.04 this weekend and time the complete discharge of the battery after it's fully-charged. I'll report back then.

Cheers!

---

### Post by sallam on 2010-10-08
> **HeWhoE said:**
> If I have time, I'll reinstall 10.04 this weekend and time the complete discharge of the battery after it's fully-charged. I'll report back then.

That would be really interesting to know..
I hope this is fixed in the 10.10 release version.

---

