---
title: "Benq wireless internet problem"
date: 2005-02-21
forum: Networking &amp; Wireless
---

### Post by A_deeper_blue on 2005-02-21
first problem:

I have a Benq awl 300 usb wireless internet adapter
but haven't got a linux driver for it... after some googling I found out that it probably is a Atmel AT76C502/3/5A based wireless USB device since it's listed in the table here 
[http://at76c503a.berlios.de/devices.html](http://at76c503a.berlios.de/devices.html)

now since I can only connect to the internet via windows xp
it's giving me a hard time to install it (only one pc here atm)

so I tried to compile the driver on that site but it couldn't find GCC it's a fesh installation.. so I downloaded a deb package
at76c503a-source.deb
and 
atmel-firmware.deb

and dit 
dbpkg -i atmel-firmware.deb
dbpkg -i at76c503a.deb

and it seemded to install without errors...
but now what...

(I have installed ubuntu from the latest warty installation cd)



could you please tell me if I have the correct driver
and which steps I should take to connect from this point on

ps. there are 2 wireless networks near, but only one is accessible since the other one is restricted to certain mac adresses

thanks in advance

---

### Post by lao_V on 2005-02-28
GCC is not installed by default under Ubuntu I think. You will have to manually install it from synaptic along with gcc-3.4 or any other version.

---

### Post by alastair on 2005-02-28
[QUOTE=A_deeper_blue]first problem:

I have a Benq awl 300 usb wireless internet adapter
but haven't got a linux driver for it... after some googling I found out that it probably is a Atmel AT76C502/3/5A based wireless USB device since it's listed in the table here 
[http://at76c503a.berlios.de/devices.html](http://at76c503a.berlios.de/devices.html)

now since I can only connect to the internet via windows xp
it's giving me a hard time to install it (only one pc here atm)

so I tried to compile the driver on that site but it couldn't find GCC it's a fesh installation.. so I downloaded a deb package
at76c503a-source.deb
and 
atmel-firmware.deb

and dit 
dbpkg -i atmel-firmware.deb
dbpkg -i at76c503a.deb

and it seemded to install without errors...
but now what...

(I have installed ubuntu from the latest warty installation cd)



could you please tell me if I have the correct driver
and which steps I should take to connect from this point on

ps. there are 2 wireless networks near, but only one is accessible since the other one is restricted to certain mac adresses

thanks in advance[/QUOTE]
 If you use synaptic, "search" for "at76c503a" - then look at properties for it  and "installed files".

It has probably installed under /usr/src somewhere - there should  be a README in there as well.

For compiling - try installing the "build-essential" package - it should pull in everything you need to compile/build programs.

---

