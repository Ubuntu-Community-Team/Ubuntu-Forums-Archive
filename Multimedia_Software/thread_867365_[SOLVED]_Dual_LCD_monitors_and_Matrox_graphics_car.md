---
title: "[SOLVED] Dual LCD monitors and Matrox graphics card"
date: 2008-07-22
forum: Multimedia Software
---

### Post by TonyUb on 2008-07-22
Folks,

I have dual Samsung SyndMaster 191T LCD monitors connected via DVI cable to a Matrox Milennium G550 graphics card.

When installing Ubuntu will it recognise this arranagement or are there certain things I will need to do to get the monitors working?

Please advise.

Thanks and regards,


Tony

---

### Post by overdrank on 2008-07-22
> **TonyUb said:**
> Folks,

I have dual Samsung SyndMaster 191T LCD monitors connected via DVI cable to a Matrox Milennium G550 graphics card.

When installing Ubuntu will it recognise this arranagement or are there certain things I will need to do to get the monitors working?

Please advise.

Thanks and regards,


Tony
Hi and welcome, you may try the command using the alt, F2 ```
gksu displayconfig-gtk
```
and adjust your monitors and resolution there.
I have not had the pleasure of using that graphics card but have seen users that have had success.

---

### Post by TonyUb on 2008-07-22
> **overdrank said:**
> Hi and welcome, you may try the command using the alt, F2 ```
gksu displayconfig-gtk
```
and adjust your monitors and resolution there.
I have not had the pleasure of using that graphics card but have seen users that have had success.

Thanks for the information. Greatly appreciated.

---

### Post by DCKelley on 2011-05-29
> **Ringi said:**
>  (in a similar thread)
Try gksu displayconfig-gtk
see if your monitor is supported,
if not choose Generic
and resolution that your monitor supports.

When I use gksu displayconfig-gtk the command prompt returns with nothing else. If I use --help it will pause  a moment  and I see a process called "Starting admin.." but still nothing. What's up?

I am trying to get a dual monitor working for a Matrox card,  on Ubuntu 11.-4 the device is:
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G550 AGP (rev 01)

System->Prefs->Monitors shows only the single monitor, and currently both screen show the same image.  I do not see a way to "chose generic" but perhaps another dialogue is what is meant in the above. 
/etc/x11/ does not seem to have a config file, and I do not have any private drivers loaded.

As Unbuntu newbie I am somewhat clueless how to proceed, but the inablity to run displayconfig has me stumped.

---

