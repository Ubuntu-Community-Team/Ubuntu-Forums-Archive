---
title: "Vino-preferences advanced options in Jaunty"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Zerocool3001 on 2009-05-21
Since Jaunty removed the "Advanced" settings from vino-preferences, I was wondering how to change some of the settings found there (most importantly the port used). I'm trying to connect to an Ubuntu box from Mac OS 10.5.7 and I need to set the port. I would use gconf, but I can't seem to find any guides for editing %gconf.xml. Any help would be appreciated.

---

### Post by AlanB66 on 2009-06-04
I tried adding these lines ...
[INDENT]<entry name="alternative_port" mtime="1216949631" type="int" value="5969"></entry>
<entry name="use_alternative_port" mtime="1216751966" type="bool" value="true"></entry>[/INDENT]

... but the new Vino will not swallow them properly. Still hacking away.

---

### Post by AlanB66 on 2009-06-04
Solved!

First, edit the %gconf.xml file adding the lines I displayed in my last post.

Next, open the Gnome Configuration Editor: gconf-editor

Proceed to **desktop -> gnome -> remote_access**

Place a check in the box for: **use_alternative_port**
Also, change the port to the value of your liking by double-clicking on **alternative_port **and changing the last two digits to any number between 01 and 99 (use two digit notation).

Close the Gnome Configuration Editor and re-try your VNC connection to the port you prefer (e.g.: jaunty:69)

---

### Post by diablo75 on 2009-06-13
> **AlanB66 said:**
> Solved!

First, edit the %gconf.xml file adding the lines I displayed in my last post.

Next, open the Gnome Configuration Editor: gconf-editor

Proceed to **desktop -> gnome -> remote_access**

Place a check in the box for: **use_alternative_port**
Also, change the port to the value of your liking by double-clicking on **alternative_port **and changing the last two digits to any number between 01 and 99 (use two digit notation).

Close the Gnome Configuration Editor and re-try your VNC connection to the port you prefer (e.g.: jaunty:69)

I've had luck with your instructions, except I did not have to edit any xml files.  I only opened gconf-editor, checked off the use-alternate box and edited the value for the alternative port to the desired port number.  Thanks!!

---

