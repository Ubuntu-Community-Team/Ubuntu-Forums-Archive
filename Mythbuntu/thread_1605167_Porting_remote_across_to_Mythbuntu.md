---
title: "Porting remote across to Mythbuntu"
date: 2010-10-25
forum: Mythbuntu
---

### Post by Epiphyte on 2010-10-25
I am seriously considering putting Mythbuntu onto an older HMC MythTV machine. This came with a proprietary IR remote control.

Can anyone suggest what files I need to preserve/save to have some hope of getting this working under Mythbuntu?:confused:

All comments will be well received.

Thank you in advance.

---

### Post by azmyth on 2010-10-25
Really tough to say without more info like how old, what distro and what rev of MythTV. Is it the system currently running so you can see what mods are loaded. IMO, the thing you'll mostly have to worry about is the driver for the remote. If it's some remote that needs a special driver compiled could cause some issues if you try compiling on a new rev of linux. Could do a lsmod | grep lirc or just a straight lsmod to see what's there. For sure, I'd save the lircd.conf file and the .lircrc file.

---

### Post by Epiphyte on 2010-10-25
Thanks azmyth.

I'll post any interesting results here. My preliminary look tells me the remote is unusual.

More to follow........... :-|

---

### Post by Epiphyte on 2010-10-25
BTW, what is the command to get a list of my h/w config as well?

---

### Post by nickrout on 2010-10-25
> **Epiphyte said:**
> BTW, what is the command to get a list of my h/w config as well?

lshw
dmidecode

Also save everything in /etc/lirc and ~/.lirc/

---

### Post by LowSky on 2010-10-26
hopefully you can open a terminal on the older machine. 
type 
```
irw
```

the results will tell you what type of remote it is.
and we can the check to see if it is normally supported.

---

### Post by Epiphyte on 2010-10-26
LowSky:

I get "irw 0.7.0-CVS". Is that the driver version?

What now?

---

### Post by LowSky on 2010-10-26
sorry I'm an idiot and forgot to mention type irw, then hit a few buttons on the remote... the output will then tell you the remote model...

my bad

---

### Post by Epiphyte on 2010-10-26
Hi LowSky:

It gave me "d1ldo" (yes, truly !) This is a D1 "special", I think.

I have seen this source in poking around. Which files should I save for my Mythbuntu m/c?

---

### Post by LowSky on 2010-10-27
i found this link
[http://mysettopbox.tv/phpBB2/viewtopic.php?t=6232&start=45&sid=22aeb7127b43c9a0abf1e0381f1fed64](http://mysettopbox.tv/phpBB2/viewtopic.php?t=6232&start=45&sid=22aeb7127b43c9a0abf1e0381f1fed64)

the remote dose exist and its kinda old yu can try saving the old lirc file like nickrout said and maybe it will work. but no way to really confirm

if you can just type irw in a terminal on the new running machine and see if it works.. if not try porting the lirc files form the older machine over to the new one

---

### Post by Epiphyte on 2011-01-04
Thanks to nickrout and LowSky.

Solved by Mark in Melbourne. :D

---

