---
title: "Ubuntu server, when Wake on Lan is preformed, cannot power off laptop"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by Melclic on 2011-08-01
Hello all,

I have just installed ubuntu server 10.04 LTS on a laptop, and I would like to control it remotely.

When I manually turn on the computer I can successfully use SSH commands to turn it off. But when I wake on lan turn it on, it doesn't power off. It hangs on a black screen where the fan and the hard drive seem to be off, but the ethernet light is on and so are all the computer lights.

I have tried a lot of different methods such as apci=off and none have been successful. 

Any help would be greatly appreciated, thanks

---

### Post by Melclic on 2011-08-02
Hello,

I have installed turnkey which is based on Ubuntu 10.04 LTS I think. 

I have this weird behaviour/ Whenever I turn the computer on using wake on lan feature, when I then turn the computer off (whatever the method; meaning ssh or actually pressing the power button) the computer starts to turn off and then either hangs on a black screen with all lights flashing or it stops at " now will halt".

Any help would be appreciated

---

### Post by Melclic on 2011-08-03
Updates:

I have tried to suspend, hibernate the computer after WOL and still no luck. 

Does anyone have an idea of what could be the problem?

Could it be a BIOS issue?

---

### Post by Melclic on 2011-08-03
Update:

I have tried to suspend or hibernate after I WOL but both have the same issue.

Could anyome help?

Could it be a BIOS issue?

---

### Post by pqwoerituytrueiwoq on 2011-08-03
to use wake on lan a system never enters a true off state
for the system to shut completely off wake on lan will not work
i am surprised a laptop has a wake on lan option

---

### Post by Iowan on 2011-08-03
Threads merged...
From Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.

---

### Post by Melclic on 2011-08-04
sorry about multiple posting. I thought it might of been a network issue but I wasn't sure.

my laptop is a Toshiba satellite pro U300 and it dies support WOL

I don't think you understand what is going on pqwoerituytrueiwoq so I will go step by step through the two situations:

1) When I manually turn on my computer I can then shut it off completely, hibernate or suspend it through whatever method (ssh, webmin, manually)

2) When I turn on my compute on from any of the states (complete shutdown, hibernate or suspend) using WOL. Then I cannot power off the laptop completely. It goes throught the steps of powering down, but then the computer stays with all lights flashing (ethernet, power etc....)

Could anyone tell me where to look to for the error?

---

### Post by pqwoerituytrueiwoq on 2011-08-04
maybe a bios update will help
i cant find your laptop on the manufactures site to link you to the update
i don't see how shut down would be affected based on how it was booted
you can get your current bios version with this command to see if there is a update
```
sudo hwinfo --bios | less
```

---

### Post by Melclic on 2011-08-04
I got it fixed from the turnkey forum thanks to Jeremy's help. 

I already updated the BIOS and I went to the realtek website and downloaded the appropriate driver

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I followed the README and disabled the old module using:

```

rmmod r8169 
```The installation replaced the old driver which was strangely exctly the same and that did it. I can now shutdown my laptop using this line in ssh even if I have just performed WOL

```

Shutdown -h now
```Thanks for your attention and help

PS: I don't know how to mark a thread SOLVED

---

