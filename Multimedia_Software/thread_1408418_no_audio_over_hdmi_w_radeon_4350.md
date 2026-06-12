---
title: "no audio over hdmi w radeon 4350"
date: 2010-02-16
forum: Multimedia Software
---

### Post by karrank% on 2010-02-16
Hope I'm posting in the right place.
Just installed an MSI Radeon 4350 on my 1st build with an AsRock A780full HD mobo. Patched thru my Pioneer receiver to our Vizio VX37L via the 4350's hdmi out and I get wonderful picture but no sound. Just installed the latest ATI drivers (v10.1 I believe)

Still no audio.

Any ideas where to start looking?

Thanks.

---

### Post by karrank% on 2010-02-17
anybody?

perhaps this is posted in the wrong place?

---

### Post by karrank% on 2010-02-18
and I already had disabled onboard audio in Bios.

---

### Post by 0br0k3n0 on 2010-02-18
eee i no this 1....



System--->Preferences--->Hardware. then click the one that says HDMI out :D

---

### Post by karrank% on 2010-02-18
thanks for looking, in my hardy system menu there is no hardware submenu. 

could you please elaborate? 

Thanks again.

---

### Post by karrank% on 2010-02-24
Solved, for anyone interested: 

System> Preferences>  ATI CCC (admin) 

select display in question

select Adjustments tab

under image options, select  Use graphics processor for scaling

Apply> OK
 
Close ATI CCC

Now audio comes through the hdmi out from your 4350 through to your home theater.

Obvious, wasn't it?

---

