---
title: "Can you please put a Power OFF button the FrontEND?"
date: 2008-03-17
forum: Mythbuntu
---

### Post by rictec on 2008-03-17
Can you please put a Power OFF button the FrontEND?
just a simple way for me to power down the sistem with the remote control like a TV

Thank you

---

### Post by ian dobson on 2008-03-18
Hi,

On my system when I press the right arrow button in the main menu MyhTV brings up a small window with the opton Continue, Stop MythTV or Shutdown computer.

You need to configure the shutdown command in the myth setup and from what I can remember allow everyone to run poweroff (something to do with sudousers).

Hope this helps 
Regards
Ian Dobson

---

### Post by laga on 2008-03-18
> **ian dobson said:**
> 
You need to configure the shutdown command in the myth setup and from what I can remember allow everyone to run poweroff (something to do with sudousers).


We'll try to make this mostly preconfigured in Mythbuntu 8.04..

---

### Post by zagor on 2008-03-19
You can edit the mainmanu.xml file and create a button "power off".
Check [this ]("http://www.knoppmythwiki.org/index.php?page=MythMenuChanges") link.

Add at the bottom a menu entry such as:

```
   <button>
     <type>SHUTDOWN</type>
     <text>Power Off</text>
     <action>EXEC /usr/bin/sudo halt</action>
   </button>
```

Also, edit the sudoers:
```
# sudo visudo
```

And add at the bottom
```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /sbin/halt
```

Note that this must be the only item related to the mythtv group.

Hope it helps.
I did like this (also a reboot button) but didn't know about the trick noted by Ian. That would be much simpler, but much less intuitive (or children-compatible, if you wish...) than adding a clear and simple button in the mainmenu.

---

### Post by spalVl on 2008-03-19
I recall with MythtTV .21 there is now an option to add a "Exit & Power Off" and/or "Exit and Restart" command that to the exit frontend meu. (hitting esc/back)

---

