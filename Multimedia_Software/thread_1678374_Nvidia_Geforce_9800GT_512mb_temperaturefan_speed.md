---
title: "Nvidia Geforce 9800GT 512mb temperature/fan speed"
date: 2011-01-30
forum: Multimedia Software
---

### Post by runeh76 on 2011-01-30
Hi

I have been wondering, googling and testing (nvclock) to get FANSPEED control to my nvidia-control panel but my card doesnt support nvclock. I did add line (Option “Coolbits” “4&#8243;) to xorg.conf (using this [http://ncatarino.net/archives/573](http://ncatarino.net/archives/573) )but nothing happened. Should i use older drivers or what? Im worried about card temperature, no load and still 62-celsius and FAN only 35%. I know its not SO high temp but still, what i can do? BIOS dont have options for that, only CPU. I did take side-panel off and temperature drops 10C. I know that i could add extra-fan, but i wanna try first config fan-speed if its possible?

Thanx




Driver Version            : 260.19.29


GPU 0:
    Product Name        : GeForce 9800 GT
    PCI Device/Vendor ID    : 60510de
    PCI Location ID        : 0:4:0
    Board Serial        : 73366820241
    Display            : Connected
    Temperature        : 62 C
    Fan Speed        : 35%
    Utilization
        GPU            : 0%
        Memory        : 0%

---

### Post by runeh76 on 2011-01-30
LOL!! It seems that i have to solve my own thread again.

Founded another site, where guys talking about that "Coolbits 4"
Problem was that i copyed that code from the site, and there was (curly-quotes, not straight `"`s.)

So, i got it working like this:

Terminal
```
cd /
``````
cd etc/X11
``````
gksudo gedit xorg.conf
``` This to "Section Device":   ```
Option         "Coolbits" "4"
```Section "Device"
    
Identifier     "Device0"
       Driver         "nvidia"
   VendorName     "NVIDIA Corporation"
       BoardName      "GeForce GT9800"
       Option         "Coolbits" "4"
    EndSection

Save xorg.conf, close it and restart computer

Now i have FAN SPEED control under **Nvidia X Server Settings**
COOL!!     ):P

---

### Post by cchhrriiss121212 on 2011-01-30
I don't think there are any utilities for controlling GPU fan speed. Nvclock is buggy and only allows adjustment of fan times and not intensity.

Besides those temps are fine, I have a 9600GT and it runs at 61 C with 35% fan speed at idle, if put under any use the fan should speed up. Nvidia cards can run at up to 100C+ without damage.

---

### Post by runeh76 on 2011-01-30
Well my card maximum temperature is 105C. [http://www.nvidia.com/object/product_geforce_9800gt_us.html](http://www.nvidia.com/object/product_geforce_9800gt_us.html)
Yes i can run it over 100 BUT why should heating it, becouse i dont have to.


[URL="http://www.nvidia.com/object/product_geforce_9800gt_us.html"]

[/URL]

---

### Post by cchhrriiss121212 on 2011-01-30
> Yes i can run it over 100 BUT why should heating it, becouse i dont have to.Or because:
The temps you have are not dangerous
Increasing the fan speed will increase noise and power consumption
Setting the fan speed manually will stop it from dynamically changing with the temp

I'm not trying to criticise, it's just that other people worried about card temps will read this and think they need to change their settings when it is not necessary.

---

### Post by runeh76 on 2011-01-30
Yeah ur right about noise and that **temperature isnt dangerous** BUT its warm enough to me, and im still going to get extra fans for ventilation, now when i know what fan-speed did (max-speed drops 10C , but noisy)  :)
People makes their own decisions  ;) 

When summer comes, temperature goes much higher.
Cooler the better!

---

### Post by runeh76 on 2011-02-02
Did buy 2 extra fans today. 1 to take fresh air in, and one to blow warm air out. Now graphic-card temperature 52celsius. 
Im glad now   :-\"

---

### Post by j813 on 2012-11-11
Is there a way to activate GPU Clock adjustment?
Thanks

---

