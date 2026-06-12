---
title: "No Panels with Alpha 2"
date: 2011-02-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mildenhall on 2011-02-04
I upgraded to Alpha2 and I have no Panels. Fortunately I use Docky so can access some apps, however it's going to be interesting finding other apps until I can show the main panel.

Anyone know how I can display the main panel please? TIA

On the plus side, the intel drivers have been upgraded and unity does not report errors with my graphics card any more.

---

### Post by Quackers on 2011-02-04
Same here after installing 3D experimental driver. It was ok until I ran updates. Just an empty desktop now, apart from cairo dock.

---

### Post by xgt001 on 2011-02-04
they have acknowledged this bug already and you might find the link for the fix here
[http://www.ubuntu.com/testing/natty/alpha2](http://www.ubuntu.com/testing/natty/alpha2)

best of luck and happy testing!!

---

### Post by farooq23 on 2011-02-04
Hi,

Any solution for this issue. I am having a nvidia 210 graphics card

---

### Post by cariboo on 2011-02-04
I'm posting from one of my testing installs, fully updated to alpha2 running the nouveau drivers and libgl1-mesa-dri-experimental, Unity runs OK, ram usage seems a bit high though.

---

### Post by Quackers on 2011-02-04
Cariboo907, that same driver is shown as installed in my alpha2 install. Is that the experimental 3D driver that Additional Drivers picks up? I can't get normal Unity or compiz to run with it :-(

---

### Post by cariboo on 2011-02-04
This install is has been used since shortly after the tool chain was uploaded, it's always run the experimental library, It has all the Xorg updates installed. Yesterday after updates I got the same as you are experiencing, but after more updates this morning Unity now works, but if ram usage stays high high, I may have to put some ram in there.  Currently only chromium and synaptic are running, and it's using 428MB ram, and into swap for about 150MB.

It looks like synaptic may be the problem, after closing it ram usage dropped to 178MB.

System specs are:

Celeron 2.6Ghz
512MB ram
AGP Nvidia 6600GT
40GB hard drive

---

### Post by Quackers on 2011-02-04
Thanks cariboo907.
I have another problem in another thread and I think I'll re-install alpha2 and see if the new updates allow me to use the desktop edition this time. I may possibly have a user problem and I'd like to clear that up before I delve any further into problems. Probably the wise thing to do, I think.

---

### Post by cariboo on 2011-02-04
I posted in the other thread too.

---

### Post by mc4man on 2011-02-04
> **cariboo907 said:**
> 
AGP Nvidia 6600GT
40GB hard drive
So it does appear some nvidia cards will run A2 with nouveau 3d, none here will, all w/ same error in compiz  (pci-e cards 

compiz assert failure: compiz: nv50_pc_emit.c:863: emit_flop: Assertion `STYPE(i, 0) == 0x09' failed

Will have to try with a AGP card (7800

---

### Post by mc4man on 2011-02-06
> **mc4man said:**
> So it does appear some nvidia cards will run A2 with nouveau 3d, none here will, all w/ same error in compiz  (pci-e cards 

compiz assert failure: compiz: nv50_pc_emit.c:863: emit_flop: Assertion `STYPE(i, 0) == 0x09' failed

Will have to try with a AGP card (7800

nouveau 3d does work here (full A2+ updated), when using an AGP card (7800), though not at all yet with pci-e cards (8000 and 9000 series
(still prefer nvidia drivers

---

