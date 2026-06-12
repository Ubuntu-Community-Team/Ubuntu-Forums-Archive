---
title: "WinTV HVR 950 Q causes overheating"
date: 2011-01-01
forum: Multimedia Software
---

### Post by tafnyc on 2011-01-01
[SIZE=3]I have configured Kaffeine to work with my Hauppauge WinTV HVR 950Q USB device, and am able to get channels scanned, and can get sound, video from channels, etc. However, its use overheats my laptop to the degree it literally shuts down- turns off! Any suggestions? It took some effort to get this to work in Ubuntu 10.10; however, if it heats up the laptop to this degree what good is it?!
Any helpful suggestions would be most appreciated.
Regards,
tafnyc
[/SIZE]

---

### Post by gordintoronto on 2011-01-01
What laptop? What CPU?

Most people use a desktop as a MythTV back end.

---

### Post by tafnyc on 2011-01-04
[B]CPU: AMD Turion (tm) 64 x 2 Mobile Technology TL-60
Gateway Model : W350A
2.3 GB Memory[/B]

---

### Post by gordintoronto on 2011-01-04
Issue 43 of Full Circle Magazine includes my article on installing lm-sensors in the Q&A column. You might install lm-sensors to get more information.

The TL-60 uses only 35 watts, so I am surprised that it makes that much heat.

2.3 GB of memory is not a reasonable number. Could you run the commands:
sudo lshw >myconfig.txt
gedit myconfig.txt

and tell us what it says about memory? For example, on my computer:
id:	memory
description: 	System Memory
physical id: 	25
slot: 	System board or motherboard
size: 	4GiB

Then there is more about the memory installed in each slot.

---

