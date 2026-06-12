---
title: "HP Pavilion dv6 series Wireless won't turn on"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by JerecDrak2 on 2009-05-30
Hi guys,

My girlfriend recently bought a new laptop and after installing Jaunty everything works great aside from the wireless. It has an Atheros AR9285 chip inside, which I'm sure the ath9k driver supports, however the wireless refuses to work. I have a suspicion that it's because the wireless chip is not switched on as the wireless indicator is red (switches to blue when it's on) Unfortunately when the wireless switch is touched (it's a touch sensitive thing) nothing happens. Here's the dmesg output below:

```
[  906.931189] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[  906.931203] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
```Does anyone know how to get the kernel to recognise the button?

Many thanks guys

---

### Post by ddrichardson on 2009-05-30
Trial and error.  Try starting with 159 and 158:```

sudo /usr/bin/setkeycodes e014 159
```

---

### Post by JerecDrak2 on 2009-05-30
Thanks, unfortunately that didn't work, can I just ask how you know which decimal numbers to try after the e014 bit?

Thanks.

---

### Post by ddrichardson on 2009-05-30
158 / 159 work for the ath5k wireless in the Aspire.  Trial and error, unless Googling for the keycodes.

---

### Post by JerecDrak2 on 2009-05-30
Well I went through all the blank keycodes that the dumpkeys command gave but no joy :( Does anyone have any other ideas? It's so frustrating that everything works flawlessly aside from this one critical feature!

---

### Post by JerecDrak2 on 2009-05-31
Well after much toiling I decided to install Fedora 11 on the laptop and the wireless works fine! So it must just require an updated kernel or something, hopefully Karmic will work properly on it.

Thanks for the help though.

---

### Post by TimStovall on 2009-11-14
I recently got a new HP Pavilion dv6 and installed Ubuntu 9.10 (Karmic).  When first installed the wireless internet would not work.  Wired Internet worked fine.  I had to find several sources to get the wireless working, and would like to consolidate the process here.

For a freshly installed version of 9.10, the sudo apt-get install commands did not work, I would get the "E: Couldn't find package" error message.  This was fixed by following the instructions at [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php) .

Next I followed the directions at
 [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp) 
to get the correct driver.  These instructions need to use the apt-get install command previously fixed above.

Once this was updated, I went to System>Administration>Hardware Drivers.  Here I selected the Broadcom STL wireless driver.  Previously the Broadcom b43 driver was selected and this did not support the wireless chip in my HP dv6.  After switching to the STL driver and a restart, the wireless was working.  

The blue/orange wireless toggle switch worked since I installed Ubuntu, even when wireless was not working.

Hope this helps.

---

### Post by bh4714 on 2009-12-02
Hi - I'm newly converted to Ubuntu.
 
I have an HP dv6 - 1210sa with Karmic installed. Everything works perfectly except the wireless toggle switch. When I initially power up the machine, it is on by default and the wireless works perfectly. However, if I touch the switch off, I cannot turn it back on without restarting the machine. 
 
I imagine it is an isue with the switch driver. Does anyone have a solution/ know where to get the correct drivers?
 
Many thanks

---

