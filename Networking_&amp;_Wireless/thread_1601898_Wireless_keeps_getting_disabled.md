---
title: "Wireless keeps getting disabled"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by dEM3NZI4! on 2010-10-20
I got the [same problem]("http://ubuntuforums.org/showthread.php?p=10000774") but the O.S is Ubuntu 10.4. I'm not a Expert but, I try all that already found on Internet Forums. I start the session  and wirless device is "disabled", same problem, by clicking right button and put the ticket to wirless device the problem is solved, I can connect by WIFI.

The problem is when I reboot the machine and the wirless lan is "Disabled" Again, WTF. I don´t have connman installed like the bug report. But the problem is the same. Others forums recomends me change this line on** nm-system-settings.conf**
-----------------------------------------------------------------------------
[ifupdown] managed=false

**for this**

[ifupdown] managed=true

**and then:**

sudo killall nm-system-settings
-----------------------------------------------------------------------------
and reboot the machine now the NM is work better than ever, Bla, bla that 
don't work to me

but console says that the process is not found or in spanish
PROCESO NO ENCONTRADO.

I wrote on the console..
---------------------------------
Sudo killall nm-applet
---------------------------------
closed the NM ,reboot but nothing...:confused:

I hope any can help me with this..
Best Regards from Chile

dEM3NZI4!

---

### Post by akoskm on 2010-10-20
> **dEM3NZI4! said:**
> I got the same problem but the O.S is Ubuntu 10.4. I'm not a Expert but, I try all that already found on Internet Forums. I start the session  and wirless device is "disabled", same problem, by clicking right button and put the ticket to wirless device the problem is solved, I can connect by WIFI.

The problem is when I reboot the machine and the wirless lan is "Disabled" Again, WTF. I don´t have connman installed like the bug report. But the problem is the same. Others forums recomends me change this line on** nm-system-settings.conf**
-----------------------------------------------------------------------------
[ifupdown] managed=false

**for this**

[ifupdown] managed=true

**and then:**

sudo killall nm-system-settings
-----------------------------------------------------------------------------
and reboot the machine now the NM is work better than ever, Bla, bla that 
don't work to me

but console says that the process is not found or in spanish
PROCESO NO ENCONTRADO.

I wrote on the console..
---------------------------------
Sudo killall nm-applet
---------------------------------
closed the NM ,reboot but nothing...:confused:

I hope any can help me with this..
Best Regards from Chile

dEM3NZI4!

Your problem is a bit different from what is being discussed here.
I suggest you to open a new post under Networking section.

---

### Post by Iowan on 2010-10-20
Moved to new thread.
Original: [http://ubuntuforums.org/showthread.php?p=10000774]("http://ubuntuforums.org/showthread.php?p=10000774")

---

### Post by dEM3NZI4! on 2010-10-20
> **akoskm said:**
> Your problem is a bit different from what is being discussed here.
I suggest you to open a new post under Networking section.

Any help?

---

