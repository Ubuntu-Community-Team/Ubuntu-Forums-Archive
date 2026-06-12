---
title: "Via UniChrome Configuration"
date: 2008-06-23
forum: Multimedia Software
---

### Post by Uchiha_madara on 2008-06-23
hi Every One

I have Mother Board "VIA"
and installed Ubuntu hardy
then The Resolution is very bad
and The AGP is Build in "Unichrome" 

i need a method that to Configure it By Driver or Manually,

I Typed

> 
lspci


> 
lspci -v



> 
*From The Result :*

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)



> 


bebo@bebo-desktop:~$ lspci -v


01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA controller])
	Subsystem: Unknown device 3344:1122
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	


What Next ???? What shall I do??

---

### Post by Uchiha_madara on 2008-06-23
Please Help????

No One ???????


I ll be very sad

---

### Post by sim-value on 2008-06-23
Wait ... i once had this one (i still have it but have an AGP now) what did i do again ... *thinks*.... a wait i failed finding something usefull

---

### Post by gyterpena on 2008-07-19
Try this driver
[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220](http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220)
you might need to uninstall openchrome first.

---

