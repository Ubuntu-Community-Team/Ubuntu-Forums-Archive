---
title: "nvidia ignoring &quot;Coolbits&quot; Option"
date: 2012-05-29
forum: Multimedia Software
---

### Post by Swanmate on 2012-05-29
Hi,

I'm trying to get fan control working with an old GeForce 6600GT by adding 

```
Option "Coolbits" "4"
```

to my xorg.conf. This should unlock the fan control in nvidia-settings (and it does, working like a charm on another PC with the same driver version and a GTS450).

However, it doesn't on this PC. Changing the value to "1" or "5" also doesn't do anything. The fan is definitely controllable, setting the speed of the fan in Windows is working fine. nvidia-settings is also reporting the fan speed as "Variable", indicating that speed control is possible.

The fan is permanently at 100%, which is pretty noisy and gets really annoying after some time. I'd hate to have to change to Windows completely just because of the damn fan :frown:.

---

### Post by JLNemisis on 2012-06-16
> **Swanmate said:**
>  
The fan is permanently at 100%, which is pretty noisy and gets really annoying after some time. I'd hate to have to change to Windows completely just because of the damn fan :frown:.
 
 
Lucky you. Mine is stuck at 40% fan rpm and overheats really fast.
Can't make the changes to xorg.conf fast enough.
 
~Dev Team:
Here is an Idea. maybe. coolbits should be turned ON by default and
set to oh say 50%  that way the cards don't over heat before you can change any settings.
 
In windows 7 I had to install Precision X from Evga in order to get it to run longer than a few minutes.

---

