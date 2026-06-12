---
title: "I messed up gfx on Intrepid Ibex!"
date: 2008-12-14
forum: Multimedia Software
---

### Post by f76 on 2008-12-14
Really messsed it up i think. After an update of my Intrepid Ibex runnin on an Aspire 5920g with Geforce 8600m GT i lost gfx acceleration. So I tried to reinstall nvidia drivers to no avial. 

Can anyone help me get the acceleration working again - i would hate to have to reinstall everything from scratch!

Then i really messed up by(don't do this):
```

sudo apt-get remove nvidia*
```

And I just cant seem to get gfx acceleration to work again. 

This is my xorg.conf:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Thanx!!

---

### Post by f76 on 2008-12-16
really need this help! I should have found a guide when gfx acceleration stopped working after update, but now Im stuck here!

---

### Post by f76 on 2008-12-19
bump ;) pls!

---

