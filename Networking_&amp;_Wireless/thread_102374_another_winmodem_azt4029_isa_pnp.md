---
title: "another winmodem: azt4029 isa pnp"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by towsonu2003 on 2005-12-11
I have this aztech winmodem, and I cannot find up-to-date info on it in terms of drivers. scanModem does not work as it is an ISA modem... Should I email linmodems??? Maybe someone here knows something about this stuff below? any ideas & pointers appreciated... 

Here is info I was able to gather till now:

from dmesg:
isapnp: Card 'AZT4029 PnP MODEM CARD'
pnp: device 00:09 activated (not sure if this is talking about modem)
ttyS0 at I/O 0x3f8 (irq=4) is a 16550A (wvdial tries to get ttyS0 to work, but no luck)

from lspnp: 
/proc/bus/pnp not available (why, how?)

'aplay -l' (alsa player list) talks about 2 cards (refers to Yamaha)

On ISA winmodem list (from **2003** at [http://freewebhosting.hostdepartment.com/g/gromitkc/isa_list.html](http://freewebhosting.hostdepartment.com/g/gromitkc/isa_list.html) )
FCC ID or REG # is 4J2SNG-25073-M5-E
Marked as 'no report yet as whether it works with linux' (WM mark with red background)
chipset: TI (what's that?)

I am expecting **any** sort of help :) , any pointers (even about pnp / isapnp) or anythig you know... It could even be the up-to-date version of [http://freewebhosting.hostdepartment.com/g/gromitkc/isa_list.html](http://freewebhosting.hostdepartment.com/g/gromitkc/isa_list.html) :)

thanks so much in advance!

---

### Post by az on 2005-12-12
Aztech "Azmodem" Model MD6802-U, TI chipset (PNPID: AZT4029)
[http://65.70.147.202:8080/gromitkc/isa_list.html](http://65.70.147.202:8080/gromitkc/isa_list.html)


I never heard of any TI chipset modem working in linux.  TI are long gone from the modem business.

---

### Post by towsonu2003 on 2005-12-12
[QUOTE=azz]Aztech "Azmodem" Model MD6802-U, TI chipset (PNPID: AZT4029)
[http://65.70.147.202:8080/gromitkc/isa_list.html](http://65.70.147.202:8080/gromitkc/isa_list.html) [/quote]

thanks :) although that page is from 2003 (end of page) as well, I am guessing they are not updating the list anymore? 

[QUOTE=azz]
I never heard of any TI chipset modem working in linux.  TI are long gone from the modem business.[/QUOTE]
Well, the computer is almost out of business as well :) xubuntu is keeping the poor thing alive :) my wife is using it to play frozen-bubbles (for which I spent 4 hours to set up, those dependencies!!!) heheh :)

thanks so much for the reply :)

---

### Post by az on 2005-12-12
[QUOTE=towsonu2003]thanks :) although that page is from 2003 (end of page) as well, I am guessing they are not updating the list anymore? 
[/QUOTE]

I don't think much ISA hardware has been made since 2000.  2003 is pretty up-to-date.

---

