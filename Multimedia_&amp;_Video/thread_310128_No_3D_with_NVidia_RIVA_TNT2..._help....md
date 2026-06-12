---
title: "No 3D with NVidia RIVA TNT2... help...?"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by splashtech on 2006-11-30
Hi, I'm hoping someone can help me.

I've got an old NVidia RIVA TNT2 card, and I've got fed up of having worse than useless 3D support using the 'nv' driver. However, since installing the proper nvidia driver, (the legacy one, to be exact), 3D doesnt work at all! All the openGL screensavers just show up in the small preview box as a black box and nothing else, and in the full screen preview as nothing (i.e. a blank cream screen).

I have installed the nvidia-glx-legacy drivers, and all the dependancies which came along with that. Also, having done some searches (in order to solve this for myself), I came up with having to change the driver line in xorg.conf to 'nvidia' rather than 'nv', which I have done. Also, some sources suggested the following:

- disable 'Load dri' -- this I have done -- makes no difference
- adding this line:
```
Option		"RenderAccel" "true"
``` -- makes no difference


All relevent sections of xorg.conf are shown below:
```

...
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
...
Section "Device"
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"NoLogo" "True"
	Option		"RenderAccel" "true"
EndSection
...

```

I have attached the whole xorg.conf file in case you need it.

Sorry to ask for help like this, but I am sure I have done everything correctly. Can this rubbish card simply not do 3D at all?!


**Edit:** forgot to say, this is on Edgy (6.10).

---

### Post by crazedgremlin on 2006-11-30
try installing nvidia-glx instead of the legacy package

---

### Post by splashtech on 2006-11-30
I'll give it a shot, but everywhere I've seen suggests that this is the correct one for this card.

---

### Post by splashtech on 2006-11-30
Update: I just tried that, and X would not even start, complaining about a mismatch in kernal module version vs x module version, or something along those lines... I had to re-'apt-get install nvidia-glx-legacy' from recovery mode to get X back...:confused:

---

### Post by tseliot on 2006-11-30
You need to disable composite.

Read Method 1 of my guide (and keep using the legacy driver):
[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

---

### Post by splashtech on 2006-11-30
> **tseliot said:**
> You need to disable composite.

Read Method 1 of my guide (and keep using the legacy driver):
[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

Thanks for your reply... but I don't know if I'm being stupid or something, but I've read through your guide (the one at: [http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_1](http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_1)) and I cant find the part to disable composite. Could you point me at what I should be doing please?:)

---

### Post by crazedgremlin on 2006-11-30
> **splashtech said:**
> Update: I just tried that, and X would not even start, complaining about a mismatch in kernal module version vs x module version, or something along those lines... I had to re-'apt-get install nvidia-glx-legacy' from recovery mode to get X back...:confused:


:( Sorry:( 

just a guess

---

### Post by splashtech on 2006-11-30
> **crazedgremlin said:**
> :( Sorry:( 

just a guess

That's ok. Thanks for your input anyway. I guess we learn from these little mistakes, its the thought which counts. :) :biggrin:

---

### Post by splashtech on 2006-11-30
Well I found out how to disable composite... thanks **tseliot** :) 

I added the following:
```
Section "Extensions"
     Option     "Composite" "false"
EndSection
```
to my xorg.conf underneath the 'modules' section, and logged out and restarted X. It now works perfectly (well as good as you'll get for a 8 year old or whatever card).

Excellent. :) Thanks to everyone for their help. :cool:

---

### Post by RJARRRPCGP on 2006-12-02
That video card can do 3D, AFAIK. If it can't, it probably is because of a driver problem.

---

### Post by splashtech on 2006-12-02
> **RJARRRPCGP said:**
> That video card can do 3D, AFAIK. If it can't, it probably is because of a driver problem.

Yeah, it can. My last post said I got it working. :)

---

