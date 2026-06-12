---
title: "C-1501's own remote"
date: 2009-01-17
forum: Mythbuntu
---

### Post by ikke2808 on 2009-01-17
Hi all,

I've got a TechnoTrend C-1501 including it's own remote. 
I got the remote working, but not all keys...
The numbers are ok and volume up and down, the arrow keys work, but OK, text and exit not.

I maybe found something when I do 'xinput list':
"Budget-CI dvb ir receiver saa7146 (0)"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

The keys that do not work have a code that exceeds 255...which is the Max_keycode...
Is this coincidence? Can I increase this number?
I tried with xinput but that does not change anything. Where in the X conf files I can set this? 

Or if I am totally took the wrong road here please tell me! 

Cheers.

---

