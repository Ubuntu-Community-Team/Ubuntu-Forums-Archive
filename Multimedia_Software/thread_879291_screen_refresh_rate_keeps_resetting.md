---
title: "screen refresh rate keeps resetting"
date: 2008-08-03
forum: Multimedia Software
---

### Post by kiyiko on 2008-08-03
every time i restart my computer, my resolution is set to 1024x768 89hz interlaced
every time i have to go into my "nvidia x server panel" and set it to 85hz

i was directed to a thread that told me to edit xorg.conf
[http://ubuntuforums.org/showthread.php?t=472756](http://ubuntuforums.org/showthread.php?t=472756)
but the lines i am suposed to edit arent there.

> If you want those specifically, then in the "screen" section of your xorg.conf, add _<refresh> to each mode where it's listed.

So if you have a line under the 24 bit color depth that looks like:

```
"1280X1024" "1152X864" "1024X768"....
```

Change them to:
```
"1280X1024_65" "1152X864_75" "1024X768_85" and so on.
```

but this is what i have under screen
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection
```
nvidia 6200

---

### Post by overdrank on 2008-08-03
Hi and are you using the nvidia settings as root ```
gksu nvidia-settings
```

---

### Post by kiyiko on 2008-08-03
i was not, but it was still changing my resolution/refresh rate
will try that, and post back, if it stayed as i set it, or not

did not make any difference
it is still restarting at 1024x768 89hz

like i think i need to change the xorg.conf because it it restarts with the settings in "screen resolution" setting, not nvidia settings
but the only refresh rates it lets me choose are
102
89
60
59
58
57
56

---

### Post by overdrank on 2008-08-04
> **kiyiko said:**
> i was not, but it was still changing my resolution/refresh rate
will try that, and post back, if it stayed as i set it, or not

did not make any difference
it is still restarting at 1024x768 89hz

like i think i need to change the xorg.conf because it it restarts with the settings in "screen resolution" setting, not nvidia settings
but the only refresh rates it lets me choose are
102
89
60
59
58
57
56

Ok you set it in nvidia settings and it changed in the screen resolution. But did it change in nvidia settings? The nvidia settings will show a different refresh rate then screens and graphics. Or am I totally not understanding :)

---

### Post by kiyiko on 2008-08-05
"screen resolution" and "nvidia x server" show different refresh rates in it.
i have to set the refresh rate, and resolution in "nvidia x server" but the setting in "screen resolution" do not change, ant when restarted, it reverts back to that
i have tired to have nvidia save the setting in xorg.conf, fut it gives an error, saying it is unable to create a backup, and it makes no changes

---

