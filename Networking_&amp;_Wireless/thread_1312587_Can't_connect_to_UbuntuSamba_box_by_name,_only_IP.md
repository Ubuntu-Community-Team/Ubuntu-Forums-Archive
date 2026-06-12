---
title: "Can't connect to Ubuntu/Samba box by name, only IP"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by ml_nelson on 2009-11-03
[COLOR=black][FONT=Verdana]The Ubuntu box running Samba can ping any of my Windows machines just fine.[/FONT][/COLOR]
 
[FONT=Verdana][COLOR=black]Problem is the other way around... The Windows boxes can't ping the Ubuntu box by name. They can ping it only by IP. In fact, I can even connect to & view files using the IP address, but not the name.[/COLOR][/FONT]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]I changed the name of the Ubuntu & it was immediately pingable by name.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I turned everything off for the night. Next day, problem is back. I can only ping the Ubuntu box by IP, not by name. [/FONT][/COLOR]
 
[FONT=Verdana][COLOR=black]I tried changing the name again, just one letter & restart the Ubuntu box. Windows can then see & ping it by name.[/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]If I turn the computers off for some hours, & restart... The problem returns![/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]How do I get Windows to reliably find the Ubuntu box by name?[/COLOR][/FONT]

---

### Post by pedro_orange on 2009-11-03
Add the ubuntu box's hostname to /system32/drivers/etc/hosts (On your windows box!)

I imagine your Windows Box is trying to use NetBIOS to resolve the name of the Ubuntu box, but it's not responding to it.

Adding it to the hosts file will make life a lot easier

---

### Post by ml_nelson on 2009-11-03
> **pedro_orange said:**
> Add the ubuntu box's hostname to /system32/drivers/etc/hosts (On your windows box!)
 
 
Adding it to the hosts file will make life a lot easierActually that file want the host name & IP. .....So what is the IP address is not fixed? This doesn't work.
 
Is there not some way to get the name automatically recognized by the Windows boxes?

---

### Post by Iowan on 2009-11-03
Check [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To... see problem 3 part 2. That may be the other-way-around.

---

### Post by ml_nelson on 2009-11-03
> **Iowan said:**
> Check [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To... see problem 3 part 2. That may be the other-way-around.
"other way around" is the issue. The link is how to fix the opposite of my problem. I need... **[COLOR=#ff0000][B][COLOR=#ff0000]Windows[/COLOR]**[/COLOR][/B] **[COLOR=#ff0000]is[/COLOR]** **[COLOR=#ff0000]unable[/COLOR]** **[COLOR=#ff0000]to[/COLOR]** **[COLOR=#ff0000]browse[/COLOR]** **[COLOR=#ff0000]Ubuntu[/COLOR]** **[COLOR=#ff0000]host[/COLOR]** [COLOR=#ff0000]**names**[/COLOR][COLOR=#000000], but that is not what the link is about. [/COLOR]

---

### Post by Iowan on 2009-11-03
Another suggestion that probably won't help... if connection is via DHCP, edit */etc/dhcp3/dhclient.conf* and add hostname to the line:```
send host-name "<hostname>";

```

---

### Post by ml_nelson on 2009-11-03
> **Iowan said:**
> Another suggestion that probably won't help... if connection is via DHCP, edit */etc/dhcp3/dhclient.conf* and add hostname to the line:```
send host-name "<hostname>";

``` **[COLOR=darkred]Actually.... That works![/COLOR]** **Windows boxes find the Ubuntu machine without fail.**
 
Thanks much,
Mike

---

### Post by Iowan on 2009-11-04
GREAT!!! Mark this one [SOLVED] (under Thread Tools).

---

